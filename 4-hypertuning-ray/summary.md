# Summary week 4
Hypertuning fashion

1. Introduction
   In de hypertuner lessen hebben we stilgestaan bij hypertunen. In het voorbeeld werden er 2 parameters gehypertuned (hidden size en num layers) op de gestures database
   Dit notebook is aangepast naar de fashion dataset, waar we met een CNN model de 10 klasses proberen te voorspellen. Hierbij hebbnen we 2 paramaters die we hypertunen, te weten de
   learning rate en het aantal filters.
   In verband met de performance van de surf omgeving zijn de parameters beperkt qua grootte.

3. Hypothese
   Ik heb een eenvoudige hypothese neergezet:
   Een hoger aantal filters leid tot een hogere accuracy, maar ook een langere trainingstijd

4. Experiment
**Random search** 
   Er zijn met een 4-tal hypertuners (random search, bayes, hyperband en hyperopt) een 10-tal epochs gedraaid.
   De configuratie voor alle hypertuners is gelijk:
   * filters": tune.randint(2,16),
   * units1": 128,
   * units2": 64,
   * lr": tune.loguniform(1e-4, 3e-3)

   **Random search**
   
| Trial name              | Status      | Loc                  | Filters | LR          | Iter | Total time (s) | Valid loss | Train loss | Accuracy |
|--------------------------|-------------|----------------------|----------|--------------|------|----------------|-------------|-------------|-----------|
| tune_model_79a39_00000  | TERMINATED  | 192.168.3.171:62204 | 4        | 0.000309012  | 10   | 107.409        | 0.727666    | 0.731288    | 0.720453  |
| tune_model_79a39_00001  | TERMINATED  | 192.168.3.171:62203 | 14       | 0.000548393  | 10   | 245.611        | 0.384764    | 0.354075    | 0.856971  |
| tune_model_79a39_00002  | TERMINATED  | 192.168.3.171:66378 | 6        | 0.000195148  | 10   | 121.345        | 0.631182    | 0.618717    | 0.767127  |
| tune_model_79a39_00003  | TERMINATED  | 192.168.3.171:70614 | 12       | 0.000115214  | 10   | 179.696        | 0.580061    | 0.567077    | 0.777344  |
| tune_model_79a39_00004  | TERMINATED  | 192.168.3.171:70718 | 12       | 0.00122907   | 10   | 200.350        | 0.333882    | 0.317045    | 0.881010  |
| tune_model_79a39_00005  | TERMINATED  | 192.168.3.171:76905 | 7        | 0.000227039  | 10   | 123.184        | 0.557570    | 0.548583    | 0.791967  |
| tune_model_79a39_00006  | TERMINATED  | 192.168.3.171:78943 | 2        | 0.000161092  | 10   | 96.039         | 0.981258    | 0.959404    | 0.617188  |
| tune_model_79a39_00007  | TERMINATED  | 192.168.3.171:81163 | 13       | 0.000142938  | 10   | 193.846        | 0.564669    | 0.557135    | 0.789964  |
| tune_model_79a39_00008  | TERMINATED  | 192.168.3.171:81249 | 3        | 0.00127434   | 10   | 100.683        | 0.650254    | 0.643429    | 0.771034  |
| tune_model_79a39_00009  | TERMINATED  | 192.168.3.171:85391 | 13       | 0.000293134  | 10   | 197.160        | 0.477137    | 0.458287    | 0.825721  |
| tune_model_79a39_00010  | TERMINATED  | 192.168.3.171:88900 | 9        | 0.000845781  | 10   | 162.942        | 0.384921    | 0.362950    | 0.858574  |
| tune_model_79a39_00011  | TERMINATED  | 192.168.3.171:91798 | 7        | 0.00234909   | 10   | 122.680        | 0.468837    | 0.439809    | 0.829026  |
| tune_model_79a39_00012  | TERMINATED  | 192.168.3.171:93859 | 6        | 0.000134423  | 10   | 119.805        | 0.619143    | 0.602998    | 0.770132  |
| tune_model_79a39_00013  | TERMINATED  | 192.168.3.171:97904 | 2        | 0.000215996  | 10   | 97.009         | 0.907961    | 0.900510    | 0.655449  |
| tune_model_79a39_00014  | TERMINATED  | 192.168.3.171:98119 | 3        | 0.000811335  | 10   | 98.770         | 0.653565    | 0.629498    | 0.753005  |
| tune_model_79a39_00015  | TERMINATED  | 192.168.3.171:100213| 7        | 0.000300583  | 10   | 125.740        | 0.551293    | 0.536275    | 0.796775  |
| tune_model_79a39_00016  | TERMINATED  | 192.168.3.171:102306| 2        | 0.000228982  | 10   | 97.173         | 1.076780    | 1.079840    | 0.566106  |
| tune_model_79a39_00017  | TERMINATED  | 192.168.3.171:104510| 9        | 0.000230799  | 10   | 154.308        | 0.505274    | 0.490095    | 0.814002  |

