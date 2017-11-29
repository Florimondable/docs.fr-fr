---
title: ICorDebug, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebug
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebug
helpviewer_keywords: ICorDebug interface [.NET Framework debugging]
ms.assetid: 33f431d7-ab1a-494d-8af2-20ab15aba194
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 62a29133252277cbf614a1916af6fa4c6905a920
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebug-interface"></a><span data-ttu-id="72a6e-102">ICorDebug, interface</span><span class="sxs-lookup"><span data-stu-id="72a6e-102">ICorDebug Interface</span></span>
<span data-ttu-id="72a6e-103">Fournit des méthodes qui permettent aux développeurs de déboguer des applications dans l’environnement du common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="72a6e-103">Provides methods that allow developers to debug applications in the common language runtime (CLR) environment.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="72a6e-104">Débogage en mode mixte (code managé et natif) n’est pas pris en charge sur Windows 95, Windows 98 ou Windows Millennium Edition ou sur les plateformes non-x86 (par exemple, IA64 et AMD64).</span><span class="sxs-lookup"><span data-stu-id="72a6e-104">Mixed-mode (managed and native code) debugging is not supported on Windows 95, Windows 98, or Windows ME, or on non-x86 platforms (such as IA64 and AMD64).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="72a6e-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="72a6e-105">Methods</span></span>  
  
