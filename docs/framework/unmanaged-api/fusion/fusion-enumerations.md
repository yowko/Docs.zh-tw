---
title: "融合列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged enumerations [.NET Framework], fusion
- fusion enumerations [.NET Framework]
- enumerations [.NET Framework fusion]
ms.assetid: 5817b4bc-b0ba-4b2f-a11c-a03dd8cb8f84
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 53c346418234fd0be45242f3e7aa0212dcef477a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="fusion-enumerations"></a><span data-ttu-id="f72b5-102">融合列舉</span><span class="sxs-lookup"><span data-stu-id="f72b5-102">Fusion Enumerations</span></span>
<span data-ttu-id="f72b5-103">本章節描述融合 API 使用的 unmanaged 的列舉。</span><span class="sxs-lookup"><span data-stu-id="f72b5-103">This section describes the unmanaged enumerations that the fusion API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f72b5-104">本章節內容</span><span class="sxs-lookup"><span data-stu-id="f72b5-104">In This Section</span></span>  
 [<span data-ttu-id="f72b5-105">ASM_CACHE_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="f72b5-105">ASM_CACHE_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md)  
 <span data-ttu-id="f72b5-106">表示由組件的來源[IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)在全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="f72b5-106">Indicates the source of an assembly represented by [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md) in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="f72b5-107">ASM_CMP_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="f72b5-107">ASM_CMP_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/fusion/asm-cmp-flags-enumeration.md)  
 <span data-ttu-id="f72b5-108">表示版本、 組建、 文化特性、 簽章，依此類推，所要比較的兩個組件的[iassemblyname:: Isequal](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-isequal-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="f72b5-108">Indicates the version, build, culture, signature, and so on, of two assemblies to be compared by the [IAssemblyName::IsEqual](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-isequal-method.md) method.</span></span>  
  
 [<span data-ttu-id="f72b5-109">ASM_DISPLAY_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="f72b5-109">ASM_DISPLAY_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/fusion/asm-display-flags-enumeration.md)  
 <span data-ttu-id="f72b5-110">表示版本、 組建、 文化特性、 簽章，依此類推，將擷取其顯示名稱的組件[iassemblyname:: Getdisplayname](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getdisplayname-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="f72b5-110">Indicates the version, build, culture, signature, and so on, of the assembly whose display name will be retrieved by the [IAssemblyName::GetDisplayName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getdisplayname-method.md) method.</span></span>  
  
 [<span data-ttu-id="f72b5-111">ASM_NAME 列舉</span><span class="sxs-lookup"><span data-stu-id="f72b5-111">ASM_NAME Enumeration</span></span>](../../../../docs/framework/unmanaged-api/fusion/asm-name-enumeration.md)  
 <span data-ttu-id="f72b5-112">表示版本、 組建、 文化特性、 簽章，以及等等，將會擷取或設定其屬性的組件[IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)方法。</span><span class="sxs-lookup"><span data-stu-id="f72b5-112">Indicates the version, build, culture, signature, and so on, of the assembly whose properties will be retrieved or set by [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) methods.</span></span>  
  
 [<span data-ttu-id="f72b5-113">AssemblyComparisonResult 列舉</span><span class="sxs-lookup"><span data-stu-id="f72b5-113">AssemblyComparisonResult Enumeration</span></span>](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md)  
 <span data-ttu-id="f72b5-114">指出兩個組件識別是否相等由[CompareAssemblyIdentity](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="f72b5-114">Indicates the equivalence of two assembly identities, as determined by the [CompareAssemblyIdentity](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md) function.</span></span>  
  
 [<span data-ttu-id="f72b5-115">CREATE_ASM_NAME_OBJ_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="f72b5-115">CREATE_ASM_NAME_OBJ_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/fusion/create-asm-name-obj-flags-enumeration.md)  
 <span data-ttu-id="f72b5-116">指定的屬性`IAssemblyName`物件來建構時[CreateAssemblyNameObject](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="f72b5-116">Specifies the attributes of an `IAssemblyName` object when it is constructed by the [CreateAssemblyNameObject](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md) function.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f72b5-117">相關章節</span><span class="sxs-lookup"><span data-stu-id="f72b5-117">Related Sections</span></span>  
 [<span data-ttu-id="f72b5-118">融合介面</span><span class="sxs-lookup"><span data-stu-id="f72b5-118">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
  
 [<span data-ttu-id="f72b5-119">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="f72b5-119">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)  
  
 [<span data-ttu-id="f72b5-120">融合結構</span><span class="sxs-lookup"><span data-stu-id="f72b5-120">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
