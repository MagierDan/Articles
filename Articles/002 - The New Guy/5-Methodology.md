Voici quelsques techniques/méthodes pour intégrer au mieux un nouveau:

##### le pair programming
Cette technique consiste à binômer deux personnes. Les avantages de cette techniques sont nombreux:
- elle favorise la communication entre les pairs
- elle permet aux pairs d'apprendre à travailler ensemble
- elle renforce les liens entre les gens et permet ainsi de créer un esprit d'équipe
Dans le cas précis de l'arrivée d'un npouveau, pairer une personne connaissant bien le logiciel sur lequel doit intervenir
avec ce lui, devrait lui permettre de monter en compétence plus rapidement.
Un problème ou une question sont rencontrés, les échanges étant dynamiques, le nouveau est à même d'être aidé par
l'ancien.
En dehors de la montée en connaissances du nouveau, le fait de pairer va lui permettre de donner son point de vue. Il a
un regard neuf sur l'existant et les méthodes déjà en place, il pourrait donc aussi permeettre d'améliorer cela.

Enfin le pair a d'autres avantages, comme le fait de permettre de développer des applications mieux pensées et de
meilleure qualité:  deux cerveaux valent mieux qu'un.


##### Faire des feedbacks réguliers : rapports d'étonnments, points réguliers
Un feedback est un moyen de faire un retour à une personne ou un groupe de personnes sur ses/leurs actions passées
(merci Captain Obvious:)) et ce dans le but d'agir sur les actions futures de celle(s)-ci, dans le but de les améliorer.

Faire des points réguliers afin de mieux intégrer le nouveau est important. Quelque soit le type de critiques, il est
important de les exprimer d'un côté ou de l'autre:
- si elles sont positives par rapport au travail et ou comportement du nouveau, cela le confortera et l'incitera à
continuer sur cette voix. Dans le cas où les retours du nouveau concenrnant l'équipe sont bons, cela montrera à l'équipe
 que ses méthodes de travail et d'intégrations sont bonnes, et qu'avoir capitabiliser dessus paie ;-)
- si elles sont négatives vis à vis du nouveau, cela doit lui permettre de corriger le tir. Idem concernant l'équipe
déjà en place, surtout si cette personne n'est pas la première à les remonter. Dans tous les cas ici, le feebback se
devra d'être constructif.

Dans cette optique, faire quelques rapports d'étonnements du côté du nouveau et des points réguliers devraient permettre
d'aller en ce sens. La communication est la clé de voûte pour améliorer l'intégration d'un nouveau et les processus
afférents.

##### Echanges avecc le métier: formation métier pour tous les nouveaux arrivants
En tant que développeur, nous transcrivons un besoin exprimé par le métier en code. De facto, si nous ne comprenons pas
le métier, il sera dur de réaliser convenablement cette transforamtion en code.
Il est donc important de bien comprendre le métier sous jacent aux applications sur lesquelles nous travaillons.
Pour ce faire, suivre une formation sur le métier peut s'avérer extrêmement utile.
Cela peut paraître évident et pourtant bien souvent lorsqu'un développeur arrive sur un nouveau périmètre fonctionnel,
on lui fait une courte présentation du métier et on le lâche sur le code. Le but étant de viser une rentabilité dès
l'arrivée du nouveau T_T.
Celui-ci se dépatouille tant bien que mal avec les objets d'un métier qu'il ne maîtrise pas, ce qui pourrait le frustrer
et le pousser à partir. De plus le code produit serait certainement d'un qualité moindre dans ce cas-ci.

Former convenablement un nouveau sur le métier permet plus que sa bonne intégration, cela pemret aussi d'investir dans
la qualité du code qu'il va produire et pouvoir générer à moyen et long terme des économies plus importantes que le coût
de la formation.

##### Passer au tout début du temps avec le métier ou la QA afin de bien s'impregner du fonctionnel
En plus de former de manière académique le nouveau sur le métier, le fait de lui faire passer du temps avec le métier ou
la QA peut lui permettre de s'en imprégner encore plus fortement et aussi plus rapidement.
Il partagera le même vocabulaire que le métier (ubiquitous language), et sera à même de mieux transcrire le besoin en
code par la suite. Cela permet aussi de rapprocher les équipes, d'améliorer leur communication, et de produire le plus
constamment possible du code de qualité et de la valeur pour le métier.
Autre avantage, le nouveau voit aussi comment est utilisé le logiciel et quels sont les cas d'utilisation les plus
fréquents, mais aussi certains qui auraient pu échapper au Bussiness Analyst (BA) ayant transcris le besoin du métier vers
les développeurs.

##### Macro vers Micro et Micro vers Macro:
Lorsque le nouveau arrive, et qu'il ne connait pas le fonctionnel, il est important de le lui expliquer.
Pour cela, on commence à lui expliquer dans les grandes lignes (Macro) ce qu'est le coeur de métier. Plus le temps passe,
plus sa compréhension augmente, et plus on descend au niveau des détails (Micro).
On commence donc d'une explication macroscopique vers une explication microscopique.

Concernnat les développements, le cheminement est inversé, à savoir commencer au plus spécifique (Micro) pour devenir le
plus généraliste possible (Macro) avec le temps.
Vous ne pouvez pas décemment attendre du nouveau d'avoir une vision globale du ou des logiciels sur lesquels il va
travailler en arrivant.
Il faudra donc le faire monter en compétences et connaisances avec le temps, ene enchaînant parfois par baby-steps en
fonction de la compléxité rencontrée. On commence donc par des développements spécifiques à faire, et plus le temps
passe et plus on pourra lui attribuer des développements transverses.

Tout cela peut sembler logique mais comme dit précedemment, il arrive parfois que le nouveau soit lancé quasiment directement
dans le code sans autre forme de formation que celle qu'il acquièrera au niveau de sa compréhension du code et de ses
échanges avec les autres.

##### Living documentation:
Avoir une documentation de qualité peut aider le nouveau dans son intégration. Malheureusement bien souvent celle-ci est
obsolète et génère encore une fois une perte de temps et de la frustration pour le nouveau ainsiq u'une perte d'argent
pour l'entreprise .

Mais comment arriver à avor une documentation à jour et compréhensible alors que le code ne cesse de changer et éviter
un écart possible entre le comportement de nos applications et ce qui en est spécifié ?

Une réponse possible est de faire de la living documentation. C'est un ensemble de méthodes permettant de fournir
dynamiquement de la documentation à jour.
Si vous faites du BDD, chacun des tests que vous avez écrit correspond à un fonctionnement attendu de la part du métier
(spéciffication par l'exemple ?). De plus ces tests présentent aussi les termes du métiers et permmetent au nouveau de
s'en imprégner encore un peu plus.
Le fait de faire du pair programming y contribue aussi; la connaissance est trasmise de manière dynamique par la
communication entre les pairs, les connaissances étant censées être à jour.

Concernnat ce dernier point, je vous invite à lire le livre de Cyrille MARTRAIRE ([@Cyriux](https://twitter.com/cyriux?lang=fr))
que vous pourrez trouver à l'adresse suivante: https://leanpub.com/livingdocumentation