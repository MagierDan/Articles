





### Techniques ou méthodes d'intégration
Voici quelsques techniques/méthodes pour intégrer au mieux un nouveau:

##### le pair programming
Cette technique consiste à binômer deux personnes. Les avantages de cette techniques sont nombreux:
- elle favorise la communication entre les pairs
- elle permet aux pairs d'apprendre à travailler ensemble
- elle renforce les liens entre les gens et permet ainsi de créer un esprit d'équipe
Dans le cas précis de l'arrivée d'un nouveau, pairer une personne connaissant bien le logiciel sur lequel doit intervenir
avec ce lui, devrait lui permettre de monter en compétence plus rapidement.
Un problème ou une question sont rencontrés, les échanges étant dynamiques, le nouveau est à même d'être aidé par
l'ancien.
En dehors de la montée en connaissances du nouveau, le fait de pairer va lui permettre de donner son point de vue. Il a
un regard neuf sur l'existant et les méthodes déjà en place, il pourrait donc aussi permeettre d'améliorer cela.

Enfin le pair a d'autres avantages, comme le fait de permettre de développer des applications mieux pensées et de
meilleure qualité: deux cerveaux valent mieux qu'un.


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

##### Echanges avec le métier: formation métier pour tous les nouveaux arrivants
En tant que développeur, nous transcrivons un besoin exprimé par le métier en code. De facto, si nous ne comprenons pas
le métier, il sera dur de réaliser convenablement cette transformation en code.
Il est donc important de bien comprendre le métier sous jacent aux applications sur lesquelles nous travaillons.
Pour ce faire, suivre une formation sur le métier peut s'avérer extrêmement utile.
Cela peut paraître évident et pourtant bien souvent lorsqu'un développeur arrive sur un nouveau périmètre fonctionnel,
on lui fait une courte présentation du métier et on le lâche sur le code. Le but étant de viser une rentabilité dès
l'arrivée du nouveau T_T.
Celui-ci se dépatouille tant bien que mal avec les objets d'un métier qu'il ne maîtrise pas, ce qui pourrait le frustrer
et le pousser à partir. De plus le code produit serait certainement d'une qualité moindre dans ce cas-ci.

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

Concernant les développements, le cheminement est inversé, à savoir commencer au plus spécifique (Micro) pour devenir le
plus généraliste possible (Macro) avec le temps.
Vous ne pouvez pas décemment attendre du nouveau d'avoir une vision globale du ou des logiciels sur lesquels il va
travailler en arrivant.
Il faudra donc le faire monter en compétences et connaisances avec le temps, en enchaînant parfois par baby-steps en
fonction de la complexité rencontrée. On commence donc par des développements spécifiques à faire, et plus le temps
passe et plus on pourra lui attribuer des développements transverses.

Tout cela peut sembler logique mais comme dit précédemment, il arrive parfois que le nouveau soit lancé quasiment directement
dans le code sans autre forme de formation que celle qu'il acquièrera au niveau de sa compréhension du code et de ses
échanges avec les autres.

##### Living documentation:
Avoir une documentation de qualité peut aider le nouveau dans son intégration. Malheureusement bien souvent celle-ci est
obsolète et génère encore une fois une perte de temps et de la frustration pour le nouveau ainsi qu'une perte d'argent
pour l'entreprise.

Mais comment arriver à avoir une documentation à jour et compréhensible alors que le code ne cesse de changer et éviter
un écart possible entre le comportement de nos applications et ce qui en est spécifié ?

