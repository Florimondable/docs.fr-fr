---
title: Fonction CreateDebuggingInterfaceFromVersion Function pour Silverlight
ms.date: 03/30/2017
f1_keywords:
- CreateDebuggingInterfaceFromVersion
helpviewer_keywords:
- CreateDebuggingInterfaceFromVersion function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 35c7a18f-133a-4584-bd25-bb338568b0c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 53571268391011cc1dc0ff112d484e1fa140057f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407712"
---
# <a name="createdebugginginterfacefromversion-function-for-silverlight"></a>Fonction CreateDebuggingInterfaceFromVersion Function pour Silverlight
Accepte une chaîne de version de runtime (CLR) langage commun qui est retournée à partir de la [fonction CreateVersionStringFromModule](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)et retourne une interface de débogueur correspondante (en général, [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  LPCWSTR      szDebuggeeVersion,  
    [out] IUnknown**   ppCordb,  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `szDebuggeeVersion`  
 [in] Chaîne de version du CLR dans le programme débogué cible qui est retourné par la [fonction CreateVersionStringFromModule](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md).  
  
 `ppCordb`  
 [out] Pointeur vers un autre pointeur vers un objet COM (`IUnknown`). Cet objet sera converti en un [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) de l’objet avant d’être retournée.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK  
 `ppCordb` fait référence à un objet valide qui implémente le [interface ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface.  
  
 E_INVALIDARG  
 `szDebuggeeVersion` ou `ppCordb` a la valeur null.  
  
 CORDBG_E_DEBUG_COMPONENT_MISSING  
 Un composant nécessaire pour le débogage CLR est introuvable. Cela signifie que mscordbi.dll ou mscordaccore.dll est introuvable dans le répertoire dans lequel figure le fichier CoreCLR.dll cible.  
  
 CORDBG_E_INCOMPATIBLE_PROTOCOL  
 La version de mscordbi.dll ou de mscordaccore.dll n'est pas la même que celle du fichier CoreCLR.dll cible.  
  
 E_FAIL (ou autres codes de retour E_)  
 Impossible de retourner un [interface ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md).  
  
## <a name="remarks"></a>Notes  
 L'interface retournée fournit les fonctionnalités permettant l'attachement à un CLR dans un processus cible et le débogage du code managé exécuté par le CLR.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** dbgshim.h  
  
 **Bibliothèque :** dbgshim.dll  
  
 **Versions du .NET framework :** 3.5 SP1
