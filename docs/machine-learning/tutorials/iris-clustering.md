---
title: Créer un cluster de fleurs d’iris à l’aide d’un apprenant de clustering - ML.NET
description: Découvrez comment utiliser ML.NET dans un scénario de clustering
author: pkulikov
ms.author: johalex
ms.date: 01/11/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 60506a6a8640a4f37e9f181bc88ae4f757502cb9
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56093604"
---
# <a name="tutorial-cluster-iris-flowers-using-a-clustering-learner-with-mlnet"></a>Tutoriel : créer un cluster de fleurs d’iris à l’aide d’un apprenant de clustering avec ML.NET

> [!NOTE]
> Cette rubrique fait référence à ML.NET, actuellement en préversion, et les ressources sont susceptibles d’être modifiées. Pour plus d’informations, consultez l’[introduction à ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Ce tutoriel montre comment utiliser ML.NET pour générer un [modèle de clustering](../resources/tasks.md#clustering) pour le [jeu de données Iris](https://en.wikipedia.org/wiki/Iris_flower_data_set).

Dans ce didacticiel, vous apprendrez à :
> [!div class="checklist"]
> - Comprendre le problème
> - Sélectionner la tâche d’apprentissage automatique appropriée
> - Préparer les données
> - Charger et transformer les données
> - Choisir un algorithme d’apprentissage
> - Effectuer l’apprentissage du modèle
> - Utiliser le modèle pour les prévisions

## <a name="prerequisites"></a>Prérequis

- [Visual Studio 2017 15.6 ou version ultérieure](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), avec la charge de travail « Développement multiplateforme .Net Core » installée.

## <a name="understand-the-problem"></a>Comprendre le problème

Ce problème concerne la division de l’ensemble des iris en différents groupes basés sur les caractéristiques de la fleur. Ces caractéristiques sont la longueur et la largeur d’un sépale, ainsi que la longueur et la largeur d’un pétale. Pour ce tutoriel, supposons que le type de chaque fleur est inconnu. Vous souhaitez connaître la structure d’un jeu de données à partir des caractéristiques et prédire la façon dont une instance de données s’intègre à cette structure.

## <a name="select-the-appropriate-machine-learning-task"></a>Sélectionner la tâche d’apprentissage automatique appropriée

Comme vous ne savez pas à quel groupe appartient chaque fleur, vous choisissez la tâche [Apprentissage automatique non supervisé](../resources/glossary.md#unsupervised-machine-learning). Pour diviser un jeu de données en groupes de telle sorte que les éléments dans le même groupe soient plus similaires les uns aux autres qu’à ceux des autres groupes, utilisez une tâche d’apprentissage automatique de [clustering](../resources/tasks.md#clustering).

## <a name="create-a-console-application"></a>Créer une application console

1. Ouvrez Visual Studio 2017. Sélectionnez **Fichier** > **Nouveau** > **Projet** dans la barre de menus. Dans la boîte de dialogue **Nouveau projet**, sélectionnez le nœud **Visual C#** suivi du nœud **.NET Core**. Ensuite, sélectionnez le modèle de projet **Application console (.NET Core)**. Dans la zone de texte **Nom**, tapez « IrisFlowerClustering », puis sélectionnez le bouton **OK**.

1. Créez un répertoire nommé *Data* dans votre projet pour enregistrer le jeu de données et les fichiers de modèle :

    Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis sélectionnez **Ajouter** > **Nouveau dossier**. Tapez « Données » et appuyez sur Entrée.

1. Installez le package NuGet **Microsoft.ML** :

    Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis sélectionnez **Gérer les packages NuGet**. Choisissez « nuget.org » comme Source du package, sélectionnez l’onglet **Parcourir**, recherchez **Microsoft.ML**, sélectionnez ce package dans la liste, puis sélectionnez le bouton **Installer**. Cliquez sur le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis sur le bouton **J’accepte** dans la boîte de dialogue **Acceptation de la licence** si vous acceptez les termes du contrat de licence pour les packages répertoriés.

## <a name="prepare-the-data"></a>Préparer les données

1. Téléchargez le jeu de données [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) et enregistrez-le dans le dossier *Data* que vous avez créé à l’étape précédente. Pour plus d’informations sur le jeu de données Iris, consultez la page Wikipédia [Iris de Fisher](https://en.wikipedia.org/wiki/Iris_flower_data_set) et la page [Iris Data Set](https://archive.ics.uci.edu/ml/datasets/Iris), qui est la source du jeu de données.

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le fichier *iris.data* et sélectionnez **Propriétés**. Sous **Avancé**, définissez la valeur **Copier dans le répertoire de sortie** sur **Copier si plus récent**.

Le fichier *iris.data* contient cinq colonnes qui représentent :

- la longueur des sépales en centimètres
- la largeur des sépales en centimètres
- la longueur des pétales en centimètres
- la largeur des pétales en centimètres
- le type d’iris

Dans le cadre de cet exemple de clustering, ce tutoriel ignore la dernière colonne.

## <a name="create-data-classes"></a>Créer des classes de données

Créez des classes pour les données d’entrée et les prédictions :

1. Dans l **’Explorateur de solutions**, cliquez avec le bouton de droite sur le projet, puis sélectionnez **Ajouter** > **Nouvel élément**.
1. Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe** et définissez la valeur du champ **Nom** sur *IrisData.cs*. Ensuite, sélectionnez le bouton **Ajouter**.
1. Ajoutez la directive `using` suivante au nouveau fichier :

   [!code-csharp[Add necessary usings](~/samples/machine-learning/tutorials/IrisFlowerClustering/IrisData.cs#Usings)]

Supprimez la définition de classe existante et ajoutez le code suivant, qui définit les classes `IrisData` et `ClusterPrediction`, au fichier *IrisData.cs* :

[!code-csharp[Define data classes](~/samples/machine-learning/tutorials/IrisFlowerClustering/IrisData.cs#ClassDefinitions)]

`IrisData` est la classe des données d’entrée et a des définitions pour chaque caractéristique du jeu de données. Utilisez l’attribut [Column](xref:Microsoft.ML.Data.ColumnAttribute) pour spécifier les index des colonnes sources dans le fichier de jeu de données.

La classe `ClusterPrediction` représente la sortie du modèle de clustering appliqué à une instance `IrisData`. Utilisez l’attribut [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute) pour lier les champs `PredictedClusterId` et `Distances` aux colonnes **PredictedLabel** et **Score** respectivement. Dans le cas de la tâche de clustering, ces colonnes ont la signification suivante :

- La colonne **PredictedLabel** contient l’ID du cluster prédit.
- La colonne **Score** contient un tableau avec les distances Euclidiennes au carré jusqu’aux centroïdes des clusters. La longueur du tableau est égale au nombre de clusters.

> [!NOTE]
> Utilisez le type `float` pour représenter les valeurs à virgule flottante dans les classes de données d’entrée et de prédiction.

## <a name="define-data-and-model-paths"></a>Définir des chemins de données et de modèle

Revenez au fichier *Program.cs* et ajoutez deux champs pour contenir les chemins du fichier de jeu de données et du fichier pour enregistrer le modèle :

- `_dataPath` contient le chemin du fichier avec le jeu de données utilisé pour l’apprentissage du modèle.
- `_modelPath` contient le chemin du fichier où le modèle formé est stocké.

Ajoutez le code suivant juste au-dessus de la méthode `Main` pour spécifier ces chemins :

[!code-csharp[Initialize paths](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#Paths)]

Pour compiler le code précédent, ajoutez les directives `using` suivantes en haut du fichier *Program.cs* :

[!code-csharp[Add usings for paths](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#UsingsForPaths)]

## <a name="create-ml-context"></a>Créer un contexte ML

Ajoutez les directives `using` supplémentaires suivantes en haut du fichier *Program.cs* :

[!code-csharp[Add Microsoft.ML usings](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#MLUsings)]

Dans la méthode `Main`, remplacez la ligne `Console.WriteLine("Hello World!");` par le code suivant :

[!code-csharp[Create ML context](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreateContext)]

La classe <xref:Microsoft.ML.MLContext?displayProperty=nameWithType> représente l’environnement Machine Learning et fournit des mécanismes de journalisation et des points d’entrée pour le chargement des données, l’apprentissage du modèle, la prédiction et d’autres tâches. Cela s’apparente conceptuellement à l’aide `DbContext` dans Entity Framework.

## <a name="setup-data-loading"></a>Configurer le chargement des données

Ajoutez le code suivant à la méthode `Main` pour configurer la façon de charger des données :

[!code-csharp[Create text loader](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#SetupTextLoader)]

Notez que les noms de colonnes et les indices correspondent au schéma défini par la classe `IrisData`. La valeur <xref:Microsoft.ML.Data.DataKind.R4?displayProperty=nameWithType> spécifie le type `float`.

Utilisez l’instance <xref:Microsoft.ML.Data.TextLoader> pour créer une instance <xref:Microsoft.Data.DataView.IDataView>, qui représente la source de données du jeu de données d’apprentissage :

[!code-csharp[Create IDataView](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreateDataView)]

## <a name="create-a-learning-pipeline"></a>Créer un pipeline d’apprentissage

Pour ce tutoriel, le pipeline d’apprentissage de la tâche de clustering comprend les deux étapes suivantes :

- concaténer des colonnes chargées en une seule colonne **Fonctionnalités**, utilisée par un formateur en clustering ;
- utiliser un formateur <xref:Microsoft.ML.Trainers.KMeans.KMeansPlusPlusTrainer> pour former le modèle à l’aide de l’algorithme de clustering k-means++.

Ajoutez le code suivant à la méthode `Main` :

[!code-csharp[Create pipeline](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreatePipeline)]

Le code spécifie que le jeu de données doit être divisé en trois clusters.

## <a name="train-the-model"></a>Effectuer l’apprentissage du modèle

Les étapes ajoutées dans les sections précédentes ont préparé le pipeline pour l’apprentissage, toutefois, aucune n’a été exécutée. Ajoutez la ligne suivante à la méthode `Main` pour effectuer le chargement des données et l’apprentissage du modèle :

[!code-csharp[Train the model](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#TrainModel)]

### <a name="save-the-model"></a>Enregistrer le modèle

À ce stade, vous disposez d’un modèle qui peut être intégré à n’importe laquelle de vos applications .NET existantes ou nouvelles. Pour enregistrer votre modèle dans un fichier .zip, ajoutez le code suivant à la méthode `Main` :

[!code-csharp[Save the model](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#SaveModel)]

## <a name="use-the-model-for-predictions"></a>Utiliser le modèle pour les prévisions

Pour effectuer des prédictions, utilisez la classe <xref:Microsoft.ML.PredictionEngine%602> qui prend des instances du type d’entrée via le pipeline de transformateur et produit des instances du type de sortie. Ajoutez la ligne suivante à la méthode `Main` pour créer une instance de cette classe :

[!code-csharp[Create predictor](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#Predictor)]

Créez la classe `TestIrisData` qui contiendra les instances de données de test :

1. Dans l **’Explorateur de solutions**, cliquez avec le bouton de droite sur le projet, puis sélectionnez **Ajouter** > **Nouvel élément**.
1. Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe**, puis remplacez la valeur du champ **Nom** par *TestIrisData.cs*. Ensuite, sélectionnez le bouton **Ajouter**.
1. Modifiez la classe pour la rendre statique, comme dans l’exemple suivant :

   [!code-csharp[Make class static](~/samples/machine-learning/tutorials/IrisFlowerClustering/TestIrisData.cs#Static)]

Ce tutoriel présente une instance de données d’iris au sein de cette classe. Vous pouvez ajouter d’autres scénarios à tester avec le modèle. Ajoutez le code suivant à la classe `TestIrisData` :

[!code-csharp[Test data](~/samples/machine-learning/tutorials/IrisFlowerClustering/TestIrisData.cs#TestData)]

Pour déterminer à quel cluster l’élément spécifié appartient, revenez au fichier *Program.cs* et ajoutez le code suivant dans la méthode `Main`:

[!code-csharp[Predict and output results](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#PredictionExample)]

Exécutez le programme pour voir quel cluster contient l’instance de données spécifiée et les distances au carré à partir de cette instance jusqu’aux centroïdes des clusters. Vous devriez obtenir les résultats suivants :

```text
Cluster: 2
Distances: 11.69127 0.02159119 25.59896
```

Félicitations ! Vous venez de créer un modèle d’apprentissage automatique de clustering des iris et l’avez utilisé pour réaliser des prédictions. Vous trouverez le code source de ce tutoriel dans le dépôt GitHub [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering).

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez appris à :
> [!div class="checklist"]
> - Comprendre le problème
> - Sélectionner la tâche d’apprentissage automatique appropriée
> - Préparer les données
> - Charger et transformer les données
> - Choisir un algorithme d’apprentissage
> - Effectuer l’apprentissage du modèle
> - Utiliser le modèle pour les prévisions

Consultez notre référentiel GitHub pour continuer l’apprentissage et obtenir d’autres exemples.
> [!div class="nextstepaction"]
> [Référentiel GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/)
