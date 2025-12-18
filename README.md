# Johdatus agentteihin ja MCP-palvelimiin

Agentit ovat tekoälyyn perustuvia ohjelmia, jotka pystyvät toimimaan itsenäisesti käyttäjän puolesta. Ne eivät ainoastaan vastaa kysymyksiin, vaan voivat myös tehdä päätöksiä, suorittaa monivaiheisia tehtäviä ja käyttää erilaisia työkaluja tai palveluita, kuten tiedonhakua, tiedostojen käsittelyä tai ohjelmointirajapintoja. Agentti toimii sille annettujen ohjeiden (kehotteiden), käytettävän kielimallin ja saatavilla olevien työkalujen perusteella, ja sitä voidaan käyttää esimerkiksi apuohjelmana, chatbotina tai osana laajempaa sovellusta.

MCP-palvelimet (Model Context Protocol, mallikontekstiprotokolla) ovat palveluita, jotka tarjoavat agenteille pääsyn ulkoisiin toimintoihin ja tietolähteisiin yhtenäisellä tavalla. MCP määrittelee standardoidun rajapinnan, jonka kautta agentti voi pyytää esimerkiksi tietokantahakuja, tiedostojen lukemista tai muiden järjestelmien toimintoja.

Tässä opetusmateriaalissa kokeillaan agenttien luomista ja käyttöä sekä MCP-palvelinten hyödyntämistä kahdella eri ohjelmalla ja kielimallilla: Microsoftin Visual Studio Codella ja OpenAI:n GPT-kielimallilla sekä Anthropicin Claude Desktopilla ja sen käyttämällä Sonnet-kielimallilla. 

Opetusmateriaali on laadittu Seinäjoen ammattikorkeakoulussa osana Tekoälyn hyödyntäminen ja ohjelmistorobotiikka -hanketta, jonka rahoitti Jatkuvan oppimisen ja työllisyyden palvelukeskus (JOTPA). 

<img src="kuvituskuvat/SEAMK_lila_logo_nimella_FI.png" alt="SEAMKin logo" width="200"/>

<img src="kuvituskuvat/Rahoittaja_Jotpa_fi.png" alt="JOTPAn logo" width="300"/>



## Visual Studio Coden AI Toolkit -lisäosa

Visual Studio Code (VS Code) on Microsoftin kehittämä ilmainen ja avoimen lähdekoodin koodieditori, jota käytetään laajasti ohjelmoinnin opetuksessa ja ohjelmistokehityksessä. Se tukee monia ohjelmointikieliä, kuten Pythonia, JavaScriptiä, Javaa ja C++:aa, sekä tarjoaa ominaisuuksia kuten syntaksin korostuksen, automaattisen koodintäydennyksen ja virheiden korostamisen. VS Codea voidaan laajentaa lukuisilla lisäosilla, joiden avulla siihen saa esimerkiksi kielikohtaisia työkaluja ja debuggausominaisuuksia. 

Microsoftin oma AI Toolkit -lisäosa Visual Studio Codeen on asennettavissa Extensions-välilehdeltä. Tämä lisäosa tuo editoriin työkaluja ja käyttöliittymän tekoälymallien hyödyntämiseen ohjelmistokehityksessä. Sen avulla voi selata ja ladata valmiita AI-malleja eri tarjoajilta, kokeilla niitä vuorovaikutteisessa “Playgroundissa”.

AI Toolkitin Agent Builder on laajennuksen osa, jonka avulla voi luoda, muokata, testata ja optimoida tekoälyagentteja suoraan VS Codessa. Kokeillaan Agent Builderin toimintaa.

Asennetaan ensin AI Toolkit Extensions-välilehden kautta.

![alt text](/kuvituskuvat/01_Aitoolkit_extensions.png "AI Toolkit Extensions -välilehdellä") \
*AI Toolkit Extensions -välilehdellä*

Lisäosan asennuksen jälkeen se saa oman symbolin Visual Studio coden vasemman laidan palkkiin. Sitä klikkaamalla avautuvasta valikosta löytyy Agent Builder -työkalu.

![alt text](/kuvituskuvat/02_Aitoolkit_logo.png "AI Toolkitin logo vaseammassa palkissa")\
*AI Toolkitin logo vaseammassa palkissa ja Agent Builder*

Koska AI Toolkit hyödyntää OpenAI:n GPT-mallia GitHubin kautta, täytyy ensin kirjautua GitHubiin. Jos GitHubin tunnus puuttuu, se täytyy tietysti ensin tehdä. Kun alla olevan ilmoituksen Allow-nappia painaa, täytyy vain kirjautua GitHub-tililleen. 

![alt text](/kuvituskuvat/02_githubiin_kirjautuminen.png "GitHubiin kirjautuminen")\
*GitHubiin kirjautuminen*

Agentti luodaan nimeämällä se, valitsemalla käytettävä suuri kielimalli alasvetovalikosta ja antamalla agentille toimintaohjeet Instructions-kenttään. Yksinkertaisin agentti - tosin voi kiistellä, onko silloin kyseessä varsinainen agentti - on tekstiä tiettyyn tarkoitukseen tuottava chattibotti. Tässä esimerkissä teemme palautetta antavan englannin oikolukijan. Ohjeet ovat seuraavat:

```
Your task is to correct the grammatical errors in the given English text and give supportive feedback and tips to help the author to write more fluent text. The author is a non-native student so adjust the level of the feedback accordingly.
```

Tämä teksti siis sijoitetaan Agent Builderin Instructions-laatikkoon, kuten alla oleva kuva näyttää.


![alt text](/kuvituskuvat/03_oikolukija.png "Ohjeet paikallaan Agent Builderissa")*Ohjeet paikallaan Agent Builderissa*

Nyt voimme kokeilla agentin toimintaa kirjoittamalla sille viestin oikean laidan Playground-osion viestikenttään. Seuraavassa esimerkissä on pikaisesti käännetty Ylen sivuilta uutisen alku englanniksi ja näköjään mukaan on päässyt pari typoakin, mikä on tässä tapauksessa vain hyvä asia. Alla oleva kuva näyttää agentin toiminnan eli korjatun tekstin ja saadun palautteen tällä syötteellä.

![alt text](/kuvituskuvat/04_oikolukija2.png "Esimerkki oikolukija-agentin käytöstä")*Esimerkki oikolukija-agentin käytöstä*

Ohjeet voi antaa myös suomeksi. Valitettavasti kieli ei ole aivan yhtä hyvää silloin, koska suomenkielisen opetusmateriaalin määrä on ollut vähäisempää kuin englanninkielisen Seuraavassa esimerkissä ohjeeksi on annettu tiivistää annettu teksti kolmeen pointtiin, ja agenttia kokeillaan taas Ylen uutissivuilta kopioidulla tekstillä.

