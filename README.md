# IBMi

- https://developer.ibm.com/articles/i-newtoibmi/
- https://developer.ibm.com/components/ibm-i/tutorials/

- IBMi Documentation – https://www.ibm.com/docs/en/ibm-i  
- IBMi ACS – https://www.ibm.com/support/pages/ibm-i-access-client-solutions  
- IBMi Redbooks – https://www.redbooks.ibm.com

- https://www.ibm.com/support/pages/ibm-i-access-acs-getting-started

## 2.1. Kluczowe elementy IBMi
- **LPAR** – partycja logiczna systemu  
- **Library (LIB)** – główny kontener na obiekty  
- **Object** – jednostka funkcjonalna (program, plik, kolejka, user space itd.)  
- **Db2 for i** – wbudowana baza danych  
- **Subsystem (SBS)** – środowisko uruchomieniowe dla jobów  
- **Job** – proces w systemie  

## 2.2. Tryby pracy
- **Green screen (5250)** – podstawowa konsola administracyjna  
- **Narzędzia nowoczesne**:  
  - ACS (Access Client Solutions)  
  - Navigator for i  
  - SQL Performance Center  

---

# 3. Najważniejsze komendy administracyjne

## 3.1. Monitorowanie systemu
```WRKACTJOB - aktywne joby (monitoring)
WRKSYSSTS - statystyki systemowe
WRKSBS - subsystemy
WRKDSKSTS - status dysków
WRKCFGSTS - konfiguracja urządzeń
DSPMSG - komunikaty systemowe
```

## 3.2. Zarządzanie jobami

```WRKJOB - praca z jobem
ENDJOB - zakończenie jobu
SBMJOB - submit job (tło)
WRKJOBSCDE - harmonogram zadań
```

## 3.3. Użytkownicy i bezpieczeństwo
```WRKUSRPRF - lista profili
DSPUSRPRF - szczegóły profilu
CHGUSRPRF - zmiana użytkownika
GO SECTOOLS - narzędzia bezpieczeństwa
```


## 3.4. Obiekty i biblioteki
```WRKLIB - lista bibliotek
WRKOBJ - obiekty w systemie
DSPOBJD - informacje o obiektach
DSPLIB - zawartość biblioteki
```


## 3.5. Baza danych / SQL
```STRSQL - interaktywny SQL
RUNSQLSTM - uruchom skrypt .sql
DSPFD - definicja pliku
DSPFFD - pola pliku
WRKDBF - przegląd danych
```


## 3.6. Backup / Restore
```GO SAVE - menu backupu
SAVLIB - backup biblioteki
SAVOBJ - backup obiektu
RSTLIB - restore biblioteki
RSTOBJ - restore obiektu
```

## 3.7. System i operacje krytyczne
```CHGSYSVAL - zmiana wartości systemowej
PWRDWNSYS - wyłącz / restart systemu
RSTLICPGM - reinstalacja pakietów licencyjnych
GO LICPGM - zarządzanie LICPGM
```


---

# 4. Narzędzia administratorskie

## 4.1. IBM Access Client Solutions (ACS)
- SQL Scripts  
- Database Navigator  
- Console  
- Virtual Control Panel  
- Transfer plików  

## 4.2. Navigator for i
- Monitorowanie wydajności  
- Zarządzanie użytkownikami  
- Analiza SQL  
- IFS browser  

## 4.3. Logi i diagnostyka
- QSYSOPR — komunikaty operacyjne  
- QHST — historia systemu  
- DSPLOG — logi jobów  

---

# 5. Podstawowe procedury

## 5.1. Restart subsystemu
```ENDSBS SBS(Nazwa) OPTION(*IMMED)
STRSBS SBSD(Nazwa)
```

## 5.2. Sprawdzenie kto blokuje obiekt
```
WRKOBJLCK OBJ(LIB/OBIEKT) OBJTYPE(*FILE)
```

## 5.3. Uruchomienie programu
```
CALL PGM(LIB/PROGRAM)
```

## 5.4. Sprawdzenie statusu systemu
W green screen:
```
WRKSYSSTS
```

W ACS:
- Performance → System Status

---

# 6. Najważniejsze biblioteki systemowe

| Biblioteka | Opis |
|------------|-------|
| **QSYS** | główna biblioteka systemu |
| **QGPL** | domyślna biblioteka użytkowników |
| **QUSRSYS** | profile, kolejki, konfiguracja |
| **QHLPSYS** | help |
| **QIBMDB** | baza Db2 for i |
| **QSECOFR** | profil administratora root |

---

# 7. Dobre praktyki dla admina

- **Zawsze monitoruj WRKACTJOB** → anomalia CPU/LCK są tam widoczne pierwsze.  
- **Pracuj na osobnym profilu, nie na QSECOFR**.  
- Regularnie czyść:
  - QEZJOBLOG  
  - stare spool file (WRKSPLF)  
  - IFS /tmp  
- Dokumentuj zmiany w system values (CHGSYSVAL).  
- Testuj joby najpierw w tle z niskim priorytetem.  
- Używaj ACS SQL Scripts do automatyzacji.  

---



