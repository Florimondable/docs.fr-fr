---
title: CorNativeLinkType, énumération
ms.date: 03/30/2017
api_name:
- CorNativeLinkType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeLinkType
helpviewer_keywords:
- CorNativeLinkType enumeration [.NET Framework metadata]
ms.assetid: 4f86ff37-2dab-4e64-819a-76b3bfe828ff
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0f946179fc31adebc8e8fc67c394e0b55a876f49
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54641328"
---
# <a name="cornativelinktype-enumeration"></a>CorNativeLinkType, énumération
Fournit des valeurs qui indiquent le type lié en code natif.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum   
{  
    nltNone       = 1,  
    nltAnsi       = 2,  
    nltUnicode    = 3,  
    nltAuto       = 4,  
    nltOle        = 5,  
    nltMaxValue   = 7  
} CorNativeLinkType;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`nltNone`|Indique qu’aucun des mots clés sont spécifiés.|  
|`nltAnsi`|Indique qu’un mot clé ANSI est spécifié.|  
|`nltUnicode`|Indique qu’un mot clé Unicode est spécifié.|  
|`nltAuto`|Indique qu’un mot clé auto est spécifié.|  
|`nltOle`|Indique qu’un mot clé OLE est spécifié.|  
|`nltMaxValue`|Non utilisé.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi
- [Énumérations de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
