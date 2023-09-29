# Rapport
## Introduktion
### Bakgrund
### Syfte
### Frågeställning
## Databeskrivning / EDA (Exploratory Data Analysis)
- Modifiera kod till att visa bilder från fler uttryck
## Metod och Modeller (Teori)
- För att testa potentiella modeller körde jag på en mindre del av datasetet först.
## Projekt Resultat och Analys
Resultat är deskriptiva i sin natur, t.ex. att man presenterar RMSE för sina olika modeller om man har ett regressionsproblem. Ofta kan tabeller vara användbara vid redogörelse av resultaten.
## Slutsats och förslag på potentiell vidareutveckling

## Redogörslse
### Utmaningar du haft under arbetet samt hur du hanterat dem.
- Deprekerade paket i kodexemplet
- Samköra Kaggle och lokal miljö
- Klassen ImageDataGenerator deprekerad, uppdaterade kod till utils.image_dataset_from_directory istället ([TensorFlow-artikel](https://www.tensorflow.org/api_docs/python/tf/keras/preprocessing/image/ImageDataGenerator))
### Vilket betyg du anser att du skall ha och varför.
### Tips du hade ”gett till dig själv” i början av kursen nu när du slutfört den.
- Bekymra dig inte så mycket över att förstå all teoretiskt direkt från början, det är bättre att börja jobba tidigare direkt med kod för det hjälper förståelsen.
- Ha kul och våga experimentera. Det finns jättebra verktyg för att kontrollera hur väl modeller presterar.
- Det finns inget "perfekt" sätt att lösa en uppgift på, använd fantasin och iterera modellerna tills du är nöjd.

## Anteckningar
**On shuffling the validation dataset:**

Shuffling the validation data can introduce some randomness into the evaluation process, which may make it more difficult to interpret the results. For example, if you shuffle the validation data and get a different set of images each time you evaluate the model, it may be harder to compare the performance of the model across different evaluations.

However, there may be some cases where shuffling the validation data is appropriate. For example, if your validation data is sorted in some way (e.g., by class label), shuffling the data can help to ensure that the model is evaluated on a representative sample of the data. Additionally, if your validation data is very large and you are only evaluating the model on a subset of the data, shuffling the data can help to ensure that the subset is representative of the larger dataset.

- https://keras.io/keras_tuner/
- https://keras.io/guides/transfer_learning/#finetuning
