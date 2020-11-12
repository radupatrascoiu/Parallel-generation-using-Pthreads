## Patrascoiu Radu, 336CC

# Tema 1 APD

    In cadrul acestei teme am paralelizat cei doi algorimi: *Julia* si
*Mandelbrot* pentru a genera fractali. Idea consta in paralelizarea primului
for din fiecare algoritm, cel care parcurge pe latime. Asfel, am impartit
iteratia pentru cele P threaduri, am calculat indicii de start si stop, in
functie de formulele de la laborator. De asemenea, am paralelizat si
transformarea rezultatului din coordonate matematice in coordonate ecran
eliminand for-ul care face interschimbarea liniilor si incorporandu-l in
generare.
    In functia de thread am calculat start-ul si end-ul, am rulat algoritmul
Julia, am sincronizat thread-urile prin intructiunea
**pthread_barrier_wait(&barrier)**, apoi am recalculat cei doi indici precizati
mai sus, am rulat algoritmul Mandelbrot si am incheiat apelul functiei.
    In main, se citesc argumentele, datele de intrare, se intializeaza bariera
cu P(numarul de fire de executie), se calculeaza width si height pentru Julia
si se citeste inpului pentru acest algoritm. Analog, am facut si pentru
Mandelbrot. Urmatorul pas a fost creearea thread-urilor si apelarea functie de
thread descrise mai sus. Dupa terminarea executiei, se face join la thread-uri
si se scrie in fisier fiecare matrice. Se distruge bariera si se elibereaza
memoria. Precizez ca atat citirea, cat si scrierea se fac pe un singur fir de
executie.
    Rezultatul rularii pe FEP s-a dovedit a fi cu succes, asfel ca programul
scaleaza, avand urmatoarele acceleratii:
    1. Acceleratie 1-2: 1,38
    2. Acceleratie 1-4: 2,45
    3. Acceleratie 2-4: 1,78