<img width="927" height="405" alt="plot accuracy" src="https://github.com/user-attachments/assets/c5e59bbd-6610-43bf-b322-87cec5aa5807" />|

**Bayes**
| Trial name         | Status      | Loc                   | Filters | LR         | Iter | Total time (s) | Valid loss | Train loss | Accuracy |
|---------------------|-------------|-----------------------|----------|-------------|------|----------------|-------------|-------------|-----------|
| tune_model_5f78883e | TERMINATED  | 192.168.3.171:116842 | 7.24356  | 0.00285707  | 10   | 122.176        | 0.467691    | 0.452028    | 0.824419  |
| tune_model_65fc9c5b | TERMINATED  | 192.168.3.171:116890 | 12.2479  | 0.00183611  | 10   | 181.936        | 0.351693    | 0.327246    | 0.871294  |
| tune_model_59367f34 | TERMINATED  | 192.168.3.171:121106 | 4.18426  | 0.000552384 | 10   | 108.299        | 0.708200    | 0.657060    | 0.737179  |
| tune_model_ece80553 | TERMINATED  | 192.168.3.171:123247 | 2.81317  | 0.00261191  | 10   | 98.127         | 2.303030    | 2.302940    | 0.099960  |
| tune_model_bece31c7 | TERMINATED  | 192.168.3.171:125326 | 10.4156  | 0.00215341  | 10   | 168.489        | 0.360762    | 0.335467    | 0.871094  |
| tune_model_545c1fb1 | TERMINATED  | 192.168.3.171:127419 | 2.28818  | 0.00291274  | 10   | 95.256         | 0.761646    | 0.755690    | 0.722556  |
| tune_model_c5ccc037 | TERMINATED  | 192.168.3.171:129657 | 13.6542  | 0.000715783 | 10   | 235.216        | 0.364605    | 0.344463    | 0.866086  |
| tune_model_338aec03 | TERMINATED  | 192.168.3.171:131654 | 4.54555  | 0.000631873 | 10   | 108.945        | 0.635046    | 0.634717    | 0.757011  |
| tune_model_2d4e9dd3 | TERMINATED  | 192.168.3.171:135802 | 6.25939  | 0.00162179  | 10   | 117.782        | 0.458425    | 0.446128    | 0.831831  |
| tune_model_ed6dac3b | TERMINATED  | 192.168.3.171:138065 | 8.04723  | 0.000944565 | 10   | 121.391        | 0.417086    | 0.411803    | 0.848858  |
| tune_model_b9db59d6 | TERMINATED  | 192.168.3.171:142308 | 2.30995  | 0.000734621 | 10   | 97.280         | 0.897623    | 0.901156    | 0.643830  |
| tune_model_9f29dd0a | TERMINATED  | 192.168.3.171:144048 | 12.1279  | 0.000879826 | 10   | 213.053        | 0.381970    | 0.352440    | 0.863882  |
| tune_model_26534897 | TERMINATED  | 192.168.3.171:146430 | 12.6878  | 0.000705197 | 10   | 186.420        | 0.371561    | 0.350321    | 0.864683  |
| tune_model_4f729bd1 | TERMINATED  | 192.168.3.171:150610 | 12.4293  | 0.00241609  | 10   | 177.635        | 0.406013    | 0.331158    | 0.844752  |
| tune_model_e159aed3 | TERMINATED  | 192.168.3.171:152808 | 12.2526  | 0.000790019 | 10   | 181.222        | 0.358030    | 0.338584    | 0.868389  |
| tune_model_ab38c71d | TERMINATED  | 192.168.3.171:157042 | 12.2481  | 0.00176234  | 10   | 232.293        | 0.372272    | 0.329483    | 0.861278  |
| tune_model_a4e28031 | TERMINATED  | 192.168.3.171:159250 | 2.00000  | 0.00300000  | 10   | 98.096         | 2.302990    | 2.303010    | 0.099760  |
| tune_model_ba91d987 | TERMINATED  | 192.168.3.171:163411 | 9.53281  | 0.001040400 | 10   | 155.628        | 0.436543    | 0.404136    | 0.842248  |

