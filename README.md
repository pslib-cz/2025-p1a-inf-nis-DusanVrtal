# MatchOps - Systém pro správu esport turnajů

Moderní webová aplikace určená pro kompletní organizaci, správu a zaznamenávání esportovních turnajů a zápasů v rámci škol, firem nebo komunitních lig. 

**Odkaz na běžící web:** [MatchOps na GitHub Pages](https://pslib-cz.github.io/2025-p1a-inf-nis-DusanVrtal/)

---

## 🚀 Klíčové funkce systému

* **Komplexní správa uživatelů a rolí:** Rozlišení uživatelských práv (Administrátor, Kapitán týmu, Hráč, Divák) s možností rychlého přihlášení přes Discord.
* **Registrace a správa týmů:** Možnost zakládání týmů kapitány, generování pozvánkových odkazů a správa soupisek včetně náhradníků.
* **Automatizované generování turnajů:** Podpora různých herních formátů – *Single Elimination* (pavouk na jednu prohru), *Double Elimination* (opravný pavouk) a *Round Robin* (každý s každým).
* **Zabezpečené zapisování výsledků:** Systém proti podvodům vyžadující potvrzení výsledku oběma kapitány, s možností nahrání screenshotu jako důkazu a manuálním zásahem admina v případě sporů.
* **Statistiky a globální žebříčky:** Sledování individuální historie a herních metrik (výhry/prohry, specifická data podle her) spojené s veřejným leaderboardem.
* **Integrace s platformou Discord:** Automatické zasílání notifikací (začátky zápasů, výsledky, nové turnaje) na herní servery pomocí Discord Webhooků.

---

## 📊 UML Specifikace projektu (v2.5)

Architektura a chování systému jsou podrobně navrženy a zdokumentovány pomocí následujících UML diagramů, které najdeš přímo na úvodní stránce projektu:

1.  **Uživatelské role a oprávnění (Actor Diagram):** Znázorňuje hierarchii uživatelů a dědičnost přístupových práv.
2.  **Případy užití (Use Case Diagram):** Mapuje konkrétní funkce systému na jednotlivé aktéry uvnitř systémové hranice.
3.  **Databázový model (ERD / Class Diagram):** Reprezentuje strukturu entit (Uživatelé, Týmy, Turnaje, Zápasy) v relační databázi a jejich kardinality.
4.  **Architektura a infrastruktura (Deployment Diagram):** Zobrazuje fyzické nasazení aplikace (Frontend, REST API backend, PostgreSQL databáze) a integraci s Discord API.

---

## 🛠️ Navržený technologický stoh (Tech Stack)

* **Frontend:** Responzivní webová aplikace optimalizovaná pro mobilní zařízení (hráči zadávají výsledky přímo z telefonů po zápase).
* **Backend:** REST API post