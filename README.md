# dictionary-assets
Most frequent words for foreign language learners


## Assigning word category through NLP
Word category or Part of Speech is assigned using Natural Language Processing.
In this case, Spacy, a mainstream NLP library can help do the job.

```python
# pip install -U spacy
# python -m spacy download en_core_web_sm

import spacy
from spacy.matcher import Matcher
import json
nlp = spacy.load("en_core_web_sm")

f = open(<INPUT_JSON_FILE>)
words = json.load(f)

for i in range(len(words)):
    words[i]["category"] = "".join([x.pos_ for x in nlp(words[i]["source"])])

print(words)

## export data
f = open(<OUTPUT_JSON_FILE>, 'w+')
f.write(json.dumps(words, ensure_ascii=False))
```
