---
title: 'Procédure : Utiliser le Mode d’Interpolation pour contrôler la qualité d’Image pendant la mise à l’échelle'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interpolation mode [Windows Forms], controlling image quality
- images [Windows Forms], scaling
- images [Windows Forms], controlling quality
ms.assetid: fde9bccf-8aa5-4b0d-ba4b-788740627b02
ms.openlocfilehash: 0c295411418dabac74626c3c4ab43fb8210bbfa4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54631423"
---
# <a name="how-to-use-interpolation-mode-to-control-image-quality-during-scaling"></a>Procédure : Utiliser le Mode d’Interpolation pour contrôler la qualité d’Image pendant la mise à l’échelle
Le mode d’interpolation d’une <xref:System.Drawing.Graphics> objet influence la façon dont [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] dimensionne (étire et réduit) les images. Le <xref:System.Drawing.Drawing2D.InterpolationMode> énumération définit plusieurs modes d’interpolation, certains d'entre eux sont affichés dans la liste suivante :  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.Bilinear>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBilinear>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.Bicubic>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic>  
  
 Pour étirer une image, chaque pixel de l’image d’origine doit être mappé à un groupe de pixels dans l’image plus grande. Pour réduire une image, des groupes de pixels dans l’image d’origine doivent être mappés en pixels individuels dans l’image plus petite. L’efficacité des algorithmes qui effectuent ces mappages détermine la qualité d’une image à l’échelle. Les algorithmes qui produisent des images à l’échelle de qualité supérieure ont tendance à nécessiter plus de temps de traitement. Dans la liste précédente, <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor> est le mode de qualité et <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic> est le mode de qualité optimale.  
  
 Pour définir le mode d’interpolation, assignez un des membres de la <xref:System.Drawing.Drawing2D.InterpolationMode> énumération à la <xref:System.Drawing.Graphics.InterpolationMode%2A> propriété d’un <xref:System.Drawing.Graphics> objet.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant dessine une image, puis réduit l’image avec trois modes d’interpolation différent.  
  
 L’illustration suivante montre l’image d’origine et les trois images plus petites.  
  
 ![Image avec paramètres d’Interpolation variés](../../../../docs/framework/winforms/advanced/media/csgrapes1.png "csgrapes1")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#81](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#81)]
 [!code-vb[System.Drawing.WorkingWithImages#81](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#81)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 L'exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.  
  
## <a name="see-also"></a>Voir aussi
- [Images, bitmaps et métafichiers](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
- [Utilisation des images, bitmaps, icônes et métafichiers](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
