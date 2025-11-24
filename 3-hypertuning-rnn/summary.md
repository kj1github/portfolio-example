# Verslag experimenten met RNN-modellen voor gesture recognition 

## Doel  
Het doel van dit experiment was het verbeteren van de prestaties van een  RNN-model voor classificatie van de Gestures. We hebben systematisch gevarieerd met hyperparameters (hidden size, aantal lagen), RNN-types (GRU vs. LSTM) en toevoeging van convolutielagen.

---

## Startpunt  
Het basismodel (GRU, hidden size = 64, 1 laag) haalde een initiële accuracy van ca. 48%. Dit ligt boven toevalsniveau (5%, bij 20 klassen)..

---

## Variatie in hidden size  
- Kleine hidden sizes (1–16) presteerden slecht (3–21%).  
- 64 units gaf ~48% (default, training in enkele seconden).  
- 128 units gaf een forse sprong naar ~76%.  
- 256–512 units bereikten >90% (tot ~96%), maar met langere trainingstijden (30–60 seconden).  
- 2048 units bereikte bijna 99%, maar training duurde ~12 minuten.  

**Conclusie:** vergroten van hidden size levert de grootste winst op, maar met sterk stijgende rekentijd.

---

## Variatie in aantal lagen  
- 1 laag (64 units): ~50%.  
- 3 lagen (64 units): ~67% (30 sec).  
- 6 lagen (64 units): geen verdere verbetering (~60%).  
- 128 hidden size, 3 lagen: ~92% in 40 sec.  

**Conclusie:** meer lagen tot ca. 3 helpt, maar méér lagen levert geen extra winst en kost extra tijd.

---

## GRU versus LSTM  
- Default GRU: ~51%.  
- Default LSTM: ~46%.  
- Met 128 hidden size, 1 laag: LSTM ~54%, GRU ~76%.  
- Met 3 lagen, 128 hidden size: GRU ~91%, LSTM ~52%.  

**Conclusie:** in deze dataset presteert GRU duidelijk beter dan LSTM bij vergelijkbare instellingen.

---

## Conv1D-lagen  
- Input `(batch, tijd, features)` moest worden omgezet naar `(batch, features, tijd)` om met `nn.Conv1d` te werken (bv. 32×3×31).  
- Convolutie werd correct toegepast en leverde prestaties vergelijkbaar met RNN’s.  
- Conv1D kan nuttig zijn om lokale patronen te leren, maar gaf in dit experiment geen grote winst boven de sterkere RNN-instellingen.

---

## Eindconclusie  
- De grootste prestatieverbetering kwam door opschalen van hidden size en het gebruik van 3 lagen GRU.  
- GRU’s zijn robuuster en efficiënter dan LSTM’s in dit scenario.  
- Conv1D-lagen werken technisch correct maar gaven geen doorslaggevende verbetering.  
- Met de juiste hyperparameters zijn accuracies van >90% haalbaar, en zelfs ~99% met zeer grote modellen (maar dit is minder efficiënt).
