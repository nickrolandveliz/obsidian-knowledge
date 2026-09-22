### 1. Interpolació de Cometes

PHP

<?php

$nom = "Jordi";

echo 'Benvingut, $nom!\n';

echo "Benvingut, $nom!\n";

?>

Preguntes:

### 1. Què imprimirà la primera línia?

La primera línia imprimirà:

**Benvingut, $nom!\n**

La variable `$nom` no se substitueix pel seu valor i `\n` tampoc es converteix en un salt de línia.


### 2. Què imprimirà la segona línia?

La segona línia imprimirà:

**Benvingut, Jordi!**

i després farà un salt de línia.

### 3. Explica breument per què són diferents?

Les cometes simples (`' '`) no permeten interpolar variables ni interpreten `\n` com un salt de línia. En canvi, les cometes dobles (`" "`) sí que interpreten les variables i les seqüències especials.

Per tant, la sortida conjunta serà:

**Benvingut, $nom!\nBenvingut, Jordi!**

En aquest exercici no es produeix cap Warning ni cap error i l'execució finalitza normalment.


## 2. Mal·leabilitat de Tipus (Type Juggling)

### 1. Què imprimirà la Línia 1?

**echo "10" + 5;**

Imprimirà:

**15**

PHP converteix automàticament la cadena numèrica `"10"` en el número `10` i realitza la suma.

### 2. Què imprimirà la Línia 2?

**echo "10" . 5;**

Imprimirà:

**105**

L'operador `.` serveix per concatenar. Per tant, uneix `"10"` i `5` com a text.

### 3. Què imprimirà la Línia 3 i per què?

**echo "10 gossos" + 5;


En PHP 8.x imprimirà:

**15

però també generarà un Warning semblant a:

**Warning: A non-numeric value encountered**

Això passa perquè la cadena comença pel valor numèric `10`, que PHP utilitza per fer l'operació, però la resta de la cadena (`gossos`) no és numèrica. El Warning no atura l'execució.

Aquest comportament pot presentar diferències segons la versió de PHP utilitzada.

### 4. Què imprimirà la Línia 4?

**echo 10 + 5 . " gossos";

Imprimirà:

**15 gossos

Primer es realitza `10 + 5`, que dona `15`, i després aquest resultat es concatena amb `" gossos"`.

---

## 3. Àmbit de Variables (Scope)

### 1. Quina és la sortida exacta d'aquest script? (Pensa en els "Notices" o "Warnings").

La variable `$nom_global` no està definida dins de la funció. En PHP 8.x apareixerà un Warning semblant a:

**Warning: Undefined variable $nom_global

La instrucció `echo` imprimirà:

**Hola,** 

El Warning no és fatal i, per tant, l'execució pot continuar.

### 2. Per què la funció no pot "veure" la variable $nom_global?

Perquè `$nom_global` està declarada fora de la funció i té àmbit global. Les variables globals no estan disponibles automàticament dins de l'àmbit local d'una funció.

### 3. Escriu dues maneres diferents d'arreglar-ho.

Una primera manera és utilitzar `global`:


**function saludar() {
    global $nom_global;
    echo "Hola, " . $nom_global;
}

Una segona manera és passar la variable com a paràmetre:

**function saludar($nom) {
    echo "Hola, " . $nom;
}

saludar($nom_global);


La segona opció permet que la funció rebi explícitament la informació que necessita.

---

## 4. Bucles foreach (Clau i Valor)

### 1. Què conté la variable $fruita a la primera iteració del bucle?

Conté:

**pomes

`$fruita` representa la clau de l'array.

### 2. Què conté la variable $quantitat a la primera iteració del bucle?

Conté:

**5

`$quantitat` representa el valor associat a la clau `"pomes"`.

### 3. Escriu la sortida completa i exacta que produirà aquest script.


**Queden 5 de pomes.
Queden 10 de peres.
Queden 0 de taronges.
CAL REPOSAR: taronges!


