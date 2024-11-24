In clasa App am creat clasele Utilizator, Postare si Comentariu, precum si interfata Likeable.

## Clasa Utilizator 
Reprezintă un utilizator într-o platformă de socializare. Include informații precum username, password, lista de postari ale utilizatorului, urmăritori, utilizatori urmăriți și numărul de aprecieri. Clasa oferă, de asemenea, metode pentru interacțiunea cu urmăritorii și cei urmăriți, precum și gestionarea postărilor și aprecierilor.

Constructorul cu parametri primeste un nume de utilizator și o parolă pentru a crea un utilizator cu liste inițializate pentru postări, urmăritori și utilizatori urmăriți.

### Metode:

addPost(Postare post) adaugă o postare la lista de postări a utilizatorului.

isFollowing(Utilizator user) verifică dacă utilizatorul curent îl urmărește pe alt utilizator.

follow(Utilizator user) adaugă utilizatorul dat în lista de urmăriți și utilizatorul curent în lista de urmăritori a utilizatorului dat.

addFollower(Utilizator user) adaugă un utilizator în lista de urmăritori ai utilizatorului curent.

unfollow(Utilizator user) elimină un utilizator din lista de urmăriți și utilizatorul curent din lista de urmăritori a utilizatorului dat.

removeFollower(Utilizator user) elimină un utilizator din lista de urmăritori a utilizatorului curent.

setLikes(int likes) setează numărul total de aprecieri ale utilizatorului.

## Clasa Postare 

Reprezintă o postare în cadrul unei platforme de socializare. Aceasta include informații precum conținutul postării, data publicării, autorul, lista de utilizatori care au apreciat postarea, lista de comentarii și un identificator unic.

Constructorul Postare(int id, String content, Utilizator author, String date) inițializează o postare cu un identificator unic, conținut, autor, data publicării și liste goale pentru aprecieri și comentarii.

### Metode:

setId(int id) setează identificatorul unic al postării.

like(Utilizator user) adaugă utilizatorul dat în lista de aprecieri.

unlike(Utilizator user) elimină utilizatorul dat din lista de aprecieri.

getLikesCount() returnează numărul de aprecieri.

getLikedBy() returnează o listă cu utilizatorii care au apreciat postarea.

addComment(Comentariu comment) adaugă un comentariu la lista de comentarii ale postării.

## Clasa Comentariu 
Reprezintă un comentariu asociat unei postări în cadrul unei platforme de socializare. Aceasta include informații precum conținutul comentariului, data publicării, autorul, postarea la care este atașat, lista de utilizatori care au apreciat comentariul și un identificator unic.

Constructorul Comentariu(int id, String content, Postare post, Utilizator author, String date) inițializează un comentariu cu un identificator unic, conținut, postarea la care este atașat, autor, data publicării și o listă goală pentru aprecieri.

Metodele like(Utilizator user), unlike(Utilizator user), getLikesCount() si getLikedBy() fac parte din interfata Likeable, avand aceleasi atribute atat pentru obiectele din clasa Postare, cat si pentru cele din clasa Comentariu.

### Metodele Auxiliare:

printErrorMessage(String message), printOkMessage(String message): Metode pentru afișarea unui mesajului în format JSON.

getArg(String string): Metodă pentru extragerea informațiilor din argumente, bazată pe delimitatoarele apostrofelor.

createUser(String username, String password): Metodă pentru crearea unui utilizator nou, cu verificarea existenței prealabile a acestuia.

userExists(String username): Metodă pentru verificarea existenței unui utilizator cu un anumit nume de utilizator.

login(String username, String password): Metodă pentru autentificarea unui utilizator, verificând existența și corectitudinea parolei.

getUser(String username): Metodă pentru obținerea unui obiect Utilizator bazat pe numele de utilizator dat.

getPost(int postId): Metodă pentru obținerea unei postări bazate pe identificatorul unic al postării (postId).

getComment(int id): Metodă pentru obținerea unui comentariu bazat pe identificatorul unic al comentariului (id).

cleanupAll(): Metodă pentru curățarea și resetarea tuturor datelor, inclusiv postări, comentarii, și utilizatori.


## Main:

Pentru fiecare comanda se verifica numarul de argumente furnizate.

