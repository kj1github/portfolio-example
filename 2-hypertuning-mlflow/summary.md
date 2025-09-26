# Verslag experimenten met dropout, normalisatie en extra lagen

## Doelstelling
Deze week stond in het teken van het uitbreiden van eerdere experimenten met meer hyperparameters en architectuurcomponenten. Volgens de opdracht zouden dropout, normalisatielagen, convolutionele/poolinglagen en logging met MLflow toegevoegd moeten worden. Daarnaast lag de nadruk op het wetenschappelijke proces: hypothese formuleren, experiment opzetten, uitvoeren en reflecteren.

## Hypothese
Mijn verwachting was dat **dropout** overfitting zou verminderen en de generalisatie zou verbeteren zonder dat de trainingstijd significant zou toenemen. Ook dacht ik dat **normalisatie** (bijv. batchnorm) zou zorgen voor stabielere training en snellere convergentie. Verder verwachtte ik dat **convolutielagen** patronen efficiënter zouden leren dan enkel dense lagen.

## Experimenten
Door omstandigheden (server bij SURF niet beschikbaar) heb ik slechts beperkt kunnen experimenteren. Ik heb vooral gekeken naar het effect van **dropout in de dense lagen**.

- Model zonder dropout (baseline): na 3 epochs een accuracy van ~87,8%.  
- Model met dropout (p=0.5 na twee dense lagen): na 3 epochs een accuracy van ~84,1%.  
- Trainingstijden bleven ongeveer gelijk (~5:47 minuten).

Ik heb ook kort gekeken naar MLflow-logging: runs worden geregistreerd, inclusief accuracy en verlies, dit kost wel veel tijd om vertrouwd mee te worden. Daarom schrijf ik het ook nog vaak apart op (configuratie en accuracy)

## Analyse
- Dropout gaf in deze configuratie **geen verbetering**, de accuracy was zelfs iets lager. Mogelijk is de dataset groot genoeg en het model klein genoeg dat overfitting nog geen groot probleem vormt.  
- De **trainingsduur veranderde nauwelijks** door het toevoegen van dropout, in tegenstelling tot mijn verwachting dat het sneller zou gaan.  
- Dit benadrukt dat de keuze van hyperparameters altijd dataset- en modelafhankelijk is. Dropout is geen garantie voor winst, zeker niet bij relatief eenvoudige modellen.  

## Reflectie
Door de technische beperkingen heb ik slechts een deel van de opdracht kunnen uitvoeren. Toch heb ik geleerd dat:
- Het belangrijk is om **één variabele tegelijk te testen**, zodat resultaten duidelijk te interpreteren zijn.  

## Conclusie
Ivm server probleem maar beperkt kunnen werken aan deze opdracht.
