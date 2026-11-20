# Databaser-struktur-
databaser : struktur , ER-diagram ,relasjoner og GDPR

Steg -1 
Behovet til Fjordtek-
ER-diagram 
Fjordtek – Kundestøttesystem

KUNDE                                ANSATT

kundeID                             AnsattID (pk)
E-post                                   E-post
Telefonnummer
(1kunde og 1 Ansatte kan behandle flere saker )

Supportsak
•	Sakid (pk)
•	KundeID 
•	ansattID
•	opprettetDato
•	Beskrivelse

•	Fjordtek – Kndestøttesystem

Table kunde{
  kundeID integer [pk, increment]
  navn varchar (100)
  Epost varchar (100)
 Telefonnummer varchar (20)
}Table Ansatt {
 AnsattID integer [primary key]
  navn varchar (100)
  Epost varchar(100)
  }Table supportsak {
 Sakid integer [pk, increment]
 kundeID int [not null]
AnsattID integer [not null]
  Beskrivelse text
  status varchar (50)
  opprettetDato datatime 
}

Ref: kunde.kundeID < supportsak.kundeID
Ref: Ansatt.AnsattID < supportsak.AnsattID

Vi kan se tre tabel –
Kunde 
Ansatt
Supportsak

<img width="408" height="195" alt="image" src="https://github.com/user-attachments/assets/8d7825fe-a261-4302-bf66-6fd4ac741cbd" />


•	STEG 2- Forstå tabell ,rad og felt
Lager vi tabel som samler informasjon om en type thing
Eksemple – kundetabell:

KundeID              navn                      E-post
(pk)
1                         Kari Hansen         kari,gmail.com

Table Kunde {
  KundeID integer [pk , increment]
  Navn varchar
  Epost varchar  }

  <img width="175" height="134" alt="image" src="https://github.com/user-attachments/assets/4b1d6b7b-30a9-4152-9df0-39d28b5484c6" />


STEG -3  Entitet og tabell
En Entitet er noe vi trenger å lagre info om i databasen.DET blir vanligvis i en tabell.
Jeg lagt tre separate tabeller .
Table Kunde{  }
Table Ansatt {  }
Table Sak {   }

•	STEG 4- legg til felter i tabellen
Jeg lagt tre tabeller .
Kunde             Ansatt              Sak 
Navn              Navn              Tittel
e-post            Avdeling          Status
Telefon            E-post          OpprettetDato

•	Diagram -
Table Kunde {
  KundeID int [pk, increment]
  Navn varchar (100)
  Epost varcher (100)
  Telefon varchar (20)
} Table Ansatt {
  AnsattID int [ pk, increment]
  Navn varchar(100)
  Avdeling varchar(100)
  Epost varchar (100)
 }    Table Sak {
  SakID int [pk, increment]
  Tittel varchar (100)
  status varchar (50)
  opprettetDato datetime }
vi  gjør dette separat for å kontrollere at info  ligger i riktig tabell før vi lager relasjoner .

<img width="300" height="259" alt="image" src="https://github.com/user-attachments/assets/e98df6bd-c679-4dd0-bd54-4759df86befc" />

Steg-5   Primærnøkkel 
EN pk er et felt som identifiserer hver rad unikt i en tabell.
Desse feltene er Pk 
Kunde – pk kundeID
Ansatt – PK AnsattID
Sak – SakID
Bruker vi en egne ID  fordi –
Navn og E-post Kan endres.
Flere person kan ha samme navn .
En ID identifisere hver rad unik og stabilt.

Steg -6    Første møte med datatyper 
En datatype bestemmer hvilken type info et felt kan innhonlde.
Oversikt over datatypene.

Datatype        Betydning                 Eksempler 
Integer           Heltall                     1,2 3
Varchar           kort tekst                  Kari Hansen
Text              lang tekst              Beskrivelse av problem.
Timestamp         dato og tidspunkt              2026-11-16 10:00
Decimal           tall med desimaler           12.50

Kunde – Ansatt -sak
kundeID  -integer(pk)
Navn-varchar 
E-post – varchar
Telefon – varchar 
Avdeling-varchar
Status- varchar
opprettetDato- timestamp.