![alt text](/kuvituskuvat/05_stubuttaja.png "Esimerkki kolmeen pointtiin tiivistävän agentin käytöstä")*Esimerkki kolmeen pointtiin tiivistävän agentin käytöstä. Ensimmäisen pointin 'lapsi' &rarr; 'lasta' käy esimerkiksi suomenkielisessä tekstissä tavattavasta ajoittaisesta kömpelyydestä.*

### Työkalujen lisääminen MCP-palvelimesta

Pelkkä chatbot ei välttämättä kauaa ilahduta. Agentista on enemmän hyötyä, kun se pystyy auttamaan joidenkin konkreettisten tehtävien tekemisessä. Kuten johdanto-osuudessa kerrottiin, tätä varten on MCP-palvelimet. Model Context Protocol (MCP) eli mallin kontekstiprotokolla määrittelee tavan, jolla suurille kielimalleille annetaan pääsy ulkoiseen tietoon ja työkaluihin. 

Luodaan siis uusi agentti ja kokeillaan MCP-palvelimia. Edellisen agentin voisi tallettaa, mutta eipä siihen juuri syytä ole, koska kyseessä oli vain yksinkertainen testi. Agent Builderissa työkaluja annetaan Tool-valikosta. Käytettäessä MCP-palvelimia, sieltä valitaan vaihtoehto MCP Server.

![alt text](/kuvituskuvat/06_1tool_mcp.png "Työkalun lisääminen agentille")*Työkalun lisääminen agentille*

Seuraavaksi aukeaa ylälaidan valikko, jossa näkyvät kaikki mallille määritetyt MCP-palvelimet. Koska vielä yhtäkään ei ole määritetty, tyhjältä näyttää.

![alt text](/kuvituskuvat/06_1palvelinpalkki.png "MCP-palvelimen lisääminen")*MCP-palvelimen lisääminen*

Kun klikkaa alinta vaihtoehtoa eli *Could not find one? Browse more MCP Servers*, aukeaa lista vaihtoehdoista.

![alt text](/kuvituskuvat/06_2palvelinlistaus.png "MCP-palvelinlistaus")*MCP-palvelinlistaus*

Kokeillaan muutamaa MCP-palvelinta, jotta nähdään, kuinka ne toimivat.

#### Esimerkki 1: GitHubin MCP-palvelin

Kun valitaan listauksen ensimmäinen vaihtoehto eli GitHub, Agent Builder lisää tiedot siitä mcp.json-nimiseen json-tiedostoon. Tiedosto näyttää nyt tältä:

```
{
  "servers": {
    "github": {
      "type": "http",
      "url": "https://api.githubcopilot.com/mcp/",
      "headers": {
        "Authorization": "Bearer {{YOUR_ACCESS_TOKEN}}"
      }
    }
  }
}
```
Varsinaisia työkaluja ei kuitenkaan vielä ole lisätty, vaan tämä json-tiedosto pitää määritellä loppuun asti. Autorisointikohtaan täytyy nimittäin lisätä henkilökohtainen GitHubin tokeni. Sen avulla agentti pystyy käyttämään GitHubin työkaluja, joita sinäkin Gitiä käyttäessäsi hyödynnät. Käytännössä se siis korvaa käyttäjänimen ja salasanan, ja agentti pääsee näin kirjautumaan GitHub-tilillesi. Tokenin saa luotua kirjautumalla ensin GitHub-tilille, klikkaamalla sitten oikeasta yläkulmasta omaa profiilikuvaansa ja valitsemalla Settings puolivälin tienoilta alasvetovalikosta.

![alt text](/kuvituskuvat/06_github_settings.png "GitHub-tilin valikko") \
*GitHub-tilin valikko*

Tämän jälkeen sivun vasemman laidan valikosta valitaan viimeinen kohta, Developer Settings.

![alt text](/kuvituskuvat/07_dev_settings.png "Kehittäjäasetukset vasemman laidan valikossa") \
 *Kehittäjäasetukset vasemman laidan valikossa*

Sieltä aukeavasta valikosta valitaan Personal access tokens ja Tokens (classic). Uusi token luodaan aukevan sivun nappia Generate New Token &rarr; Token (classic) 

![alt text](/kuvituskuvat/08_tokens.png "Käyttäjäasetusten sisältö") \
 *Käyttäjäasetusten sisältö* 

Nyt tokenille kirjoittaa lyhyen luontisyyn, määritellä, kauanko se on voimassa, ja valita, mihin kaikkeen sille antaa pääsyn. Annetaan ainakin kaikkiin henkilökohtaisiin repositorioihin.  

![alt text](/kuvituskuvat/08_repo.png "Tokenin pääsylupien määrittely") \
 *Tokenin pääsylupien määrittely* 

 Kun token on luotu, se näytetään käyttäjälle kerran, jotta sen saa kopioitua. Nyt tällä ghp_-alkuinen tekstirimpsulla korvataan mcp.jsonin kohta {{YOUR_ACCESS_TOKEN}}. Lopputuloksena tuo rivi näyttää siis tämäntyyliseltä:

```
 "Authorization": "Bearer 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"
```
Kun nyt lisätään työkalu uudestaan eli valitaan Agent Builderista Tool &rarr; MCP Server, löytyy github tästä aukeavasta valikosta. Kun se nyt valitaan, saa agentti käyttöön kaikkiaan 40 työkalua. Näistä voi tietysti valita vain ne, joita oikeasti tarvitsee, jos mielessä on jokin tarkemmin määritelty agentti. Koska tässä on vain tarkoitus kokeilla eri toimintoja, pidetään kaikki työkalut ja painetaan nappia OK.

![alt text](/kuvituskuvat/09_github_mcp.png "GitHubin MCP-palvelimen työkalulistaus")*GitHubin MCP-palvelimen työkalulistaus*

Nyt Tool-osiossa näkyy MCP:n alla nimi github, ja sen alta työkalulistausta voi muokata.

![alt text](/kuvituskuvat/10_github_tools.png "GitHubin MCP-palvelin listattuna agentin työkaluihin")*GitHubin MCP-palvelin listattuna agentin työkaluihin*

Kokeillaan agentin käyttöä. Annetaan toimintaohjeiksi

```
List all open issues of the repository, whose URL is given to you as a message.
```

Annetaan viestissä seuraava repositorio: https://github.com/SeAMKedu/dxf_contour_comparer. Siellä on yksi avoin kehityskohde. Kuitenkin VS Coden oikeaan alakulmaan aukeaa seuraava virheilmoitus:

![alt text](/kuvituskuvat/11_error_too_large.png "Virheilmoitus liian suuresta mallille annetusta syötteestä")*Virheilmoitus liian suuresta mallille annetusta syötteestä*

