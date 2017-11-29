---
title: "ICorPublishProcess::GetDisplayName, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishProcess.GetDisplayName
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishProcess::GetDisplayName
helpviewer_keywords:
- ICorPublishProcess::GetDisplayName method [.NET Framework debugging]
- GetDisplayName method, ICorPublishProcess interface [.NET Framework debugging]
ms.assetid: 7c0af9e9-a73f-41aa-a685-b21c439e059d
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2bbaa05d767302bcd75303ec902a82e7992e1db3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icorpublishprocessgetdisplayname-method"></a><span data-ttu-id="7462a-102">ICorPublishProcess::GetDisplayName, méthode</span><span class="sxs-lookup"><span data-stu-id="7462a-102">ICorPublishProcess::GetDisplayName Method</span></span>
<span data-ttu-id="7462a-103">Obtient le chemin d’accès complet du fichier exécutable pour le processus référencé par ce [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span><span class="sxs-lookup"><span data-stu-id="7462a-103">Gets the full path of the executable for the process referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7462a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7462a-104">Syntax</span></span>  
  
```  
HRESULT GetDisplayName (  
    [in]  ULONG32                    cchName,   
    [out] ULONG32                    *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR                        *szName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7462a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7462a-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="7462a-106">[in] Taille du tableau `szName`.</span><span class="sxs-lookup"><span data-stu-id="7462a-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="7462a-107">[out] Le nombre de caractères étendus retournés dans le `szName` tableau.</span><span class="sxs-lookup"><span data-stu-id="7462a-107">[out] The number of wide characters returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="7462a-108">[out] Un tableau pour stocker le nom, y compris le chemin d’accès complet du fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="7462a-108">[out] An array to store the name, including the full path, of the executable.</span></span> <span data-ttu-id="7462a-109">Le nom se termine par null.</span><span class="sxs-lookup"><span data-stu-id="7462a-109">The name is null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7462a-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="7462a-110">Requirements</span></span>  
 <span data-ttu-id="7462a-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7462a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7462a-112">**En-tête :** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="7462a-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="7462a-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7462a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7462a-114">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7462a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7462a-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7462a-115">See Also</span></span>  
 [<span data-ttu-id="7462a-116">ICorPublishProcess (Interface)</span><span class="sxs-lookup"><span data-stu-id="7462a-116">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)