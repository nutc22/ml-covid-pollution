# ml-covid-pollution

### Esame Data Science e Applicazioni in Fisica - UniPG
## Osservazione del quadro epidemiologico COVID-19 e studio della possibile interazione con l'inquinamento da polveri sottili nel periodo Gennaio - Giugno 2020
##### Daniele Nucciarelli 
Perugia, 1 settembre 2023

## setup

```shell
git clone https://github.com/nutc22/ml-covid-pollution.git
chmod a+rw ml-covid-pollution
cd ml-covid-pollution

docker pull nutc22/ml-covid-pollution:0.1
docker run -it --rm --user $(id -u):$(id -g) --group-add users -v ${PWD}:/home/jovyan/work/ -p <PORT>:8888 -e GEN_CERT=yes nutc22/ml-covid-pollution:0.1
```
Ricordarsi di sostituire la porta da esporre al posto di `<PORT>`

Visitare il sito `https://<IP-ADDR>:<PORT`
e fidarsi del certificato auto firmato.


per terminare il processo `^C`

## features description

|               Feature               |                                                    Descrizione                                                   |
|:-----------------------------------:|:----------------------------------------------------------------------------------------------------------------:|
| City                                | Nome del comune                                                                                                  |
| lat                                 | Latitudine del comune                                                                                            |
| lng                                 | Longitudine del comune                                                                                           |
| Population                          | Numero di abitanti del comune                                                                                    |
| Density                             | Densità di popolazione in ab./km2                                                                                |
| Surface                             | Superficie del comune in km2                                                                                     |
| Depriv_idx                          | Indicatore della condizione socio-economica (definito rispetto alla media italiana)                              |
| CovidCases_jan_jun_2020             | Numero di casi covid registrati nel comune, nel periodo gen-giu 2020                                             |
| MaxHospitalized_jan_jun_2020        | Numero massimo di casi covid ospedalizzati nel comune, nel periodo gen-giu 2020                                  |
| AvgHospitalized_jan_jun_2020        | Numero medio di casi covid ospedalizzati nel comune, nel periodo gen-giu 2020                                    |
| Deceased_jan_jun_2020               | Numero di casi covid deceduti nel comune, nel periodo gen-giu 2020                                               |
| MaxIntensiveCare_jan_jun_2020       | Numero massimo di casi covid ricoverati in terapia intensiva nel comune, nel periodo gen-giu 2020                |
| AvgIntensiveCare_jan_jun_2020       | Numero medio di casi covid ricoverati in terapia intensiva nel comune, nel periodo gen-giu 2020                  |
| mean_pm10_ug/m3_mean_2019           | Valore medio espresso in μg/m3 della media giornaliera di pm10 rilevato nel 2019                                 |
| mean_pm10_ug/m3_std_2019            | Valore medio espresso in μg/m3 della deviazione standard giornaliera di pm10 rilevato nel 2019                   |
| mean_pm10_ug/m3_median_2019         | Valore medio espresso in μg/m3 della mediana giornaliera di pm10 rilevato nel 2019                               |
| max_pm10_ug/m3_mean_2019            | Valore massimo espresso in μg/m3 della media giornaliera di pm10 rilevato nel 2019                               |
| max_pm10_ug/m3_std_2019             | Valore massimo espresso in μg/m3 della deviazione standard giornaliera di pm10 rilevato nel 2019                 |
| max_pm10_ug/m3_median_2019          | Valore massimo espresso in μg/m3 della mediana giornaliera di pm10 rilevato nel 2019                             |
| min_pm10_ug/m3_mean_2019            | Valore minimo espresso in μg/m3 della media giornaliera di pm10 rilevato nel 2019                                |
| min_pm10_ug/m3_std_2019             | Valore minimo espresso in μg/m3 della deviazione standard giornaliera di pm10 rilevato nel 2019                  |
| min_pm10_ug/m3_median_2019          | Valore minimo espresso in μg/m3 della mediana giornaliera di pm10 rilevato nel 2019                              |
| mean_pm10_ug/m3_mean_jan_jun_2020   | Valore medio espresso in μg/m3 della media giornaliera di pm10 rilevato nel periodo gen-giu 2020                 |
| mean_pm10_ug/m3_std_jan_jun_2020    | Valore medio espresso in μg/m3 della deviazione standard giornaliera di pm10 rilevato nel periodo gen-giu 2020   |
| mean_pm10_ug/m3_median_jan_jun_2020 | Valore medio espresso in μg/m3 della mediana giornaliera di pm10 rilevato nel periodo gen-giu 2020               |
| max_pm10_ug/m3_mean_jan_jun_2020    | Valore massimo espresso in μg/m3 della media giornaliera di pm10 rilevato nel periodo gen-giu 2020               |
| max_pm10_ug/m3_std_jan_jun_2020     | Valore massimo espresso in μg/m3 della deviazione standard giornaliera di pm10 rilevato nel periodo gen-giu 2020 |
| max_pm10_ug/m3_median_jan_jun_2020  | Valore massimo espresso in μg/m3 della mediana giornaliera di pm10 rilevato nel periodo gen-giu 2020             |
| min_pm10_ug/m3_mean_jan_jun_2020    | Valore minimo espresso in μg/m3 della media giornaliera di pm10 rilevato nel periodo gen-giu 2020                |
| min_pm10_ug/m3_std_jan_jun_2020     | Valore minimo espresso in μg/m3 della deviazione standard giornaliera di pm10 rilevato nel periodo gen-giu 2020  |
| min_pm10_ug/m3_median_jan_jun_2020  | Valore minimo espresso in μg/m3 della mediana giornaliera di pm10 rilevato nel periodo gen-giu 2020              |
| Zone                                | Area geografica di appartenenza del comune                                                                       |
| Region                              | Regione di appartenenza del comune                                                                               |


## modificare o clonare l'immagine

se si desidera ri-costruire l'immagine docker:

```shell
docker build . -t datascience-notebook:<tag>
```

a questo punto si può creare il container:
```shell
docker run -it --user $(id -u):$(id -g) --group-add users -v ${PWD}:/home/jovyan/work/ -p <PORT>:8888 -e GEN_CERT=yes datascience-notebook:<tag>
```
