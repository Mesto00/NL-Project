## Méthodes du NLP


[Home](./)          [Historique](./Historique.html)          [Techniques du NLP](./Techniques_du_NLP.html)      [Domaines d'application du NLP](./Domaines_Application_NLP.html)

# Phase de prétraitement de texte
Les données collectées sont souvent incohérentes, incomplètes et contenant généralement beaucoup de bruit est susceptibles d’avoir des erreurs. Par conséquent, comme dans les autres domaines de la science des données, la première étape est l’étape du nettoyage et la préparation du texte brute pour le transformer en un format compréhensible. On note text = "This IS an Introduction To NLP. Tell Me how do you find it? I Hope you found it amazing and interesting."
1.	Conversion des données textuelles en minuscules 
Cette étape vise à mettre toutes les données dans un format uniforme et de s'assurer que "NLP" et "nlp" sont traités de la même manière. Donc text devient: "this is an introduction to nlp. tell me how do you find it? i hope you found it amazing and interesting."
2.	Suppression de la ponctuation
Etant donné que la ponctuation n’apporte aucune information ou valeur supplémentaire dans ce contexte, la suppression de ces instances permet d’augmenter l’efficacité de calcul en réduisant la taille des données. Donc text devient: "this is an introduction to nlp tell me how do you find it i hope you found it amazing and interesting"
3.	Tokenisation du texte
Cette étape consiste à diviser le texte d’entrée en unités minimales significatives. Cette étape est une étape obligatoire du prétraitement du texte pour tout type d'analyse.
text devient: 
['this', 'is', 'an', 'introduction', 'to', 'nlp', 'tell', 'me', 'how', 'do', 'you', 'find', 'it', 'i', 'hope', 'you', 'found', 'it', 'amazing', 'and', 'interesting']
4.	Suppression des mots d'arrêt (Stop words)
Les mots d’arrêt (Exemple : à, en, comment, quel, auquel….) n’ont aucune signification ou une signification moindre par rapport aux autres mots-clés et leur suppression permettrait de se concentrer sur l’analyse de ces mots-clés. Donc text devient: ['introduction', 'nlp', 'tell', 'find', 'hope', 'found', 'amazing', 'interesting']
5.	Stemming
Le Stemming est un processus d'extraction de la racine d'un mot. Par exemple, "Poisson", "Poissons" sont transformés en "Poisson".
Exemple: The Boys’ cars are different colors => the boy car be differ color
text devient : ['introduct', 'nlp', 'tell', 'find', 'hope', 'found', 'amaz', 'interest']
6.	Lemmatisation
La lemmatisation consiste à extraire un mot racine en tenant compte du vocabulaire. Par exemple, "good", "better" ou "best" est lemmatisé en ’’good’’.  
Par exemple si on applique le stemming sur ’’ leafs’’ on aura ’’leaf’’ comme résultat et si on l’applique sur ’’leaves’’ on aura ’’leav’’, alors la lemmatisation permet d’avoir ’’leaf’’ dans les deux cas. Donc text devient: ""['introduct', 'nlp', 'tell', 'find', 'hope', 'find', 'amazing', 'interesting']

# Vectorisation du texte
Aprés le nettoyage et la préparation des données vient la partie de vectorisation des données. Cela signifie d'encoder l’ensemble de mots en un vecteur de nombres. Cela 
peut être dait par les méthodes N-gram, Bag of Words et Word Embeddings.
## N-grams
La méthode N-grams prend en compte les voisinages des mots en considérant les mots précédents et suivants, pour voir si cela donne un sens correct et complet aux mots.
Par exemple, considérons le mot "pas mal". S'il est divisé en plusieurs mots, il ne pourra pas transmettre le mot "bon", qui est le sens réel de ce mot. Ce problème peut être résolu par N-grams.
Les N-grams sont la fusion de plusieurs lettres ou de plusieurs mots. Elles sont formés de telle manière que même les mots précédents et suivants sont capturés.
 - Les unigrammes sont les mots uniques présents dans la phrase.
- Le bigramme est la combinaison de 2 mots.
- Le trigramme est la combinaison de 3 mots et ainsi de suite.
Par exemple, pour la phrase "I am learning NLP":
- Unigrammes : “I”, “am”, “ learning”, “NLP”
- Bigrammes : “I am”, “am learning”, “learning NLP”
- Trigrammes : “I am learning”, “am learning NLP”
## Bag of words (TF-IDF) 
L'idée générale du TF-IDF est de refléter l'importance d'un mot pour un document dans une collection, et donc de normaliser les mots apparaissant fréquemment dans tous les documents.
- Fréquence des termes (TF) : La fréquence des termes est simplement le rapport entre le nombre de mots présents dans une phrase et la longueur de la phrase. La TF permet de saisir l'importance du mot indépendamment de la longueur du document. Par exemple, un mot dont la fréquence est de 3 pour une phrase de 10 mots n'a pas la même importance que pour une phrase de 100 mots. Il devrait avoir plus d'importance dans le premier scénario ; c'est ce que fait la TF.
- Fréquence inverse des documents (IDF) : L'IDF de chaque mot est le logarithme du le rapport entre le nombre total de lignes et le nombre de lignes d'un document particulier dans lequel ce mot est présent. document particulier dans lequel ce mot est présent. IDF = log(N/n), où N est le nombre total de lignes et n le nombre de lignes dans lesquelles le mot est présent. n est le nombre de lignes dans lesquelles le mot est présent. L'IDF mesure la rareté d'un terme. Des mots comme "a" et "the" apparaissent dans tous les documents du corpus. documents du corpus, mais les mots rares ne seront pas présents dans tous les documents. dans tous les documents. Donc, si un mot apparaît dans presque tous les documents, alors ce mot ne nous est d'aucune utilité puisqu'il ne nous aide pas à classer ou à recherche d'informations. L'IDF annulera ce problème.

TF-IDF est le simple produit de TF et IDF de sorte que les deux inconvénients sont traités, ce qui rend les prédictions et la recherche d'informations d'information.
## Word Embeddings
Une diffculté que font face les deux méthodes citées ci-dessus est d'arriver à saisir le contexte et le sens des mots. Les deux méthodes discutées dépendent essentiellement de l'apparition ou de la fréquence des mots. Mais nous devons examiner comment saisir le contexte ou les relations sémantiques, c'est-à-dire la fréquence à laquelle les mots apparaissent à proximité les uns des autres.
- Je mange une pomme.
- J'utilise apple

 Dans l'exemple ci-dessus, Pomme donne des significations différentes lorsqu'il est utilisé avec différents mots adjacents (proches), manger et utiliser.
 Ainsi, dans le cas d'un problème tel que la classification de documents (classification de livres dans une bibliothèque), un document est vraiment très volumineux et un nombre énorme de tokens est généré. Dans ces scénarios, le nombre de caractéristiques peut devenir incontrôlable, ce qui nuit à la précision et aux performances.
 
 Les défis ci-dessus sont relevés par Word Embeddings. Word Embeddings est une technique d'apprentissage de caractéristiques où les mots du vocabulaire sont mis en correspondance avec des vecteurs de nombres réels capturant la hiérarchie contextuelle.
 
 Word Embeddings est basée sur la prédiction et utilisent des réseaux neuronaux peu profonds pour former le modèle qui conduira à l'apprentissage des poids et à leur utilisation comme représentation vectorielle.
 - word2vec : word2vec est une framework de Google basé sur l'apprentissage profond  pour former woord Embeddings. Il utilise tous les mots du corpus entier et prédit les mots proches. Il créera un vecteur pour tous les mots présents dans le corpus de manière à ce que le contexte soit capturé. Elle surpasse également toutes les autres méthodologies dans l'espace de similarité et d'analogie des mots.

Il y a principalement 2 types dans word2vec : 
- Skip-Gram
- Continuous Bag of Words (CBOW)
### Skip-gram 
Le modèle skip-gram  est utilisé pour prédire les probabilités d'un mot étant donné le contexte du ou des mots. Prenons une petite phrase pour comprendre comment il fonctionne réellement. Chaque phrase va générer un mot cible et un contexte, qui sont les mots à proximité. Le nombre de mots à prendre en compte autour de la variable cible est appelé la taille de la fenêtre. La taille de la fenêtre doit être sélectionnée en fonction des données et des ressources dont on dispose. Plus la taille de la fenêtre est grande, plus la puissance de calcul est élevée.
### Continuous Bag of Words (CBOW)
Dans le modèle CBOW, le contexte est représenté par plusieurs mots pour un mot cible donné. Par exemple, nous pourrions utiliser "chat" et "arbre" comme mots contextuels pour "grimpé" comme mot cible. Cela nécessite une modification de l'architecture du réseau neuronal utilisé au début. La modification consiste à répliquer C fois les connexions entre l'entrée et la couche cachée, soit le nombre de mots contextuels, et à ajouter une opération de division par C dans les neurones de la couche cachée.


