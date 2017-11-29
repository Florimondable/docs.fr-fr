---
title: "ICorDebugController::SetAllThreadsDebugState, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController.SetAllThreadsDebugState
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController::SetAllThreadsDebugState
helpviewer_keywords:
- SetAllThreadsDebugState method [.NET Framework debugging]
- ICorDebugController::SetAllThreadsDebugState method [.NET Framework debugging]
ms.assetid: bdda4bd7-4743-4d58-a22b-8067e967db95
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d5a033ef2efd8fa5e3b519e19b62ce2dfb84a5e2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcontrollersetallthreadsdebugstate-method"></a><span data-ttu-id="67bcc-102">ICorDebugController::SetAllThreadsDebugState, méthode</span><span class="sxs-lookup"><span data-stu-id="67bcc-102">ICorDebugController::SetAllThreadsDebugState Method</span></span>
<span data-ttu-id="67bcc-103">Définit l’état de débogage de tous les threads managés dans le processus.</span><span class="sxs-lookup"><span data-stu-id="67bcc-103">Sets the debug state of all managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67bcc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="67bcc-104">Syntax</span></span>  
  
```  
HRESULT SetAllThreadsDebugState (  
    [in] CorDebugThreadState  state,  
    [in] ICorDebugThread      *pExceptThisThread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="67bcc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="67bcc-105">Parameters</span></span>  
 `state`  
 <span data-ttu-id="67bcc-106">[in] Valeur de l’énumération « CorDebugThreadState » qui spécifie l’état du thread pour le débogage.</span><span class="sxs-lookup"><span data-stu-id="67bcc-106">[in] A value of the "CorDebugThreadState" enumeration that specifies the state of the thread for debugging.</span></span>  
  
 `pExceptThisThread`  
 <span data-ttu-id="67bcc-107">[in] Pointeur vers un objet « ICorDebugThread » qui représente un thread à exempter du paramètre d’état de débogage.</span><span class="sxs-lookup"><span data-stu-id="67bcc-107">[in] A pointer to an "ICorDebugThread" object that represents a thread to be exempted from the debug state setting.</span></span> <span data-ttu-id="67bcc-108">Si cette valeur est null, aucun thread n’est exempté.</span><span class="sxs-lookup"><span data-stu-id="67bcc-108">If this value is null, no thread is exempted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67bcc-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="67bcc-109">Remarks</span></span>  
 <span data-ttu-id="67bcc-110">Le `SetAllThreadsDebugState` threads qui ne sont pas visibles via la méthode peut affecter [EnumerateThreads, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md), les threads qui ont été interrompus avec le `SetAllThreadsDebugState` méthode devra être repris avec le `SetAllThreadsDebugState` (méthode).</span><span class="sxs-lookup"><span data-stu-id="67bcc-110">The `SetAllThreadsDebugState` method may affect threads that are not visible via [EnumerateThreads Method](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md), so threads that were suspended with the `SetAllThreadsDebugState` method will need to be resumed with the `SetAllThreadsDebugState` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67bcc-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="67bcc-111">Requirements</span></span>  
 <span data-ttu-id="67bcc-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67bcc-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67bcc-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="67bcc-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="67bcc-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67bcc-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67bcc-115">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67bcc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67bcc-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="67bcc-116">See Also</span></span>  
 