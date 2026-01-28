
Navn: Tahmina Nargis Noori

Bruker navn: tanoo6678@oslomet.no

# Besvarelse av refleksjonsspørsmål - DATA1500 Oppgavesett 1.3

Skriv dine svar på refleksjonsspørsmålene fra hver oppgave her.

---

## Oppgave 1: Docker-oppsett og PostgreSQL-tilkobling

### Spørsmål 1: Hva er fordelen med å bruke Docker i stedet for å installere PostgreSQL direkte på maskinen?

**Ditt svar:**

Jeg foretrekker Docker fordi jeg får samme oppsett uansett maskin. Databasen kjører isolert i en container, så jeg «søler» ikke til operativsystemet mitt, og jeg kan ha flere versjoner side om side. Det er også mye enklere å starte/stoppe og dele prosjektet med andre – en compose-fil og et par kommandoer er nok.



### Spørsmål 2: Hva betyr "persistent volum" i docker-compose.yml? Hvorfor er det viktig?

**Ditt svar:**

Et «persistent volum» betyr at dataene lagres utenfor selve containeren. Da overlever databasen min når jeg stopper eller sletter containeren. Dette er viktig for at jeg ikke mister data ved restart, og det gjør det enklere å ta backup og jobbe videre senere.



### Spørsmål 3: Hva skjer når du kjører `docker-compose down`? Mister du dataene?

**Ditt svar:**

Når jeg kjører docker-compose down, stopper og sletter jeg containerne og nettverket. Dataene blir likevel ikke borte så lenge jeg bruker et navngitt volum (slik som i oppgaven). Jeg mister data først hvis jeg også sletter volumene med -v.

### Spørsmål 4: Forklar hva som skjer når du kjører `docker-compose up -d` første gang vs. andre gang.

**Ditt svar:**

Første gang jeg kjører docker-compose up -d, lastes image ned, volum og nettverk lages, og PostgreSQL initialiseres. Da kjøres også init-skriptene og testdata legges inn. Andre gang starter containeren raskere og bruker de samme dataene i volumet; init-skriptene kjøres ikke på nytt.

### Spørsmål 5: Hvordan ville du delt docker-compose.yml-filen med en annen student? Hvilke sikkerhetshensyn må du ta?

**Ditt svar:**

Hvis jeg skulle delt docker-compose.yml med en annen student, ville jeg ikke lagt inn ekte passord der. Jeg ville brukt en .env-fil og delt en /.env.example med eksempelverdier, og sørget for at .env er i .gitignore. Jeg ville også bare eksponert nødvendige porter og unngått personlige filstier. Hvis passord har vært delt offentlig, bør de byttes.


## Oppgave 2: SQL-spørringer og databaseskjema

### Spørsmål 1: Hva er forskjellen mellom INNER JOIN og LEFT JOIN? Når bruker du hver av dem?

**Ditt svar:**

[Skriv ditt svar her]

---

### Spørsmål 2: Hvorfor bruker vi fremmednøkler? Hva skjer hvis du prøver å slette et program som har studenter?

**Ditt svar:**

[Skriv ditt svar her]

---

### Spørsmål 3: Forklar hva `GROUP BY` gjør og hvorfor det er nødvendig når du bruker aggregatfunksjoner.

**Ditt svar:**

[Skriv ditt svar her]

---

### Spørsmål 4: Hva er en indeks og hvorfor er den viktig for ytelse?

**Ditt svar:**

[Skriv ditt svar her]

---

### Spørsmål 5: Hvordan ville du optimalisert en spørring som er veldig treg?

**Ditt svar:**

[Skriv ditt svar her]

---

## Oppgave 3: Brukeradministrasjon og GRANT

### Spørsmål 1: Hva er prinsippet om minste rettighet? Hvorfor er det viktig?

**Ditt svar:**

[Skriv ditt svar her]

---

### Spørsmål 2: Hva er forskjellen mellom en bruker og en rolle i PostgreSQL?

**Ditt svar:**

[Skriv ditt svar her]

---

### Spørsmål 3: Hvorfor er det bedre å bruke roller enn å gi rettigheter direkte til brukere?

**Ditt svar:**

[Skriv ditt svar her]

---

### Spørsmål 4: Hva skjer hvis du gir en bruker `DROP` rettighet? Hvilke sikkerhetsproblemer kan det skape?

**Ditt svar:**

[Skriv ditt svar her]

---

### Spørsmål 5: Hvordan ville du implementert at en student bare kan se sine egne karakterer, ikke andres?

**Ditt svar:**

[Skriv ditt svar her]

---

## Notater og observasjoner

Bruk denne delen til å dokumentere interessante funn, problemer du møtte, eller andre observasjoner:

[Skriv dine notater her]


## Oppgave 4: Brukeradministrasjon og GRANT

1. **Hva er Row-Level Security og hvorfor er det viktig?**
   - Svar her...

2. **Hva er forskjellen mellom RLS og kolonnebegrenset tilgang?**
   - Svar her...

3. **Hvordan ville du implementert at en student bare kan se karakterer for sitt eget program?**
   - Svar her...

4. **Hva er sikkerhetsproblemene ved å bruke views i stedet for RLS?**
   - Svar her...

5. **Hvordan ville du testet at RLS-policyer fungerer korrekt?**
   - Svar her...

---

## Referanser

- PostgreSQL dokumentasjon: https://www.postgresql.org/docs/
- Docker dokumentasjon: https://docs.docker.com/

