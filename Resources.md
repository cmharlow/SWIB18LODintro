# SWIB 2018 Intro to Linked Open Data Workshop Resources

- Workshop GitHub repository (central source of information): [github.com/cmh2166/SWIB18LODintro](https://github.com/cmh2166/SWIB18LODintro)
- Live Workshop Google Slides: [bit.ly/SWIBLODIntroSlides](http://bit.ly/SWIBLODIntroSlides)

## Group Etherpads

- Group A: https://pad.riseup.net/p/swib-18-ws-a
- Group B: https://pad.riseup.net/p/swib-18-ws-b
- Group C: https://pad.riseup.net/p/swib-18-ws-c
- Group D: https://pad.riseup.net/p/swib-18-ws-d
- Group E: https://pad.riseup.net/p/swib-18-ws-e
- Group F: https://pad.riseup.net/p/swib-18-ws-f
- Group G: https://pad.riseup.net/p/swib-18-ws-g
- Facilitators'/Demo Pad: https://pad.riseup.net/p/swib-18-ws-facilitators
- Complete Facilitators'/Demo Pad: https://pad.riseup.net/p/swib-18-ws-done
- Wikipedia: https://en.wikipedia.org/wiki/

## Visualization & Query Services

- Our Workshop Data LODLive Visualization: http://ec2-3-120-108-78.eu-central-1.compute.amazonaws.com:8080/LodLive/app_en.html
- Other Open Data LODLive Visualization: http://en.lodlive.it/?http://dbpedia.org/resource/Riga
- Workshop Fuseki Triplestore: http://ec2-3-120-108-78.eu-central-1.compute.amazonaws.com:8080/fuseki/index.html

### SPARQL Queries Demoed

```
# Names of Workshop Participants

PREFIX schema: <http://schema.org/>

SELECT * WHERE {
  ?person schema:name ?name .
}
```

```
# Acquaintances of workshop participants

PREFIX schema: <http://schema.org/>

SELECT * WHERE {
  ?who schema:knows ?whom .
}
```

```
---
# Acquaintances of workshop participants by name

PREFIX schema: <http://schema.org/>

SELECT ?namewho ?namewhom WHERE {
  ?who schema:knows ?whom .
  ?who schema:name ?namewho .
  ?whom schema:name ?namewhom .
}
```

```
# Localities and Countries of workshop participants

PREFIX schema: <http://schema.org/>
PREFIX dbo: <http://dbpedia.org/ontology/>

SELECT * WHERE {
  ?person schema:location ?place .
  ?place dbo:country ?country .
}
```

```
# Shared Interests of workshop participants
PREFIX schema: <http://schema.org/>
PREFIX dbo: <http://dbpedia.org/ontology/>
PREFIX z: <https://pad.riseup.net/p/swib-17-ws-facilitators#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
SELECT * WHERE {
  z:ub foaf:interest ?interest .
  ?person foaf:interest ?interest .
  FILTER (?person != z:ub)
}
```

```
# Home cities with population greater than 100.000 people of workshop participants

PREFIX schema: <http://schema.org/>
PREFIX dbo: <http://dbpedia.org/ontology/>

SELECT * WHERE {
  ?person schema:location ?place .
  ?place dbo:populationTotal ?population .
  FILTER (?population > 100000) .
}
```
