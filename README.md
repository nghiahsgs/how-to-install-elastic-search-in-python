# how-to-install-elastic-search-in-python
how to install elastic search in python


## Install elastic search in macos
```
brew tap elastic/tap
brew install elastic/tap/elasticsearch-full
```

```
brew services start elastic/tap/elasticsearch-full
brew services info elastic/tap/elasticsearch-full
```

```
elasticsearch
```

```
curl localhost:9200
```

## Install elastic search in python
```
pip install elasticsearch
pip install elasticsearch[async]
```

```
from datetime import datetime
from elasticsearch import Elasticsearch
es = Elasticsearch()

doc = {
    'author': 'kimchy',
    'text': 'Elasticsearch: cool. bonsai cool.',
    'timestamp': datetime.now(),
}
resp = es.index(index="test-index", id=1, document=doc)
print(resp['result'])

resp = es.get(index="test-index", id=1)
print(resp['_source'])

es.indices.refresh(index="test-index")

resp = es.search(index="test-index", query={"match_all": {}})
print("Got %d Hits:" % resp['hits']['total']['value'])
for hit in resp['hits']['hits']:
    print("%(timestamp)s %(author)s: %(text)s" % hit["_source"])
```

## More informations
```
https://elasticsearch-py.readthedocs.io/en/v8.5.1/
```
