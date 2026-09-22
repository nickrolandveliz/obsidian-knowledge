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