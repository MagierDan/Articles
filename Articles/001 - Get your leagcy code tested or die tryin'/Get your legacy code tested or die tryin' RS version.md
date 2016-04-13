Nos applications, lorsqu'elles sont utiles, doivent répondre à de plus en plus de besoins. Jusqu'à devenir énormes, gigantesque, "monstrueuses" :) 
Et c'est exceptionnel lorsque la couverture de test permet de refactorer et d'ajouter du fonctionnel sans crainte.
Commencer des développements sur des nouveaux besoins n'est pas forcément simple (même en TDD), mais lorsqu'il s'agit de refactorer ou modifier du code existant, celà devient très complexe. En effet, il ne faut surtout pas perdre le fonctionnement actuel, résultat de parfois plusieurs années de modifications ce qui conduit à un comportement implicite, non conforme à la documentation.

Il existe pourtant des techniques pour nous aider à tendre un filet de sécurité avant de refactorer une fonctionnalité non testée (ou pas assez) . Ces techniques, que je vais introduire ci dessous,  fonctionnent sur le principe de la boite noire : on a un jeu de données en entrées et on n’analyse que la sortie. C’est à dire que l’on va comparer les outputs produits entre différentes implémentations à partir d’un même input. Dans notre cas, il s’agit de comparer les résultats d’exécutions de la version de production avec ceux de la version en cours de réécriture/modification.
Ces méthodes vont surtout varier sur la façon dont on génère le jeu d’inputs.

(pour Dan : qu’est il des fonctions qui délèguent des appels vers l’extérieur. Exemple : un utilisateur de ton moteur de recherche se demande comment on découpe une tête avec un grand sabre, ton système a pour comportement : recherche, création fiche S,  affichage des résultats. Création fiche S n’est pas un output ici.)



Golden Master (GM)
——————
Ici, on sélectionne/génère préalablement un vaste jeu de données (1). On va stocker les résultats d’exécutions de la version « certifiée ». On va appliquer ces mêmes inputs à la version en cours d’écriture. On va ensuite comparer les différences. En fonction des différences, attendues ou non, on acceptera la version modifiée comme le nouveau GM ou on la corrigera. Ceci, jusqu’à ce que la nouvelle version soit acceptée.

Attention !!! En fonction de la granularité du système que vous testerez, vos états possibles pourront être si nombreux que le jeu d’entrées deviendra rapidement devenir énorme. La génération et surtout la maintenance de celui-ci peuvent rapidement engendrer des coûts prohibitifs. C’est pourquoi il sera préférable de n’utiliser ce genre de techniques que pour des refactoring rapides, 1, 2 ou 3 sprints, en n’embarquant aucune modification fonctionnelle.

(1) explique comment on génère, ou donne des exemples, selon ce que j’ai compris le RecordAndReplay est un sous ensemble du GM


Record and Play (RaP)
-------------
Autre technique: le Record and Play (RaP). Toujours dans le but de créer un harnais de tests, le moyen est ici d’enregistrer un ou des scénarii d’utilisation de l’application via une IHM. Puis de rejouer ces scénarii sur les deux plateformes et comparer les résultats.
Généralement, c’est Sélénium qui est utilisé pour enregistrer ces scénarii. 
Ces tests sont cependant assez fragiles car en plus du système sous-jacent, les résultats d’exécutions dépendent de l’IHM. Pour que les résultats soient exploitables, il faut donc figer l’IHM en plus du système à tester. Le nombre de personnes impactées par ce refactoring augmente. La difficulté aussi.

 Leur maintenance s'avère par ailleurs plus pénible que celle du GM. 
-> tu peux en dire plus ?
Il existe aussi d'autres outils payant qui permettent aussi de tester des applications desktop ou mobile, par exemple Ranorex.
-> soit tu en dis plus sur Ranorex (avantages, inconvénients) soit tu ne dis rien
Il est possible d'utiliser Sélénium autrement qu'en RaP et d'écrire du tests plus facilement maintenance.
-> à ce moment là, explique comment ?  
Je conseillerais dans ce cas la librairie Simplelenium.
-> pourquoi ?

Technique de Sequential Runs
-------------
Voici la dernière technique que j’aborderais dans ce le cadre de cet article, le Sequential Runs.
Commençons par un exemple : 
Lorsque GitHub a décidé de réécrire sa fonction de merge, il leur était impossible de prévoir à l’avance les différents cas qui allaient se présenter. Impossible donc de sélectionner des cas d’utilisation et de générer les inputs correspondants.
Le plus sûr était donc de comparer ce qui se passait sur la prod avec une version refactorée. Pour ce faire, il faut envoyer 2 implémentations d’une même fonctionnalité en production, une effective, l’autre dormante. 
Lorsque la fonctionnalité est utilisée, les inputs sont envoyés en parallèle aux deux versions. Les résultats des 2 exécutions sont enregistrés et comparés(4). Attention, seuls les résultats de la version legacy sont utilisées pour la suite de l’interaction avec l’utilisateur.

En comparant à chaque appel de la méthode de merge, les résultats obtenus par la version legacy et la version en cours de refactoring, il est possible de combler petit à petit les différences et de détecter les fonctionnements précisés ni dans les specs ni les tests. 
Au fur et à mesure de cette amélioration continue, les différences se sont amenuisées jusqu’à ce que la nouvelle version devienne la version de production. Ceci, sans que jamais les utilisateurs en pâtissent.
Je rappelle que lors de la phase de comparaison, la vérité est et reste le code legacy. Seule son exécution est prise en compte pour tout ce qui est traitement fait par l’utilisateur.
Lors de la bascule, il suffit de remplacer l’appel à l’ancien code par un appel au nouveau.

Pour en savoir plus sur la façon dont à procédé GitHub, je vous invite à lire cet article(2) présentant le framework Ruby nommé « Scientist » créé à l’occasion. Il faut signaler qu’un portage Java de ce framework existe et s’appelle « Experiment4J »(3) 


(2) source de l’article
(3) lien vers le framework
(4) en live ? a postériori ? les deux ? ça dépend du contexte ?

En conclusion, je pense que ces méthodes utilisant d’énormes quantités de tests, comportent quand même quelques risques au delà du coût de génération/sélections des inputs ou du surcout d’un double run. 
Plus la surface de tests sera grande, plus le risque de figer l’application sera grand (tests de comportements vs tests d’implémentation). Pour éviter cela, un travail de sélection en amont doit être très important, ou bien un travail de maintenance énorme.
Il faut donc être très vigilant sur la granularité et l’indépendance du système à tester, afin de pouvoir refactorer rapidement, sans gêner les autres. 
Enfin, ces tests, dans la plupart des cas, n’ont pas pour vocation d’être automatisés. En effet, une fois le refactoring terminé, on jette le tout à la poubelle et on repart sur du test classique afin que cette nouvelle version puisse vivre sa vie.