Syöte siis ylittää agentin käyttämän GitHubin isännöimän ilmaisen GPT-mallin vuorokausittaisen käyttörajoituksen. Alkuun tämä vaikuttaa kummalliselta, koska repositoriossa oli vain yksi avoin kehityskohde. Sama viesti tulee repositorioista, joissa ei ole yhtäkään avointa kehityskohdetta. Tämä johtuu siitä, että MCP-palvelimen työkalu lähettää mallille syötteenä koko repositorion kontekstin kaikkine metadatoineen. Syötteen koko ei siis riipu avointen kehityskohteiden määrästä, vaan repositorion itsensä koosta ja itse asiassa niin pientä repositoriota, jonka URLilla komento menisi läpi, vaikuttaa olevan hyvin vaikea löytää.

On siis kaksi vaihtoehtoa: joko maksaa mallin käytöstä tai käyttää Azuren AI Foundrya. Kokeillaan näistä ensimmäistä. Odotettavissa ei kuitenkaan ole kovin monen sentin kuluja.

Kirjaudutaan GitHubiin omalle tilille. Klikataan taas omaa profiilikuvaa oikeasta ylänurkasta ja valitaan Settings. Sitten mennään vasemman laidan valikosta otsikon Access alle ja avataan sieltä pudotusvalikko Billing and licensing. Valitaan pudotusvalikosta Payment information. Syötetään auennelle sivulle omat maksukorttitiedot tai Paypal-tiedot.

![alt text](/kuvituskuvat/12_payment_info.png "Billing and licensing -pudotusvalikon sisältö") \
*Billing and licensing -pudotusvalikon sisältö*

Tämän jälkeen täytyy ottaa käyttöön mallien maksullinen käyttäminen. Access-osion jälkeen on osio Code, planning, and automation, josta löytyy kohta Models. Klikataan sitä 

![alt text](/kuvituskuvat/13_models_frame.png "Code, planning, and automation -valikko") \
*Code, planning, and automation  -valikko*

Aukevalla sivulla ei ole muita otsikoita kuin Billing. Tämän alla on alaotsikko Models paid usage, joka on oletuksena poistettu käytöstä (disabled). Otetaan se käyttöön eli valitaan pudotusvalikosta enabled.

![alt text](/kuvituskuvat/14_models_paid_enabled.png "Mallien maksullinen käyttö hyväksytty") \
*Mallien maksullinen käyttö hyväksytty*

Nyt pitää vielä määritellä budjetin rajat mallien maksulliselle käytölle (kuten sivun harmaalla pohjalla lukee). Avataan siis taas Access-osion Billing and licensing pudotusvalikko, ja valitaan sieltä neljäs kohta eli Budgets and alert. Asetetaan täältä haluttu raja mallien kuukausittaiselle käytölle, esim. 5 dollaria. Tällä varmistetaan, ettei testailu käy liikaa lompakolle. 

Nyt kokeillaan VS Coden puolella uudestaan agentin toimintaa.

![alt text](/kuvituskuvat/15_github_agentti_issueviesti.png "Kehityskohteita listaavan agentin syöte ja vastaus") \
*Kehityskohteita listaavan agentin syöte ja vastaus*

Nyt agentti tekee pyydetyn asian, eikä virheilmoitusta enää tule. GitHubin käyttäjäasetuksista voidaan katsoa, paljonko tämän komennon suorittaminen maksoi. Billing and licensing -pudotusvalikon Usage-sivulta näkee päiväkohtaisen kulutuksen sekä kokonaiskulutuksen. Tähän kului näköjään 5 dollarisenttiä.

![alt text](/kuvituskuvat/16_githubin_lasku.png "Mallin käytöstä aiheutunut lasku") \
*Mallin käytöstä aiheutunut lasku*

Annetaan agentille vähän avoimempi tehtäväkuvaus, jotta päästään kokeilemaan GitHubin työkaluja laajemmin:

```
Perform only tasks related to GitHub repositories. Tell clearly what you have done.
```

