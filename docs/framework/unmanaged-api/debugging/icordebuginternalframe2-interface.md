---
title: ICorDebugInternalFrame2, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugInternalFrame2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugInternalFrame2
helpviewer_keywords: ICorDebugInternalFrame2 interface [.NET Framework debugging]
ms.assetid: d4755569-85b8-4ff4-bf50-0e608e76429f
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b612cb2fb8b2a84555ccf36a8537ebecff673d47
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebuginternalframe2-interface"></a><span data-ttu-id="0287d-102">ICorDebugInternalFrame2, interface</span><span class="sxs-lookup"><span data-stu-id="0287d-102">ICorDebugInternalFrame2 Interface</span></span>
<span data-ttu-id="0287d-103">Fournit des informations sur les frames internes, notamment l’adresse de la pile et la position par rapport aux objets ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="0287d-103">Provides information about internal frames, including stack address and position in relation to ICorDebugFrame objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0287d-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="0287d-104">Methods</span></span>  
  
|<span data-ttu-id="0287d-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="0287d-105">Method</span></span>|<span data-ttu-id="0287d-106">Description</span><span class="sxs-lookup"><span data-stu-id="0287d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0287d-107">GetFrameAddress (méthode)</span><span class="sxs-lookup"><span data-stu-id="0287d-107">GetFrameAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-getframeaddress-method.md)|<span data-ttu-id="0287d-108">Retourne l’adresse de la pile du frame interne.</span><span class="sxs-lookup"><span data-stu-id="0287d-108">Returns the stack address of the internal frame.</span></span>|  
|[<span data-ttu-id="0287d-109">IsCloserToLeaf (méthode)</span><span class="sxs-lookup"><span data-stu-id="0287d-109">IsCloserToLeaf Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-isclosertoleaf-method.md)|<span data-ttu-id="0287d-110">Vérifie si le `this` frame interne est proche de la feuille de l’objet ICorDebugFrame spécifié.</span><span class="sxs-lookup"><span data-stu-id="0287d-110">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0287d-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="0287d-111">Remarks</span></span>  
 <span data-ttu-id="0287d-112">Cette interface étend l’interface ICorDebugInternalFrame.</span><span class="sxs-lookup"><span data-stu-id="0287d-112">This interface extends the ICorDebugInternalFrame interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0287d-113">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="0287d-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0287d-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0287d-114">Requirements</span></span>  
 <span data-ttu-id="0287d-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0287d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0287d-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0287d-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0287d-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0287d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0287d-118">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0287d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0287d-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0287d-119">See Also</span></span>  
 [<span data-ttu-id="0287d-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="0287d-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="0287d-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="0287d-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)