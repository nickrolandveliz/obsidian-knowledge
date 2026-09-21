![[Pasted image 20260921170133.png]]

- **Microsoft Office (Word, Excel)** vs. **Google Docs / Google Sheets**


#### **Part 1: Anàlisi Comparativa (Basada en la presentació)**

| Criteri d'Avaluació                  | Microsoft Office                                                                                                                                              | Google Docs                                                                                                                                                                                                                         |
| ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Instal·lació i Actualitzacions**   | S'han d'instal·lar a l'ordinador. Les actualitzacions es descarreguen i s'instal·len al dispositiu, normalment de manera automàtica.                          | No necessiten instal·lació per utilitzar-los des del navegador. Les actualitzacions es fan al servidor i l'usuari disposa de la nova versió automàticament.                                                                         |
| **Accessibilitat i Multiplataforma** | Depenen del sistema operatiu i del dispositiu on estiguin instal·lats. Per treballar en un altre ordinador cal tenir-hi el programa disponible.               | Es poden utilitzar des de diferents sistemes operatius i dispositius simplement amb un navegador compatible i iniciant sessió.                                                                                                      |
| **Dependència de la Connexió**       | Poden funcionar sense connexió a Internet perquè els programes i els documents poden estar emmagatzemats localment.                                           | Depenen més d'Internet. Algunes funcions poden estar disponibles sense connexió si s'han configurat prèviament, però la connexió és necessària per aprofitar totes les funcions, especialment la sincronització i la col·laboració. |
| **Rendiment i Ús de Hardware**       | Poden aprofitar millor els recursos de l'ordinador i solen oferir més funcionalitats per a documents o fulls de càlcul complexos.                             | Funcionen dins del navegador i poden tenir més limitacions en tasques molt complexes o que necessiten molts recursos. L'accés directe al hardware també és més limitat.                                                             |
| **Treball Col·laboratiu**            | Permeten compartir documents i també disposen de funcions de col·laboració, però tradicionalment estan més orientats al treball amb aplicacions instal·lades. | Estan especialment pensats per al núvol. Diversos usuaris poden modificar un mateix document simultàniament, veure els canvis en temps real i afegir comentaris.                                                                    |


#### **Part 2: Cas Pràctic de Raonament**

Per a aquesta empresa d'arquitectura, **recomanaria principalment una solució d'ofimàtica web**, ja que les seves característiques encaixen millor amb les necessitats plantejades.

**Ofimàtica:** els treballadors necessiten crear documents, pressupostos i presentacions. Una suite ofimàtica web permet realitzar aquestes tasques directament des del navegador sense haver d'instal·lar els programes en cada ordinador.

**Mobilitat:** diversos arquitectes viatgen constantment i necessiten accedir als documents des de portàtils, tauletes o ordinadors d'altres llocs. Amb una aplicació web poden accedir als seus documents des de diferents dispositius sempre que disposin d'un navegador i connexió a Internet. Això evita dependre d'un únic ordinador.

**Treball col·laboratiu:** aquest és un dels principals avantatges de les aplicacions web per a aquesta empresa. Diverses persones poden treballar simultàniament sobre un mateix document, veure els canvis en temps real i evitar tenir diverses còpies diferents del mateix fitxer.

**Pressupost:** les aplicacions web redueixen les necessitats d'instal·lació i manteniment dels programes en els diferents equips. A més, existeixen solucions web amb opcions gratuïtes o plans que poden reduir els costos respecte a determinades llicències tradicionals.

Tot i aquests avantatges, també s'ha de tenir en compte una limitació important: **la dependència d'Internet**. Si un arquitecte es troba en una obra sense connexió o amb una connexió inestable, podria tenir dificultats per accedir o sincronitzar els documents. Per aquest motiu, seria convenient disposar de funcionalitats de treball sense connexió quan sigui possible.

En conclusió, en aquest cas l'ofimàtica web s'adapta especialment bé a una empresa amb treballadors que es desplacen, necessiten compartir informació constantment i disposen d'un pressupost limitat.



#### **Part 3: Recerca i Aprofundiment**

1. Què és una PWA?
Una **Progressive Web App (PWA)** és una aplicació web que utilitza tecnologies modernes per oferir una experiència semblant a la d'una aplicació tradicional instal·lada. S'hi pot accedir des d'un navegador, però en molts casos també es pot instal·lar al dispositiu i tenir una icona pròpia a l'escriptori o a la pantalla d'inici.

Les PWA combinen, per tant, els avantatges de les pàgines web, com l'accés des de diferents dispositius, amb algunes característiques de les aplicacions natives, com el funcionament sense connexió o les notificacions.


2. Com superen les limitacions?
**Dependència de la connexió a Internet:**  
Un dels principals inconvenients de les aplicacions web tradicionals és que depenen d'una connexió a Internet. Les PWA intenten solucionar aquest problema mitjançant els **Service Workers**, que permeten guardar determinats recursos i informació a la memòria cau del dispositiu.

Gràcies a això, l'usuari pot continuar accedint a algunes parts de l'aplicació encara que perdi temporalment la connexió. Tot i així, les funcions que necessiten obtenir informació nova d'un servidor continuaran requerint Internet.

**Aprofitament del hardware:**  
Les aplicacions web tradicionals tenen un accés més limitat a les funcions del dispositiu. Les PWA poden utilitzar diferents **APIs web** per interactuar amb algunes d'aquestes funcions, com les **notificacions push, la càmera o la ubicació**.

Això permet oferir una experiència més semblant a la d'una aplicació instal·lada. Tot i això, l'accés a aquestes funcions depèn del navegador i del sistema operatiu, de manera que encara poden existir limitacions respecte a les aplicacions natives.



3. Exemples de PWA

**Starbucks:** és un exemple conegut d'implementació d'una PWA. La seva aplicació web va ser dissenyada per permetre consultar el menú i preparar comandes fins i tot quan la connexió era limitada. Això permetia oferir una experiència ràpida i adaptada als dispositius mòbils.

**Pinterest:** també ha utilitzat tecnologies PWA per millorar la seva experiència web, especialment en dispositius mòbils. L'objectiu era aconseguir una navegació més ràpida i una experiència més semblant a la d'una aplicació convencional, sense necessitat de dependre exclusivament d'una aplicació nativa.