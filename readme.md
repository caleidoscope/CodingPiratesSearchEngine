# Her er nogle citater som vi skal lave en søgemaskine ovenpå. Forestil dig at de repræsenterer alle hjemmesider, bøger, artikler, blogs mv på hele internettet

Beregning af Term Frequency

```python

# data og variable
quotes = [ 
    "Forskellen mellem arkæologer og kosmetikere består i, at de første udgraver oldtidsminder, og de sidste dækker dem til.",
    "Man skal ikke kaste med Sten, hvis hans far er i nærheden.",
    "Det er bedre at se godt ud langtfra, end at se langtfra godt ud.",
    "Tro kan flytte bjerge, men almindelig sund fornuft kan få folk til at gå udenom.",
    "Der findes ingen dumme spørgsmål, kun dumme mennesker."
]

# tokeniserede sætninger
documents = []

# beregnede Term Frequency score
tf_scores = []

# modtager en tekst streng og returnere en renset liste af ord
def tokenize(text):
    return text.replace(',','').replace('.','').lower().split()

# beregner term frequency per ord i dokument
def compute_tf1(doc):
    tf_score = {}
    length_of_quote = len(doc)
    for word in set(doc):
        tf_score[word] = doc.count(word) / length_of_quote
    return tf_score

# beregner term frequency per ord i dokument vha indbygget funktion
def compute_tf2(doc):
    term_count = Counter(doc)
    total_terms = len(doc)
    return {term: count / total_terms for term, count in term_count.items()}

def find_all_words(documents):
    all_words = set()
    for doc in documents:
        for word in doc:
            all_words.add(word)
    return all_words

def compute_idf(words):
    idf_scores = {}
    for word in words:
        docs_count = 0
        for doc in documents:
            if word in doc:
                docs_count += 1
        idf_scores[word] = math.log(len(documents) / docs_count)
    return idf_scores

def compute_tf_idf(tf_score):
    tf_idf_score = {}
    for key, value in tf_score.items():
        tf_idf_score[key] = value * idf_scores[key]
    return tf_idf_score

# Script start

# Preprocessing
for quote in quotes:
    documents.append(tokenize(quote))
#print("Documents:",documents)

# Calculate Term Frequence
for doc in documents:
    tf_scores.append(compute_tf1(doc))
#print("TF Scores:",tf_scores)

# Find all words
all_words = find_all_words(documents)
idf_scores = compute_idf(all_words)
#print("IDF Scores:", idf_scores)
```
