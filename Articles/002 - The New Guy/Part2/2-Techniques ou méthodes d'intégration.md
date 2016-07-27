Voici quelques techniques/méthodes pour aider au mieux Gil à s'intégrer:

##### le pair programming
Cette technique consiste à binômer deux personnes. Les avantages de cette techniques sont nombreux:
- elle favorise la communication entre les pairs
- elle permet aux pairs d'apprendre à travailler ensemble
- elle renforce les liens entre les gens et permet ainsi de créer un esprit d'équipe
Dans le cas précis de l'arrivée de Gil, le pairer avec une personne connaissant bien le logiciel sur lequel il doit intervenir,
devrait lui permettre de monter en compétence plus rapidement. Le pairer avec la personne qu'il doit remplacer devrait 
aussi l'aider en ce sens. Prévoyez dans ce cas un temps suffisamment large pour que Gil ait le temps de récupérer toutes 
les connaissances de son prédécesseur. Un problème ou une question sont rencontrés, les échanges étant dynamiques, Gil est 
à même d'être aidé par son pair expérimenté.
En dehors de sa montée en connaissances, cela va lui permettre de donner son point de vue. Gil a un regard neuf sur l'existant 
et les méthodes déjà en place, il pourrait donc aussi permettre d'améliorer cela.

Enfin le pair a d'autres avantages, comme le fait de permettre de développer des applications mieux pensées et de
meilleure qualité: deux cerveaux valent mieux qu'un.

Vous l'aurez compris tout est bon dans le pair-programming.

##### Faire des feedbacks réguliers : rapports d'étonnements, points réguliers
Un feedback est un moyen de faire un retour à une personne ou un groupe de personnes sur ses/leurs actions passées
(merci Captain Obvious:)) et ce dans le but d'agir sur les actions futures de celle(s)-ci, afin de les améliorer.

Faire des points réguliers afin de mieux intégrer Gil est important.
**Quelque soit le type de critiques, il est important de les exprimer d'un côté ou de l'autre.**
- si elles sont positives par rapport à son travail et ou son comportement, cela le confortera et l'incitera à
continuer. Dans le cas où les retours de Gil concernant l'équipe sont bons, cela montrera à celle-ci que ses méthodes de 
travail et d'intégrations sont bonnes. Avoir capitalisé dessus paie ;-)
- si elles sont négatives vis à vis de Gil, cela doit lui permettre de corriger le tir. Idem si elles sont négatives vis 
à vis de l'équipe déjà en place. Cela est encore plus vrai si Gil n'est pas le premier à les remonter. Dans tous les cas 
ici, le feebback se devra d'être constructif.

Dans cette optique, faire quelques rapports d'étonnements du côté de Gil et des points réguliers devraient permettre
d'aller en ce sens. **La communication est la clé de voûte pour améliorer l'intégration d'un nouveau et les processus
afférents.**

##### Échanges avec le métier: formation métier pour tous les nouveaux arrivants
**En tant que développeur, nous transcrivons un besoin exprimé par le métier en code. Il est important de réaliser que 
ce qui part en production n'est pas l'idée qu'en a le métier mais ce qu'en comprennent les développeurs.**
Il est donc important de bien se familiariser avec le métier sous-jacent aux applications sur lesquelles nous travaillons.
Suivre une formation sur le métier peut s'avérer extrêmement utile.
Cela peut paraître évident. Pourtant trop souvent, lorsqu'un développeur arrive sur un nouveau périmètre fonctionnel,
on lui fait une courte présentation du métier. Par la suite il sera lâché directement sur le code. Le but étant de viser 
une rentabilité dès son arrivée T_T.
Celui-ci se dépatouille tant bien que mal avec les objets d'un métier qu'il ne maîtrise pas. Cela pourrait le frustrer, 
voire le pousser au départ. De plus, le code produit sera certainement d'une qualité moindre.

**Former convenablement un nouveau sur le métier permet plus que sa bonne intégration, cela permet aussi d'investir dans
un code de meilleure qualité.** Cela générera à moyen et long terme des économies plus importantes que le coût
de la formation.

##### Passer au tout début du temps avec le métier ou la QA afin de bien s'imprégner du fonctionnel
En plus de former de manière académique Gil sur le fonctionnel, lui faire passer du temps avec le métier ou la QA peut lui permettre 
de s'en imprégner plus fortement et plus rapidement.
Il partagera le même vocabulaire que le métier (ubiquitous language), et sera à même de mieux transcrire le besoin en
code par la suite. **Cela permet aussi de rapprocher les équipes, d'améliorer leur communication, et de produire le plus
constamment possible de la valeur et du code de qualité.**
Autre avantage, Gil voit aussi comment est utilisé le logiciel et quels sont les cas d'utilisation les plus fréquents.
Il peut aussi voir ce qui auraient échappé au Business Analyst (BA) ayant transcris le besoin du métier vers
les développeurs.

##### Macro vers Micro et Micro vers Macro:
Lorsque Gil arrive, et qu'il ne connaît pas le fonctionnel, il est important de le lui expliquer.
On commence à le lui expliquer dans les grandes lignes (Macro). Plus le temps passe, plus sa compréhension augmente, et 
plus on descend au niveau des détails (Micro).
**On commence donc d'une explication fonctionnelle macroscopique vers une explication fonctionnelle microscopique.**

Concernant les développements, le cheminement est inversé.
On commence du plus spécifique (Micro), pour devenir le plus généraliste possible (Macro) avec le temps.
Vous ne pouvez pas décemment attendre du nouveau d'avoir une vision globale du ou des logiciels sur lesquels il va
travailler en arrivant.
Il faudra donc le faire monter en compétences et connaissances avec le temps. Il fuadra procéder par baby-steps en
fonction de la complexité rencontrée.
**On commence donc par des développements spécifiques à faire (micro), et avec le temps passant on pourra lui attribuer des
développements transverses (macro).**

Tout cela peut sembler logique. Mais comme dit précédemment, il arrive parfois que le nouveau soit lancé directement
dans du code sans aucune formation. Dans ce cas la seule qu'il acquerra sera au niveau de sa compréhension du
code et de ses échanges avec les autres.

##### Living documentation:
Avoir une documentation de qualité peut aider Gil dans son intégration. Malheureusement bien souvent celle-ci est
obsolète. De facto, elle génère encore une fois une perte de temps, de la frustration pour Gil ainsi qu'une perte d'argent
pour l'entreprise.

Mais comment arriver à avoir une documentation à jour et compréhensible alors que le code ne cesse de changer?
Comment éviter un écart possible entre le comportement de nos applications et ce qui en est spécifié?

Une réponse possible est de faire de la living documentation.
C'est un ensemble de méthodes permettant de fournir dynamiquement de la documentation à jour.
Si vous faites du BDD, chacun des tests que vous avez écrit correspond à un fonctionnement attendu de la part du métier
(spécification par l'exemple). Ces tests présentent aussi les termes du métiers et permettent à Gil de s'en imprégner encore un peu plus.
Le fait de faire du pair programming y contribue aussi; la connaissance est transmise de manière dynamique par la
communication entre les pairs. Dans ce contexte, les connaissances sont censées être à jour.

Je vous invite à lire le livre sur la living documentation de Cyrille MARTRAIRE ([@Cyriux](https://twitter.com/cyriux?lang=fr))
que vous pourrez trouver à l'adresse suivante: https://leanpub.com/livingdocumentation