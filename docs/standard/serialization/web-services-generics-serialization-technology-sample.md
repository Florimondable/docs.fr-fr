---
title: Sérialisation de génériques de services Web, exemple de technologie
ms.date: 03/30/2017
ms.assetid: cdc15ea4-f678-4729-8ebe-188ae720bef7
ms.openlocfilehash: 27e0a7621bc77b62e36a0bbbdfa25f0ec3778798
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54636581"
---
# <a name="web-services-generics-serialization-technology-sample"></a>Sérialisation de génériques de services Web, exemple de technologie
[Télécharger l’exemple](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/GenericsSerialization.zip.exe)  
  
 Cet exemple montre comment utiliser et contrôler la sérialisation de génériques dans les services Web ASP.NET.  
  
### <a name="to-build-the-sample-using-visual-studio"></a>Pour générer l'exemple à l'aide de Visual Studio  
  
1.  Ouvrez Visual Studio et sélectionnez **Nouveau site web** dans le menu **Fichier**.  
  
2.  Dans le volet gauche de la boîte de dialogue **Nouveau site web**, sélectionnez le langage de programmation de votre choix, puis dans le volet droit, sélectionnez **Service web ASP.NET**.  
  
3.  Cliquez sur **Parcourir** et accédez au sous-répertoire \CS\GenericsService.  
  
4.  Sélectionnez Service.asmx pour ouvrir le fichier dans Visual Studio.  
  
5.  Dans le menu **Générer** , cliquez sur **Générer la solution**.  
  
> [!NOTE]
>  Les cinq premières étapes de cette liste sont facultatives. L'exécution .NET Framework générera automatiquement le service Web lors de la première demande du service.  
  
> [!NOTE]
>  Les étapes suivantes sont obligatoires pour générer l'exemple.  
  
1.  Ouvrez l'[!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] et accédez au sous-répertoire \CS.  
  
2.  Cliquez avec le bouton droit sur l’icône du sous-répertoire GenericsService et sélectionnez **Partage et sécurité**.  
  
3.  Sous l’onglet **Partage web**, sélectionnez **Partager ce dossier**.  
  
> [!IMPORTANT]
>  Notez le nom du répertoire virtuel affiché dans le volet **Alias**, car vous en aurez besoin pour exécuter l’exemple.  
  
### <a name="to-build-the-sample-using-internet-information-services"></a>Pour générer l'exemple à l'aide des services IIS (Internet Information Services)  
  
1.  Ouvrez le composant logiciel enfichable de gestion **Internet Information Services** et développez **Sites web**.  
  
2.  Cliquez sur **Site web par défaut**, sélectionnez **Nouveau**, puis sélectionnez **Répertoire virtuel** pour créer l’**Assistant Création de répertoire virtuel**.  
  
3.  Cliquez sur **Suivant**, entrez l’alias public de votre répertoire virtuel, puis cliquez sur **Suivant**.  
  
4.  Entrez le chemin d’accès au répertoire où vous avez enregistré l’exemple (en général, il s’agit du sous-répertoire \CS\GenericsService) et cliquez sur **Suivant**. Cliquez sur **Suivant** pour quitter l’Assistant.  
  
> [!IMPORTANT]
>  Notez le nom du répertoire virtuel affiché dans le volet **Alias**, car vous en aurez besoin pour exécuter l’exemple.  
  
### <a name="to-run-the-sample"></a>Pour exécuter l'exemple  
  
1.  Ouvrez une fenêtre de navigateur et sélectionnez sa barre d'adresses.  
  
2.  Type `http://localhost/[virtual directory]/Service.asmx`, où `[virtual directory]` représente le répertoire virtuel que vous avez créé lors de la création de l’exemple.  
  
## <a name="remarks"></a>Notes  
 L'exemple affiche une page ASP.NET par défaut qui contient des liens vers la définition du service Web. Vous pouvez modifier le code source pour le service Web, mais également personnaliser l'affichage. Pour plus d’informations, consultez [Création de clients de service web XML](https://msdn.microsoft.com/library/c606f3cb-4111-45b4-ae42-9300420fa16c).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Collections.Generic>
- <xref:System.Web.Services>
- <xref:System.Xml.Serialization>
- [Sérialisation](../../../docs/standard/serialization/index.md)
- [Création de services Web XML à l’aide de clients de service Web XML et ASP.NET](https://msdn.microsoft.com/library/1e64af78-d705-4384-b08d-591a45f4379c)
