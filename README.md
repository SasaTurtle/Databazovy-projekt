<h1>Databazovy projekt - Golf</h1>

<h3>Projekt je zamereny na golfovy rezervacni system.</h3>

Projekt bezi na mssql serveru a logika je vytvorena v .NET core projektu za pomoci Entity Frameworku (EF).
Nektere API jsou ochranene JWT tokenem.
Konfigurace je ulozena v appsetings.json souboru.

Zakladem projektu je rezervace, ktera je pres rezervacni API (viz. Swagger: 'https://localhost:44304/swagger/index.html') pomoci EF napojena do tabulky rezevace.
Tabulka Rezervace je vazebni tabulka Mezi Uzivatelem a Mistem. K Uzivateli jsou jeste napojeny tabuky Platebni historie a Role(admin nebo user).
Cely projekt je nadesignovan podle navrhoveho vzoru MVC - model, viewer(momentalne swagger) a controller. Coz znamena, ze kazda tabulka ma svuj model a crud controller.

Cotroller tridy krome crud metod maji metodu pro vlozeni vice zaznamu najednou.
Abych vyhovel zadani tak UserController ma metodu 'PostUserReservation' navic pro import vice tabulek najednou.

LoginCrontroller se po zadani emailu nebo jmena a hesla podiva do databaze a pokud najde schodu s existujicim uzivatelem tak vrati vygenerovany bearer token. Ten se pak pro autorizaci vklada do ostatnich API.

<h2>Swagger</h2>
V mem pripade je toto moje uzivatelske rozhrani ve kterem uzivatel muze: vypsat vsechny zaznamy nebo vypsat 1 zaznam podle id, vytvorit 1 zaznam, updatnout zaznam, vymazat zaznam a vytvorit vice zaznamu. Uzivatel navic muze pridat zaznam uzivatele s rezervacni tabulkou.
Tady jsou videt vsechny moje API:
<img width="564" alt="image" src="https://github.com/SasaTurtle/Databazovy-projekt/assets/56025180/71d61962-d95c-4a94-94c9-7c29f10561b1">

Tady je screenshot jak se vklada zaznam pro uzivatele. Staci kliknout na API -> pak dat "Try it out" -> pak vlozite data do **Jsonu** v policku "Request body" -> a pak kliknete Execute, pokud vsecno probehne v poradku tak se uzivatel ulkozi do databaze.
<img width="765" alt="Untitled" src="https://github.com/SasaTurtle/Databazovy-projekt/assets/56025180/3c8b5451-1071-4d88-8b19-529070e0f049">
<h2>Diagram databaze</h2>
<img width="550" alt="image" src="https://github.com/SasaTurtle/Databazovy-projekt/assets/56025180/f8841d98-18cb-4ca4-832d-eae155b95758">
