---
title: 'Procédure : Définir l’Image affichée par un Windows Forms de contrôle'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Button control [Windows Forms], images
- Windows Forms controls, images
- controls [Windows Forms], images
- images [Windows Forms], Windows Forms controls
- examples [Windows Forms], controls
ms.assetid: 9445af8f-4f62-48b0-a3f6-068058964b9f
ms.openlocfilehash: 93bc7970ce7c287273f8bd7ff50b07c6658e2a08
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54644922"
---
# <a name="how-to-set-the-image-displayed-by-a-windows-forms-control"></a>Procédure : Définir l’Image affichée par un Windows Forms de contrôle
Plusieurs contrôles Windows Forms peuvent afficher des images. Ces images peuvent être des icônes qui clarifient l’objectif du contrôle, par exemple une icône de disquette sur un bouton qui dénote le **enregistrer** commande. Les icônes peuvent être également des images d’arrière-plan pour donner le contrôle l’apparence et le comportement de que votre choix.  
  
### <a name="to-set-the-image-displayed-by-a-control"></a>Pour définir l’image affichée par un contrôle  
  
1.  Définir le contrôle `Image` ou `BackgroundImage` propriété à un objet de type <xref:System.Drawing.Image>. En règle générale, vous chargez l’image à partir d’un fichier à l’aide de la <xref:System.Drawing.Image.FromFile%2A> (méthode).  
  
     Dans l’exemple de code suivant, le chemin d’accès défini pour l’emplacement de l’image est la **Mes images** dossier. La plupart des ordinateurs exécutant le système d’exploitation Windows incluent ce répertoire. Cela permet également aux utilisateurs avec des niveaux d’accès système minimal exécuter l’application en toute sécurité. L’exemple de code suivant requiert que vous disposez déjà d’un formulaire avec un <xref:System.Windows.Forms.PictureBox> contrôle ajouté.  
  
    ```vb  
    ' Replace the image named below  
    ' with an icon of your own choosing.  
    PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.MyPictures) _  
       & "\Image.gif")  
    ```  
  
    ```csharp  
    // Replace the image named below  
    // with an icon of your own choosing.  
    // Note the escape character used (@) when specifying the path.  
    pictureBox1.Image = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.MyPictures)  
       + @"\Image.gif");  
    ```  
  
    ```cpp  
    // Replace the image named below  
    // with an icon of your own choosing.  
    pictureBox1->Image = Image::FromFile(String::Concat  
       (System::Environment::GetFolderPath  
       (System::Environment::SpecialFolder::MyPictures),  
       "\\Image.gif"));  
    ```  
  
## <a name="see-also"></a>Voir aussi
- <xref:System.Drawing.Image.FromFile%2A>
- <xref:System.Drawing.Image>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
