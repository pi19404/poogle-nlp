# poogle-nlp
NLP Tool for Poogle Project

poogle-nlp is a project for detecting intent from turkish sentences. I have tried to used elasticsearch indexing for solving this problem. Project developers must set specific mappings to es given below.

##### Requirements
1. elasticsearch 1.6
2. poogle-auth (https://github.com/erhmutlu/poogle-auth)
3. django 1.8.5, djangorestframework 3.3.2
4. other requirements can be installed with `pip` from /service/etc/requirements/common.txt

##### Elasticsearch Documents
1. Entity

An entity is like a variable, it has 3 field: entity_key, entity_synonyms, value. 
Example;
```json
{
    "entity_synonyms": ["İstanbul", "Megakent"],
    "value": "İstanbul",
    "entity_key":"@City"
}
```

According to above entity object, basically İstanbul and Megakent are `synonym`. If in a sentence one of them appears, it will hit this entity object.

`value` field is for later calculations, for example a user can refer to İstanbul with Megakent, but thirdparty weather api's are waiting for İstanbul as a city request.

`entity_key` shows what this entity is. In this scenario the entity is a city.

##### Elasticsearch Mapping
[/service/etc/es/mapping.json](https://github.com/erhmutlu/poogle-nlp/blob/master/service/etc/es/mapping.json)

