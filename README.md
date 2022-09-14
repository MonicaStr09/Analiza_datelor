 # Dezvoltare Software pentru Analiza Datelor

                                ANALIZA ÎN COMPONENTE PRINCIPALE - ANIMALE ZOO
 
 
# Motivatia alegerii temei si a metodei de analiza

În cadrul acestui proiect pentru disciplina Analiza Datelor, am ales să efectuez analiza în componente principale pentru animalele de la Zoo.
Analiza în Componente Principale permite abordarea caracterului multidimensional a datelor (variabilelor) ce caracterizează un individ. Principiul fundamental al acestei metode este de a extrage cel mai mic număr de componente care să recupereze cât mai mult din informaţia totală conţinută în datele originale, aceste noi componente exprimând atribute noi ale indivizilor şi construite astfel încât să fie necorelate între ele, fiecare din aceste noi variabile fiind o combinaţie liniară de variabile originale
Deşi la baza acestei metode stă acelaşi principiu ca şi la analiza factorială (în principiu este o metodă factorială liniară), analiza în componente principale diferă de aceasta prin modul de definire a elementelor tabelului de date iniţial şi modul de calcul al distanţelor dintre puncte. Ca metodă descriptivă de analiză a datelor se aplică doar variabilelor cantitative şi tabelelor de dimensiuni mari care cuprind informaţii referitoare la mai mult de 15 indivizi şi 4 variabile. De aceea, am ales-o pentru a analiza influența anumitor trăsături ale animalelor de la zoo.

# Setul de date ales

