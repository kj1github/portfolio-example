# Summary week 1

Change the number of epochs, eg to 5 or 10 -> 

Default with 3 epochs it goes to max 86.2 % accuracy, durataion is 1:47
10 epochs it's goes to 88.5% accuracy, duration is longer, like 6 minutes. 
So it helps a little

Changing the amount of units1 and units2 to values between 16 and 1024. Use factors of 2 to easily scan the ranges: 16, 32, 64, etc.

Hoe kleiner de units, hoe slechter de prestatie, maar veel hoger dan 256 worden de prestaties ook weer minder, in ieder geval niet beter
units 4 = 75%, units 2 = 20%
512=87% en nog redelijk snel, 
1024 duurt lang, 86,5, duurt langer, geen winst meer
2048 nog steeds zelfde, geen winst, duurt langer


changing the batchsize to values between 4 and 128. Again, use factors of two for convenience.

batch size 4 = 86,7%, 10 minuten
batch size 32 =  86,9%, 4 minuten
batch size 64 = 86,2 = 2 minuten (standaard)
batch size 128 = 87,5% en 1,5 minuut

hogere batch size lijkt iets beter, lager niet goed


change the depth of your model by adding a additional linear layer + activation function
       nn.Linear(units2, units2),
            nn.ReLU()

standaard:
1,5 minuut, 87%% 
Extra laag: 
2 minuut, 86,6%

Extra laag niet perse voordelig, mogelijk spelen met unit grootte, nu niet gedaan.

changing the learningrate to values between 1e-2 and 1e-5

nu zit learning rate scheduler er al in, ik zie (nog) niet waar ik dat kan aanpassen

changing the optimizer from SGD to one of the other available algoritms at torch (scroll down for the algorithms)

kwam ik niet uit 


Epochs: what is the upside, what is the downside of increasing epochs? Do you need more epochs to find out which configuration is best? When do you need that, when not?
what is an upside of using factors of 2 for hypertuning? What is a downside?

Upside: More training, better results, but cost a lot of extra compute. 


# 2. Reflect
Doing a master means you don't just start engineering a pipeline, but you need to reflect. Why do you see the results you see? What does this mean, considering the theory? Write down lessons learned and reflections, based on experimental results. This is the `science` part of `data science`.

You follow this cycle:
- make a hypothesis
Epoch's gaan omhoog, dan accuracy ook.
- design an experiment
Aanpassen aantal epoc's
- run the experiment

# 3. Report:

Hypothesis

Ik verwachtte dat meer epochs en grotere netwerken (meer units) zouden zorgen voor hogere accuracy. 

Experiments & Results
Epochs

3 epochs: 86,2% accuracy (1:47 min)

10 epochs: 88,5% accuracy (± 6 min)
→ Meer epochs helpt iets, maar kost veel extra tijd.

Units (units1 & units2)

units = 4: 75%

units = 2: 20%

units = 512: 87%

units = 1024: 86,5% (traag)
→ Minder units is slecht, maar boven de 512 geen winst meer.

Batchsize

4: 86,7% (10 min)

32: 86,9% (4 min)

64 (default): 86,2% (2 min)

128: 87,5% (1,5 min)
→ Grotere batchsize werkt sneller en iets beter.

Extra Layer (dieper netwerk)

Standaard: 87%, 1,5 min

Met extra laag: 86,6%, 2 min
→ Geen duidelijke verbetering.

Learning rate / Optimizer

Niet getest vanwege tijd en setup-beperkingen.

Conclusie:

Meer trainen (epochs) werkt, maar de winst is beperkt vs. de tijd.

Middelgrote netwerken (256–512 units) presteren het beste. Groter wordt traag zonder extra winst.

Batchsize omhoog maakt training sneller en soms zelfs iets beter.

Extra lagen toevoegen werkt niet zomaar. Je moet dan waarschijnlijk ook andere parameters finetunen.

Combinaties van instellingen testen is belangrijk om een goede balans te vinden.


