---
title: -target:exe (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /exe
helpviewer_keywords:
- target compiler options [C#], /target:exe
- /target compiler options [C#], /target:exe
- -target compiler options [C#], /target:exe
ms.assetid: bda5717d-1b91-4848-956b-fcf85c30e432
ms.openlocfilehash: b9efa25870e11e0140cba2ad39c3bc4515056ce3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54697879"
---
# <a name="-targetexe-c-compiler-options"></a>-target:exe (Options du compilateur C#)
L’option **-target:exe** indique au compilateur de créer une application console exécutable (EXE).  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-target:exe  
```  
  
## <a name="remarks"></a>Notes  
 L’option **-target:exe** est activée par défaut. Le fichier exécutable est créé avec l’extension .exe.  
  
 Utilisez [-target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) pour créer un programme exécutable Windows.  
  
 À moins que l’option [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) spécifie autre chose, le fichier de sortie prend le nom du fichier d’entrée qui contient la méthode [Main](../../../csharp/programming-guide/main-and-command-args/index.md).  
  
 Quand ils sont spécifiés dans la ligne de commande, tous les fichiers jusqu’à l’option **-out** ou **-target:module** suivante sont utilisés pour créer le fichier .exe.  
  
 Une seule et unique méthode **Main** est requise dans les fichiers de code source qui sont compilés dans un fichier .exe. L’option de compilateur [-main](../../../csharp/language-reference/compiler-options/main-compiler-option.md) vous permet de spécifier la classe contenant la méthode **Main**, au cas où votre code possède plusieurs classes avec une méthode **Main**.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la page **Propriétés** du projet.  
  
2.  Cliquez sur la page de propriétés **Application**.  
  
3.  Modifiez la propriété **Type de sortie**.  
  
 Pour plus d’informations sur la définition de cette option du compilateur par programmation, consultez <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Exemple  
 Chacune des lignes de commande suivantes compile `in.cs` et crée `in.exe` :  
  
```console  
csc -target:exe in.cs  
csc in.cs  
```  
  
## <a name="see-also"></a>Voir aussi

- [-target (Options du compilateur C#)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)
- [Options du compilateur C#](../../../csharp/language-reference/compiler-options/index.md)