Une réponse possible est de faire de la living documentation. C'est un ensemble de méthodes permettant de fournir
dynamiquement de la documentation à jour.
Si vous faites du BDD, chacun des tests que vous avez écrit correspond à un fonctionnement attendu de la part du métier
(spécification par l'exemple). De plus ces tests présentent aussi les termes du métiers et permettent au nouveau de
s'en imprégner encore un peu plus.
Le fait de faire du pair programming y contribue aussi; la connaissance est trasmise de manière dynamique par la
communication entre les pairs, les connaissances étant censées être à jour.

Concernant ce dernier point, je vous invite à lire le livre de Cyrille MARTRAIRE ([@Cyriux](https://twitter.com/cyriux?lang=fr))
que vous pourrez trouver à l'adresse suivante: https://leanpub.com/livingdocumentation

### Environnement
L’environnement dans lequel va évoluer le nouveau va aussi jouer un rôle important à son intégration.
Les méthodes agiles ainsi que des événements relatifs à la fonction de développeur peuvent être aussi des facteurs
décideurs en ce sens.

#### Agilité
L'agilité est aussi un moyen d'intégrer au mieux un nouveau. Les méthodes agiles favorisent la communication et les
interactions entre toutes les parties du processus de développement. Grâce aux différents rituels (sprint plannings,
daily stand-ups, rétrospectives, reviews), le nouveau se retrouve directement au cœur de ce qui se passe dans l'équipe
et peut interagir avec elle. Les pratiques défendues dans les principes sous-jacents au manifeste agile favorisent
l’autonomie de l'équipe, la qualité et l'excellence technique, ce que tout développeur se disant appartenir à la mouvance
crafts doit désirer. C'est le genre d'environnement où il fait bon travailler et qui puisse permettre au nouveau de
s'épanouir, et par la même de rester. Imaginez un environnent qui ne soit pas agile. Imaginez un environnement sans
stand-up, sans rétrospective, sans pair-programming, grosso-modo un environnement sans communication. Imaginez aussi
cet environnement sans excellence technique, sans simplicité, sans faire aucune confiance dans ses choix à l'équipe de
développement (Personnellement j’appellerai cela l'enfer du développeur mais cela n'engage que moi). Et imaginez-vous
dès lors dans cet environnment. Que feriez-vous si jamais vous ne pouviez pas introduire un mode de fonctionnent plus
agile? Resteriez-vous? Moi pas!

Le manque d'agilité peut être un frein puissant à l'intégration d'un nouveau. Il pourrait être intéressant si vous
n'êtes pas encore dans ce mode de songer à y passer. Au delà de favoriser l'intégration des nouveaux, elles apportent
d'autres avantages:
- ouverture aux changements
- meilleure visibilité entre les parties entre ce qui est attendue et ce qui est livrée
- et donc meilleure collaboration avec le client.
Il en existe encore d'autres, le but n'étant pas de tous les lister ici mais de présenter ceux que vous proposer à votre
hiéarchie afin de pouvoir la mettre en place.

#### Evénements
Pour certains d'entre nous, participer à différents types d’événements nous permet de rencontrer nos pairs, des gens
ayants des intérêts communs avec nous et donc de mous intégrer à une communauté. C'est donc un moment d'échanges, qui
nous permet de monter en compétence sur certains sujets. Certains développeurs en sont très friants.
Organisés ce type d’événements en interne ou permettre aux membres de vos équipes d'y participer peut grandement aider à
conserver à plus ou moins long termes ces personnes, et faciliter aussi l’intégration du nouveau qui verra que vous
portez de l’attention à ses centres d'intérêts.

Plusieurs formes existent pour ces types d’événements:

### Brown Bag Lunch (BBL)
Un sujet vous intéresse et vous avez envie de l'approfondir, soit en faisant venir un expert, soit en partageant vos
connaissances dessus. Mais le soir vous n'avez pas le temps car vous devez renter vous occuper de votre famille.
Pourquoi ne pas faire cela le midi lors de la pause déjeuner. C'est le principe du BBL. Un expert vient vous présenter
le midi un sujet. Vous ramenez votre déjeuner dans votre BBL et pendant que l'on vous expose les bienfaits d'une
technologie/méthodologie vous savourez votre mets. Votre estomac ainsi que votre esprit en ressortent rassasiés ^^.

#### Meetup ou User Group
Si vous pouvez le soir, pourquoi héberger un meetup ou un User Group. Un meetup est une rencontre informelle qui peut
toucher tous les types de sujets. Les suejts peuvent être les mêmes que pour un BBL mais plutôt que de se limiter à une
ou deux heures maximum le midi, ici il est possible de pousser cela un peu plus longtemps: trois aou quatre heures.
Cela aura aussi pour mérite de rencontrer des gens susceptibles d'être de futurs employés du fait de leur attraits
communs avec ceux étant déjà en poste chez vous.
N'oubliez pas dès lors de faire un effort sur les boissons et les "mets" que vous proposerez aux gens qui viendront
(qui a dit que nous sommes des gens intéressés ^^).

#### Conférences
Pendant deux ou trois jours, n'hésitez pas à envoyer vos internes à des conférences telles que Devoxx ou NCrafts entre autre.
Cela permet à vos équipes de voir des sujets connexes à vos besoins ou qui le intéresse fortement et même de répondre à
des problématiques qui jusque là n'avaient pas encore trouvé de réponses. Plus que les conférences, ce sont les échanges
qui ont lieu à côté qui peuvent amener à cela car les speakers sont souvent des gens sympas avec qui vous pouvez échanger
très simplement.

### Team building
Le team building permet de renforcer la cohésion d'équipe. Cela a pour but de créer des liens entre les membres
de l'équipe, leur apprendre à se connaître dans un lieu autre que le travail et parfois d'apaiser les tensions qui
peuvent y régner.

Plusieurs moyens/activités existent pour aller en ce sens:
- Organiser des petits déjeuners, des restaurants ou des sorties dans un bar
- faire des activités sportives ou autres (foot en salle, tournoi de baby-foot, etc...)
- faire des katas en équipe
- Organiser des sorties lors de certains événements comme un cinéma lors de la sortie du dernier Star Wars.
Cette liste n'est pas exhaustive, à vous de voir ce qu'il est possible de lui rajouter afin de correspondre à votre contexte.

Si tout se passe bien lors de ces événements, les membres de l'équipe ont tendance à se rapprocher, les tensions à
diminuer et donc les problèmes de se régler plus facilement (si jamais il y en a).

On voit facilement qu'il est possible de favoriser l'intégration du nouveau avec des activités de team building.
Après il faut faire aussi en fonction de ce dernier. Lors du recrutement, vous avez peut être pu scanner ses goûts en la
matière. Dans un premier temps, sans trop en faire, adaptez-vous à lui afin de le faire se sentir bien, et par
la suite faîtes des choses qui soient plus en accord au goût de tous les membres de l'équipe.

Il ne faut pas forcément négliger ce point car mal intégrer humainement/socialement parlant le nouveau peut conduire à
son départ.

### Conclusion
Comme vu précédemment, l'arrivée d'un nouveau se prépare. Il peut être fortement intéressant d'investir sur ce
processus d'onboarding et cela pour deux raisons:
- être sûr que la personne choisie est la bonne
- tout faire pour que son intégration se déroule au mieux et qu'elle reste

Parfois cela marchera et parfois non. Rien n'est absolu en ce sens. Si la personne ne reste pas, il faut essayer de
comprendre ce qui n'a pas marché et corriger cela quand c'est possible. C'est en améliorant petit à petit ce porcessus,
que l'on arrivera à maximiser l'intégration du nouveau et le retour à une vélocité de croisière.

Nous avons beaucoup parlé de comment bien intégrer le nouveau. Il ne faut pas oublier non plus que le nouveau doit aussi
faire des efforts pour s'intégrer. Ce n'est pas à sens unique. Parfois des erreurs de casting peuvent se produire. Plutôt
que d'insister alors que l'on sait pertinemment que la sauce ne prend pas, il vaut mieux se séparer avant d'avoir perdu
trop de temps d'un côté comme de l'autre. Ce ne sera pas une expérience inutile dans ce cas non plus, car il vous sera
encore possible d'apprendre de cette impair.

Dans tous les cas rien n'étant jamais acquis, améliorez le plus possible vottre processus d'onboarding. Celui-ci évoluera,
s'améliorera avec le temps et correspondra de plus en plus à votre équipe. Soyez aussi créatif, une touche d'originalité
peut avoir beaucoup d'effets positifs sur l'intégration du nouveau et aussi sur l'équipe. Tout le monde y gagne ^^

### Remerciements
Je tiens à remercier tout particulièrement les personnes qui ont voté et assisté à la présentation/table ronde du meetup
Software Craftsmanship Paris du 26 janvier 2016. Certaines des idées présentes ici sont les leurs. Encore un grand merci,
car sans eux cet article ne serait pas ce qu'il est.