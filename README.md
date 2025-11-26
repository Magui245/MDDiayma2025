## 1. Récupération et exécution du projet

Le projet a été récupéré depuis le dépôt GitHub fourni par l'enseignant :
git clone https://github.com/devehod/BoutiqueDiayma2025.git
L'application s'exécute correctement via le navigateur.

## 2. Structure de la solution

Les projets de la solution ont été identifiés avec la commande PowerShell suivante :
Get-ChildItem -Recurse -Include *.sln, *.csproj

Projets trouvés :
- Diayma.csproj
- Diayma.sln


## 3. Version SDK .NET utilisée

La version du SDK utilisée se trouve dans le fichier `Diayma.csproj` :
xml
<PropertyGroup>
    <TargetFramework>netcoreapp2.0</TargetFramework>
</PropertyGroup>

**Version identifiée :** `netcoreapp2.0`

## 4. Installation du SDK

Le SDK .NET a été installé depuis le site officiel de Microsoft.  
Les commandes suivantes permettent  de vérifier les versions installées :
dotnet --version
dotnet --list-sdks

**Versions installées :**
- `2.0.0` [C:\Program Files\dotnet\sdk]
- `10.0.100` [C:\Program Files\dotnet\sdk]

## 5. Création du dépôt GitHub
Création d'un repos Git sous le nom de MDDiayma2025(MD= Magatte Diawara) pour héberger le projey

## 6. Bugs identifiés

## Premier bug : Stock non décrémenté
Description :
Après avoir ajouté un produit au panier, rempli le formulaire et terminé le passage de la commande, le message suivant s'affiche :
"Merci! Nous nous occupons de votre commande. La démo est terminée, cliquez sur le logo pour recommencer."

**Problème :** Quand on revient sur l'interface d'accueil, le stock ne se décrémente pas, la valeur reste toujours la même.

### Deuxième bug : Changement de langue

Description :
Le changement de langue en espagnol ne s'effectue pas.


## 7. Points d'arrêt et débogage

## Placement des points d'arrêt

Les points d'arrêt ont été placés en cliquant à gauche de chaque ligne suivante :

a) **CartSummaryViewComponent** - ligne 12  
b) **ProductController** - ligne 15  
c) **OrderController** - ligne 17  
d) **CartController** - ligne 15  
e) **Startup** - ligne 20

### Lancement du débogage

Le débogage a été lancé à l'aide de la touche **F5** dans Visual Studio Code.  
L'application a été ouverte dans le navigateur sur l'URL : `https://localhost:62929`

**Observation :** Le débogueur s'arrête automatiquement aux points d'arrêts.


## 8. Ordre d'exécution avant l'affichage des produits

Avant l'affichage des produits sur la page d'accueil, les éléments suivants sont exécutés :

### 1. CartSummaryViewComponent
- **Namespace :** `P2FixAnAppDotNetCode.Components`
- **Classe :** `CartSummaryViewComponent`
- **Méthode :** `Invoke()`

### 2. ProductController
- **Namespace :** `P2FixAnAppDotNetCode.Controllers`
- **Classe :** `ProductController`
- **Méthode :** `Index()`

### 3. OrderController
- **Namespace :** `P2FixAnAppDotNetCode.Controllers`
- **Classe :** `OrderController`
- **Méthode :** [à préciser]

### 4. CartController
- **Namespace :** `P2FixAnAppDotNetCode.Controllers`
- **Classe :** `CartController`
- **Méthode :** [à préciser]

### 5. Startup
- **Namespace :** `P2FixAnAppDotNetCode`
- **Classe :** `Startup`
- **Méthode :** `Startup()`

---

## 9. Modes de débogage utilisés

- **Pas à pas principal (F10)** : Exécuter la ligne actuelle sans entrer dans les fonctions
- **Pas à pas détaillé (F11)** : Entrée dans les méthodes
- **Pas à pas sortant (Shift + F11)** : Retour à la méthode appelante

---

## 10. Points de vérification du débogage

1. **Startup.cs, ligne 20** : Vérifier que la configuration est chargée
2. **ProductController.cs, ligne 15** : Vérifier l'injection des services
3. **CartSummaryViewComponent.cs, ligne 12** : Vérifier l'injection du panier
4. **ProductRepository.cs, ligne 43** : Vérifier le filtrage des produits (Stock > 0)
5. **ProductService.cs, ligne 29** : Vérifier la conversion en `List<Product>`

## Déploiement de notre application .NET en exécutable Windows
j'ai utilisé cette commande **dotnet publish -c Release -r win-x64 --self-contained true** 
pour créer un exécutable Windows autonome donc après la publication le fichier se trouvera dans **bin\Release\netcoreapp2.0\win-x64\publish**

## Création d'une archive ZIP
Dans le dossier publish on :
Sélectionne tous les fichiers
fait un clic droit -> Envoyer vers -> Dossier compressé (zip)
Nomme l'archive en : BoutiqueDiayma2025.zip

## Téléchargement sur Google Drive
Via l'interface web de google drive on :
Clique sur + Nouveau -> Importer un fichier
Sélectionne notre fichier BoutiqueDiayma2025.zip
Une fois téléchargé, on fait un clic droit sur le fichier ensuite Partager
Changee les permissions en : Toute personne disposant du lien
Clique sur Copier le lien
voici le lien: https://drive.google.com/file/d/1WvL3vj40BJOyowkl2FFNJCZBvILJNlDI/view?usp=sharing

