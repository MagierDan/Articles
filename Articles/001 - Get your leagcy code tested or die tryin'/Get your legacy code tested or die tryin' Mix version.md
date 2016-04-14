Aujourd'hui Nos applications répondent à de plus en plus de besoins, et ce jusqu'à devenir énormes, gigantesques, "monstrueuses" :).
Il est beaucoup trop rare d'avoir une couverture de tests permettant de refactorer et/ou d'ajouter du fonctionnel sans crainte.
Commencer des développements sur des nouveaux besoins n'est pas forcément chose simple (même en TDD), mais lorsqu'il s'agit de refactorer ou modifier du code existant, celà devient très complexe. En effet, il ne faut surtout pas perdre le fonctionnement actuel, qui est le résultat de parfois plusieurs années de modifications. Cela conduit à un comportement implicite de l'application, non conforme à la documentation, hélas devenue obsolète.

Il existe pourtant des techniques pour nous aider à tendre un filet de sécurité avant de refactorer une fonctionnalité non testée (ou pas assez) . Ces techniques, que nous verrons par la suite, se basent sur le principe que le code de l'application est une boîte noire : on a un jeu de données en entrée et en sortie. Le but sera de comparer les outputs produits entre différentes implémentations à partir d’un même input. Dans notre cas, il s’agira de comparer les résultats d’exécutions de la version de production avec ceux de la version en cours de réécriture/modification.
Ces méthodes vont surtout varier sur la façon dont on génère le jeu d’inputs.


Golden Master (GM)
-------------
Avant de refactorer/modifier le code de la version "certifiée" (en règle générale la production), on effectue les actions suivantes:
* on créé un vaste jeu de données (de manière aléatoire ou non)
* on passe à la méthode à modifier l'ensemble des éléments du précédents jeu de données
* on stockera ensuite les entrées et les résultats de ces exécutions dans un fichier ou en base par exemple. Cet ensemble entrées-sorties constituera le Goden Master.

Après chaque modification de code, on réexecute le jeu de tests précédents. Dans le cas d'un refactoring, s'il y a une différence dans les résultats on corrige le tir. Dans le cas d'une modification fonctionnelle, si différence il y a, on vérifie que le nouveau résultat correspond bien à ce qui est attendu. Si c'est le cas, nous modifions le GM pour prendre en compte ce nouveau résultat et obtenons ainsi un nouveau GM, sinon on corrige le tir.

Attention !!! En fonction de la granularité du système que vous testerez, vos états possibles pourront être nombreux. Le jeu d’entrées pourra rapidement devenir énorme. La génération et surtout la maintenance de celui-ci peuvent rapidement engendrer des coûts prohibitifs. C’est pourquoi il sera préférable de n’utiliser ce genre de techniques que pour des refactorings rapides, 1, 2 ou 3 sprints, en n’embarquant aucune modification fonctionnelle.


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
Voici la dernière technique abordée dans le cadre de cet article, le Sequential Runs.
Lorsque GitHub a décidé de réécrire sa fonction de merge, il leur était impossible de prévoir à l’avance les différents cas qui allaient se présenter. Impossible donc de sélectionner des cas d’utilisation et de générer les inputs correspondants.
Le plus sûr était donc de comparer ce qui se passait sur la production avec une version refactorée. Pour ce faire, il faut envoyer deux implémentations d’une même fonctionnalité en production, une effective (le contrôle), l’autre "dormante" (la candidate).
Lorsque la fonctionnalité est utilisée, les inputs sont passées à chacune de ces deux versions. Les résultats des deux exécutions sont enregistrés et comparés directement. Si des exceptions ou des différences sont rencontrées entre les deux versions, celles-ci sont logguées dans l'interface web de Scientist. Seuls les résultats de la version legacy sont utilisés pour la suite de l’interaction avec l’utilisateur, le fait d'avoir cette double exécution étant complètement transparente pour lui.

En comparant à chaque appel de la méthode de merge, les résultats obtenus par la version legacy et la version en cours de refactoring, il est possible de combler petit à petit les différences et de détecter les fonctionnements précisés ni dans les specs ni les tests. 
Au fur et à mesure de cette amélioration continue, les différences se sont amenuisées jusqu’à ce que la nouvelle version devienne la version de production. Ceci, sans que jamais les utilisateurs en pâtissent.
Je rappelle que lors de la phase de comparaison, la vérité est et reste le code legacy. Seule son exécution est prise en compte pour tout ce qui est traitement fait par l’utilisateur.
Lors de la bascule, il suffit de remplacer l’appel à l’ancien code par un appel au nouveau.

Pour en savoir plus sur la façon dont à procédé GitHub, je vous invite à lire cet [article](http://githubengineering.com/move-fast/) présentant le framework Ruby nommé « Scientist » créé à l’occasion. Il faut signaler qu’un portage Java de ce framework existe et s’appelle « Experiment4J » trouvable [ici](https://github.com/dannwebster/experiment4j)

(4) en live ? a postériori ? les deux ? ça dépend du contexte ?

En conclusion, je pense que ces méthodes utilisant d’énormes quantités de tests, comportent quand même quelques risques au delà du coût de génération/sélections des inputs ou du surcout d’un double run. 
Plus la surface de tests sera grande, plus le risque de figer l’application sera grand (tests de comportements vs tests d’implémentation). Pour éviter cela, un travail de sélection en amont doit être très important, ou bien un travail de maintenance énorme.
Il faut donc être très vigilant sur la granularité et l’indépendance du système à tester, afin de pouvoir refactorer rapidement, sans gêner les autres. 
Enfin, ces tests, dans la plupart des cas, n’ont pas pour vocation d’être automatisés. En effet, une fois le refactoring terminé, on jette le tout à la poubelle et on repart sur du test classique afin que cette nouvelle version puisse vivre sa vie.