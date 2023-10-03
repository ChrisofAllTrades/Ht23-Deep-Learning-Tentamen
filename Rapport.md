# Rapport
## Introduktion
Uppgiften består i att undersöka en deep learning-modell för ansiktsuttryckigenkänning byggd av Akshit Madan (hädanefter kallad *grundmodellen*) och få den att fungera i min egen miljö. Den här rapporten beskriver tillvägagångssättet.
### Bakgrund
En Deep Learning-modell tränad på bilder av ansikten med olika uttryck som analyserar en kamerafeed i realtid och markerar upptäckta ansiktsuttryck med en kvadrat och en etikett.
#### Syfte
Det är användbart att kunna utröna ansiktsuttryck på människor i många olika sammanhang. Det skulle till exempel kunna användas inom sjukvården i videosamtal med patienter för att see hur de reagerar på behandlingen. Ett annat användningsområde skulle kunna vara att övervaka förare av diverse fordon för att se huruvida de är trötta, alerta, fokuserade eller distraherade.
#### Frågeställning
- För att träna en modell på ansiktsigenkänning, vilken typ av neuralt nätverk behövs?
- Vilken data finns tillgänglig till att träna modellen?
- Vad är en rimlig precision i modellen?
    - Kan jag bygga en bättre modell än den som fanns tillgänglig inför uppgiften?
- Hur kan en överföra den tränade modellen till att läsa av en livefeed från en kamera?
## Databeskrivning / EDA (Exploratory Data Analysis)
Datasetet i projektet är "Face expression recognition dataset" av Jonathan Oheix och är taget från Kaggle (https://www.kaggle.com/datasets/jonathanoheix/face-expression-recognition-dataset). Det innehåller ett träningsset med 28823 bilder och ett valideringsset med 7066 bilder fördelat på sju kategorier, som vardera representerar ett av följande ansiktsuttryck: ['angry', 'disgust', 'fear', 'happy', 'neutral', 'sad', 'surprise']. Alla bilder är 48x48 pixlar stora och är i gråskala.

Det innehåller en stor mängd olika ansikten av alla åldrar, kön och utseenden hos människor och bilderna verkar vara tagna i olika naturliga situationer i varierande ljusa och mörka bakgrunder. Bilderna är beskurna så att ansiktet tar upp i stort sett hela filen. Jag kunde inte upptäcka några outliers eller defekta bilder i datasetet.
## Metod och Modeller (Teori)
Grundmodellen använder funktionen ImageDataGenerator för att bygga dataseten av bilderna och eftersom de redan är indelade i ett tränings- och ett valideringsset behövs inte det göras i funktionen.
Grundmodellen bygger på en stack av fyra Convolutional Neural Networks som vardera består av ett Conv2D-lager, ett BatchNormalization, ett Activation-lager med ReLU, ett MaxPooling2D-lager och ett Dropout-lager. De följs av ett Flatten-lager och två Dense-lager med BatchNormalization, Activation-lager med ReLU och Dropout.

- Data redan indelad i tränings- och valideringsset så behöver inte göra det själv
- Mindre urval för att testa olika modeller
## Projekt Resultat och Analys
Resultat är deskriptiva i sin natur, t.ex. att man presenterar RMSE för sina olika modeller om man har ett regressionsproblem. Ofta kan tabeller vara användbara vid redogörelse av resultaten.
## Slutsats och förslag på potentiell vidareutveckling
- Utveckla verifikationsprocessen för datakvaliteten (outliers)
- Data augumentation

## Redogörslse
- För att få en bättre känsla för datasetet byggde jag ut grundmodellens funktion till att visa tre bilder från varje kategori istället för nio bilder från en.
- La till validation_split i träningssetet
- För att testa potentiella modeller och testa koden körde jag på en mindre del av datasetet först.
- Testade att grundkoden fungerade innan jag gjorde större ändringar
- Output function as per tabell 10-1 och 10-2
- Antar MSE - inga outliers i dataseten
### Utmaningar du haft under arbetet samt hur du hanterat dem.
- Deprekerade paket i kodexemplet
    - Borde ha kört modellen med deprekerade paket bara för att få den att funka direkt. Nu gjorde jag nya funktioner direkt för att bygga dataseten.
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
- https://www.tensorflow.org/tutorials/load_data/images