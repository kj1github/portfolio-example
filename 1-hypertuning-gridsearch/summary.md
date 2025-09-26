# Week 1 – Hypertuning Experimenten

## Hypothese
Ik verwachtte dat **meer epochs** en **grotere netwerken (meer units)** zouden leiden tot hogere accuracy.

---

## Experimenten & Resultaten

### Epochs
- 3 epochs: **86,2%** (1:47 min)  
- 10 epochs: **88,5%** (±6 min)  
→ Meer epochs helpt iets, maar kost veel extra tijd.

### Units (units1 & units2)
- 2 units: **20%**  
- 4 units: **75%**  
- 512 units: **87%**  
- 1024 units: **86,5%** (traag)  
- 2048 units: idem, geen winst, nog trager  

→ Te weinig units werkt slecht, maar boven de ~512 units levert het geen winst meer op en kost het vooral rekentijd.

### Batch size
- 4: **86,7%** (10 min)  
- 32: **86,9%** (4 min)  
- 64 (default): **86,2%** (2 min)  
- 128: **87,5%** (1,5 min)  

→ Grotere batch sizes trainen sneller en soms zelfs iets beter. Te kleine batch sizes zijn inefficiënt.

### Extra laag (dieper netwerk)
- Standaard: **87%** (1,5 min)  
- Extra dense laag: **86,6%** (2 min)  

→ Geen duidelijke verbetering; extra diepte vraagt waarschijnlijk om gelijktijdig aanpassen van andere parameters.

### Learning rate / Optimizer
- Niet getest wegens tijd en setup-beperkingen.  



![Hypertuning Resultaat](https://github.com/kj1github/portfolio-example/blob/main/1-hypertuning-gridsearch/2025-09-17%2021_30_49-Map2%20-%20Excel.png?raw=true)

---

## Reflectie
- **Meer epochs** geven hogere accuracy, maar de winst weegt vaak niet op tegen de extra rekentijd.  
- **Middelgrote netwerken (256–512 units)** zijn het meest efficiënt.  
- **Batch size vergroten** levert tijdswinst en soms een lichte kwaliteitsverbetering op.  
- **Extra lagen** toevoegen zonder verdere tuning helpt niet.  
- **Hypertuning** moet systematisch gebeuren: één parameter tegelijk aanpassen, resultaten analyseren en zo leren hoe hyperparameters elkaar beïnvloeden.

---

## Conclusie
- Er is altijd een trade-off tussen **modelgrootte, trainingstijd en accuracy**.  
- Voor dit experiment leveren **256–512 units, grotere batch sizes en een beperkt aantal epochs** de beste balans.  
- Combinaties van hyperparameters moeten verder onderzocht worden om een optimaal model te vinden.
