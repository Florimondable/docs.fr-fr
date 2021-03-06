---
title: ISymUnmanagedMethod::GetSequencePoints, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSequencePoints
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSequencePoints
helpviewer_keywords:
- ISymUnmanagedMethod::GetSequencePoints method [.NET Framework debugging]
- GetSequencePoints method [.NET Framework debugging]
ms.assetid: f909ac48-3d8f-49fb-a369-e3d9959151cd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bf6528e8fe6a979db26ae44819bf34a36592ed6b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54623623"
---
# <a name="isymunmanagedmethodgetsequencepoints-method"></a>ISymUnmanagedMethod::GetSequencePoints, méthode
Obtient tous les points de séquence au sein de cette méthode.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetSequencePoints(  
    [in]  ULONG32  cPoints,  
    [out] ULONG32  *pcPoints,  
    [in, size_is(cPoints)] ULONG32  offsets[],  
    [in, size_is(cPoints)] ISymUnmanagedDocument* documents[],  
    [in, size_is(cPoints)] ULONG32  lines[],  
    [in, size_is(cPoints)] ULONG32  columns[],  
    [in, size_is(cPoints)] ULONG32  endLines[],  
    [in, size_is(cPoints)] ULONG32  endColumns[]);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cPoints`  
 [in] Un `ULONG32` qui reçoit la taille de la `offsets`, `documents`, `lines`, `columns`, `endLines`, et `endColumns` tableaux.  
  
 `pcPoints`  
 [out] Un pointeur vers un `ULONG32` qui reçoit la longueur de la mémoire tampon requise pour contenir les points de séquence.  
  
 `offsets`  
 [in] Tableau dans lequel stocker le Microsoft intermediate language (MSIL) offsets à partir du début de la méthode pour les points de séquence.  
  
 `documents`  
 [in] Tableau dans lequel stocker les documents dans laquelle se trouvent les points de séquence.  
  
 `lines`  
 [in] Tableau dans lequel stocker les lignes des documents auxquelles figurent les points de séquence.  
  
 `columns`  
 [in] Tableau dans lequel stocker les colonnes des documents auxquelles figurent les points de séquence.  
  
 `endLines`  
 [in] Tableau de lignes des documents auxquelles la séquence de points de fin.  
  
 `endColumns`  
 [in] Tableau de colonnes des documents auxquelles la séquence de points de fin.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Voir aussi
- [ISymUnmanagedMethod, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