**Hyperband**

| Trial name          | Status      | Loc                   | Filters | LR          | Iter | Total time (s) | Valid loss | Train loss | Accuracy |
|----------------------|-------------|-----------------------|----------|--------------|------|----------------|-------------|-------------|-----------|
| tune_model_8d9ec_00000 | TERMINATED | 192.168.3.171:169671 | 5  | 0.00291310  | 10 | 113.473 | 0.606242 | 0.587895 | 0.771935 |
| tune_model_8d9ec_00001 | TERMINATED | 192.168.3.171:169701 | 12 | 0.000136051 | 1  | 23.447  | 0.894540 | 1.364560 | 0.664964 |
| tune_model_8d9ec_00002 | TERMINATED | 192.168.3.171:169914 | 15 | 0.000244237 | 10 | 198.085 | 0.479416 | 0.463769 | 0.826222 |
| tune_model_8d9ec_00003 | TERMINATED | 192.168.3.171:174037 | 9  | 0.000241269 | 10 | 170.660 | 0.528276 | 0.517014 | 0.810096 |
| tune_model_8d9ec_00004 | TERMINATED | 192.168.3.171:178239 | 8  | 0.000239102 | 1  | 14.832  | 0.834702 | 1.108660 | 0.689503 |
| tune_model_8d9ec_00005 | TERMINATED | 192.168.3.171:178378 | 9  | 0.000601963 | 10 | 169.229 | 0.471869 | 0.456172 | 0.824219 |
| tune_model_8d9ec_00006 | TERMINATED | 192.168.3.171:180476 | 5  | 0.000156859 | 1  | 13.642  | 1.170860 | 1.633010 | 0.546174 |
| tune_model_8d9ec_00007 | TERMINATED | 192.168.3.171:180610 | 10 | 0.00292395  | 10 | 168.481 | 0.470003 | 0.425584 | 0.831130 |
| tune_model_8d9ec_00008 | TERMINATED | 192.168.3.171:184808 | 6  | 0.000973481 | 1  | 13.911  | 0.821394 | 1.044690 | 0.684595 |
| tune_model_8d9ec_00009 | TERMINATED | 192.168.3.171:184944 | 4  | 0.000971072 | 1  | 12.891  | 0.798633 | 1.132400 | 0.707332 |
| tune_model_8d9ec_00010 | TERMINATED | 192.168.3.171:185078 | 14 | 0.000115370 | 1  | 23.371  | 0.922678 | 1.403960 | 0.660056 |
| tune_model_8d9ec_00011 | TERMINATED | 192.168.3.171:187123 | 6  | 0.000133762 | 1  | 13.647  | 1.299300 | 1.819430 | 0.553786 |
| tune_model_8d9ec_00012 | TERMINATED | 192.168.3.171:187162 | 14 | 0.00259551  | 10 | 203.759 | 0.340534 | 0.302554 | 0.875601 |
| tune_model_8d9ec_00013 | TERMINATED | 192.168.3.171:187294 | 12 | 0.000166883 | 1  | 21.888  | 0.885238 | 1.232750 | 0.659054 |
| tune_model_8d9ec_00014 | TERMINATED | 192.168.3.171:189327 | 12 | 0.000209766 | 1  | 20.800  | 0.820914 | 1.236660 | 0.700220 |
| tune_model_8d9ec_00015 | TERMINATED | 192.168.3.171:189481 | 14 | 0.000228867 | 1  | 21.609  | 0.814945 | 1.091520 | 0.698518 |
| tune_model_8d9ec_00016 | TERMINATED | 192.168.3.171:189649 | 11 | 0.000358142 | 1  | 19.923  | 0.833489 | 1.126890 | 0.694311 |
| tune_model_8d9ec_00017 | TERMINATED | 192.168.3.171:191675 | 7  | 0.00174804  | 10 | 120.874 | 0.434041 | 0.388890 | 0.839143 |

