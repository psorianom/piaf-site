## Foire aux questions

### Usages

**A quoi sert un jeu de données de questions-réponses en français ?**

Un jeu de questions-réponses comme celui créé par PIAF sert à entraîner des intelligences artificielles sur une tâche bien spécifique du [traitement automatique du langage naturel](https://fr.wikipedia.org/wiki/Traitement_automatique_du_langage_naturel) appelé "question answering" en anglais. Ces algorithmes dit "de questions-réponses" permettent de trouver des réponses à des questions précises portant sur un ensemble de documents, en pointant une portion du texte d’origine qu'ils estiment répondre à une question de l'utilisateur. Pour permettre à ces algorithmes d'être performants sur cette tâche complexe, il est nécessaire de les entraîner, c'est-à-dire (pour faire simple) de leur montrer un très grand nombre de questions et la réponse associée. Aujourd'hui, la majorité de ces ressources ne sont disponibles presque qu'en anglais, la plus connue étant par exemple [SQuAD](https://rajpurkar.github.io/SQuAD-explorer/). La construction d'une ressource de questions-réponses en français va permettre d'évaluer la performance des algorithmes sur le français et potentiellement d'améliorer leur performance.

**Quels sont les exemples d'usages des futures données de questions-réponses en français ?**

Les cas d'usages de ces algorithmes de questions-réponses francophones sont nombreux, aussi bien pour l'administration, les entreprises, et même la recherche. Rien que dans les services public, [les possibilités sont déjà nombreuses](https://piaf.etalab.studio/cas-usage/). Par exemple, en créant des IA capables de répondre correctement à des questions, on peut construire des agents conversationnels (ou chatbots) plus performants pour répondre à des questions simples des citoyens tout en libérant du temps aux (vrais) agents pour répondre à des demandes plus complexes. Ou encore pour améliorer des outils pré-existants : par exemple, dans le [code du travail numérique](https://code.travail.gouv.fr/), qui permet aujourd'hui de poser questions sur le droit du travail et d’obtenir en réponse des extraits pertinents de textes légaux, une IA de questions-réponses permettrait de surligner précisément dans le texte obtenu la réponse et ainsi faciliter la recherche d'informations. 

### Données / Démarche scientifique

**Pourquoi avoir élaboré un protocole comparable à SQuAD ?**

Notre démarche comporte un volet scientifique. Nous avons fait le choix de nous inspirer d'une démarche réalisée par l'Université de Standford, le projet SQuAD (pour "[Stanford Question Answering Dataset](https://rajpurkar.github.io/SQuAD-explorer/)"), qui a permis de construire un jeu de données de questions-réponses en anglais. Le [protocole](https://piaf.etalab.studio/protocole-fr/) que nous avons élaboré s'inspire de SQuAD afin de rendre les évaluations de notre travail comparables aux résultats obtenus avec leur jeu de données.

**Pourquoi avoir sélectionné des articles issus de Wikipédia pour constituer le jeu de questions-réponses ?**

Afin de se rapprocher le plus possible de la méthodologie du projet SQuAD, les données de questions-réponses sont collectées à partir d'extraits d'articles de Wikipédia en français.

**Comment les extraits d'articles Wikipédia ont-ils été sélectionnés ?**

Afin de disposer d'une diversité d'articles (thèmes et types de rédaction), nous avons sélectionné environ 1 500 articles parmi les 25 000 les plus populaires sur Wikipédia (en utilisant PageRank, l'algorithme qui mesure la centralité d'une page sur le Web). Nous avons ensuite "découpé" ces articles en "chapitres" de 5 paragraphes pour faciliter l'annotation et avons classé ces extraits selon le type de données en sortie (test, évaluation, entraînement). Sur l'interface d'annotation, les extraits sont classés en 8 thématiques, ce qui ouvre un choix aux utilisateurs.

Cette démarche est documentée dans [le protocole (section 7.1)](https://piaf.etalab.studio/protocole-fr).

**Quels sont les chiffres clés sur le jeu de données à annoter ?**

Nous parlons du chiffre 100 000 pour simplifier le nombre de questions-réponses attendus. Pour être précis, il s'agira de collecter 87 230 questions-réponses. Pourquoi ce chiffre ? Il est dû à la sélection technique des paragraphes Wikipédia, et cette sélection est expliquée plus en détail dans [le protocole](https://piaf.etalab.studio/protocole-fr/).

Ces 87 230 questions-réponses vont être produits à partir de 17 446 paragraphes (5 questions-réponses par paragraphe), eux-mêmes issus de 1 446 articles Wikipédia. Pour rendre plus sympathique l'annotation, nous avons manuellement créé des "thèmes". Voici la distribution des articles par thème :
Arts : 280
Géographie : 207
Histoire : 290
Religion : 101
Sciences : 242
Société et autres : 203
Sport : 123

**Sous quelle licence les données annotées seront publiées ? Et à quelle fréquence ?**

Les données d'entraînement de PIAF seront publiées en licence CC-by-SA. Comme le mentionnent nos [conditions générales d'utilisation](https://piaf.etalab.studio/cgu.html), pour des questions d'évaluation scientifique, une partie de données (10%) ne sera pas rendue publique. Cette partie permettra d'élaborer un "leader board" pour que des acteurs puisse comparer la performance de leurs modèles entraînés sur PIAF.

**A quoi correspondent les différentes données (test, évaluation, entraînement) collectées ?**

Il s'agit de trois sous-domaines du jeu de données de questions-réponses final :
* **Test** (10% des articles sources) + **Evaluation** (10% des articles sources) = **Développement** : données qui doivent être de qualité, qui permettront d'évaluer la qualité de la démarche et à des modèles existants d'évaluer leur performance.
* **Entraînement** (80% des articles sources) : données moins robustes en qualité, qui correspondent aux 80 000 questions-réponses qui permettront d'entraîner des algorithmes pour des applications diverses.

**Quels modèles peut-on entraîner sur la base de données collectées ?**

Les données collectées peuvent être utilisées comme vous le souhaitez à condition de respecter la licence CC-by-SA.   

**Quels sont les risques d'introduction de biais dans la démarche ?**

Les risques de biais sont multipes. Nous avons 2 exigences principales pour réduire l'impact des biais :   
* **la diversité** : si les données issues de la collecte ont été produites par un trop petit nombre d'annotateurs, ou une catégorie unique de francophones, il est possible que les données de questions-réponses n'embrassent pas la diversité de la langue française ; 
* **la qualité** : il est important de disposer d'ensemble de questions-réponses assez complexes sur un texte. C'est pour cela que nous formons les contributeurs et analysons régulièrement la qualité des données collectées.

**Comment s'assurer de la qualité de la base de données ?**

Pour entraîner des IA performantes sur les données, nous avons besoin de nous assurer de la qualité des contributions à la base de données. Deux axes sont sources particulières d'attention :
* éviter les contributions malveillantes ;
* vérifier le niveau de compréhension de la tâche avec des indicateurs statistiques.

### Annotation / Questions-réponses

**Pourquoi est-il nécessaire de se créer un compte avant d'annoter ?**

En vous créant un compte, à partir uniquement d'une adresse mail, vous pourrez avoir un suivi de vos annotations. De notre côté, un compte nous permet d'assurer la qualité des annotations en bloquant les bots et en nous offrant la possibilité d'analyser le nombre et le niveau de diversité de nos contributeurs.

**Pourquoi faire appel à une méthode de contribution volontaire ?**

Contrairement à d'autres démarches qui font appel à des plateformes de microtravail, nous avons fait le choix d'une méthode de collecte des données basée sur le volontariat. D'autres voies sont possibles, par exemple le recrutement d'annotateurs, et il n'est pas impossible que nous faisions ce choix à un stade de notre projet.

Notre pari du volontariat tient d'une double intuition : la constitution d'une base de données ouverte à besoin de tous - facteur de quantité et de diversité - et se fait au bénéifce de tous - base de donnée réutilisable et cas d'usage bénéficiant au plus grand nombre. Un volontaire participe donc à la constitution d'une infrastructure d'intérêt général dont il pourra par la suite bénéficier de manière directe ou indirecte. 

Ce choix du volontariat s'inscrit aussi dans les valeurs de pédagogie d'Etalab. PIAF comporte ainsi un "aspect explicatif de l'IA". PIAF permet aux participants d'enrichir leurs connaissances sur l'IA et leur permet d'agir directement dans sa création. Consulter notre [charte de contribution](https://piaf.etalab.studio/contribution.html). 

**Est-ce grave de faire des erreurs d’orthographe en posant des questions ?**

Vous pouvez faire des erreurs d'orthographes lorsque vous posez des questions. Premièrement, lors de l'analyse, nous pourrons facilement corriger des petites erreurs. Deuxièment, PIAF entraine l'IA à comprendre notre langage et, soyons honnètes, dans notre quotidien, les fautes arrivent ! 

Par ailleurs, vous pouvez également poser des questions dont la réponse dans le texte n'est pas 100% cohérente en termes de syntaxe. Par exemple, cette paire est tout à fait possible : 

* Question : quelle langue était parlée dans la région de l'Acadie ?
* Réponse : francophone

**Quels types de questions faut-il poser pour disposer de données de qualité ?**

L'enjeu principal est le suivant : il faut formuler une question dont la réponse se trouve dans le texte.

Quelques conseils pour vous guider : 
* Poser des questions qui ne reprennent pas les mots exacts du texte : paraphraser, c'est la clef.
* Ne pas poser une question équivoque c'est à dire qui peut avoir plusieurs réponses différentes situées à différents du texte.
* Faire simple et court : plus la réponse à votre question est courte, mieux c'est.
* Ne pas hésiter à poser des questions *comment*, *pourquoi* : le but, c'est d'apprendre à des robots à comprendre le français.
* Lorsque vous êtes coincés, n'hésitez pas à chercher une réponse dans le texte et trouver dans un second temps la question qui correspond. 

**A quel point les questions peuvent-t-elles être complexes ?**

Les questions peuvent être complexes mais l'IA doit pouvoir les comprendre. En pratique :
* L'IA a une culture générale d'un enfant de 8 ans.
* L'IA sait qu'elle lit tel article et spécifiquement tel paragraphe. Ainsi, elle connait le contexte.
* Cette contextualisation a certaines limites. Par exemple, si vous êtes spécialiste d'Harry Potter mais que l'extrait que vous annotez ne comporte pas de mention des cours de Quidditch, vous ne pouvez pas en parler dans la question.

