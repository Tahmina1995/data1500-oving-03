# Konfigurasjon av arbeidssmiljø for DATA1500
Bruk god tid for å forstå konfigurasjon og en "prøve-og-feile"-strategi, slik at du sparer tid neste gang du skal øve med Github og Docker. 
Tegnet `$` brukes for å markere prompt og kan variere fra datamaskin til datamaskin (avhenger av lokal konfigurasjon). Eksemplene av utførelse av kommandoene på kommandolinje blir i dette dokumentet fremstilt slikt:
```bash
  $ <kommando>
  <output til stdout og stderr>
```


## macOS 
### Steg 1: Sjekk OpenSSH
Først, sørg for at du har **OpenSSH Client** installert. Moderne versjoner av macOS inkluderer dette som standard. Du kan verifisere installasjonen ved å åpne Terminal og kjøre `ssh -V`.

Eksempel (eksemplene er utført på Sonoma 14.3.1, Apple M2 Pro):
  ```bash
  $ ssh -V
  OpenSSH_9.4p1, LibreSSL 3.3.6
  ```
### Steg 2: Generer nøkkel for din konto
Generer et unikt SSH-nøkkelpar for GitHub-kontoen din. Det er kritisk å lagre nøkkel i en fil med et spesifikt navn for å unngå overskriving.

1.  **Åpne Terminal**.

2.  **Generer en nøkkel for din github-konto** (f.eks. `ghbruker`). Bruk `-f` flagget for å spesifisere et unikt filnavn. `ed25519`-algoritmen er anbefalt for bedre sikkerhet og ytelse [1].

    ```bash
    $ ssh-keygen -t ed25519 -C "din-epost-for-ghbruker@example.com" -f ~/.ssh/id_ed25519_ghbruker
    ```
Når du blir spurt om en "passphrase", kan du trykke Enter for å la den være tom, eller angi et passord for ekstra sikkerhet. Du trenger ikke å spesifisere "passphrase" i denne omgangen. 

### Steg 3: Legg til Nøkkelen i SSH-Agenten
SSH-agenten er et bakgrunnsprogram som holder styr på SSH-nøklene dine og passordene deres. Dette forhindrer at du må skrive inn passordet hver gang du kobler til.

1.  **Sørg for at SSH-agenten kjører**. Åpne Terminal som administrator og kjør følgende kommandoer:

Eksempel (tallet for prosessen blir forskjellig fra datamaskin til datamaskin):
    ```bash
    # Sjekk statusen til agenten
    $ eval "$(ssh-agent -s)"
    Agent pid 8383
    ```

2.  **Legg til de nye SSH-nøklene** i agenten:

    ```bash
    $ ssh-add ~/.ssh/id_ed25519_ghbruker
    Identity added: /Users/bruker/.ssh/id_ed25519_ghbruker (<din-epost-for-ghbruker>)
    $ ssh-add ~/.ssh/id_ed25519_brB
    ```
`din-epost-for-ghbruker` bør være den e-posten som er registert i github-kontoen og som man brukte for å generere nøkler i **Steg 2**.

## Steg 4: Legg til Offentlige Nøkler i GitHub

Hver GitHub-konto må kjenne til den offentlige delen av SSH-nøkkelen din for å kunne autentisere deg.

1.  **Kopier innholdet i den offentlige nøkkelen**. For konto `ghbruker`:

    ```powershell
    cat ~/.ssh/id_ed25519_ghbruker.pub
    ```
Og kopier outputen fra kommandoen i Terminal til utklippstavle på din datamaskin.

2.  **Naviger til GitHub-innstillingene**:
    - Logg inn på GitHub-kontoen `ghbruker`.
    - Gå til **Settings** > **SSH and GPG keys**.
    - Klikk på **New SSH key**.

3.  **Lim inn nøkkelen**: Gi den et beskrivende navn (f.eks. "Min studie-mac") og lim inn nøkkelen fra utklippstavlen.






[1] https://en.wikipedia.org/wiki/EdDSA 
