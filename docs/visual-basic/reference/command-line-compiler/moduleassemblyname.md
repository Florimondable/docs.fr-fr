---
title: -moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
ms.openlocfilehash: f88a0001bb2ba55c0a3eac3ed208f14292d86734
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56745662"
---
# <a name="-moduleassemblyname"></a>-moduleassemblyname
Spécifie le nom de l’assembly dont ce module doit faire partie.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terme|Définition|  
|---|---|  
|`assembly_name`|Le nom de l’assembly de ce module fera partie.|  
  
## <a name="remarks"></a>Notes  
 Le compilateur traite la `-moduleassemblyname` option uniquement si le `-target:module` option a été spécifiée. Cela indique au compilateur de créer un module. Le module créé par le compilateur est valide uniquement pour l’assembly spécifié avec la `-moduleassemblyname` option. Si vous placez le module dans un assembly différent, les erreurs d’exécution seront produit.  
  
 Le `-moduleassemblyname` option est uniquement requise lorsque les conditions suivantes sont remplies :  
  
-   Un type de données dans le module a besoin d’accéder à un `Friend` type dans un assembly référencé.  
  
-   L’assembly référencé a accordé l’accès d’assembly friend à l’assembly dans lequel le module sera généré.  
  
 Pour plus d’informations sur la création d’un module, consultez [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md). Pour plus d’informations sur les assemblys friend, consultez [assemblys Friend](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).  
  
> [!NOTE]
>  Le `-moduleassemblyname` option n’est pas disponible dans l’environnement de développement Visual Studio ; il est disponible uniquement lorsque vous compilez à partir d’une invite de commandes.  
  
## <a name="see-also"></a>Voir aussi
- [Guide pratique pour générer un assembly multifichier](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)
- [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [-main](../../../visual-basic/reference/command-line-compiler/main.md)
- [-référence (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)
- [Assemblys dans .NET](../../../standard/assembly/index.md)
- [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Assemblys friend](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)
