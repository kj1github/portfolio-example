# Summary week 1
Lorem ipsum dolor sit amet, consectetur adipiscing elit.

change the number of epochs, eg to 5 or 10 -> 

Default with 3 epochs it goes to max 86.2 % accuracy, durataion is 1:47
10 epochs it's goes to 88.5% accuracy, duration is longer, like 6 minutes. 
So it helps a little


changing the amount of units1 and units2 to values between 16 and 1024. Use factors of 2 to easily scan the ranges: 16, 32, 64, etc.

Hoe kleiner de units, hoe slechter de prestatie, maar veel hoger dan 256 worden de prestaties ook weer minder.
units 4 = 75%, units 2 = 20%
512=87% en nog redelijk snel, 
1024 duurt lang, 86,5, duurt langer, geen winst meer
2048 nog steeds zelfde, geen winst, duurt langer


changing the batchsize to values between 4 and 128. Again, use factors of two for convenience.
standaard batch size = 86,2 = 1:47

batch size = 4 dan rond de 86,7%, duurt langer, ca 10 minuten

128 = 87,5 en 1 minuut 26, sneller en goede performance

hogere batch size lijkt iets beter, lager niet goed



change the depth of your model by adding a additional linear layer + activation function

changing the learningrate to values between 1e-2 and 1e-5

changing the optimizer from SGD to one of the other available algoritms at torch (scroll down for the algorithms)




Epochs: what is the upside, what is the downside of increasing epochs? Do you need more epochs to find out which configuration is best? When do you need that, when not?
what is an upside of using factors of 2 for hypertuning? What is a downside?

Upside: More training, better results, but cost a lot of extra compute. 


Find the [notebook](./notebook.ipynb) and the [instructions](./instructions.md)

[Go back to Homepage](../README.md)