"-create-user" verifică dacă sunt furnizate atât numele de utilizator, cât și parola. Apelează metoda createUser cu numele de utilizator și parola furnizate pentru a crea un nou utilizator.

Urmatoarele comenzi validează numărul de argumente și starea de autentificare. Apelează metoda login pentru autentificarea utilizatorului.

"-create-post" creează o nouă postare dacă autentificarea este reușită, verifică lungimea postării și o adaugă în lista de postări a utilizatorului.

"-delete-post-by-id" sterge o postare după ID, actualizând ID-urile postărilor în lista de postări a utilizatorului autentificat.

"-follow-user-by-username" urmărește un utilizator specificat după numele de utilizator, daca acesta exista sau nu este deja urmarit, apeland metoda 'follow' din clasa Utilizator.

"-unfollow-user-by-username" anulează urmărirea unui utilizator specificat după numele de utilizator, daca acesta exista si este in lista de utilizatori urmariti.

"-like-post" si "-like-comment" apreciază o postare/un comentariu specificate prin identificator, daca nu au fost deja apreciate si daca nu apartin utilizatorului autentificat.

"-unlike-post" si "-unlike-comment" dezapreciază o postare/un comentariu specificate prin identificator, daca au fost apreciate inainte.

"-get-followings-posts" obține postările utilizatorilor urmăriți și le sortează după ID, afișând informațiile relevante în format JSON.

"-get-user-posts" obține postările unui utilizator specificat (cel urmărit) și le sortează după ID, afișând informațiile relevante în format JSON.

"-get-post-details" obține detaliile despre o postare specificată prin identificator și afișează informațiile relevante într-un format JSON structurat.

"-comment-post" verifică lungimea comentariului și afișează un mesaj de eroare dacă este depășită limita. Creează un comentariu și îl adaugă la lista de comentarii a postării specificate.

"-delete-comment-by-id" obține identificatorul comentariului și caută în toate postările și comentariile pentru a găsi poziția acestuia. Verifică dacă utilizatorul curent este autorul postării sau al 
comentariului și șterge comentariul.

"-get-following" obține lista de utilizatori urmăriți și afișează numele lor de utilizator într-un format JSON structurat.

"-get-followers" obține lista de urmăritori și afișează numele lor de utilizator într-un format JSON structurat.

"-get-most-liked-posts" obține toate postările din sistem și le sortează în funcție de numărul de aprecieri în ordine descrescătoare. Afișează primele 5 postări într-un format JSON structurat.

"-get-most-commented-posts" obține toate postările din sistem și le sortează în funcție de numărul de comentarii în ordine descrescătoare. Afișează primele 5 postări într-un format JSON structurat.

"-get-most-followed-users" sortează lista de utilizatori în funcție de numărul de urmăritori în ordine descrescătoare. Afișează primele 5 rezultate într-un format JSON structurat.

"-get-most-liked-users" calculează numărul total de aprecieri pentru fiecare utilizator, adunând aprecierile de la postările proprii și de la comentariile scrise de utilizator. Sortează lista de utilizatori în 
funcție de numărul total de aprecieri în ordine descrescătoare. Afișează primele 5 rezultate într-un format JSON structurat.

"-cleanup-all" apeleaza metoda cleanupAll() pentru a reseta reteaua de socializare.

#### Bonus:
Pe langa cazurile tratate, ar mai putea fi puse conditii cu privire la argumentele furnizate. Spre exemplu, ce se intampla in cazul in care este furnizat doar username-ul, nu si parola, si mai apoi inca un argument precum textul pentru o postare.

De asemenea, un utilizator ar trebui sa urmareasca utilizatorul caruia doreste sa ii aprecieze o postare sau sa lase un comentariu la postare, sa nu fie necesar doar pentru a afisa postarile.

Continuand aceeasi idee, contul unui utilizator ar putea sa aiba atribuita o stare: 'public' sau 'private', in functie de care sa existe anumite permisiuni. Pentru un utilizator public, oricine poate vedea lista 
de urmaritori si persoane urmarite, dar si postarile si datele despre aceastea. Pentru un utilizator private, pot vedea toate aceste date doar persoanele care il urmaresc.