El `foreach` recorre totes les parelles clau-valor. Quan `$quantitat` val `0`, es compleix la condició de l'`if` i s'imprimeix el missatge de reposició.

No es produeix cap Warning ni cap error.

---

## 5. Superglobals ($_GET i $_POST)

### 1. Què imprimirà la línia "ID URL:"?

Imprimirà:

**ID URL: 123

El valor `123` està inclòs a la URL (`processar.php?id=123`) i es recupera amb `$_GET['id']`.

### 2. Què imprimirà la línia "Nom Formulari:"?

Imprimirà:

**Nom Formulari: Carles

El formulari s'ha enviat amb el mètode POST i el camp `usuari` conté el valor `"Carles"`. Per això es pot recuperar amb `$_POST['usuari']`.

### 3. Què passarà a la línia "ID Formulari:"? Per què?

El formulari no conté cap camp POST anomenat `id`. Per tant:

**$_POST['id']

no existeix i en PHP 8.x es generarà un Warning semblant a:


**Warning: Undefined array key "id"

Després s'imprimirà:

**ID Formulari:

sense cap valor.

Això passa perquè l'`id=123` s'ha enviat mitjançant la URL i, per tant, està a `$_GET`, no a `$_POST`. El Warning no atura l'execució.

---

## 6. include vs. require

### 1. Quina serà la sortida completa del Codi A? (Què es veurà a la pantalla?)

Primer s'imprimirà:

**Inici Codi A

Quan s'executi:

**include 'config.php';

PHP generarà avisos perquè `config.php` no existeix. De manera simplificada, la sortida serà:

**Inici Codi A
Warning: include(config.php): Failed to open stream...
Warning: include(): Failed opening 'config.php'...
Final Codi A

El text exacte dels Warnings pot variar segons la versió, configuració i ruta del sistema.

L'important és que `include` genera avisos, però **l'execució continua**, i per això s'arriba a imprimir `Final Codi A`.

### 2. Quina serà la sortida completa del Codi B?

Primer s'imprimirà:

**Inici Codi B

Quan s'executi:

**require 'config.php';

PHP no podrà trobar el fitxer i generarà un Warning i un error fatal. De manera simplificada:


**Inici Codi B
Warning: require(config.php): Failed to open stream...
Fatal error: Uncaught Error: Failed opening required 'config.php'...


L'execució s'atura, per tant:

**Final Codi B

no s'imprimirà.

### 3. Quina és la diferència fonamental entre include i require quan un fitxer falla?

Quan falla `include`, PHP genera un Warning però permet que el programa continuï executant-se.

Quan falla `require`, es produeix un error que atura l'execució del programa.

---

## 7. Arrays: Còpia vs. Referència

### 1. Quina serà la sortida de print_r($array_a)?


**Array
(
    [0] => a
    [1] => Y
    [2] => c
)


### 2. Quina serà la sortida de print_r($array_b)?


**Array
(
    [0] => X
    [1] => b
    [2] => c
)


`$array_c` tindrà el mateix contingut que `$array_a`:

**
Array
(
    [0] => a
    [1] => Y
    [2] => c
)


### 3. Explica per què $array_a ha canviat en modificar $array_c, però no en modificar $array_b.

Quan fem:

**$array_b = $array_a;

l'assignació és per valor. Per això modificar `$array_b` no modifica `$array_a`.

En canvi:

**$array_c = &$array_a;

utilitza `&` per fer una assignació per referència. Això fa que `$array_c` faci referència a la mateixa variable que `$array_a`.

Per tant, quan fem:


**$array_c[1] = "Y";


també canvia `$array_a[1]`.

No es produeix cap Warning ni cap error.

---

## 8. El Parany del $this (OOP)

### 1. Quina és la sortida exacta d'aquest script?

Quan s'executa `getNom()`, PHP intenta retornar una variable local `$nom` que no existeix.

En PHP 8.x apareixerà un Warning semblant a:

**Warning: Undefined variable $nom


No s'imprimirà `"Elsa"`.

### 2. Per què no imprimeix "Elsa"?

