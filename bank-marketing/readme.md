
1. Dataset-ul nu contine valori lipsa sau aberante. Dataset-ul contine atat variabile numerice cat si categorice,
 variabila target e ultima coloana din dataset si anume "deposit" care poate fi "yes" ceea ce inseamna ca clientul isi va deschide depozit sau "no" adica nu isi va deschide depozit.
 Variabilele care sunt mai importante pentru prezicerea variabilei target din pct meu de vedere sunt: "age" care reprezinta varsta clientul, "housing" care spune daca clientul are o casa sau nu,
"marital" care spune daca clientul este casatorit sau singur sau divortat, "balance" care reprezinta soldul curent al clientului, "loan" daca clientul are imprumut sau nu si "duration" care 
reprezinta durata apelului (de unde poti sa iti dai seama daca clientul a fost interesat de depozit sau nu).

2. Nu avem istoricul tranzacțiilor bancare, valoarea sumelor în cont,date temporale detaliate de ex istoric complet al interacțiunilor, acestea ar putea fi relevante pentru prioritizarea clientilor.
Variabila "duration" este durata apelului telefonic in secunde si este disponibila numai dupa ce apelul a fost efectuat. Daca duration e mare atunci clientul a acceptat depozitul, daca e mic .. nu a acceptat. Asta nu ajuta in viata reala, nu vrem sa avem variabile ce tin de target ca si features.

3. Toate variabilele care au valori "yes"/"no" le-am mapat ca fiind 1/0 pentru a putea fi folosite ca si features in Logistic Regression.
Am ales sa folosesc "Logistic Regression" deoarece e un model care e folosit pentru a putea prezice valori binare si in acest caz target-ul  nostru e de tip binar.

4. Accuracy atat pe datele de pe train cat si pe datele de test este de "0,77" ceea ce mi se pare un rezultat bun, se poate mai bine dar e ok deoarece e > 0.5.

5. Pentru a imbunatati performanta as folosi un alt model cum ar fi Randorm Forest, unde nu este nevoie de scalarea datelor si poti avea atat features categorice cat si numerice, si m-as juca cu GridSearchCv pentru a gasi cei mai optimi parametrii.
Dupa ce am folosit modelul Random Forest se poate observa ca acuratetea creste la "0.8110" si ROC-AUC la "0.8861", iar in urma matricei de confuzie se poate observa ca 194 de clienti au fost identificati ca nu isi vor deschide deposit, dar ei defapt au optat pentru deposit. Deci sunt 194 de clienti pierduti, iar 228 vor fi resunati pentru ca au fost identificati ca isi vor deschide deposit dar ei defapt nu isi doresc deposit.

Acuratetea si ROC-AUC se imbunatatesc cu ajutorul lui XG-Boost, iar in urma matricei de confuzie putem spune ca 193 de clienti au fost identificati ca nu isi vor deschide deposit, dar ei defapt au optat pentru deposit. Deci sunt 193 de clienti pierduti, iar 223 vor fi resunati pentru ca au fost identificati ca isi vor deschide deposit dar ei defapt nu isi doresc deposit.