În acest set de date, denumit zoo2.csv și extras de la adresa https://www.kaggle.com/agajorte/zoo-animals-extended-dataset  , se află 43 de observații care conțin detalii despre 13 trăsături, precum în imaginea de mai jos.
![image](https://user-images.githubusercontent.com/94632149/189905029-3c2b5a3d-8cb7-4ddd-aa29-b9c6cdfedfd7.png)

Datele sunt extrase în urmă cu 4 ani, precum este specificat și pe site și reprezintă animale din diferite clase, exceptând Mamiferele și Păsările, fiind extrem de întâlnite în multe alte seturi de date. Acest set de date este des utilizat în Machine Learning, și astfel l-am ales pentru a obține rezultate concludente și ușor de interpretat. De asemenea, este indicat pentru a fi utilizat în clasificări.


# Rezultate si interpretari

Primii pași în conceperea unei analize sunt constituiți de pregătirea unui script corespunzător ( precum cel de la seminar), care conține fișiere .py cu funcții, grafice și clase concepute în acest sens, toate integrate și apelate în fișierul main.
Am importat librăriile necesare, am extras datele din fișierul csv, eliminând valorile NaN și păstrând totodată într-un vector numele variabilelor observate pentru utilizarea lor ulterioară, dar am și creat modelul ACP din clasa eponimă. Funcțiile integrate au generat și grafice - 
![image](https://user-images.githubusercontent.com/94632149/189905297-ef95b776-e5c1-411e-b46f-8a8e53adbe8b.png)

 Astfel, în graficul anterior creat se află varianța componentelor din cadrul modelului meu. Componentele principale sunt construite sub formă de combinații liniare de variabile inițiale, care concentrează o cât mai mare parte din varianță. Fiecare componentă preia o parte din varianța ramasă neexplicată de cele precedente. 
 Apelul funcției de varianță generează și un fișier csv – 
![image](https://user-images.githubusercontent.com/94632149/189905413-3d85bfed-50e6-44cc-b08e-d6a382744212.png)

Astfel, sunt salvate date pentru fiecare componentă.  Varianța pentru componenta 1 este 4.91, înseamnând că aceasta concentreză de 4.91 ori mai multă informație decât o variabilă obișnuită. Aceasta explică o mare parte din varianța totală, mai exact 36%. De asemenea, este reprezentată și varianța cumulată, dar și procentul cumulat. Echivalent se interpretează și datele pentru celelalte componente. Practic, 6 componente sunt suficiente pentru a explica o varianță de 90%.

  În continuare, urmează corelațiile factoriale - cu cât o valoare este mai apropiată în modul de 1, cu atât acea variabilă este mai semnificativă pentru componenta aleasă. Observăm că prezența cozii are cea mai mare corelație, de 88% pentru componenta 1, care reprezintă airborne – viața aeriană a animalului. Astfel, ne așteptăm ca variabilele cu mai mute picioare să fie în dreapta plotului instanțelor care au componenta 1 pe axa OX. 
![image](https://user-images.githubusercontent.com/94632149/189905665-f5d4af61-c342-487e-8748-bc47b883729e.png)

	Aceste colerații pot fi vizualizate într-o manieră extrem de facilă și în graficele de mai jos, în care pe axele ox și oy avem primele două componente, pentru primul grafic, și componenta 1 cu 3 în cel de-al doilea, deoarece în ele regăsim cele mai mari valori.
![image](https://user-images.githubusercontent.com/94632149/189905756-2cd33d27-66f1-46a8-a2b4-575e0458c05e.png)
![image](https://user-images.githubusercontent.com/94632149/189905819-3033f34f-f68c-4fed-916a-b65e18a545e1.png)

 De asemenea, s-a creat și un grafic, cel de mai jos, în care sunt reprezentate toate cele 43 de observații inițiale, animale, pe fiecare componentă. Astfel, se observă coeficientul pe scorurile, adică componentele principale standardizate:
![image](https://user-images.githubusercontent.com/94632149/189905900-317c6c69-773c-406b-89df-157d41f6b5e0.png)

 Ulterior, se calculează cosinusurile, care denotă faptul că o instanță este cu atât mai bine reprezentată pe o axă cu cât cosinusul unghiului format între vectorul punct asociat instanței și axa respectivă este mai mare:
![image](https://user-images.githubusercontent.com/94632149/189905992-77fc3593-dd81-48ef-a675-a7bb7d2eef39.png)

 Se observă că unele componente au un cosinus de aproape 1, precum animalul marlin sau trout pentru cea de-a doua componentă, denumită aquatic, ce arată dacă animalul respectiv provine din mediul acvatic sau nu. 
În continuare, se află contribuțiile, care arată ce procent din varianța axei este datorat instanței alese. O parte din aceste contribuții salvate și într-un csv le-am ilustrat mai jos:
![image](https://user-images.githubusercontent.com/94632149/189906106-d7547ea2-5596-4b77-a75f-65ae31470355.png)

 Din nou, se observă o contribuție mare a peștilor și a altor animale marine pentru componenta cu numărul doi, care specifică acvaticitatea animalelor, fapt ce se justifică de altfel.  
Urmează comunalitățile - care reprezintă cantitatea de varianță explicată în comun de către un grup din componentele principale. O parte din valorile calculate sunt ilustrate și mai jos.
![image](https://user-images.githubusercontent.com/94632149/189906228-991b7883-e853-415e-ac12-1e09c17bd426.png)

Pentru o mai bună vizualizare a rezultatelor, voi atașa și graficul desenat.
![image](https://user-images.githubusercontent.com/94632149/189906304-5de7af2a-3d69-4185-ad9c-ba1f4aebc2c9.png)

Aceasta manifestă procentul varianței unei variabile explicată de factorii reuniți, și poate fi interpretată ca siguranța indicatorului reprezentat de acea variabilă.
Valorile mici indică faptul că o caracteristică nu este bine reprezentată de acea componentă, astfel de valori regăsindu-se pentru proprietatea venomous. În schimb, backbone are cele mai mari valori.

# Concluzii

 În urma analizei efectuate, am obținut o sumedenie de rezultate asupra celor 43 animale de la zoo, ce reprezintă observații, și cele 13 variabile inițiale, proprietăți ale acestor viețuitoare necuvântătoare, constituite în componente. Prin puterea acestei metode de analiză a datelor, am realizat diferite grafice rezultate în urma funcțiilor modelului ACP, pe care le-am intepretat anterior. 
Componentele ACP explică maximul varianței și sunt ortogonale între ele, fiind combinații liniare are variabilelor observate. Această metodă este una observațională de reducere a dimensionalității. 
