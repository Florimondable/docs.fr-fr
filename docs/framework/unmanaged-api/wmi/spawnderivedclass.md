---
title: SpawnDerivedClass (fonction) (référence des API non managées)
description: La fonction SpawnDerivedClass crée un nouvel objet qui dérive d’un objet.
ms.date: 11/06/2017
api_name:
- SpawnDerivedClass
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SpawnDerivedClass
helpviewer_keywords:
- SpawnDerivedClass function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 99b996cf848de968d71cc1d325d3bbda7bd5386f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54715551"
---
# <a name="spawnderivedclass-function"></a>SpawnDerivedClass (fonction)
Crée un objet de classe dérivé à partir d’un objet spécifié.    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SpawnDerivedClass (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewClass); 
```  

## <a name="parameters"></a>Paramètres

`vFunc`  
[in] Ce paramètre n’est pas utilisé.

`ptr`  
[in] Un pointeur vers un [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.

`lFlags`  
[in] Réservée. Ce paramètre doit être 0.

`ppNewClass`  
[out] Reçoit le pointeur vers le nouvel objet de définition de classe. Si une erreur se produit, un nouvel objet n’est pas retournée, et `ppNewClass` est gauche tels quels. Sa valeur ne peut pas être `null`.

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :

|Constante  |Value  |Description  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Il y a eu une défaillance générale. |
| `WBEM_E_INVALID_OPERATION` | 0x80041016 | Une opération non valide, telle que la génération d’une classe à partir d’une instance, a été demandée. |
| `WBEM_E_INCOMPLETE_CLASS` | La classe source n’a pas complètement a été définie ou inscrite avec la gestion de Windows, donc une nouvelle classe dérivée n’est pas autorisée. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Mémoire est insuffisante pour terminer l’opération. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `ppNewClass` a la valeur `null`. |
| `WBEM_S_NO_ERROR` | 0 | L’appel de fonction a réussi.  |
  
## <a name="remarks"></a>Notes

Cette fonction encapsule un appel à la [IWbemClassObject::SpawnDerivedClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) (méthode).

`ptr` doit être une définition de classe qui devient la classe parente de l’objet généré. L’objet retourné est une sous-classe de l’objet actuel.

Le nouvel objet retourné dans `ppNewClass` devient automatiquement une sous-classe de l’objet actuel. Ce comportement ne peut pas être remplacé. Il n’existe aucune autre méthode par laquelle les sous-classes (classes dérivées) peuvent être créés.

## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils.idl  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi
- [WMI et compteurs de performances (référence des API non managées)](index.md)