Steg 7- Første relasjon: kunde og sak 
Reglen for Fjodtek er – 
en kunde kan ha mange supportsaker .
Hver supportsak tilhører en kunde.

Relasjonen kunde med sak 
Kunde 
kundeID (PK)
Navn
Epost
 SAK
SakID (pk)
Tittle 
Status
KundeID (kobling)

Table Kunde {
  KundeID int [pk, increment]
  Navn varchar (100)
  Epost varcher (100)
  Telefon varchar (20)
}

 Table Ansatt {
  AnsattID int [ pk, increment]
  Navn varchar(100)
  Avdeling varchar(100)
  Epost varchar (100)
 } Table Sak {
  SakID int [pk, increment]
  Tittle varchar (100)
  Status varchar (50)
  opprettetDato integer }
Ref: Kunde.KundeID < Sak.KundeID

Vi har lagt KundeID i Sak -tabellen .
KundeID er PK i Kunde tabellen.
KundeID brukes som kobling i Sak.tabellen.
<img width="302" height="200" alt="image" src="https://github.com/user-attachments/assets/f6876e27-c96f-449a-abf0-a7857be643a6" />


•	STEG8-oppgave A 
En avdeling kan ha mange ansatte, men hver ansatt tilhører en avdeling. 
Avdeling - Table Avdeling {
  AvdelingID integer (pk,increment)
Navn varchar (100)
} Table Ansatt {
  AnsattID integer (pk,increment)
  Navn varchar(100)
  Epost varchar(100)
  AvdelingID integer }
Ref: Avdeling.AvdelingID < Ansatt.AvdelingID
<img width="365" height="140" alt="image" src="https://github.com/user-attachments/assets/10f9b3a9-3623-4c82-b608-35ef33153a68" />


OPPGAVE -B 
EN kategori kan ha mange produktet , men hvert produkt tilhører en kategori.
1:M-relasjon
Table Kategori {
KategoriID integer (pk,increment)
Navn varchar (100)
} 

Table Produkt{
  ProduktID integer (pk,increment)
  Navn varchar(100)
  Pris decimal (10,2)
  KategoriID integer}
  Ref:Kategori.KategoriID < Produkt.KategoriID
  
   <img width="364" height="125" alt="image" src="https://github.com/user-attachments/assets/8910600e-1a22-41bc-b6d6-123afb11c5ed" />

Oppgave -2
steg-1
En bruker kan skrive mange innlegg, men hvert innlegg tilhører bare en bruker.BrukerID brukes som fremmednøkkel i tabellen innlegg for å koble tabellene sammen.

Table Bruker {
  BrukerID int [pk]
  Brukernavn varchar
  Rolle varchar
}
Table Innlegg {
  InnleggID int [pk]
  Tittle varchar
  Tekst text
  BrukerID int [ref: >Bruker.BrukerID]
}

<img width="233" height="287" alt="image" src="https://github.com/user-attachments/assets/b5d81396-112d-4a70-841f-a969e0a23681" />

steg-2
Kontroll av ER- modellen

begge tabellene en Primærnøkkel - Bruker har BrukerID som PK. Innlegg har innleggID som PK.

BrukerID i innlegg som koblingsfelt- BrukerID er fremmednøkkel (FK)

Relasjonen 1:M - En bruker kan skrive  mange innlegg, men hvert innlegg tilhører en bruker. 

Brukernavn  ikke kopieres inn i hvert innlegg  fordi det blir unødvendig  dobbeltlagring. HVis brukernavnet endres, må vi endre det i mange innlegg. Det er bedre å bruke BrukerID  som kobling til Bruker-tabellen.

STEG 3-
En kunde kan ha mange bestillinger , men hver bestilling tilhører bare en kunde. KundeID brukes som fremmednøkkel i Bestilling -tabellen for å koble bestillingen til riktig kunde. 
Table Kunde {
  KundeID integer [pk]
  Navn varchar
  Epost varchar
}
Table Bestilling {
  BestillingID interger [pk]
  Dato date
  Status varchar 
  KundeID integer [ref: > Kunde.KundeID]
}

<img width="232" height="283" alt="image" src="https://github.com/user-attachments/assets/c1bfbb3d-a786-403d-a962-664aae98ca13" />

