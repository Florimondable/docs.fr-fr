---
title: CoEEShutDownCOM, fonction
ms.date: 03/30/2017
api_name:
- CoEEShutDownCOM
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CoEEShutDownCOM
helpviewer_keywords:
- CoEEShutDownCOM function [.NET Framework hosting]
ms.assetid: b634cae2-632f-4737-9be4-92d0652844d7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 755ff827300dd9fef5944924f6373415f6d8fa6a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568580"
---
# <a name="coeeshutdowncom-function"></a>CoEEShutDownCOM, fonction
Force le common language runtime (CLR) pour libérer tous les pointeurs d’interface qu’il conserve dans callable wrappers RCW (runtime). Cela a pour effet de libérer tous les caches de wrapper RCW. Cette fonction globale est déconseillée dans le [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. Au lieu de cela, utilisez le point d’entrée pour une exécution spécifique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a>Notes  
 Le `CoEEShutDownCOM` fonction libère tout d’abord tous les wrappers RCW dans tous les contextes et dans tous les caches et la supprime ensuite toute notification de destruction existante dans le programme d’installation. Aucun déchargement de DLL se produit.  
  
> [!CAUTION]
>  Cette fonction affecte tous les runtimes chargés dans le processus.  
  
 Compter les [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], appelez le point d’entrée pour cette fonction sur le runtime spécifique que vous souhaitez affecter. Pour obtenir le point d’entrée, appelez le [ICLRRuntimeInfo::GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) (méthode) et spécifiez « CoEEShutDownCOM ».  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi
- [Fonctions statiques globales des métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