Kokeillaan nyt tehdä muutoksia repositorioon agenttia käyttämällä. Vanhan hupiprojektin (https://github.com/Matopeli/sanapeli) README.md-tiedoston sisältö näyttää tältä:

![alt text](/kuvituskuvat/17_readme.png "Alkuperäisen README-tiedoston sisältö") \
*Alkuperäisen README-tiedoston sisältö*

Pyydetään agenttia lisäämään siihen suomennos. Kokeillaan hyvin yksityiskohtaista ja useampaan askeleen jaoteltua kehotetta, jotta varmasti menee oikein.

![alt text](/kuvituskuvat/18_readmen_paivityskehote.png "Readme-tiedoston päivityskehote ja agentin vastaukset siihen") \
*Readme-tiedoston päivityskehote ja agentin vastaukset siihen*

Agentti hienosti varmisti, että aikoo tehdä oikeat toimenpiteet ja raportoi lopuksi tehneensä, mitä pyydettiin. Kun nyt katsotaan tehtyä pull requestia uudesta haarasta, se näyttää tältä (punaisella siis poistot ja vihreällä lisäykset):

![alt text](/kuvituskuvat/19_pull_request.png "Päivitetyn Readme-tiedoston pull request") \
*Päivitetyn Readme-tiedoston pull request*

Kuten nähdään, muuten meni hyvin, mutta agentti on kirjoittanut kokonaan uusiksi englanninkielisen tekstin. Kun asiasta huomauttaa agentille, se kokeilee uudestaan ja vannoo, että alkuperäinen englanninkielinen teksti säilytettiin. Tuloksen voi käydä lukemassa täältä: https://github.com/Matopeli/sanapeli/tree/add-finnish-readme-translation

Periaatteessa siis näppärä apuri, mutta ihan maaliin asti ei mene. Sanan 'overwrite' lisäksi kokeiltiin muina vaihtoehtoina sanoja 'edit' ja 'modify'. Näiden neljä lisäkehotetta nostivat mallien käytön laskun yhteensä 36 dollarisenttiin. Kovin kalliita yksittäiset komennot eivät siis ole, mutta jos agentin on tarkoitus toteuttaa kymmeniä pyyntöjä päivässä, kyllä kuukaudessa toiminnalle hintaa tulee.


#### Esimerkki 2: MarkItDownin MCP-palvelin

Toisena esimerkkinä kokeillaan MarkItDownin MCP-palvelinta. Tämän palvelimen työkalujen avulla saa luotua markdown-dokumentteja (kuten tämä koulutusmateriaali) mm. PDF-, Word-, PowerPoint- ja Excel-dokumenttien sekä kuvien ja tekstitiedostojen perusteella. MCP-palvelimen avulla saa mm. annettua kielimalleille rakenteellista ja helpommin hallittavaa tekstiaineistoa. Esim. kun pdf-muotoisen raportin muuntaa ensin markdowniksi, kielimalli voi tämän jälkeen vastata kysymyksiin dokumentin sisällöstä, tehdä tiivistelmiä ja poimia dataa taulukosta.

##### Esivalmistelut

MarkItDownin MCP-palvelin asentaminen vaatii uv-nimisen paketinhallintatyökalun. Uv
on Astralin tekemä nopea, Rust-kielellä kirjoitettu Pythonin paketti- ja projektinhallintatyökalu, joka pyrkii korvaamaan useita erillisiä työkaluja (kuten `pip`, `pip-tools`, `virtualenv`) yhdellä kokonaisvaltaisella ja huomattavasti nopeammalla ratkaisulla. 

Uv asennetaan seuraavalla PowerShell-komennolla:

```
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

Astralin sivuilla on listattuna [muitakin asennustapoja](https://docs.astral.sh/uv/getting-started/installation/#__tabbed_1_2).

Lisäksi MarkItDown antaa varoituksen, jos FFmpegiä ei ole asennettu. FFmpeg on avoimen lähdekoodin komentorivityökalu, jota käytetään video- ja äänitiedostojen käsittelyyn. Se tukee lähes kaikkia yleisiä mediaformaatteja ja mahdollistaa muun muassa tiedostojen muuntamisen, äänen ja videon muokkauksen, kuvien poiminnan videosta sekä median suoratoiston verkon yli. MarkItDownin pitäisi pystyä markdown-dokumenttien tekemiseen myös audiotiedostoista ja videoiden ääniraidoista, mutta VS Coden Agent Builderissa se ei ainakaan onnistunut. Jos varoituksia ei jaksa katsella, FFmpegin voi asentaa Windowsille [seuraavan ohjevideon mukaisesti](https://www.youtube.com/watch?v=eRZRXpzZfM4).

##### Itse MarkItDownin työkalujen ottaminen käyttöön ja käyttäminen

Kun esivalmistelut on tehty, työkalut MarkItDownin MCP-palvelimelta otetaan käyttöön samalla tavoin kuin GitHubinkin MCP-palvelimelta. Luodaan siis uusi agentti, nimetään se, klikataan plussaa Tool-osiosta &rarr; MCP Server &rarr; Could not find one? Valitaan listasta MarkItDown. Palvelimelta saa vain yhden työkalun, joka konvertoi annetun verkko-osoitteen tai tiedoston markdowniksi. 

![alt text](/kuvituskuvat/20_markitdown_tool.png "MarkItDown-MCP-palvelin työkalulistauksessa") \
*MarkItDown-MCP-palvelin työkalulistauksessa*

Annetaan agentille siis yksinkertainen toimintaohje:

```
Show the document whose URL is given to you as markdown so that it can be easily copied or saved.
```

Kokeillaan toimintaa lyhyen rentoutusharjoitusohjeet sisältävän pdf-dokumentin avulla. Dokumentin osoite on https://www.mielenterveystalo.fi/sites/default/files/2023-06/Lyhyt-rentoutus.pdf.

![alt text](/kuvituskuvat/21_rentoutus.png "Rentoutusharjoituksen muuntaminen markdown-formaattiin") \
*Rentoutusharjoituksen muuntaminen markdown-formaattiin ja tiedoston alku agentin vastauksessa.*

Agentti luo vastauksen ylälaitaan kätevästi napit tekstin kopioinnille ja avaamiseen omaan tiedostoonsa tallennusta varten. Valmis dokumentti on siis [tässä](testitiedostot/lyhyt_rentoutus.md).

Oheisessa taulukossa on kaksi muuta osoitetta muunnettuna markdowniksi agentin avulla. Muutaman hyvin pitkän dokumenin kanssa agentti lopetti toiminnan kesken, ja netissä olleita Word-dokumentteja  

| Osoite | markdownina |
|--------|----------------------
|https://storage.googleapis.com/seamk-production/2017/08/pysakointi-framin-alueella.pdf|[pysäköintitiedot](testitiedostot/pysakointi.md)|
|https://www.seamk.fi/tietoa-seamkista/organisaatio|[organisaatiodokumentti](testitiedostot/seamk_orga.md)|
|https://laki24.fi/wp-content/uploads/2021/05/Lahjakirja-%E2%80%93-ka%CC%88ytto%CC%88-ja-hallintaoikeuden-pida%CC%88tta%CC%88minen.docx|[lahjakirja](testitiedostot/lahjakirja.md)|

Koska osa dokumenteista oli kohtalaisen suuria (epäonnistuneiden listalla oli mm. [SEAMKin harjoitustyöpohja](https://seamk.libguides.com/ld.php?content_id=35766912)), tuli tälle leikkimiselle kaikkineen hintaa 87 dollarisenttiä. Kokonaisuudessaan onnistuneita dokumentteja luotiin seitsemän kappaletta ja epäonnistuneita yrityksiä oli yli 10 (osaan ei ollut pääsyoikeutta, osassa toiminta loppui kesken).

### Agent Builder: havainnot ja johtopäätökset

Agenttien tekeminen ja MCP-palvelinten käyttöönotto Agent Builderissa on näennäisen yksinkertaista, mutta MCP-palvelinten käyttö edellyttää usein jonkin ulkoisen ympäristön asentamista tai tokenien tekemistä palveluun, mitä ei ole millään lailla ohjeistettu. Asia vain pitää itse selvittää virheilmoitusten perusteella. Käytettävyys ei siis vielä ole aivan valtavan hyvä ja esim. ImageSorcery-MCP-palvelinta ei onnistuttu tämän materiaalin teon aikana ottamaan käyttöön ilmeisesti riippuvuusristiriitojen takia. Visual Studio Code on ohjelmoinnissa käytettävä editori ja sen agenttityökalujen käyttäminen on selvästi suunnattu enemmän ohjelmoijille kuin kenelle tahansa, vaikka mainosmateriaali antaa muuta odottaa.


Myös MCP-palvelinten käyttö GitHubin kautta isännöidyn OpenAI:n kielimallin avulla alkaa aika nopeasti maksaa jotain. Tämän materiaalin teon aikana loppulasku jäi toki reiluun dollariin, mutta työkalujen tehokas käyttö alkaa varmasti jo kuukausitasolla tuntua.


## Claude Desktop

Tutustutaan seuraavaksi MCP-palvelinten käyttöön Claude Desktopissa. Claude Desktop on työpöytäsovellus Anthropicin Claude-tekoälyavustimelle. Claudea voi siis käyttää työpöydältä sen sijaan, että käyttäisi sitä selaimen kautta. Claude Desktop tarjoaa samat keskustelu- ja tekoälyominaisuudet kuin verkkoversio mutta syvemmällä integraatiolla käyttöjärjestelmään ja paikallisiin resursseihin. Tässä materiaalissa ei varsinaisesti tehdä Claudella agenttia, mutta sitä käytetään agenttimaisesti eli sille annetaan käyttöön työkaluja ja sillä suoritetaan automatisoidusti tehtäviä.

Claude Desktop asennetaan osoitteesta https://claude.com/download, ja asentaminen on yksinkertaista. Käynnistäessä Claude aukeaa omaan ikkunaansa.

![alt text](/kuvituskuvat/claude_alku.png "Claude Desktopin alkunäyttö") \
*Claude Desktopin alkunäyttö*

### MCP-palvelimet Claudessa

MCP-palvelimia ja niiden työkaluja saa lisättyä Claude Desktopiin klikkaamalla viestikentän vasemman alakulman plussaa ja valitsemalla Connectors &rarr; Manage Connectors &rarr; Browse Connectors. 

![alt text](/kuvituskuvat/22_claude_alkunaytto.png "Työkalujen lisääminen Claude Desktopin keskustelun alkunäytöstä") \
*Työkalujen lisääminen Claude Desktopin keskustelun alkunäytöstä.*

Claudessa MCP-palvelmista käytetään tosiaan termiä konnektorit (connectors). Nyt aukaa lista eri MCP-palvelimista, joita voidaan ottaa käyttöön. Nämä on eroteltu hieman yksinkertaistaen pilvipohjaisiin MCP-palvelimiin (web) ja paikallisiin MCP-palvelimiin (desktop extensions). 

#### Esimerkki 1: Filesystem-MCP-palvelin

Kokeillaan alkuun Filesystem-MCP:tä, jonka työkalujen avulla Claude pääsee käsiksi haluttuihin hakemistoihin kovalevyllä. Se on listattuna ensimmäiseksi Desktop extensions -välilehdellä.

![alt text](/kuvituskuvat/23_claude_tyokalut.png "Laajennusvalikoima") \
*Laajennusuvalikoima.*

Filesystem-laajennusta klikattuaan näkee listauksen työkaluista, jotka laajennus tuo käyttöön. Kuten nähdään, ne liittyvät tiedostojen ja hakemistojen lukemiseen, kirjoittamiseen ja muokkaamiseen.

![alt text](/kuvituskuvat/26_filesystemin_tyokalut.png "Filesystem-laajennuksen työkalut") \
*Filesystem-laajennuksen työkalut.*

Filesystem-laajennuksen asentamisen yhteydessä täytyy valita hakemistot, joihin talletettuihin tiedostoihin se pääsee käsiksi. Claudea varten voi vaikka luoda oman hakemistonsa, jotta minimoidaan riskit tärkeiden tiedostojen tuhoamisesta. Claude pyytää varmistuksen ennemmin kuin tekee muutoksia, mutta ei vara venettä kaada.

![alt text](/kuvituskuvat/25_konffaa_hakemistot.png "Sallittujen hakemistojen lisääminen Filesystem-laajennukselle") \
*Sallittujen hakemistojen lisääminen Filesystem-laajennukselle.*

Kun hakemistot on lisätty, nähdään, että Filesystem-laajennus on otettu onnistuneesti käyttöön.

![alt text](/kuvituskuvat/24_enable.png "Filesystem-laajennus otettuna käyttöön") \
*Filesystem-laajennus otettuna käyttöön.*

Kokeillaan laajennuksen käyttöä. Nimetään sen avulla hakemistollinen tiedostoja uudelleen. Seuraava kuva esittelee hakemiston sisällön alkutilanteessa.

![alt text](/kuvituskuvat/34_alkuperainen_kuvajarjestys.png "Hakemiston sisältämien tiedostojen nimet alkutilanteessa") \
*Hakemiston sisältämien tiedostojen nimet alkutilanteessa.*

Halutaan muuttaa tiedostojen nimet siten, että niiden aluksi on järjestysnumero ja alaviiva, ja sitten on nykyinen tiedostonimi. Halutaan lisäksi, että aloitetaan numerosta 27. Kirjoitetaan siis kehote asiasta Claude Desktopille.

![alt text](/kuvituskuvat/35_jarjestamiskehote.png "Kehote tiedostojen uudelleennimeämiseen") \
*Kehote tiedostojen uudelleennimeämiseen.*

Claude pyytää käyttäjältä varmistukset kaikkiin toimiinsa. Ensin se haliaa tarkistaa hakemiston sisältämät tiedostot.

![alt text](/kuvituskuvat/36_tiedostolistauspyynto.png "Pyyntö sallia tiedostolistauksen tekeminen") 
\
*Pyyntö sallia tiedostolistauksen tekeminen.*

Hankittuaan tiedostolistauksen Claude kertoo, montako tiedostoa löysi ja pyytää luvan nimetä tiedostot uudestaan. Luvan saatuaan se niin tekee ja kertoo tuloksen

![alt text](/kuvituskuvat/37_uusi_kuvajarjestys.png "Pyynnön toteutus") 
\
*Pyynnön toteutus.*

Pyydetään vielä erikseen Claudea poistamaan ensimmäisestä ja toisesta tiedostosta ylimääräinen numerointi ja toiseksi viimeisestä ja viimeisestä _x ja _y. Lopputulos näkyy alla.

![alt text](/kuvituskuvat/38_lopullinen_kuvajarjestys.png "Lopulliset tiedostonimet") 
\
*Lopulliset tiedostonimet.*

#### Esimerkki 2: Windows-MCP

Kokeillaan seuraavaksi Windows-MCP-palvelinta. Sen avulla Claude pystyy käyttämään Windows-käyttöjärjestelmän toimintoja. Windows-MCP löytyy myös Desktop extensions -välilehdeltä neljäntenä ylhäältä. Kun keskustelu on käynnissä, konnektoreita/MCP-palvelimia saa lisättyä painamalla viestiruudun vasemman alakulman plussaa &rarr; Connectors &rarr; Manage Connectors. Connectorsin takaa nähdään myös, mitkä konnektorit ovat käytössä. Windows-MCP:n käyttöön ottamisen jälkeense näyttää tältä.

![alt text](/kuvituskuvat/55_kaytossa_olevat_konnektorit.png "Käytössä olevat MCP-palvelimet.") 
\
*Käytössä olevat MCP-palvelimet.*

Käytössä olevien MCP-palvelinten tarkemman työkalulistauksen näkee klikkaamalla edellisen kuvan valikosta Manage Connectors ja sieltä haluamansa MCP-palvelimen kohdalla Configure. Ainakin toistaiseksi (tätä materiaalia tehdessä paikka vaihtui kerran). Windows-MCP:n työkalut sekä niiden vaatimat luvat nähdään alla.

![alt text](/kuvituskuvat/56_Winkkarin_tyokalut.png "Windows-MCP:n työkalut.") 
\
*Windows-MCP:n työkalut ja luvat.*

Nähdään, että monet työkaluista liittyvät hiiren käyttämiseen. Testataan niitä yksinkertaisen tehtävän avulla.

##### Testi 1: Ohjelman käynnistys työpöydältä

Kokeillaan käynnistää ohjelma työpöydältä. Työpöytä näyttää seuraavalta.

![alt text](/kuvituskuvat/49_kuvakkeet_alussa.png "Työpöydän pikakuvakkeet.") 
\
*Työpöydän pikakuvakkeet.*

Koska Claude pyytää lupaa kaikkiin toimintoihinsa, kannattaa pienentää Clauden ikkunaa sen verran, että työpöydän pikakuvakkeet näkyvät ikkunan vierestä. Tällöin toimintojen kuittaus eli Claude-ikkunan aktivointi ei peitä näkymää työpöydälle. Pyydetään Claudea käynnistämään Pylon Viewer.

![alt text](/kuvituskuvat/50_pylonin_kaynnistys.png "Pylon Viewerin käynnistys.") 
\
*Pylon Viewerin käynnistys*

Ensin Claude pyytää lupaa katsoa, mitä työpöydällä on. Löydettyään oikean pikakuvakkeen, se pyytää lupaa liikuttaa hiirtä pikakuvakkeen päälle ja kaksoisklikata hiiren vasemmalla painikkeella. Luvat saatuaan se liikuttaa kursorin oikeaan paikkaan ja avaa ohjelman.

##### Testi 2: nettisivun sisällön tulostus

Yksi Windows-MCP:n työkaluista oli scrape tool. Suomeksi sitä voisi kutsua kaapimis- tai haravointityökaluksi, sillä sillä haravoidaan tietoa verkkosivuilta. Kokeillaan hakea sillä tietoa SEAMKin verkkosivuilta seuraavalla kehotteella.

![alt text](/kuvituskuvat/51_scrape_tool.png "Haravointityökalun käyttö tiedonhakuun SEAMKin verkkosivuilta.") 
\
*Haravointityökalun käyttö tiedonhakuun SEAMKin verkkosivuilta.*

Haravointityökalut välittävät tiedon JSONina tai markdownina. Näin ollen sitä voi käyttää myös verkkosivujen markdown-muuntimena kuten Visual Studio Coden tapauksessa kokeiltiin. Kokeillaan tämä haravointityökalun toimintoa myös SEAMKin verkkosivujen avulla.

![alt text](/kuvituskuvat/52_tki_markdowniksi.png "Sivun sisällön esittäminen markdownina.") 
\
*Sivun sisällön esittäminen markdownina.*

Vastauksen lopussa on nappi, jonka avulla vastauksen saa kopioitua. Kun sen liittää vaikka Visual Studio Codeen, voi valmiin markdown-tiedoston tallentaa. Tulos on [tässä](testitiedostot/seamk_tki.md).

##### Testi 3: Wordin käyttö

Kokeillaan viimeiseksi Windows-sovelluksen käyttämistä MCP-palvelimen työkalujen avulla sekä kirjoitustyökalua. Pyydetään Claudea avaamaan Word ja kirjoittamaan englanninkielinen tiivistelmä äsken haetusta tiedosta SEAMKin TKI-toiminnasta (kirjoitustyökalu ei näytä osaavan ääkköisiä, joten siksi käytetään englantia.)

Kuten kokkiohjelmissa, tässä pitää tehdä hieman esivalmisteluita. Claude osaa kyllä avata Wordin, mutta se ei osaa luoda siellä uutta tiedostoa. Yleensä se yrittää käyttää pikanäppäintä Ctrl + N, mutta tämä ei toimi Wordin alkunäytössä. Testeissä se kerran yritti avata uutta tiedostoa hiiren avulla, mutta tällöinkin se klikkasi Aloitus-painiketta. Tyhjä asiakirja Wordissa pitää siis avata valmiiksi. Toinen esityö on pienentää Claude-ikkunaa alle puoleen näytön leveydestä. Kun Claude yrittää aktivoida Word-ikkunan, se vie aina hiiren kursorin näytön keskelle ja klikkaa kerran. Jos keskialueella ei ole Word-ikkunaa, se epäonnistuu ja alkaa esim. kirjoittaa Clauden viestikenttään. Alla olevassa kuvassa näkyy aloitustilanne, jossa kirjoittaminen onnistuu. Se vaatii useamman askeleen, jossa aluksi käytetään tila- ja hiirityökaluja ja lopuksi vaiheittain kirjoitustyökalua.

![alt text](/kuvituskuvat/53_word.png "Kehote ja valmistelut tiivistelmän kirjoittamiseen Wordissä.") 
\
*Kehote ja valmistelut tiivistelmän kirjoittamiseen Wordissä.*

Kun Claude on saanut tekstin valmiiksi, se vielä ilmoittaa tästä ja kertoo tekstin rakenteen. Valmis Word-tiedosto on [täällä](testitiedostot/Seamk_RDI.docx).

![alt text](/kuvituskuvat/54_word_valmis.png "Ilmoitus valmiista referaatista.") 
\
*Ilmoitus valmiista referaatista.*

#### Esimerkki 3: Kolmannen osapuolen MCP

Claudeen voi myös asentaa kolmannen osapuolen paikallisesti toimivia MCP-palvelimia. Tai tarkelleen ottaen ne asennetaan paikallisesti ja otetaan käyttöön Claudessa. Kokeillaan yhtä tällaista, Dot Justin Image -MCP-palvelinta, jonka asennusohjeet Claudea varten löytyvät [täältä](https://lobehub.com/mcp/dot-justin-poke-image-mcp?activeTab=deployment) klikkaamalla vielä Claude Desktop -välilehteä. **Palvelin ei itse asiassa osoittautunut kovin hyväksi, joten sitä ei kannata välttämättä asentaa itse.** Muutkin kolmannen osapuolen palvelimet otetaan kuitenkin käyttöön samalla kaavalla. 

Ensin pitää siis asentaa MCP-palvelin Powershell-käskyillä (Installation Guide -osio). Tämä on asennusohjeissa kummallisesti Claudella käyttöönoton (Install on Claude -osio) jälkeen, mutta tehdään se ensin.  Esivaatimuksena [Node.js](https://nodejs.org/en) pitää olla asennettuna. Myös git pitää olla asennettuna. Sivulta löytyvät Powershell-komennot siis pitää suorittaa. Palvelinta ei kuitenkaan tarvitse käynnistää eli jätetään komento ```npm start``` pois.

```
git clone https://github.com/dot-Justin/poke-image-mcp.git

cd poke-image-mcp

npm install

npm run build
```

Seuraavaksi tehdään asennusohjeiden Install on Claude -osion toimenpiteet. Klikataan ensin omaa profiilikuvaa vasemmassa alakulmassa &rarr; Settings &rarr; Developer-välilehti ja sieltä nappi Edit Config. Nyt aukeaa hakemisto, josta löytyy tiedosto ```claude_desktop_config.json```. Avaa tiedosto ja liitä siihen asennusohjesivulta kopioitava konfiguraatio eli

```
{
  "mcpServers": {
    "dot-justin-poke-image-mcp": {
      "args": [
        "path/to/image-mcp-test/dist/index.js"
      ],
      "command": "node"
    }
  }
}
```
Rimpsun ```path/to/image-mcp-test/dist/index.js``` tilalle täytyy laittaa oma asennushakemistonsa samalla lailla kautta viivoilla kenoviivojen sijaan. Tämän jälkeen Claude Desktop täytyy käynnistää uudelleen. Tätä materiaalia tehdessä Claude ei kylläkään löytänyt asennettua MCP-palvelinta ennen kuin koko koneen käynnisti uudelleen.

Kun Dot Justin Image -MCP-palvelin on toiminnassa, se näkyy Connectors-valikossa muiden MCP-palvelinten kanssa.

![alt text](/kuvituskuvat/40_konnektorit_kaytossa.png "Uusi MCP-palvelin näkyy listassa.") 
\
*Uusi MCP-palvelin näkyy listassa.*

##### Testi 1: Kuvien pienentäminen

Kokeillaan uutta MCP-palvelinta ensin kuvien pienennykseen. On yleinen ongelma, että sivustolle tai blogiin pitää lisätä kuvia, ja ne ovat turhan kookkaita ja vievät siksi liikaa tilaa. Esimerkiksi kymmenen kuvan manuaalinen pienentäminen on hidasta. Tehdään tällainen askare siis MCP-palvelimen avulla. Alla näkyy kuvat, jotka halutaan pienentää, ja yhden niistä koko.

![alt text](/kuvituskuvat/41_isot_kuvat.png "Pienennettävät kuvat.") 
\
*Pienennettävät kuvat.*

![alt text](/kuvituskuvat/42_kuvan_koko.png "Kuvan koko.") 
\
*Alkuperäisen kuvan koko.*

Pyydetään Claudea pienentämään tämän hakemiston kuvat. Katsotaan, mitä työkaluja se siihen käyttää. Ensin se käyttää Filesystem-MCP-palvelinta tiedostolistaukseen.

![alt text](/kuvituskuvat/43_kuvien_pienennys_poke_kehote.png "Kehote pienentää kuvat ja vastaus.") 
\
*Kehote pienentää kuvat ja vastaus.*

Seuraavaksi Claude haluaa käyttää Dot Justin Image MCP:n työkaluja kuvien pienennykseen.

![alt text](/kuvituskuvat/44_kuvien_pienennyspyynto.png "Pyyntö käyttää Poke Image MCP:n työkalua.") 
\
*Pyyntö käyttää Dot Justin Image MCP:n työkalua.*

Claude kuitenkin huomaa, ettei Dot Justin Image MCP tue täysiä polkuja, vaan kuvien täytyy olla sen asennushakemistossa Images-nimisessä kansiossa (itse asiassa tämä mainittiin selvästi [sen sivuilla] (https://lobehub.com/mcp/dot-justin-poke-image-mcp)) ja käyttää kuvien pienennykseen Windows-MCP:n PowerShell-työkalua. Itse asiassa kaikki Image MCP:n toiminnot vaikuttavat olevan mahdollisia myös PowerShell-työkalulla, joten Windows-MCP osoittautuu hyvin monipuoliseksi.

![alt text](/kuvituskuvat/44_valmiit_kuvat.png "Kuvien pienennys PowerShell-työkalulla ja listaus valmiista kuvista.") 
\
*Kuvien pienennys PowerShell-työkalulla ja listaus valmiista kuvista.*

Tarkistetaan vielä kansiosta, että kuvien koko tosiaan on muuttunut.

![alt text](/kuvituskuvat/45_valmiin_kuvan_koko.png "Pienennetyn kuvan koko.") 
\
*Pienennetyn kuvan koko.*

##### Testi 2: kuvatiedostojen muunto

Yritetään tehdä jotain muuta. Koska käytössä on Windows-MCP-palavelin työkaluineen, voidaan kysyä Claudelta, mihin kuvat taas pitikään tallettaa, jotta Dot Justin Image MCP pystyy niitä käsittelemään. Windows-MCP:n avulla Claude pystyy etsimään tiedostoja ja hakemistoja.

![alt text](/kuvituskuvat/46_poken_kuvakansio.png "Images-kansion etsintä Clauden avulla.") 
\
*Images-kansion etsintä Clauden avulla.*

Nyt, kun kansio on löytynyt, siirretään muokattavat kuvat sinne. Kokeillaan muuttaa niiden tiedostomuotoa jpegistä png:hen.

![alt text](/kuvituskuvat/47_eri_muotoon.png "Kehote tiedostomuodon muuntamiseen.") 
\
*Kehote tiedostomuodon muuntamiseen.*

![alt text](/kuvituskuvat/48_eri_muotoon_valmis.png "Toiminta valmis.") 
\
*Ilmoitus valmiista muuntamisesta ja listaus muunnetuista kuvatiedostoista.*

Tarkastaessa kuvakansio käy kuitenkin ilmi, että tiedostot ovat edelleen jpg-muodossa. Image MCP:n työkalut eivät vaikuta toimiva oikein. Tämänkin voi sitä paitsi tehdä Windows-MCP:n PowerShell-työkalulla.

Dot Justin Image MCP on siis aika turha MCP-palvelin. Esimerkki kuitenkin osoitti, kuinka kolmannen osapuolen MCP-palvelin otetaan Claudella käyttöön.

### Artifaktit

MCP-palvelimet antavat Claudelle ulkopuolisia työkaluja käyttöön, mutta Claudella voi luoda myös sisäisiä työkaluja eli artifakteja. Claude ohjelmoi ne itse annettujen ohjeiden perusteella. Aiemmin käsitellyn kuvien pienennyksen voi toteuttaa myös raahaa ja pudota -käyttöliittymällä varustetulla artifaktilla. Kun Claudea pyydetään ohjelmoimaan artifakti kuvien pienennykseen (kehotteessa tuli mainittua, että kuvia on kaksi), se tekee seuraavanlaisen käyttöliittymän.

![alt text](/kuvituskuvat/27_kuvienpienennystyokalu.png "Artifakti kuvien pienennykseen.") 
\
*Artifakti kuvien pienennykseen.*

Vastaavalla tavalla Claudea voi pyytää tekemään markdown-muuntimen.

![alt text](/kuvituskuvat/29_markdown_muunnin.png "Dokumenttien markdown-muunnin") 
\
*Dokumenttien markdown-muunnin.*

Klikkaamalla artifaktin yläpuolelta vasemmalta puolen symbolia ```</>```, voi tarkastella artifaktin koodia. Koodin syntyistä voi myös tarkkailla Clauden luodessa artifaktia. Claude ohjelmoi artifaktit yleensä JSX:llä, joka on JavaScriptin laajennus Reactia varten. JSX yhdistää JavaScript-logiikan ja HTML-tyyppisen merkintäkielen. Claude käyttää Reactia interaktiivisiin sovelluksiin, koska se hoitaa käyttöliittymän päivitykset automaattisesti tilan muuttuessa.

![alt text](/kuvituskuvat/30_markdown_muunnin_koodi.png "Markdown-muuntimen koodi.") 
\
*Markdown-muuntimen koodi.*

Jos onnistuu luomaan toimivan ja mielestään hyödyllisen artifaktin, sen voi julkaista kaikille käyttäjille oikean yläkulman Publish-napilla. Julkaistuja artifakteja voi selailla vasemman laidan Artifaktit-napista Inspiration-välilehdeltä, joka aukeaa oletuksena. Omat luodut artifaktit löytyvät Your artifacts -välilehdeltä.

![alt text](/kuvituskuvat/39_artifaktit.png "Artifaktikirjasto.") 
\
*Artifaktikirjasto.*

Testaillaan nyt luotua markdown-muunninta ja syötetään sille docx-tiedosto. Tulee virheilmoitus. Kopioidaan virheilmoitus Claudelle.

![alt text](/kuvituskuvat/31_markdown_virheenkorjaus.png "Virheilmoistus ja virheenkorjaus.") 
\
*Virheilmoitus ja virheenkorjaus.*

Testaan muuntimen toimintaa uudelleen docx- ja pptx-tiedostoilla. Nyt muunto onnistuu.

![alt text](/kuvituskuvat/32_markdown_valmiit.png "Onnistunut muunto docx:stä ja pptx:stä markdowniksi.") 
\
*Onnistunut muunto docx:stä ja pptx:stä markdowniksi.*

Alla olevasta taulukosta voi vertailla alkuperäisiä dokumentteja ja niistä tuotettua markdownia. Nähdään, että itse teksti säilyi hyvin, mutta muotoilut eivät. Toimintaa voitaisiin mahdollisesti iteratiivisesti parantaa .

| Alkuperäinen dokumentti | Muunnettuna markdowniksi |
|-------------|-------------------------|
|[Turvallisemman tilan periaatteet.pptx](testitiedostot/Turvallisemman%20tilan%20periaatteet%202024.pptx)| [Turvallisemman tilan periaatteet.md](testitiedostot/Turvallisemman%20tilan%20periaatteet%202024.md)| 
|[Seamk_tyhja.docx](testitiedostot/Seamk_tyhja.docx)| [Seamk_tyhja.md](testitiedostot/Seamk_tyhja.md)|

Kokeillaan vielä pdf:ää. Käytetään samaa SEAMKin pysäköinti-infoa, mitä käytettiin Visual Studio Coden MarkItDown-MCP-palvelimen kanssa. [Tulos](testitiedostot/pysakointi-framin-alueella2.md) ei ole ihan kurantti. Raportoidaan siitä.

![alt text](/kuvituskuvat/33_markdown_pdf.png "Pdf-muunnoksen korjaaminen.") 
\
*Pdf-muunnoksen korjaaminen.*

Nyt muunnos onnistuu, vaikkakin [tuloksen](testitiedostot/pysakointi-framin-alueella3.md) muotoilu niin ikään on puutteellinen. Teksti on kuitenkin oikein.

Kokeillaan vielä pyytää Claudea parantamaan muunnosta.

![alt text](/kuvituskuvat/57_parannettu_markdown_muunnin.png "Markdown-muuntimen toiminnan korjaaminen.") 
\
*Markdown-muuntimen toiminnan korjaaminen.*

Katsotaan tuloksia. Ei vieläkään ihan nappiin, mutta parempaan päin.

| Alkuperäinen dokumentti | Muunnettuna markdowniksi |
|-------------|-------------------------|
|[Turvallisemman tilan periaatteet.pptx](testitiedostot/Turvallisemman%20tilan%20periaatteet%202024.pptx)| [Turvallisemman tilan periaatteet_2.md](testitiedostot/Turvallisemman%20tilan%20periaatteet%202024_2.md)| 
|[Seamk_tyhja.docx](testitiedostot/Seamk_tyhja.docx)| [Seamk_tyhja2.md](testitiedostot/Seamk_tyhja2.md)|
|[Pysäköinti-framin-alueella.pdf](https://storage.googleapis.com/seamk-production/2017/08/pysakointi-framin-alueella.pdf)|[pysakointi-framin-alueella4.md](testitiedostot/pysakointi-framin-alueella4.md) 

### Claude Desktop: havainnot

MCP-palvelinten käyttöönotto Claude Desktopissa on huomattavasti helpompaa kuin Visual Studio Coden Agent Builderissa. Kolmannen osapuolen MCP-palvelimia lukuunottamatta MCP-palvelinten asentaminen ei vaadi minkään muiden kirjastojen asentamista. MCP-palvelinten käyttäminen on lisäksi ilmaista, sillä ilmaisversion tokenit loppuivat kokeiluiden aikana vain kerran ja silloinkin käyttöä sai jatkaa parin tunnin tauon jälkeen. Lisäksi artifaktit ovat mielenkiintoinen lisä, vaikka niiden toiminta ei aina ihan täydellistä olekaan.

## Yhteenveto

Sekä Visual Studio Coden Agent Builderissa että Claude Desktopiin on rakennettu yksinkertainen käyttöliittymä MCP-palvelinten hyödyntämiseen. Claude Desktopilla MCP-palvelinten käyttäminen on kuitenkin paljon helpompaa, ja -Claude Desktop onkin suunnattu interaktiiviseksi tekoälysovellukseksi kenelle tahansa. Visual Studio Coden Agent Builder on taas kehitystyökalu, joka auttaa rakentamaan, testaamaan ja hallitsemaan tekoälyagentteja ohjelmoijille suunnatussa kehitysympäristössä. Se on suunnattu kehittäjille, jotka haluavat rakentaa ja hallita tekoälyagentteja ohjelmointi- ja automatisointitehtäviin.