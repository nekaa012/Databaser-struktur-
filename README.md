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















