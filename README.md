# Mappeeksamen i Algoritmer og Datastrukturer Høst 2020

# Krav til innlevering

Se oblig-tekst for alle krav, og husk spesielt på følgende:

* Git er brukt til å dokumentere arbeid (minst 2 commits per oppgave, beskrivende commit-meldinger)	
* git bundle er levert inn
* Hovedklassen ligger i denne path'en i git: src/no/oslomet/cs/algdat/Eksamen/EksamenSBinTre.java
* Ingen debug-utskrifter
* Alle testene i test-programmet kjører og gir null feil (også spesialtilfeller)
* Readme-filen her er fyllt ut som beskrevet


# Beskrivelse av oppgaveløsning (4-8 linjer/setninger per oppgave)

Vi har brukt git til å dokumentere arbeidet vårt. Jeg har 16 commits totalt, og hver logg-melding beskriver det jeg har gjort av endringer.

* Oppgave 1: -Kopierte Programkode 5.2 3 a)
              Metoden legger inn en ny node i treet, kan ikke legge inn null-verdier
             -Gjorde en endring på metoden:
              Node klassen skal ta inn forelder slik at
              p = new Node<>(verdi,q);
              
* Oppgave 2: -Laget en (int) teller i toppen av metoden
              Dene returenes uansett
             -Dersom treet ikke er tomt eller innheolder(verdi) er sann, søker jeg gjennom treet
              ved å bruke comp.comare(), slik at jeg går endten høyre eller venstre nedover i treet for å finne verdier jeg ser etter
             -Når verdien jeg ser etter og noden jeg ligger på er like, økes teller med en (teller++)
             -Når teller går utenfor treet (node.høyre/ node.venstre er null) går jeg ut av while-løkken og returnerer telleren
             
* Oppgave 3: -Brukt noe kode fra kompendiet programkode 5.1.7
             -Begge metodene tar inn en node. Derfor starter jeg med å komme meg helt til toppen av teet i første while-løkke
              i metoden førtstePostordem.
             -Når jeg er i toppen av treet bruker jeg igjen en while-løkke for å komme meg nederst mot venstre i treet, og på det "yngste" barnet,
              hvor første postorden ligger. Kjører denne while-løkken helt til det ikke finnes flere barn.
             -nestePostorden starter jeg med noen if-tester, for å finne ut om jeg kan enkelt returnere null om jeg er i toppen av treet,
              forelder hvis jeg er på et høyrebarn og det som må skje for et venstrebarn:
              der returneres forelder hvis p er enebarn.
              ellers må jeg gå i en while-løkke som har samme prinsipp som førstePostorden for å finne den neste i postorden.
              
* Oppgave 4: -public void postorden(Oppgave<? super T> oppgave):         
              Starter med p se om listen jeg har er tom eller ikke
              får inn første postorden, setter oppgave til utført
              videre over i en while-løkke hvor jeg kjører nestePostorden metoden helt fram til jeg er på rot-hvor p.forelder==null
             -private void postordenRecursive(Node<T> p, Oppgave<? super T> oppgave):
              starter med å sjekke at antallet er større enn 0 her også
              samme kode i en if-test som i while-løkken til postorden, p.forelder != null.
              kaller på nestePostorden med node p som parameter, oppgave utført.
              og kaller på metoden jeg er inne i for å kjøre samme rekursivt fram til p.forelder==null;

* Oppgave 5:  Hentet kode fra Programkode 5.1.6 a)
             -serialize() returnerer null for tomt tre.
              oppretter en queue og en ArrayList
              legger til roten i queue, tar ut en node fra queue og legger inn i p, hvs p har barn legges disse inn i queue.
              Legger inn i queue nivåvis.
             -deserialize:
              oppretter et nytt tre i toppen.
              legger inn i treet i en for-løkke hvor jeg kaller på metoden leggInn fra oppgave 1
              
              
* Oppgave 6: Fjern metoden er hentet fra Programkode 5.2 8 d)
            -public boolean fjern(T verdi):
             Koden har et par endringer fra kompendiet, når jeg ser på for tilgelle 1) og 2), ikk begge barnene finnes,
             der retter jeg på pekere for barnet til noden som skal gjernes, setter det til forelderen.
             jeg returnerer ture hvis koden har kjørt og fjerner en fra antallet.
            -public int fjernAlle(T verdi):
             opretter en teller i toppen som retureneres i slutten av metoden
             dersom veriden er null eller antall er 0 returerer jeg teller når den fremdels er 0
             hvis verien som skal fjernes fremdeles er i treet fjernes den en etter en med metoden fjern(verdi) og teller legges til en hver gang
             returer teller i bunn hvor jeg har telt antall ganger jeg har fjernet et element.
            -public void nullstill():
             hvis antall>0 opprettes en node og jeg går inn i en while-løkke som fjerner noder i postorden.
             passer på om det er et høyre eller venstrebarn som skal fjerens mtp pekerne, slik at de blir riktig.
             helt nederst settes rot=null siden det er den siste noden i postorden.
             Jeg har lagt på at antall() metoden kjøres i hver while-itterasjon fordi metoden gikk for raskt når jeg ikke hadde den med. 
             
             
* Warnings: 1) Non ASCII characters in an identifier, ikke fjernet fordi det er en "ø" i høyre som blir referert til
            2) endringer brukes aldri, lærer sa at vi ikke behøvde å bry oss om den
            3) Jeg bruker aldri returverdien til leggInn (true/ false), bruker den kun til å legge inn i treet.
               Kunne gjort den om til en void, men jeg endrer ikke på det, ettersom oppgaveteksten sier at det er en boolsk metode.
            4) Metoden førstePostorden(Node<T> p), samme som 1), reagerer på "ø" i metodenavnet