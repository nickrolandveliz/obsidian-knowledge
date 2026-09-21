
### **PART 1: Recerca, Selecció i Justificació**

**Aplicació web seleccionada: Tradeinn**

He triat Tradeinn perquè compleix els tres requisits demanats. Disposa d'un sistema de registre i inici de sessió per als usuaris. També permet manipular dades, per exemple creant un compte i gestionant productes durant el procés de compra. Finalment, mostra un ampli catàleg de productes organitzats per categories, marques i altres filtres, informació que és gestionada mitjançant una base de dades.

https://www.tradeinn.com/en



### **PART 2: Anàlisi Tècnica**

## 1. Anàlisi General

### Per què és una aplicació web?
Tradeinn és una **aplicació web** perquè podem accedir-hi directament des d'un navegador sense necessitat d'instal·lar cap programa a l'ordinador. L'usuari pot interactuar amb la plataforma, buscar productes, iniciar sessió, afegir productes al carret i realitzar compres. Aquestes accions impliquen una comunicació entre el navegador de l'usuari i els servidors de Tradeinn.

### Avantatges i desavantatge

**Avantatge 1 – No necessita instal·lació:** podem accedir a Tradeinn des d'un navegador sense instal·lar cap aplicació específica.

**Avantatge 2 – Accessible des de diferents dispositius:** podem entrar al nostre compte i consultar els productes des d'ordinadors, mòbils o tauletes amb connexió a Internet.

**Desavantatge – Dependència d'Internet:** la major part de les funcions de Tradeinn necessiten connexió a Internet. Sense connexió no podríem buscar productes, consultar informació actualitzada o completar una compra.


# 2. Arquitectura Client-Servidor

## Front-End

El **Front-End** és la part de l'aplicació que l'usuari veu i amb la qual interactua des del navegador. A Tradeinn podem identificar, per exemple:

1. **El cercador de productes**, on l'usuari pot escriure el producte que vol trobar.
2. **El catàleg i les fitxes dels productes**, on apareixen imatges, noms, preus i altra informació.
3. **Els botons i menús**, com ara iniciar sessió, seleccionar categories o afegir un producte al carret.

Aquests elements formen part de la interfície que es mostra i s'executa al navegador de l'usuari.

## Back-End

El **Back-End** és la part que funciona al servidor i que l'usuari no veu directament. Encara que no podem veure el seu funcionament intern, podem deduir algunes de les funcions que necessita Tradeinn:

1. **Validació de l'inici de sessió:** quan un usuari inicia sessió, el servidor ha de comprovar les seves credencials i gestionar l'accés al compte.
2. **Consulta dels productes:** quan fem una cerca, el servidor ha de consultar les dades disponibles i retornar els productes corresponents.
3. **Gestió del carret i de les comandes:** quan afegim un producte al carret o realitzem una compra, el servidor ha de processar i guardar aquesta informació.

## Tecnologies del client: HTML, CSS i JavaScript

Tradeinn utilitza tecnologies pròpies del desenvolupament web al costat del client. Amb les **eines de desenvolupador del navegador** podem inspeccionar els recursos que carrega la pàgina i observar fitxers i contingut relacionats amb **HTML, CSS i JavaScript**.

![[Pasted image 20260921185744.png]]


# 3. Anàlisi per Capes i MVC

## Diagrama de les tres capes

Per Tradeinn podem representar l'arquitectura de tres capes d'aquesta manera:

![[Pasted image 20260921190505.png]]

**Capa de Presentació:** és la interfície que veu l'usuari al navegador. Inclou el cercador, el catàleg de productes, les imatges, els menús, els botons, el carret de compra i l'inici de sessió. És la capa amb la qual l'usuari interactua directament.

**Capa de Lògica:** s'encarrega de processar les accions que realitza l'usuari. Per exemple, gestionar una cerca, comprovar un inici de sessió, afegir productes al carret o processar una comanda. Aquesta capa connecta la interfície amb les dades necessàries.

**Capa de Dades:** és l'encarregada d'emmagatzemar i proporcionar la informació necessària per al funcionament de Tradeinn. Aquí trobaríem dades com els usuaris, els productes, els preus, l'estoc i les comandes realitzades.


## Hipòtesi del Model MVC

Per explicar com podria funcionar el patró **Model-Vista-Controlador (MVC)** a Tradeinn, utilitzarem com a exemple l’acció de **buscar un producte**. Com que no tenim accés al codi intern de Tradeinn, plantegem una hipòtesi de com es gestionaria aquesta acció seguint el patró MVC.

**Controlador:** quan l’usuari escriu, per exemple, “sabatilles” al cercador i prem el botó de cerca, el controlador rep la petició. Interpreta l’acció de l’usuari i demana al model que busqui els productes corresponents.

**Model:** s’encarrega de gestionar les dades. En aquest cas, faria una consulta a la base de dades per trobar els productes relacionats amb “sabatilles” i obtindria informació com el nom, el preu, la marca i la disponibilitat.

**Vista:** rep els resultats i els mostra a l’usuari a través del navegador. En aquest cas, presentaria un catàleg amb els diferents productes trobats, les seves imatges, preus i altra informació.

El procés es podria resumir així:

**Usuari → Controlador → Model → Base de dades → Model → Controlador → Vista → Usuari**