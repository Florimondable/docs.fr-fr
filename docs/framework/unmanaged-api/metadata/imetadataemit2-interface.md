---
title: IMetaDataEmit2, interface
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2
helpviewer_keywords:
- IMetaDataEmit2 interface [.NET Framework metadata]
ms.assetid: 866dc96b-bbfc-4c0f-80c2-38ce93072106
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a9e0477adb4958a53289cd0a64f39259403fa7dd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54656932"
---
# <a name="imetadataemit2-interface"></a>IMetaDataEmit2, interface
Étend la [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface principalement pour fournir la capacité de travailler avec les types génériques.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[DefineGenericParam, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md)|Crée une définition pour un paramètre de type générique et obtient un jeton pour ce paramètre de type générique.|  
|[DefineMethodSpec, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md)|Crée une instance d’une méthode générique et obtient un jeton pour la définition.|  
|[GetDeltaSaveSize, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md)|Obtient une valeur qui indique la différence de taille des données qui sont requis pour exprimer les modifications pour la session active modifier et continuer.|  
|[ResetENCLog, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md)|Réinitialise le journal modifier et continuer et démarre une nouvelle session.|  
|[SaveDelta, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedelta-method.md)|Enregistre les modifications de la session active modifier et continuer dans le fichier spécifié.|  
|[SaveDeltaToMemory, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)|Enregistre les modifications de la session active modifier et continuer à la mémoire.|  
|[SaveDeltaToStream, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatostream-method.md)|Enregistre les modifications de la session active modifier et continuer dans le flux spécifié.|  
|[SetGenericParamProps, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-setgenericparamprops-method.md)|Définit les valeurs de propriété pour la définition de paramètre générique référencé par le jeton spécifié.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi
- [Interfaces de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