Steg 4- Begge modellene har samme relasjon, som kalles 1:M .
I Bruker : Innleg -kan en bruker skrive mange innlegg, men hvert innleng tilhører en bruker.
i Kunde :  Bestilling- kan en kunde ha mange bestiliinger ,men hver bestilling tilhører en kunde.

 i begge modellene har den første tabellen en PKJ , og denne ID- en brukes som fremmednøkkel i den andre tabellen.

 OPPGAVE -3 
 steg1 -
 En fremmednøkkel kobler to tabeller sammen ved å peke på primærnøkkelen i en annen tabell. Dette unngår dobbeltlagring av info og gjør databasen mer ryddig.
 
 Table Kunde {
  KundeID integer [pk]
  Navn varchar
  Epost varchar
}

Table Sak {
  SakID integer [pk]
  Tittel varchar
  Status varchar
  KundeID integer [ ref: > Kunde.KundeID]
}

<img width="444" height="166" alt="image" src="https://github.com/user-attachments/assets/65a3d601-69f8-4f94-a18d-4bcc6eec60de" />

steg 2-
Koble Ansatt til sak 
Ansatt brukes som fremmednøkkel i sak -tabellen for å koble saken til riktig ansatt.
Table Ansatt {
  AnsattID integer [pk]
  Navn varchar
  Avdeling varchar
}

Table Sak {
  SakID integer [pk]
  Tittel varchar
  Status varchar
  AnsattID integer [ref: > Ansatt.AnsattID]
}

<img width="446" height="175" alt="image" src="https://github.com/user-attachments/assets/3261c845-a31e-4116-8367-3b9ebe4f00bf" />

Steg 3- samlet modell
Samlet ER-modellen med alle tre tabellene og relasjonene. 

Table Kunde {
  KundeID integer [pk]
  Navn varchar
  Epost varchar
}

Table Sak {
  SakID integer [pk]
  Tittel varchar
  Status varchar
  KundeID integer [ref: > Kunde.KundeID]
  AnsattID integer [ref: > Ansatt.AnsattID]
}

Table Ansatt {
  AnsattID integer [pk]
  Navn varchar
  Avdeling varchar
}
<img width="433" height="221" alt="image" src="https://github.com/user-attachments/assets/199c6028-a4ca-4e45-8faf-e2a5697794ac" />

Modellen har  tre tabeller : Kunde, sak, og Ansatt. AnsattID , KundeID er fremmednøkler i sak-tabellen. En kunde og En Ansatt har mange saker .Hver sak tilhører en kunde og er  tildelt en Ansatt.

STEG 4- test modellen med eksempeldata
- Kan en kunde ha flere saker? Ja. Kunde 17 har sak 103 og 108.
- Kan en ansatt ha flere saker? Ja. Ansatt 4 arbeider med sak 103 og 112.
- Hvilken kunde tilhører sak 103? Kunde 17, fordi Sak.KundeID = 17.
- Hvilken ansatt arbeider med sak 103? Ansatt 4, fordi Sak.AnsattID = 4.
Vi tester med eksempeldata for å kontrollere at relasjonene støtter behovet før databasen bygges.

STEG 5 - les relasjonene som setninger 

Relasjonene i modellen kan leses slik:
- En kunde kan ha mange saker.
- Hver sak tilhører én kunde.
- En ansatt kan arbeide med mange saker.
- Hver sak er tildelt én ansatt.
Dette stemmer med modellen: Sak.KundeID peker til Kunde.KundeID, og Sak.AnsattID peker til Ansatt.AnsattID.

STEG 6- Finn riktig steg for fremmednøkkelen.
Produkt.KategoriID er fremmednøkkelen som peker til Kategori.KategoriID. Derfor kan én kategori ha mange produkter, og hvert produkt tilhører én kategori.

Table kategori { 
kategoriID integer [PK]
kategoriNavn varcar 
}
Table Produkt {
ProduktID integer [PK]
ProduktNavn varchar
Pris integer 
KategoriID integer [ref:> kategori.kategoriID]
}

<img width="453" height="186" alt="image" src="https://github.com/user-attachments/assets/8b31f931-6f3b-42ac-a0dd-db008cdf8e8f" />




