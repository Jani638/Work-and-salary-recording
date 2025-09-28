# Työajanseuranta ja palkanlaskenta -sovellus

Sovellus on **työajanseuranta ja palkanlasku**, joka on toteutettu **Spring Bootilla** ja noudattaa **MVC-arkkitehtuuria**. Se hyödyntää **JPA:ta tietokanta-rajapinnassa** ja on kytketty **ulkoiseen tietokantaan**, joka mahdollistaa pilvipalvelussa toimimisen.

Sovelluksessa on kaksi käyttäjäroolia:
- **Tavallinen käyttäjä**: näkee omat työaikakirjauksensa ja lasketun nettopalkan, mutta ei voi lisätä, muokata tai poistaa tietoja.
- **Admin**: hallinnoi kaikkia työaikakirjauksia ja käyttäjiä, ja voi suorittaa CRUD-toimintoja.

**Käyttöliittymä** on toteutettu **Thymeleafilla**, ja HTML-sivuilta haetaan tietoa tietokannasta. Sovellus tulee sisältämään vähintään yhden **OneToMany-rakenteen**: esimerkiksi `User`-entiteetti liittyy useisiin `WorkLog`-entiteetteihin.

Sovellus tukee **CRUD-toimintoja** sekä Thymeleafin kautta että **REST-rajapinnan** kautta (`GET`, `POST`, `PUT`, `DELETE`), ja kaikki käyttäjien syötteet validoidaan `@Valid`-annotaatiolla.

**Spring Security** huolehtii kirjautumisesta ja käyttöoikeuksista: vain admin-käyttäjällä on täydet oikeudet, tavallinen käyttäjä saa vain lukuoikeuden.

Lisäominaisuutena sovellus laskee käyttäjän **nettopalkan** kirjattujen työtuntien ja käyttäjän tuntipalkan perusteella, huomioiden **vakiovähennykset**.

Sovellus voidaan julkaista esim. Herokuun tai AWS:ään käyttäen ulkoista tietokantaa, kuten PostgreSQL:ää tai MySQL:ää.
