# IT_sikkerhed_1_2
## Softwaresikkerhed
Dette er et skoleprojekt på Zealand Næstved for holdet Softwaresikkerhed.
Man kan følge de opgavebesvarelser jeg har lavet. De vil stå under hver deres dato, samt vil de være i omvendt kronologisk rækkefølge. 


## Softwaresikkerhed d. 5. februar
Udarbejdet af Nichlas Damgaard og Amalie Asborg Hansen

### Ækvivalens klasser
Roller, forstået som forskellige slags brugere.
Man kan for eksempel have: 
Admin
Leder
Medarbejder
Hver slags bruger har sine egen tilladte handlinger og har adgang til forskellige dele af systemet. De er allesammen brugere, men de er delt op på baggrund af deres forskelligheder, der i dette tilfælde er deres tilladte handlinger og deres adgang. 

### Grænseværdi test
I forhold til ratelimiting kunne man have grænseværdi af:
A=9 godkendt (Lige under)
A=10 godkendt (Lige på)
A=11 fejler (Lige over)
Så hvis man antager, at man maks må lave 10 request inden for en bestemt periode, vil man tjekke både under, på og over værdien. Vi tjekker under og på værdien for at sikre at tillade en bruger kan lave request til vores system og vi tjekker over værdien for at sikre, at man ikke kan fx bruteforce ved login eller unødigt belaste systemet.

### CRUD(L)
Indenfor verdenen af IT-sikkerhed kan man bruge CRUD(L) som en testteknik ved fx at se, om en bruger har tilladelse til at udføre den handling. 
For eksempel kunne man teste med en bruger med en medarbejder-rolle, der skulle forsøge at få adgang til noget, hvor en bruger skal have en leder-rolle. Her ville man kunne se, om man succesfuldt kan blokere de forkerte typer af brugere fra at få adgang til det data, man vil beskytte.


### Cycle process test
<img width="292" height="627" alt="image" src="https://github.com/user-attachments/assets/b903d0ad-6f3d-4673-a16c-3a56389f20a2" />

-En bruger starter på start-siden.

-Brugeren forsøger at logge ind.

-Her tjekker autentifikationen om de må.

-Hvis nej, bliver de sendt tilbage til login.
(Eventuelt kan man have et tjek på antal gange de forsøger, så de bliver stoppet efter 3 måske.)

-Hvis ja, bliver får de tilladelse og bliver givet adgang til systemet. 

-Her kan de vælge at trykke på log ud-knappen, hvor der bliver spurgt om brugeren gerne vil det.

-Hvis nej, forbliver brugeren i systemet.

-Hvis ja, bliver brugeren logget ud.

-Her bliver brugeren ført tilbage til start, som før de loggede ind.



### Test Pyramiden 
<img width="617" height="322" alt="image" src="https://github.com/user-attachments/assets/92d23e34-5ae8-4733-b6c4-f52975986513" />

End-to-end-test: Brugerrejser fra ende til anden bl.a. med fokus på funktionalitet, brugervenlighed, brugeroplevelse. 

System test/UI: Om en bruger oplever cyklussen korrekt i UI. 

Integration test: teste flower uden UI (fx login også i forhold til session).

Unit Test: Funktionalitet, sessioner, om et password bliver hashet, tjekke roller.


### Decision table test


| Situation          | Test1        | Test2                         | Test3                        | Test4                         |
|--------------------|--------------|-------------------------------|------------------------------|-------------------------------|
| Gyldigt brugernavn | Ja           | Ja                            | Ja                           | Ja                            |
| Gyldigt password   | Ja           | Ja                            | Ja                           | Nej                           |
| MFA aktiveret      | Ja           | Ja                            | Nej                          | -                             |
| MFA korrekt        | Ja           | Nej                           | Nej                          | -                             |
| Resultat           | Adgang givet | Adgang nægtet - Hændelse logget | Adgang givet - Advarsel om MFA | Adgang nægtet - Hændelse logget |



### Security gates:

Ækvivalens klasser:
Code / Dev gate, System security gate

Grænseværdi test:
Code / Dev gate

CRUD(L):
Code / Dev gate, Integration security gate

Cycle process test:
Go / No-Go security gate (Prod),

Test Pyramiden:
Integration security gate, Release candidate security gate (Pre-Prod)

Decision table test:
Code / Dev gate, System security gate




## Softwaresikkerhed d. 3. februar
### Unittest
<img width="1746" height="1020" alt="image" src="https://github.com/user-attachments/assets/7a5d863a-4b6e-4e1d-9c4e-5b93d4a0f600" />




