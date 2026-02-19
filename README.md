# goodreads-database-project
  Acest proiect reprezintă designul și implementarea unei baze de date pentru o platformă de gestionare a lecturilor, inspirată de Goodreads. Sistemul permite utilizatorilor să exploreze cărți, să își organizeze listele de lecturi și să ofere recenzii pentru volumele parcurse.

Platforma facilitează interacțiunea dintre utilizatori și literatura preferată prin:

Gestionarea listelor: Utilizatorii pot adăuga cărți în lista de viitoare lecturi (TBR) sau în lista de cărți Citite.

Recenzii: Posibilitatea de a lăsa o singură recenzie per carte, condiționată de finalizarea lecturii.

Coerența datelor: Mutarea unei cărți în lista "Citite" duce la eliminarea acesteia din "TBR".

Restricții: O carte aparține unui singur autor și unui singur gen literar.

Structura Bazei de Date


<img width="1369" height="484" alt="logical" src="https://github.com/user-attachments/assets/09d392bf-9a17-443e-bf43-640817f17f8e" />

Baza de date este compusă din 8 tabele interconectate prin relații de tip 1:1 și 1:N.

Entități Principale:

Utilizatori si Profil Utilizator: Stochează datele de identificare și preferințele de profil (Relație 1:1).

Carti: Nucleul sistemului, conținând detalii precum titlul, data publicării, numărul de pagini și editura.

Autori si Genuri: Tabele de referință pentru a asigura normalizarea datelor.

TBR si Citite: Tabele de legătură (cu chei primare compuse) pentru gestionarea fluxului de lectură.

Recenzii: Stochează rating-ul (1.0 - 5.0) și comentariile utilizatorilor.


Detalii Tehnice si Normalizare

<img width="1402" height="515" alt="structural" src="https://github.com/user-attachments/assets/27a065a7-b630-4218-b95d-908a42812958" />


Proiectul respectă primele trei forme de normalizare (1NF, 2NF, 3NF):


1NF: Fiecare câmp conține o singură valoare, eliminând grupurile repetitive.

2NF: Toate atributele depind în totalitate de cheia primară; tabelele cu chei compuse (TBR, Citite) nu au atribute non-cheie.

3NF: Nu există dependențe tranzitive; informațiile despre autori și genuri sunt separate în tabele proprii.

Constrângeri și Triggere implementate:

Validare Nume: Constrângeri CHECK pentru a evita cifrele în numele autorilor sau utilizatorilor.

Validare Email: Format verificat pentru adresele de email.

Trigger Publicare: Previne introducerea cărților cu data de publicare în viitor.

Rating: Restricționat la intervalul [1, 5] cu format Number(2,1).