El mètode `setNom()` modifica correctament la propietat de l'objecte:

**$this->nom = $nou_nom;


Però `getNom()` intenta retornar:

**$nom


que PHP interpreta com una variable local.

Per accedir a la propietat `nom` de l'objecte s'ha d'utilitzar `$this->nom`.

### 3. Com s'arregla la funció getNom()?

S'ha de modificar així:

**public function getNom() {
    return $this->nom;
}


Ara `$this->nom` fa referència a la propietat `nom` de l'objecte actual i el programa imprimirà:

**Elsa


---

## 9. Propietats static vs. Instància (OOP)

### 1. Què imprimirà "Total instàncies:"?

Imprimirà:

**Total instàncies: 3


S'han creat tres objectes i cada vegada que s'executa el constructor s'incrementa la propietat estàtica `$total_instancies`.

### 2. Què imprimirà "Comptador C1:"?

Imprimirà:

**Comptador C1: 1

Quan es crea `$c1`, el seu comptador propi passa de `0` a `1`.

### 3. Què imprimirà "Comptador C3:"?

Imprimirà:

**Comptador C3: 5

Inicialment el seu valor era `1`, però després s'executa:

**$c3->comptador_propi = 5;

i el seu valor passa a ser `5`.

### 4. Explica la diferència entre $total_instancies (static) i $comptador_propi (no static).

`$total_instancies` és una propietat `static`, per tant pertany a la classe i és compartida entre totes les instàncies. Per això els tres objectes incrementen el mateix comptador.

En canvi, `$comptador_propi` és una propietat d'instància. Cada objecte té el seu propi valor independent. Per això modificar `$c3->comptador_propi` no modifica el valor de `$c1`.

La sortida completa serà:

**Total instàncies: 3
Comptador C1: 1
Comptador C3: 5

---

## 10. Visibilitat (Public, Protected, Private) (OOP)

### 1. Línia D: Funcionarà? Què imprimirà?

Sí, funcionarà.

**echo $g->getNomPrivat();

imprimirà:

**ANIMAL

La propietat `$nom_privat` és `private`, però el mètode `getNomPrivat()` està declarat dins de la mateixa classe `Animal`. Per tant, aquest mètode sí que pot accedir a la propietat privada.

### 2. Línia E: Funcionarà? Per què sí o per què no?

No funcionarà.

**echo $g->edat_protegida;

intenta accedir a una propietat `protected` des de fora de la classe.

Una propietat `protected` només és accessible des de la mateixa classe o des de les classes que hereten d'ella.

En PHP 8.x es produirà un error fatal semblant a:

**Fatal error: Uncaught Error: Cannot access protected property Gos::$edat_protegida

L'execució s'atura en aquesta línia.

### **Línia F (testAccedir): Aquesta crida fallarà. Per què? Quina línia interna (A, B o C) causa l'error fatal?**

Aquí hi ha una **incoherència en l'enunciat**.

Executant exactament el codi proporcionat, la Línia F:

**$g->testAccedir();

**no arriba a executar-se**, perquè l'execució ja s'ha aturat abans a la Línia E en intentar accedir a `$edat_protegida` des de fora de la classe.

Si comentéssim la Línia E per poder executar `testAccedir()`, tindríem:

**echo $this->nom_privat;      // Línia A
echo $this->edat_protegida;  // Línia B
echo $this->color_public;    // Línia C

La **Línia A** intenta accedir des de `Gos` a `$nom_privat`, que és una propietat `private` declarada a `Animal`. Les propietats `private` només són accessibles directament des de la classe que les declara.

La **Línia B** sí que és accessible des de `Gos`, perquè `$edat_protegida` és `protected` i les classes filles poden accedir a propietats protegides.

La **Línia C** també és accessible perquè `$color_public` és `public`.

Per tant, cal destacar que **l'error fatal real del codi complet es produeix a la Línia E abans d'arribar a la Línia F**. Aquesta és una possible incoherència de l'enunciat i és important indicar-la, tal com demana la rúbrica.