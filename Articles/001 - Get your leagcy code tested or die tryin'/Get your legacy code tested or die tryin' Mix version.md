Aujourd'hui Nos applications répondent à de plus en plus de besoins, et ce jusqu'à devenir énormes, gigantesques, "monstrueuses" :).
Il est beaucoup trop rare d'avoir une couverture de tests permettant de refactorer et/ou d'ajouter du fonctionnel sans crainte.
Commencer des développements sur des nouveaux besoins n'est pas forcément chose simple (même en TDD), mais lorsqu'il s'agit
de refactorer ou modifier du code existant, celà devient très complexe.
En effet, il ne faut surtout pas perdre le fonctionnement actuel, qui est le résultat de parfois plusieurs années de modifications.
Cela conduit à un comportement implicite de l'application, non conforme à la documentation, hélas devenue obsolète.

Il existe pourtant des techniques pour nous aider à tendre un filet de sécurité avant de refactorer une fonctionnalité non testée (ou pas assez).
Ces techniques, que nous verrons par la suite, se basent sur le principe que le code de l'application est une "boîte noire":
on le comprends peu ou pas assez (certains diront même pas du tout) et nous allons tout faire pour en modifier le minimum ou bien le réécrire.
On va donc utiliser un jeu de données en entrée et en sortie. Le but sera de comparer les outputs produits entre différentes
implémentations à partir d’un même input.
Dans notre cas, il s’agira de comparer les résultats d’exécutions de la version de production avec ceux de la version en
cours de réécriture/modification.
Ces méthodes vont surtout varier sur la façon dont on génère le jeu d’inputs.


Golden Master (GM)
-------------
Avant de refactorer/modifier le code de la version "certifiée" (en règle générale la production), on effectue les actions suivantes:
* on créé un vaste jeu de données (de manière aléatoire ou non)
* on passe à la méthode à modifier l'ensemble des éléments du précédents jeu de données
* on stockera ensuite les entrées et les résultats de ces exécutions dans un fichier ou en base par exemple. Cet ensemble
entrées-sorties constituera le Golden Master.

Après chaque modification de code, on réexecute le jeu de tests précédents. Dans le cas d'un refactoring, s'il y a une différence
dans les résultats on corrige le tir. Dans le cas d'une modification fonctionnelle, si différence il y a, on vérifie que
le nouveau résultat corresponde bien à ce qui est attendu. Si c'est le cas, nous modifions le GM pour prendre en compte
ce nouveau résultat et obtenons ainsi un nouveau GM, sinon on corrige le tir.

Attention !!! En fonction de la granularité du système que vous testerez, vos états possibles pourront être nombreux. Le jeu
d’entrées pourra rapidement devenir énorme. La génération et surtout la maintenance de celui-ci peuvent rapidement engendrer
des coûts prohibitifs. C’est pourquoi il sera préférable de n’utiliser ce genre de techniques que pour des refactorings rapides,
1, 2 ou 3 sprints, en n’embarquant aucune modification fonctionnelle.


Record and Play (RaP)
-------------
Autre technique: le Record and Play (RaP). Toujours dans le but de créer un harnais de tests, le moyen est ici d’enregistrer
un ou des scénarii d’utilisation de l’application dans son IHM (web, mobile ou desktop). Une fois le code modifié, comme
pour le GM, on rejoue les tests.
Si nous sommes dans le cas d'un refactoring, le fait de relancer les tests doit conduire aux mêmes résultats, sinon on corrige
les modifications effectuées. Dans le cas d'une modfication, on vérifie que la résultat de la modifcation correspond bien
à ce qui est attendu, et on réenregistre la séquence pour ce cas de tests.

Ces tests sont cependant assez fragiles car en plus du système sous-jacent, les résultats d’exécutions dépendent de l’IHM.
Pour que les résultats soient exploitables, il faut donc figer l’IHM en plus du système à tester. Plus le nombre de personnes
impactées par ce refactoring augmente, plus la difficulté augmente aussi.
Leur maintenance s'avère par ailleurs plus pénible que celle du GM car à la moindre modification, il faut réenregistrer
toute une séquence, ou bien modifier la valeur de certains résultats dans les fichiers de tests.

Généralement, c’est Sélénium qui est utilisé pour enregistrer ces scénarii pour une application web.
Il existe d'autres outils de RaP tel que ce dernier. Certains sont payants et permettent de tester aussi des applications
desktop ou mobile (par exemple Ranorex).

