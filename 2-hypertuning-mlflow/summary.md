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

Ik heb ook kort gekeken naar MLflow-logging: runs worden geregistreerd, inclusief accuracy en verlies, maar ik heb dit nog niet volledig benut om systematisch hyperparameters te vergelijken. Convolutielagen en normalization layers zijn in dit experiment nog niet verder uitgewerkt.

## Analyse
- Dropout gaf in deze configuratie **geen verbetering**, de accuracy was zelfs iets lager. Mogelijk is de dataset groot genoeg en het model klein genoeg dat overfitting nog geen groot probleem vormt.  
- De **trainingsduur veranderde nauwelijks** door het toevoegen van dropout, in tegenstelling tot mijn verwachting dat het sneller zou gaan.  
- Dit benadrukt dat de keuze van hyperparameters altijd dataset- en modelafhankelijk is. Dropout is geen garantie voor winst, zeker niet bij relatief eenvoudige modellen.  

## Reflectie
Door de technische beperkingen heb ik slechts een deel van de opdracht kunnen uitvoeren. Toch heb ik geleerd dat:
- Het belangrijk is om **één variabele tegelijk te testen**, zodat resultaten duidelijk te interpreteren zijn.  

## Conclusie
Hoewel de scope van de experimenten beperkt bleef, leverden de tests met dropout nuttige inzichten op: het gebruik ervan moet onderbouwd zijn door een duidelijke hypothese (bijvoorbeeld als er signalen van overfitting zijn). Voor de volgende ronde wil ik de experimenten uitbreiden met **batch normalization**, **convolutielagen** en meer uitgebreide MLflow-logging, zodat de interacties tussen hyperparameters beter zichtbaar worden.
