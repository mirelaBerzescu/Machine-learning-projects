Datasetul utilizat în acest proiect este cel al diamantelor, disponibil la adresa: "https://raw.githubusercontent.com/mwaskom/seaborn-data/master/diamonds.csv".
Obiectivul proiectului este predictia pretului unui diament pe baza unor caracteristici fizice și cantitative, precum dimensiunile sale (x, y, z) și alte atribute relevante.

În etapa de preprocesare, datasetul a fost analizat pentru identificarea valorilor lipsă sau aberante. În urma verificărilor, s-a constatat că datele sunt complete și nu necesită curățare suplimentară.

Pentru a înțelege relația dintre variabilele numerice și variabila țintă (price), a fost calculată matricea de corelație Pearson. Valorile apropiate de 1 indică o corelație liniară puternică. Analiza a evidențiat faptul că variabilele carat, x, y și z prezintă cea mai puternică corelație cu prețul diamantelor, motiv pentru care acestea au fost considerate caracteristici relevante.

Initial, a fost aplicat un model de Linear Regression având în vedere că variabila țintă este continuă. În prima etapă, modelul a fost antrenat folosind exclusiv variabila carat. De asemenea, a fost realizată o reprezentare grafică pentru a ilustra relația dintre datele observate și linia de regresie. Performanța modelului a fost evaluată prin intermediul metricilor RMSE și R². RMSE cuantifică diferența medie dintre valorile reale și cele prezise, iar în acest caz a avut valoarea de 1549, considerată acceptabilă în contextul prețurilor diamantelor. Coeficientul R² a fost de 0,84, indicând o bună capacitate explicativă a modelului, deși exista loc de îmbunătățire.

Ulterior, a fost aplicată regularizarea de tip LASSO, cu scopul de a reduce potențialul de overfitting. În acest caz, s-a observat o ușoară creștere a valorii RMSE pe setul de test, sugerând că regularizarea nu a adus beneficii semnificative pentru acest model specific.

În final, a fost utilizată Regresia Polinomială de gradul 2, care a condus la o îmbunătățire a performanței modelului. Astfel, valoarea RMSE a scăzut, iar coeficientul R² a crescut la 0,87, indicând o capacitate mai bună a modelului de a surprinde relațiile neliniare dintre variabilele explicative și prețul diamantelor.

În etapa finală a proiectului, a fost utilizat modelul XGBRegressor, integrând atât variabilele categoriale (cut, color, clarity), cât și variabilele numerice. Deoarece modelul necesită date numerice, variabilele categoriale au fost transformate prin One-Hot Encoding. Această abordare s-a dovedit extrem de eficientă, modelul obținând performanțe foarte ridicate, cu un RMSE de aproximativ 559 și un coeficient de determinare R² de 0.98, indicând o capacitate excelentă de predicție a prețului diamantelor


1. Linear Regression cu un singur feature("carat")
  R² = 0.84
  RMSE = 1549

2. Linear Regression cu multiple features("carat","x","y","z")
  R² = 0.85
  RMSE = 1521

3. Linear Regression cu multiple features("carat","x","y","z") si standardizare
  R² = 0.85
  RMSE = 1521

4. Polynomal Regression grad 2
    R² = 0.87
    RMSE = 1391

5. XGBRegressor
    R² = 0.98
    RMSE = 559