|<span data-ttu-id="72a6e-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="72a6e-106">Method</span></span>|<span data-ttu-id="72a6e-107">Description</span><span class="sxs-lookup"><span data-stu-id="72a6e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="72a6e-108">CanLaunchOrAttach (méthode)</span><span class="sxs-lookup"><span data-stu-id="72a6e-108">CanLaunchOrAttach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-canlaunchorattach-method.md)|<span data-ttu-id="72a6e-109">Détermine si le lancement d’un nouveau processus ou l’attachement au processus donné est possible dans le contexte de la configuration actuelle de l’ordinateur et d’exécution.</span><span class="sxs-lookup"><span data-stu-id="72a6e-109">Determines whether launching a new process or attaching to the given process is possible within the context of the current machine and runtime configuration.</span></span>|  
|[<span data-ttu-id="72a6e-110">CreateProcess (méthode)</span><span class="sxs-lookup"><span data-stu-id="72a6e-110">CreateProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md)|<span data-ttu-id="72a6e-111">Lance un processus et son thread principal sous le contrôle du débogueur.</span><span class="sxs-lookup"><span data-stu-id="72a6e-111">Launches a process and its primary thread under the control of the debugger.</span></span>|  
|[<span data-ttu-id="72a6e-112">DebugActiveProcess (méthode)</span><span class="sxs-lookup"><span data-stu-id="72a6e-112">DebugActiveProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md)|<span data-ttu-id="72a6e-113">Attache le débogueur à un processus existant.</span><span class="sxs-lookup"><span data-stu-id="72a6e-113">Attaches the debugger to an existing process.</span></span>|  
|[<span data-ttu-id="72a6e-114">EnumerateProcesses (méthode)</span><span class="sxs-lookup"><span data-stu-id="72a6e-114">EnumerateProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-enumerateprocesses-method.md)|<span data-ttu-id="72a6e-115">Obtient un énumérateur pour les processus en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="72a6e-115">Gets an enumerator for the processes that are being debugged.</span></span>|  
|[<span data-ttu-id="72a6e-116">GetProcess (méthode)</span><span class="sxs-lookup"><span data-stu-id="72a6e-116">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-getprocess-method.md)|<span data-ttu-id="72a6e-117">Retourne l’objet « ICorDebugProcess » avec l’ID de processus donné.</span><span class="sxs-lookup"><span data-stu-id="72a6e-117">Returns the "ICorDebugProcess" object with the given process ID.</span></span>|  
|[<span data-ttu-id="72a6e-118">Initialize (méthode)</span><span class="sxs-lookup"><span data-stu-id="72a6e-118">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md)|<span data-ttu-id="72a6e-119">Initialise le `ICorDebug` objet.</span><span class="sxs-lookup"><span data-stu-id="72a6e-119">Initializes the `ICorDebug` object.</span></span>|  
|[<span data-ttu-id="72a6e-120">SetManagedHandler (méthode)</span><span class="sxs-lookup"><span data-stu-id="72a6e-120">SetManagedHandler Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md)|<span data-ttu-id="72a6e-121">Spécifie l’objet de gestionnaire d’événements pour les événements managés.</span><span class="sxs-lookup"><span data-stu-id="72a6e-121">Specifies the event handler object for managed events.</span></span>|  
|[<span data-ttu-id="72a6e-122">SetUnmanagedHandler (méthode)</span><span class="sxs-lookup"><span data-stu-id="72a6e-122">SetUnmanagedHandler Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-setunmanagedhandler-method.md)|<span data-ttu-id="72a6e-123">Spécifie l’objet de gestionnaire d’événements pour les événements non gérés.</span><span class="sxs-lookup"><span data-stu-id="72a6e-123">Specifies the event handler object for unmanaged events.</span></span>|  
|[<span data-ttu-id="72a6e-124">Terminate (méthode)</span><span class="sxs-lookup"><span data-stu-id="72a6e-124">Terminate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md)|<span data-ttu-id="72a6e-125">Met fin à la `ICorDebug` objet.</span><span class="sxs-lookup"><span data-stu-id="72a6e-125">Terminates the `ICorDebug` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72a6e-126">Remarques</span><span class="sxs-lookup"><span data-stu-id="72a6e-126">Remarks</span></span>  
 <span data-ttu-id="72a6e-127">`ICorDebug`représente une boucle de traitement d’événements pour un processus du débogueur.</span><span class="sxs-lookup"><span data-stu-id="72a6e-127">`ICorDebug` represents an event processing loop for a debugger process.</span></span> <span data-ttu-id="72a6e-128">Le débogueur doit attendre le [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) rappel de tous les processus en cours de débogage avant de libérer cette interface.</span><span class="sxs-lookup"><span data-stu-id="72a6e-128">The debugger must wait for the [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) callback from all processes being debugged before releasing this interface.</span></span>  
  
 <span data-ttu-id="72a6e-129">Le `ICorDebug` objet est l’objet initial pour contrôler tout débogage managé supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="72a6e-129">The `ICorDebug` object is the initial object to control all further managed debugging.</span></span> <span data-ttu-id="72a6e-130">Dans les versions 1.0 et 1.1 du .NET Framework, cet objet a été un `CoClass` objet créé à partir de COM.</span><span class="sxs-lookup"><span data-stu-id="72a6e-130">In the .NET Framework versions 1.0 and 1.1, this object was a `CoClass` object created from COM.</span></span> <span data-ttu-id="72a6e-131">Dans le .NET Framework version 2.0, cet objet n’est plus un `CoClass` objet.</span><span class="sxs-lookup"><span data-stu-id="72a6e-131">In the .NET Framework version 2.0, this object is no longer a `CoClass` object.</span></span> <span data-ttu-id="72a6e-132">Il doit être créé par le [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) fonction, qui est plus en charge des versions.</span><span class="sxs-lookup"><span data-stu-id="72a6e-132">It must be created by the [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) function, which is more version-aware.</span></span> <span data-ttu-id="72a6e-133">Cette nouvelle fonction de création permet aux clients d’obtenir une implémentation spécifique de `ICorDebug`, qui émule également une version spécifique de l’API de débogage.</span><span class="sxs-lookup"><span data-stu-id="72a6e-133">This new creation function enables clients to get a specific implementation of `ICorDebug`, which also emulates a specific version of the debugging API.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="72a6e-134">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="72a6e-134">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72a6e-135">Spécifications</span><span class="sxs-lookup"><span data-stu-id="72a6e-135">Requirements</span></span>  
 <span data-ttu-id="72a6e-136">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72a6e-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72a6e-137">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="72a6e-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="72a6e-138">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="72a6e-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72a6e-139">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72a6e-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72a6e-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="72a6e-140">See Also</span></span>  
 [<span data-ttu-id="72a6e-141">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="72a6e-141">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)