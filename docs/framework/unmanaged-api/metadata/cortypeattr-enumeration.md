---
title: "CorTypeAttr, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorTypeAttr
api_location: mscoree.dll
api_type: COM
f1_keywords: CorTypeAttr
helpviewer_keywords: CorTypeAttr enumeration [.NET Framework metadata]
ms.assetid: 9bede0ec-5fdf-42a2-b5b7-bee64056acb6
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ab9ce555406dfeb16f99601e6b88af2395c91ae0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="cortypeattr-enumeration"></a><span data-ttu-id="9d8d3-102">CorTypeAttr, énumération</span><span class="sxs-lookup"><span data-stu-id="9d8d3-102">CorTypeAttr Enumeration</span></span>
<span data-ttu-id="9d8d3-103">Contient des valeurs qui indiquent les métadonnées de type.</span><span class="sxs-lookup"><span data-stu-id="9d8d3-103">Contains values that indicate type metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d8d3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d8d3-104">Syntax</span></span>  
  
```  
typedef enum CorTypeAttr {  
  
    tdVisibilityMask        =   0x00000007,  
    tdNotPublic             =   0x00000000,  
    tdPublic                =   0x00000001,  
    tdNestedPublic          =   0x00000002,  
    tdNestedPrivate         =   0x00000003,  
    tdNestedFamily          =   0x00000004,  
    tdNestedAssembly        =   0x00000005,  
    tdNestedFamANDAssem     =   0x00000006,  
    tdNestedFamORAssem      =   0x00000007,  
  
    tdLayoutMask            =   0x00000018,  
    tdAutoLayout            =   0x00000000,  
    tdSequentialLayout      =   0x00000008,  
    tdExplicitLayout        =   0x00000010,  
  
    tdClassSemanticsMask    =   0x00000020,  
    tdClass                 =   0x00000000,  
    tdInterface             =   0x00000020,  
  
    tdAbstract              =   0x00000080,  
    tdSealed                =   0x00000100,  
    tdSpecialName           =   0x00000400,  
  
    tdImport                =   0x00001000,  
    tdSerializable          =   0x00002000,  
    tdWindowsRuntime        =   0x00004000,  
  
    tdStringFormatMask      =   0x00030000,  
    tdAnsiClass             =   0x00000000,  
    tdUnicodeClass          =   0x00010000,  
    tdAutoClass             =   0x00020000,  
    tdCustomFormatClass     =   0x00030000,  
    tdCustomFormatMask      =   0x00C00000,  
  
    tdBeforeFieldInit       =   0x00100000,  
    tdForwarder             =   0x00200000,  
  
    tdReservedMask          =   0x00040800,  
    tdRTSpecialName         =   0x00000800,  
    tdHasSecurity           =   0x00040000,  
  
} CorTypeAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="9d8d3-105">Membres</span><span class="sxs-lookup"><span data-stu-id="9d8d3-105">Members</span></span>  
  
|<span data-ttu-id="9d8d3-106">Membre</span><span class="sxs-lookup"><span data-stu-id="9d8d3-106">Member</span></span>|<span data-ttu-id="9d8d3-107">Description</span><span class="sxs-lookup"><span data-stu-id="9d8d3-107">Description</span></span>|  
|------------|-----------------|  
|`tdVisibilityMask`|<span data-ttu-id="9d8d3-108">Utilisé pour les informations de visibilité de type.</span><span class="sxs-lookup"><span data-stu-id="9d8d3-108">Used for type visibility information.</span></span>|  
|`tdNotPublic`|<span data-ttu-id="9d8d3-109">Spécifie que le type n’est pas dans la portée publique.</span><span class="sxs-lookup"><span data-stu-id="9d8d3-109">Specifies that the type is not in public scope.</span></span>|  
|`tdPublic`|<span data-ttu-id="9d8d3-110">Spécifie que le type est dans la portée publique.</span><span class="sxs-lookup"><span data-stu-id="9d8d3-110">Specifies that the type is in public scope.</span></span>|  
|`tdNestedPublic`|<span data-ttu-id="9d8d3-111">Spécifie que le type est imbriqué avec une visibilité publique.</span><span class="sxs-lookup"><span data-stu-id="9d8d3-111">Specifies that the type is nested with public visibility.</span></span>|  
|`tdNestedPrivate`|<span data-ttu-id="9d8d3-112">Spécifie que le type est imbriqué avec une visibilité privée.</span><span class="sxs-lookup"><span data-stu-id="9d8d3-112">Specifies that the type is nested with private visibility.</span></span>|  
|`tdNestedFamily`|<span data-ttu-id="9d8d3-113">Spécifie que le type est imbriqué avec une visibilité de niveau famille.</span><span class="sxs-lookup"><span data-stu-id="9d8d3-113">Specifies that the type is nested with family visibility.</span></span>|  
|`tdNestedAssembly`|<span data-ttu-id="9d8d3-114">Spécifie que le type est imbriqué avec une visibilité d’assembly.</span><span class="sxs-lookup"><span data-stu-id="9d8d3-114">Specifies that the type is nested with assembly visibility.</span></span>|  
|`tdNestedFamANDAssem`|<span data-ttu-id="9d8d3-115">Spécifie que le type est imbriqué avec une visibilité family et assembly.</span><span class="sxs-lookup"><span data-stu-id="9d8d3-115">Specifies that the type is nested with family and assembly visibility.</span></span>|  
|`tdNestedFamORAssem`|<span data-ttu-id="9d8d3-116">Spécifie que le type est imbriqué avec une visibilité family ou assembly.</span><span class="sxs-lookup"><span data-stu-id="9d8d3-116">Specifies that the type is nested with family or assembly visibility.</span></span>|  
|`tdLayoutMask`|<span data-ttu-id="9d8d3-117">Obtient les informations de disposition pour le type.</span><span class="sxs-lookup"><span data-stu-id="9d8d3-117">Gets layout information for the type.</span></span>|  
|`tdAutoLayout`|<span data-ttu-id="9d8d3-118">Spécifie que les champs de ce type sont placés automatiquement.</span><span class="sxs-lookup"><span data-stu-id="9d8d3-118">Specifies that the fields of this type are laid out automatically.</span></span>|  
|`tdSequentialLayout`|<span data-ttu-id="9d8d3-119">Spécifie que les champs de ce type sont placés séquentiellement.</span><span class="sxs-lookup"><span data-stu-id="9d8d3-119">Specifies that the fields of this type are laid out sequentially.</span></span>|  
|`tdExplicitLayout`|<span data-ttu-id="9d8d3-120">Spécifie la que disposition de ce champ est fournie explicitement.</span><span class="sxs-lookup"><span data-stu-id="9d8d3-120">Specifies that field layout is supplied explicitly.</span></span>|  
|`tdClassSemanticsMask`|<span data-ttu-id="9d8d3-121">Obtient des informations de sémantiques sur le type.</span><span class="sxs-lookup"><span data-stu-id="9d8d3-121">Gets semantic information about the type.</span></span>|  
|`tdClass`|<span data-ttu-id="9d8d3-122">Spécifie que le type est une classe.</span><span class="sxs-lookup"><span data-stu-id="9d8d3-122">Specifies that the type is a class.</span></span>|  
|`tdInterface`|<span data-ttu-id="9d8d3-123">Spécifie que le type est une interface.</span><span class="sxs-lookup"><span data-stu-id="9d8d3-123">Specifies that the type is an interface.</span></span>|  
|`tdAbstract`|<span data-ttu-id="9d8d3-124">Spécifie que le type est abstrait.</span><span class="sxs-lookup"><span data-stu-id="9d8d3-124">Specifies that the type is abstract.</span></span>|  
|`tdSealed`|<span data-ttu-id="9d8d3-125">Spécifie que le type ne peut pas être étendu.</span><span class="sxs-lookup"><span data-stu-id="9d8d3-125">Specifies that the type cannot be extended.</span></span>|  
|`tdSpecialName`|<span data-ttu-id="9d8d3-126">Spécifie que le nom de classe est spécial.</span><span class="sxs-lookup"><span data-stu-id="9d8d3-126">Specifies that the class name is special.</span></span> <span data-ttu-id="9d8d3-127">Son nom décrit comment.</span><span class="sxs-lookup"><span data-stu-id="9d8d3-127">Its name describes how.</span></span>|  
|`tdImport`|<span data-ttu-id="9d8d3-128">Spécifie que le type est importé.</span><span class="sxs-lookup"><span data-stu-id="9d8d3-128">Specifies that the type is imported.</span></span>|  
|`tdSerializable`|<span data-ttu-id="9d8d3-129">Spécifie que le type est sérialisable.</span><span class="sxs-lookup"><span data-stu-id="9d8d3-129">Specifies that the type is serializable.</span></span>|  
|`tdWindowsRuntime`|<span data-ttu-id="9d8d3-130">Spécifie que ce type est un [!INCLUDE[wrt](../../../../includes/wrt-md.md)] type.</span><span class="sxs-lookup"><span data-stu-id="9d8d3-130">Specifies that this type is a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] type.</span></span>|  
|`tdStringFormatMask`|<span data-ttu-id="9d8d3-131">Obtient des informations sur comment les chaînes sont encodées et mis en forme.</span><span class="sxs-lookup"><span data-stu-id="9d8d3-131">Gets information about how strings are encoded and formatted.</span></span>|  
|`tdAnsiClass`|<span data-ttu-id="9d8d3-132">Spécifie que ce type interprète LPTSTR comme ANSI.</span><span class="sxs-lookup"><span data-stu-id="9d8d3-132">Specifies that this type interprets an LPTSTR as ANSI.</span></span>|  
|`tdUnicodeClass`|<span data-ttu-id="9d8d3-133">Spécifie que ce type interprète LPTSTR au format Unicode.</span><span class="sxs-lookup"><span data-stu-id="9d8d3-133">Specifies that this type interprets an LPTSTR as Unicode.</span></span>|  
|`tdAutoClass`|<span data-ttu-id="9d8d3-134">Spécifie que ce type interprète LPTSTR automatiquement.</span><span class="sxs-lookup"><span data-stu-id="9d8d3-134">Specifies that this type interprets an LPTSTR automatically.</span></span>|  
|`tdCustomFormatClass`|<span data-ttu-id="9d8d3-135">Spécifie que le type a un encodage non standard, comme spécifié par `CustomFormatMask`.</span><span class="sxs-lookup"><span data-stu-id="9d8d3-135">Specifies that the type has a non-standard encoding, as specified by `CustomFormatMask`.</span></span>|  
|`tdCustomFormatMask`|<span data-ttu-id="9d8d3-136">Utilisez ce masque pour obtenir des informations de codage non standard pour une interopérabilité native.</span><span class="sxs-lookup"><span data-stu-id="9d8d3-136">Use this mask to get non-standard encoding information for native interop.</span></span> <span data-ttu-id="9d8d3-137">La signification des valeurs de ces deux bits n’est pas spécifiée.</span><span class="sxs-lookup"><span data-stu-id="9d8d3-137">The meaning of the values of these two bits is unspecified.</span></span>|  
|`tdBeforeFieldInit`|<span data-ttu-id="9d8d3-138">Spécifie que le type doit être initialisé avant la première tentative d’accès à un champ statique.</span><span class="sxs-lookup"><span data-stu-id="9d8d3-138">Specifies that the type must be initialized before the first attempt to access a static field.</span></span>|  
|`tdForwarder`|<span data-ttu-id="9d8d3-139">Spécifie que le type est exporté et un redirecteur de type.</span><span class="sxs-lookup"><span data-stu-id="9d8d3-139">Specifies that the type is exported, and a type forwarder.</span></span>|  
|`tdReservedMask`|<span data-ttu-id="9d8d3-140">Cet indicateur et les indicateurs ci-après sont utilisées en interne par le common language runtime.</span><span class="sxs-lookup"><span data-stu-id="9d8d3-140">This flag and the flags below are used internally by the common language runtime.</span></span>|  
|`tdRTSpecialName`|<span data-ttu-id="9d8d3-141">Spécifie que le common language runtime doit vérifier l’encodage de nom.</span><span class="sxs-lookup"><span data-stu-id="9d8d3-141">Specifies that the common language runtime should check the name encoding.</span></span>|  
|`tdHasSecurity`|<span data-ttu-id="9d8d3-142">Spécifie que le type est associée.</span><span class="sxs-lookup"><span data-stu-id="9d8d3-142">Specifies that the type has security associated with it.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9d8d3-143">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9d8d3-143">Requirements</span></span>  
 <span data-ttu-id="9d8d3-144">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d8d3-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d8d3-145">**En-tête :** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="9d8d3-145">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="9d8d3-146">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d8d3-146">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d8d3-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d8d3-147">See Also</span></span>  
 [<span data-ttu-id="9d8d3-148">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="9d8d3-148">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)