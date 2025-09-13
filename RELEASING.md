# Releasing the dataset

## Recreate the raw data from glottography-data

In case of upstream changes in glottography-data:
```shell
cldfbench download cldfbench_suttles1985northwest.py
```

## Recreate the CLDF data

```shell
cldfbench makecldf cldfbench_suttles1985northwest.py --glottolog-version v5.2
cldfbench cldfreadme cldfbench_suttles1985northwest.py
cldfbench zenodo --communities glottography cldfbench_suttles1985northwest.py
cldfbench readme cldfbench_suttles1985northwest.py
```

## Validation

```shell
cldf validate cldf
```

```shell
cldfbench geojson.validate cldf
```

```shell
cldfbench geojson.glottolog_distance cldf --format pipe
```

```shell
cldfbench geojson.glottolog_distance cldf --format tsv | csvformat -t | csvgrep -c Distance -r"^0\.?" -i | csvsort -c Distance | csvcut -c ID,Distance | csvformat -E | termgraph
```

```
sius1254: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 1.09 
matt1238: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 1.25 
wash1253: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 1.36 
shos1248: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 1.56 
wiyo1248: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 1.67 
gwic1235: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 1.90 
siks1238: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 2.14 
sars1236: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 2.58 
crow1244: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 2.58 
lowe1425: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 3.34 
```