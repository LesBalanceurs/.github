# Norme de code

## Structure de fichiers
```
|--lib
|  |
|  |-- library1
|  |-- library2
|  |-- library...
|  |
|
|--src
   |- main.cpp
   |- example.h
   |- example.cpp
   |- ...
```
### Fichier header & source
Tout code C ou C++ doit être composé de deux fichiers un fichier header (.h) et un fichier source (.cpp).
#### Fichier header (.h)
Un fichier header ne devrait jamais contenir aucune définition, il devrait contenir la structure général du code ; namespace, function, variable externe, #define.

``` C++
#ifndef EXAMPLE_H
#define EXAMPLE_H

namespace ExampleNamespace
{
	extern int publicVariable;
    	void publicFunction();

// Declare the private variable in the anonymous namespace in the header
	namespace
	{
		extern int privateVariable;
		void privateFunction(); // Declare the private function in the header
	}
}

#endif // EXAMPLE_H
```

#### Fichier source (.cpp)
Un fichier source doit contenir le code, on y définit le code des fonctions et on y initialize les variables.

``` C++
#include "example.h"

namespace ExampleNamespace
{
	int publicVariable = 15;
    	void publicFunction()
    	{
	 // Function implementation
    	}

    	// Implement the private variable and function in the anonymous namespace
	namespace
    	{
        	int privateVariable = 42;

		void privateFunction()
        	{
		 // Function implementation
        	}
    }
}
```

## Notation
- Le code est écrit en anglais.
- Pour le code nous utiliserons la notation *Camel case*.

![Camel case](../ressources/image/CamelCase_new.svg.png)

## Règle
### Fichier main.cpp
- Les seules fonction permisse dans le main.cpp (fichier principale) sont la fonction setup et loop, si un nouvelle fonction est nécessaire, la faire dans une nouvelle *library* ou la *library* approprié.
### Fonction proscrite
- L'appel de la fonction delay() est proscrite sauf si absolument nécessaire.
### Syntaxe d'une fonction
- Une fonction devrait toujours être composé d'un verbe suivit d'un sujet.

``` C++
void verbeSujet();
```

- Une fonction ne devrait pas executer plus d'une tâche, si la tâche comporte des sous-tâche, la fonction doit appelé des fonctions qui s'occupe de ses sous-tâches.

``` C++
void tâche() {
	sous-tâche1();
	sous-tâche2();
	...
}
```

- Il faut priorisé le passage de paramètres plutôt que le hardcodadge de valeurs.

``` C++

void main()
{
	goodFunction(5);
	badFunction();
}

int goodFunction(int a)
{
	// Do something
	return a;
}

int badFunction()
{
	return 5;
}
```

## Commentaire
- Les commentaire doivent être écrit au fur à mesure dans les [fichier header & source](README.md#fichier-header--source) selon la syntaxe suivante
- Un commentaire suis les règles du franglais (Majuscule au début et point à la fin).

### prototype.cpp
``` C++
/**************************************************************************************************
Nom du fichier : prototype.cpp
Auteur : 
Date de création : 

Description : 
              
Notes : 

Modifications : -Ceci est un exemple de modifications - Samuel Hamelin - 2023-10-16
***************************************************************************************************/

// *************************************************************************************************
//  INCLUDES
// *************************************************************************************************	
#include "prototype.h"

/**
 * @brief Description du namespace
 * @author
*/
namespace Prototype {
	
	// *************************************************************************************************
	//  CONSTANTES
	// *************************************************************************************************
	/* VIDE */
	
	// *************************************************************************************************
	//  STRUCTURES ET UNIONS
	// *************************************************************************************************
	/* VIDE */
	
	// *************************************************************************************************
	// VARIABLES GLOBALES
	// *************************************************************************************************
	/* VIDE */

	// *************************************************************************************************
	// FONCTIONS GLOBALES
	// *************************************************************************************************
	/* VIDE */
				
	/**
	 * @brief Ceci est la description de la fonction
	 * @author 
	*/
	void main (void)
	{
		  /********  Variables locales **********/
		  /* VIDE */
		      
		  /****************************************/  
		  /**********  Initialisations ************/
		  /* VIDE /
		  
		  /****************************************/ 
	}
	
	/**
	 * @brief Ceci est la description de la fonction
	 * @author 
	 *
	 * @param ceciEstLeNomDeLaVariableEnParametre 
	 *
	 * @return int 
	*/
	int prototypeFonction(int ceciEstLeNomDeLaVariableEnParametre)
	{
	  	int ceciEstLeNomDeLaVariableARetourner = 0;
	
		return ceciEstLeNomDeLaVariableARetourner;
	}

	namespace {
		// *************************************************************************************************
		// VARIABLES LOCALES
		// *************************************************************************************************
		/* VIDE */

		// *************************************************************************************************
		//  FONCTIONS LOCALES
		// *************************************************************************************************
		/* VIDE */
	}
}
```

### prototype.h
``` C++
/****************************************************************************************
Nom du fichier : prototype.h
Auteur :                   
Date de création : 
  
****************************************************************************************/
#ifndef PROTOTYPE_H
#define PROTOTYPE_H

namespace Prototype
{
	
	// *************************************************************************************************
	//  CONSTANTES
	// *************************************************************************************************
	/* VIDE */		  
		  
	// *************************************************************************************************
	//  STRUCTURES ET UNIONS
	// *************************************************************************************************
	/* VIDE */
		  
	// *************************************************************************************************
	// VARIABLES GLOBALES
	// *************************************************************************************************
	/* VIDE */

	// *************************************************************************************************
	//  PROTOTYPE DE FONCTIONS
	// *************************************************************************************************

	void main(void);
	int prototypeFonction(int ceciEstLeNomDeLaVariableEnParametre);

	namespace {
		// *************************************************************************************************
		// VARIABLES LOCALES
		// *************************************************************************************************
		/* VIDE */
	}
}

#endif // PROTOTYPE_H
```
