---
title: 融合列舉
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged enumerations [.NET Framework], fusion
- fusion enumerations [.NET Framework]
- enumerations [.NET Framework fusion]
ms.assetid: 5817b4bc-b0ba-4b2f-a11c-a03dd8cb8f84
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ffee9084bd07882079b2d44de25391f2491a1520
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61936457"
---
# <a name="fusion-enumerations"></a><span data-ttu-id="4f587-102">融合列舉</span><span class="sxs-lookup"><span data-stu-id="4f587-102">Fusion Enumerations</span></span>
<span data-ttu-id="4f587-103">本章節描述融合 API 使用的 unmanaged 的列舉。</span><span class="sxs-lookup"><span data-stu-id="4f587-103">This section describes the unmanaged enumerations that the fusion API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4f587-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="4f587-104">In This Section</span></span>  
 [<span data-ttu-id="4f587-105">ASM_CACHE_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="4f587-105">ASM_CACHE_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md)  
 <span data-ttu-id="4f587-106">指出所表示之組件的來源[IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)在全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="4f587-106">Indicates the source of an assembly represented by [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md) in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="4f587-107">ASM_CMP_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="4f587-107">ASM_CMP_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/fusion/asm-cmp-flags-enumeration.md)  
 <span data-ttu-id="4f587-108">表示版本、 組建、 文化特性、 簽章，依此類推，所要比較的兩個組件的[iassemblyname:: Isequal](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-isequal-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="4f587-108">Indicates the version, build, culture, signature, and so on, of two assemblies to be compared by the [IAssemblyName::IsEqual](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-isequal-method.md) method.</span></span>  
  
 [<span data-ttu-id="4f587-109">ASM_DISPLAY_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="4f587-109">ASM_DISPLAY_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/fusion/asm-display-flags-enumeration.md)  
 <span data-ttu-id="4f587-110">表示版本、 組建、 文化特性、 簽章，依此類推，會擷取顯示名稱的組件[iassemblyname:: Getdisplayname](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getdisplayname-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="4f587-110">Indicates the version, build, culture, signature, and so on, of the assembly whose display name will be retrieved by the [IAssemblyName::GetDisplayName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getdisplayname-method.md) method.</span></span>  
  
 [<span data-ttu-id="4f587-111">ASM_NAME 列舉</span><span class="sxs-lookup"><span data-stu-id="4f587-111">ASM_NAME Enumeration</span></span>](../../../../docs/framework/unmanaged-api/fusion/asm-name-enumeration.md)  
 <span data-ttu-id="4f587-112">表示版本、 組建、 文化特性、 簽章，依此類推，會擷取或設定其屬性之組件的[IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)方法。</span><span class="sxs-lookup"><span data-stu-id="4f587-112">Indicates the version, build, culture, signature, and so on, of the assembly whose properties will be retrieved or set by [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) methods.</span></span>  
  
 [<span data-ttu-id="4f587-113">AssemblyComparisonResult 列舉</span><span class="sxs-lookup"><span data-stu-id="4f587-113">AssemblyComparisonResult Enumeration</span></span>](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md)  
 <span data-ttu-id="4f587-114">表示之兩個組件身分識別，對等，由[CompareAssemblyIdentity](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="4f587-114">Indicates the equivalence of two assembly identities, as determined by the [CompareAssemblyIdentity](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md) function.</span></span>  
  
 [<span data-ttu-id="4f587-115">CREATE_ASM_NAME_OBJ_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="4f587-115">CREATE_ASM_NAME_OBJ_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/fusion/create-asm-name-obj-flags-enumeration.md)  
 <span data-ttu-id="4f587-116">指定的屬性`IAssemblyName`物件會藉由在建構時[CreateAssemblyNameObject](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="4f587-116">Specifies the attributes of an `IAssemblyName` object when it is constructed by the [CreateAssemblyNameObject](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md) function.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4f587-117">相關章節</span><span class="sxs-lookup"><span data-stu-id="4f587-117">Related Sections</span></span>  
 [<span data-ttu-id="4f587-118">融合介面</span><span class="sxs-lookup"><span data-stu-id="4f587-118">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
  
 [<span data-ttu-id="4f587-119">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="4f587-119">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)  
  
 [<span data-ttu-id="4f587-120">融合結構</span><span class="sxs-lookup"><span data-stu-id="4f587-120">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