**Hyperopt:**
| Trial name         | Status      | Loc                   | Epochs | Filters | LR          | Tune dir              | Units1 | Units2 | Iter | Total time (s) | Valid loss | Train loss | Accuracy |
|---------------------|-------------|-----------------------|--------|----------|--------------|-----------------------|--------|--------|------|----------------|-------------|-------------|-----------|
| tune_model_38a42bc5 | TERMINATED  | 192.168.3.171:195949 | 10 | 6  | 0.000169426 | /home/kkisteman_54e0 | 128 | 64 | 10 | 121.728 | 0.686279 | 0.667693 | 0.726963 |
| tune_model_a564396d | TERMINATED  | 192.168.3.171:195997 | 10 | 10 | 0.000795922 | /home/kkisteman_54e0 | 128 | 64 | 10 | 176.175 | 0.455147 | 0.384768 | 0.831330 |
| tune_model_a09f9d4c | TERMINATED  | 192.168.3.171:200241 | 10 | 3  | 0.002040940 | /home/kkisteman_54e0 | 128 | 64 | 3  | 33.420  | 0.698634 | 0.698727 | 0.743990 |
| tune_model_a27e7b67 | TERMINATED  | 192.168.3.171:202310 | 10 | 4  | 0.000818939 | /home/kkisteman_54e0 | 128 | 64 | 1  | 12.902  | 0.996006 | 1.326140 | 0.607973 |
| tune_model_cda332af | TERMINATED  | 192.168.3.171:202437 | 10 | 5  | 0.000469569 | /home/kkisteman_54e0 | 128 | 64 | 1  | 13.789  | 0.870155 | 1.128950 | 0.689904 |
| tune_model_a7d79bcc | TERMINATED  | 192.168.3.171:202521 | 10 | 13 | 0.000643964 | /home/kkisteman_54e0 | 128 | 64 | 10 | 191.255 | 0.387011 | 0.368322 | 0.864583 |
| tune_model_298c8506 | TERMINATED  | 192.168.3.171:202641 | 10 | 4  | 0.001323130 | /home/kkisteman_54e0 | 128 | 64 | 9  | 96.930  | 0.561413 | 0.551600 | 0.788161 |
| tune_model_89065420 | TERMINATED  | 192.168.3.171:206804 | 10 | 14 | 0.000406062 | /home/kkisteman_54e0 | 128 | 64 | 10 | 205.165 | 0.375180 | 0.368434 | 0.864283 |
| tune_model_fa310024 | TERMINATED  | 192.168.3.171:209062 | 10 | 8  | 0.000477676 | /home/kkisteman_54e0 | 128 | 64 | 1  | 17.150  | 0.722050 | 1.024360 | 0.735577 |
| tune_model_592b25a9 | TERMINATED  | 192.168.3.171:211076 | 10 | 13 | 0.000357855 | /home/kkisteman_54e0 | 128 | 64 | 1  | 21.946  | 0.782915 | 1.030740 | 0.703325 |
| tune_model_e4d8f9e0 | TERMINATED  | 192.168.3.171:211238 | 10 | 8  | 0.002368710 | /home/kkisteman_54e0 | 128 | 64 | 9  | 118.074 | 0.463382 | 0.414528 | 0.822917 |
| tune_model_002d3792 | TERMINATED  | 192.168.3.171:213453 | 10 | 10 | 0.000533167 | /home/kkisteman_54e0 | 128 | 64 | 1  | 20.246  | 0.707889 | 0.967459 | 0.727364 |
| tune_model_2da5bf0c | TERMINATED  | 192.168.3.171:215463 | 10 | 15 | 0.001908550 | /home/kkisteman_54e0 | 128 | 64 | 10 | 192.965 | 0.328367 | 0.287128 | 0.884615 |
| tune_model_60f3a9e1 | TERMINATED  | 192.168.3.171:215574 | 10 | 11 | 0.001912220 | /home/kkisteman_54e0 | 128 | 64 | 10 | 174.471 | 0.377187 | 0.346744 | 0.860577 |
| tune_model_fac242ce | TERMINATED  | 192.168.3.171:221800 | 10 | 11 | 0.000587241 | /home/kkisteman_54e0 | 128 | 64 | 1  | 20.917  | 0.728034 | 0.948320 | 0.694511 |
| tune_model_2d58e898 | TERMINATED  | 192.168.3.171:221871 | 10 | 4  | 0.000790767 | /home/kkisteman_54e0 | 128 | 64 | 1  | 12.539  | 0.855960 | 1.162700 | 0.680389 |
| tune_model_3bb6886a | TERMINATED  | 192.168.3.171:221991 | 10 | 14 | 0.001470440 | /home/kkisteman_54e0 | 128 | 64 | 10 | 189.239 | 0.363981 | 0.314077 | 0.872796 |
| tune_model_bfbf3411 | TERMINATED  | 192.168.3.171:223483 | 10 | 14 | 0.000739361 | /home/kkisteman_54e0 | 128 | 64 | 10 | 190.226 | 0.371764 | 0.346046 | 0.863582 |