Par ailleurs, il est possible d'utiliser Sélénium autrement qu'en RaP. Pour cela, nous écrivons les tests directement dans
un langage comme java. Si cela est convenablement fait, les tests sont plus facilement maintenables.
Je vous renvoie pour cela vers l'utilisation du patten PageObject dont une description est disponible [ici](http://www.assertselenium.com/automation-design-practices/page-object-pattern/).
Je conseillerais dans ce cas la librairie [Simplelenium](https://github.com/dgageot/simplelenium), qui gère mieux certaines
problèmatiques de timing, et propose plus de méthodes permettant de rendre vos tests plus "human-readable".


Technique d'Experiment
-------------
Voici la dernière technique abordée dans le cadre de cet article, l'Experiment.
Lorsque GitHub a décidé de réécrire sa fonction de merge, il leur était impossible de prévoir à l’avance les différents
cas qui allaient se présenter. Impossible donc de sélectionner des cas d’utilisation et de générer les inputs correspondants.
Le plus sûr était donc de comparer ce qui se passait sur la production avec une version refactorée. Pour ce faire, il faut
envoyer deux implémentations d’une même fonctionnalité en production, une effective (le contrôle), l’autre "dormante" (la candidate).
Lorsque la fonctionnalité est utilisée, les inputs sont passées à chacune de ces deux versions. Les résultats des deux exécutions
sont enregistrés et comparés directement. Si des exceptions ou des différences sont rencontrées entre les deux versions,
celles-ci sont logguées dans l'interface web de leur framework. Seuls les résultats de la version legacy sont utilisés pour
la suite de l’interaction avec l’utilisateur, le fait d'avoir cette double exécution étant complètement transparente pour lui.

En comparant à chaque appel de la méthode de merge, les résultats obtenus par la version legacy et la version en cours de refactoring,
il est possible de combler petit à petit les différences rencontrées.
Au fur et à mesure de cette amélioration continue, les différences s'amenuisent jusqu’à ce que la nouvelle version devienne
la version de production. Ceci, sans que jamais les utilisateurs en pâtissent.
Je rappelle que lors de la phase de comparaison, la vérité est et reste le code legacy. Seule son exécution est prise en
compte pour tout ce qui est traitement fait par l’utilisateur.
Lors de la bascule, il suffit de remplacer l’appel à l’ancien code par un appel au nouveau.

Pour en savoir plus sur la façon dont à procédé GitHub, je vous invite à lire cet [article](http://githubengineering.com/move-fast/)
présentant le framework Ruby nommé « Scientist » créé à l’occasion. Il faut signaler qu’un portage Java de ce framework
existe et s’appelle « Experiment4J » trouvable [ici](https://github.com/dannwebster/experiment4j)

Il faut aussi rajouter que Github peut utiliser cette méthodologie de test car il leur est possible de passer très rapidement
leur nouveau code en production (à l'époque de leur article, ils déployaient leur application principale 60 fois par jour).
On en déduit que Github bénéficie d'un processus de mise en production bien rodé.

En conclusion
-------------

Les différentes méthodes évoquées permmettent d'avoir relativement rapidement un jeu de tests convenable pour refactorer
voire légèrement modifier le code de nos applications.
Chacune de celles-ci possède ses avantages et inconvéninets:
* Pour le GM et le RaP, leur maintenance peuvent s'avérer coûteuse. Il est parfois moins onéreux de refaire un jeu de tests
plus que de maintenir celui déjà créé.
* Dans le cas de l'Experiment, un bon processus de mise ne production est nécessaire. De plus, une double exécution peut
aussi s'avérer lourde en terme de vélocité applicative.

Pourtant malgré ces défauts, le fait d'avoir un filet de sécurité pour le refactoring/évolution du code, permet d'éviter
des régressions en production. Le fait de fixer celles-ci s'avérera certainement plus coûteux que de générer ce filet de sécurité.
Par ailleurs, il est conseillé de restreindre la surface applicative du code à modifier. Plus celle-ci sera petite, plus
il sera aisé de générer les jeux de tests, et donc de refactorer rapidement sans gêner les autres.
Pour ces méthodologies, Le plus souvent dans le cadre d'un refactoring, une fois celui-ci effectué et validé,
les jeux de tests sont purement et simplement supprimés.

Les différentes techniques détaillées dans cet article, sont celles que j'ai trouvé afin de répondre aux besoins que j'ai rencontrés.
J'ai utilisé le GM et le RaP par programmation en Java à plusieurs reprises et cela a donné de très bons résultats.
Pour le GM, c'était dans le cas d'un injecteur (trop) intelligent de documents. Des règles métiers le constituait. J'ai du
donc créé un jeu de documents à injecter (mon GM) qui constituait mes tests. A chaque évolution, on relancait l'intégralité des tests.
Cela m'a prémunis de certaines regressiosn que je n'avais pas constaté lors de l'écriture de code.
Pour le RaP, j'ai écrit des tests end-to-end de ce que faisait l'application. L'application était assez petite, donc j'ai
pu couvrir l'ensemble des cas nominaux.
Ma chance était que dans ces deux cas le nombre de tests à écrire était relativement petit par rapport à d'autres applications
(mais nombreux quand même). Cela a permis de ne pas les jetter mais de les maintenir.
Dans d'autres cas, les applications étaient un peu plus grande fonctionnellement parlant que les deux précédentes. L'écriture
des tests et leur maintenace étaient un peu plus ardu du fait de la volumétrie, mais ils étaient toujours maintenables.
Les seuls soucis rencontrés furent lorsqu'une autre feature team a refait une interface web sans nou sen informer. Les tests
n'étaient plus bons et il a fallu réadpter les tests à l'IHM.

Mais comme toutes les techniques, ce ne sont pas forcément des silver-bullets. Ce qui correspondait à mon contexte ne
sera pas forcément le cas pour le vôtre.

Dans tous les cas, bon courage à tous pour la maintenace de votre legacy.


Un grand merci à Rapahël SQUELBUT pour sa relecture, et son aide à la réécriture de cet article ^^.