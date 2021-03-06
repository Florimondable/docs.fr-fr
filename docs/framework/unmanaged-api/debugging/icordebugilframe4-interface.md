---
title: ICorDebugILFrame4, interface
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame4
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1e739183-3e05-49e5-846f-4075256e41de
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fb3f55a8a0ddff6c3202d15dc4704d443cabb44d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54656945"
---
# <a name="icordebugilframe4-interface"></a>ICorDebugILFrame4, interface
[Pris en charge dans .NET Framework 4.5.2 et ultérieur]  
  
 Fournit des méthodes qui vous permettent d'accéder aux variables locales et au code dans un frame de pile de code de langage intermédiaire. Un paramètre spécifie si le débogueur a accès aux variables et au code ajoutés dans l'instrumentation ReJIT du profileur.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[EnumerateLocalVariablesEx, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md)|Retourne une liste des variables locales disponibles dans le frame actif.|  
|[GetCodeEx, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md)|Retourne le code exécuté par ce frame de pile.|  
|[GetLocalVariableEx, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md)|Retourne la valeur d'une variable locale du frame de langage intermédiaire.|  
  
## <a name="remarks"></a>Notes  
 Ces méthodes offrent des fonctionnalités en plus de celles fournies par le [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md), [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md), et [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) méthodes. Chaque méthode comprend un paramètre `flags` qui spécifie si des variables locales ou du code supplémentaires définis par une demande ReJIT du profileur sont visibles.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi
- [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)