<img width="458" height="413" alt="plot_times" src="https://github.com/user-attachments/assets/dfa56dcf-e7fe-44be-8038-c8c1c63a9faf" />

| Methode     | Epochs | Tune dir                                                    | Filters | Units1 | Units2 | LR       | Accuracy |
|--------------|---------|------------------------------------------------------------|----------|--------|--------|-----------|-----------|
| random       | 10      | /home/kkisteman/MADS-MachineLearning-course/no...         | 12.000000 | 128    | 64     | 0.001229  | 0.881010  |
| bayes        | 10      | /home/kkisteman/MADS-MachineLearning-course/no...         | 12.247915 | 128    | 64     | 0.001836  | 0.871294  |
| hyperband    | 10      | /home/kkisteman/MADS-MachineLearning-course/no...         | 14.000000 | 128    | 64     | 0.002596  | 0.875601  |
| hyperopt     | 10      | /home/kkisteman/MADS-MachineLearning-course/no...         | 15.000000 | 128    | 64     | 0.001909  | 0.884615  |


4. Analyse/reflectie
De hypertune modellen presteren uiteindelijk allemaal ongeveer hetzelfde qua accuracy. Dat suggereert dat alle methodend redelijk dezelfde combinaties hebben gevonden.
Hyperopt doet het dan het beste. De trainingstijd: Bayes en random duren het langst, hyperband en hyperopt zijn sneller. Dit is gezien de theorie ook logisch, oa hyperband stopt op tijd als hij een slechte configuratie heeft.

Hypothese controle:
 Een hoger aantal filters leid tot een hogere accuracy, maar gaat gepaard met een significate langere trainingstijd.
 Dit klopt, hogere filter leveren een hogere accuracy op dan de lage. Dit zien we in alle methoden terugkomen. Maar we zien ook dat de tijd toeneemt, hoe hoger het aantl filters, hoe langer de trainigstijd. 

 5. Reflectie
Dit kopje nog even toegevoegd voor mezelf. Het koste me veel tijd om uberhaubt een werkende omgeving te hebben. Heb meerdere itereaties gedaan, eerst vanaf scratch begonnen met een dataset, maar daar kwam ik niet uit met hypertunen. Daarna een bestaand notebook gepakt en daar de ants en bees dataset op getraind. Ook daar liep ik vast op de hypertune onderdelen. Tot slot een bestaande hypertune opdracht aangepast naar een andere dataset en daar 2 andere parameters voor gepakt. Het viel tegen hoelang het model wel niet draaide, dus dat koste ook nog veel werk. Uiteindelijk wel een werkende oplossing, maar kost me toch heel veel tijd om iets werkends te krijgen (ligt er ook aan dat ik niet dagelijks met python / hypertunen/modellen werk). Geen excuses, maar leek me goed om dit kopje toe te voegen.




[Go back to Homepage](../README.md)
