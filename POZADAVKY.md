# Katalog požadavků – Systém pro správu esport turnajů

---

## Funkční požadavky

Funkční požadavky popisují, co systém musí umět udělat.

### Správa uživatelů a rolí

- **1: Registrace a přihlašování:** Uživatel si vytvoří účet přes e-mail, nebo se přihlásí přes Discord – to dává smysl, protože většina hráčů Discord stejně používá.
- **2: Rozlišení rolí:** Systém rozlišuje čtyři role:
    - **Administrátor / Organizátor:** Plná práva – zakládá turnaje, schvaluje výsledky, spravuje uživatele.
    - **Kapitán týmu:** Zakládá tým, zve hráče a přihlašuje tým do turnaje.
    - **Hráč:** Má profil, vidí vlastní statistiky a historii zápasů.
    - **Divák / Host:** Může procházet turnaje a žebříčky bez registrace.

### Registrace a správa týmů

- **1: Založení týmu:** Kapitán vytvoří tým, zvolí název, volitelně nahraje logo a vygeneruje pozvánkový odkaz pro ostatní hráče.
- **2: Soupiska:** Kapitán může přidávat a odebírat hráče, označit náhradníky. Maximální počet hráčů zatím není pevně daný – bude záviset na hře.

### Správa turnajů a generování pavouka

- **1: Vytvoření turnaje:** Organizátor vyplní název, hru, datum, maximální počet týmů a formát. Turnaj může být veřejný nebo uzavřený (jen přes pozvánku).
- **2: Automatické generování pavouka:** Po uzavření registrací systém vygeneruje pavouk. Podporované formáty:
    - Single Elimination – klasický pavouk, jedna prohra a je konec
    - Double Elimination – poražení dostanou druhou šanci v opravném pavouku
    - Round Robin – každý s každým, výsledky se sčítají do tabulky

### Zapisování výsledků a zápasů

- **1: Zadávání výsledků:** Po zápase kapitán zadá skóre a nahraje screenshot jako důkaz. Výsledek musí potvrdit oba kapitáni – teprve pak je finální.
- **2: Schvalování výsledků:** Pokud se kapitáni neshodnou nebo jeden nereaguje, organizátor může výsledek rozhodnout ručně. Bez toho se turnaje snadno zaseknou.
- **3: Historie zápasů:** Každý zápas zůstane v systému uložený včetně skóre a screenshotu.

### Statistiky hráčů a žebříček

- **1: Individuální statistiky:** Hráčský profil zobrazuje počet turnajů, výher a proher. Podle hry i specifičtější věci jako KDA (LoL, CS) nebo počet gólů (FIFA). Konkrétní metriky závisí na hře.
- **2: Globální žebříček:** Veřejná tabulka nejlepších hráčů a týmů podle bodů z turnajů. Přesný bodovací systém ještě není dořešený.

### Propojení s Discordem

- **1: Notifikace přes webhook:** Organizátor zadá webhook URL svého serveru a systém tam posílá oznámení – nový turnaj, start zápasu, zapsané výsledky apod.
- **2: Automatické vytváření kanálů:** (Volitelné, nízká priorita) Po zahájení zápasu by systém mohl vytvořit hlasový kanál pro oba týmy. Hezká funkce, ale není kritická pro první verzi.

---

## Nefunkční požadavky

Nefunkční požadavky říkají, jak má systém fungovat – výkon, bezpečnost, spolehlivost.

### Bezpečnost a ochrana dat

- **1: Hashování hesel:** Hesla se ukládají hashovaná pomocí bcrypt, nikde v databázi nesmí být v plaintextu.
- **2: Ochrana proti podvodům:** Kapitán nemůže potvrdit výhru sám sobě – výsledek musí schválit druhá strana nebo admin.
- **3: Autorizace:** Každý API požadavek ověřuje oprávnění uživatele. Hráč nesmí měnit výsledky zápasů, ve kterých nehraje.

### Dostupnost a výkon

- **1: Rychlost odezvy:** Pavouk a žebříčky se musí načíst do 2 sekund za normálních podmínek. Při vyšší zátěži (konec kola) max 5 sekund.
- **2: Responzivita:** Web musí fungovat na telefonu – hráči budou zadávat výsledky z mobilu přímo po zápase. Responzivní design je nutnost.

### Spolehlivost a rozšiřitelnost

- **1: Souběžný přístup:** Systém musí zvládnout desítky kapitánů zapisujících výsledky najednou (typicky konec kola turnaje). Transakce v databázi musí být řešeny správně.
- **2: Modularita:** Přidání nové hry a jejích statistik nesmí vyžadovat přepisování celého systému. Her bude časem přibývat.

### Použité technologie

- **1: Databáze:** PostgreSQL – zvolený kvůli podpoře transakcí a spolehlivosti při souběžném přístupu. MySQL by šel taky, ale Postgres má lepší podporu pro složitější dotazy.
- **2: Backend:** REST API, pravděpodobně Node.js nebo Python (FastAPI) – zatím nerozhodnuto.
- **3: Frontend:** Responzivní webová aplikace, framework zatím nerozhodnutý. Důraz na rychlé načítání na mobilech.