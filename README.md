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
- **Namespace :** P2FixAnAppDotNetCode.Components
- **Classe :** CartSummaryViewComponent
- **Méthode :** Invoke()

### 2. ProductController
- **Namespace :** P2FixAnAppDotNetCode.Controllers
- **Classe :** ProductController
- **Méthode :** Index()

### 3. ProductService.GetAllProducts()
- **Namespace :** P2FixAnAppDotNetCode.Models.Services
- **Classe :** ProductService
- **Méthode :** GetAllProducts()

### 4. ProductRepository
- **Namespace :** P2FixAnAppDotNetCode.Models.Repositories
- **Classe :** ProductRepository
- **Méthode :** GetAllProducts()
### 5. Startup
- **Namespace :** P2FixAnAppDotNetCode
- **Classe :** Startup
- **Méthode :** Startup(IConfiguration configuration)
- 
### 6. CartController
- **Namespace :** `P2FixAnAppDotNetCode.Controllers`
- **Classe :** `CartController`
- **Méthode :** `Index()

### 9. Modes de débogage : Quand les utiliser ?

#### **F10 - Pas à pas principal**
**Utilisable :**
- On veut exécuter une ligne sans entrer dans les méthodes
- On connaît déjà le fonctionnement de la méthode appelée
- On veut avancer rapidement dans le code

**Exemples dans notre projet :**
- `Startup` : Pas besoin d'entrer dans la configuration
- `CartSummaryViewComponent.Invoke()` : Simple retour de vue
- `CartController.Index()` : Retour direct de la vue

#### **F11 - Pas à pas détaillé**
**Utilisable :**
- On veut comprendre le fonctionnement interne d'une méthode
- On cherche un bug dans une fonction spécifique
- On veut voir le flux complet d'exécution

**Exemples dans notre projet :**
- `ProductController.Index()` → entrer dans `GetAllProducts()`
- `GetAllProducts()` → entrer dans le repository pour voir le filtrage
- Investigation du bug de décrémentation du stock

#### **Shift + F11 - Pas à pas sortant**
 **Utilisable:**
- On est entré trop profondément dans le code
- On veut revenir à la méthode appelante
- On a fini d'analyser une méthode

**Exemples dans notre projet :**
- Sortir de `ProductRepository.GetAllProducts()` après avoir vu le filtre
- Revenir à `ProductController` après l'analyse du service

## 10. Déploiement de notre application .NET en exécutable Windows
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
## 11. Optionnel :  
a) Ajoutez une langue d’affichage à l’interface, Wolof par exemple. Conservez les options de 
culture du français. 
L'application supporte désormais la langue **Wolof** en plus de l'anglais et du français.

### Fonctionnalités
- **Interface traduite** : Menus, panier, formulaires de commande et messages système.
- **Formatage culturel** : Utilisation des conventions françaises pour les nombres et les dates (ex: `1 000 FCFA`), afin de respecter les habitudes locales au Sénégal.
### Fichiers ajoutés
9 fichiers de ressources ont été créés pour assurer la traduction complète :
- [Resources/Controllers/OrderController.wo.resx]
- [Resources/Models/ViewModels/LanguageViewModel.wo.resx]
- [Resources/Models/ViewModels/Order.wo.resx]
- [Resources/Views/Cart/Index.wo.resx]
- [Resources/Views/Order/Completed.wo.resx]
- [Resources/Views/Order/Index.wo.resx]
- [Resources/Views/Product/Index.wo.resx]
- [Resources/Views/Shared/Components/CartSummary/Default.wo.resx]
- [Resources/Views/Shared/Components/LanguageSelector/Default.wo.resx]
### Configuration
La configuration a été effectuée dans :
- **Startup.cs** : Ajout de la culture `wo` avec les options de formatage `fr-FR`.
- **LanguageService.cs** : Prise en charge de la section du Wolof.
- **LanguageSelector/Default.cshtml** : Ajout de l'option dans le menu déroulant.

