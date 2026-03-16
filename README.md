# Prepoznavanje osjećaja pomoću neuronskih mreža 

Ovaj projekt koristi PyTorch za klasifikaciju izraza lica (emocija) na temelju poznatog **FER2013** skupa podataka. Projekt prolazi kroz proces učitavanja podataka, augmentacije slika, te treniranja i evaluacije nekoliko popularnih pre-treniranih modela konvolucijskih neuronskih mreža (CNN) pomoću tehnike prijenosa znanja (*transfer learning*).

## Skup podataka

Korišten je [FER2013 dataset](https://www.kaggle.com/datasets/msambare/fer2013/data) dostupan na Kaggleu. Skup se sastoji od crno-bijelih slika lica rezolucije 48x48 piksela koje su svrstane u nekoliko kategorija emocija (sreća, tuga, ljutnja, iznenađenje, neutralno, itd.). 
Slike se prije ulaza u modele transformiraju i po potrebi skaliraju na 224x224 rezoluciju kako bi odgovarale pre-treniranim mrežama.

Projekt automatski provodi podjelu originalnog skupa za učenje na **trening (80%)** i **validacijski (20%)** dio uz zadržavanje stratifikacije klasa.

## Modeli

Trenirani su i uspoređeni sljedeći arhitektonski modeli:
- **ResNet-18** 
- **ResNet-50**
- **EfficientNet-B0**

**Značajke treninga:**
- Optimizer: **AdamW** (stopa učenja: `1e-4`, opadanje težina: `1e-4`)
- Funkcija gubitka: **CrossEntropyLoss**
- Augmentacija podataka: nasumično okretanje (HorizontalFlip), rotacija, te skalirani izrezi (ResizedCrop).
- Broj epoha: 10 po modelu (bilježe se težine iz epohe s najboljom validacijskom točnošću).
