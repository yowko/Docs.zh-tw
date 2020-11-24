---
title: 融合列舉
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged enumerations [.NET Framework], fusion
- fusion enumerations [.NET Framework]
- enumerations [.NET Framework fusion]
ms.assetid: 5817b4bc-b0ba-4b2f-a11c-a03dd8cb8f84
ms.openlocfilehash: c014d6fcf8ac34ebc82b43214a358039d8c28907
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688753"
---
# <a name="fusion-enumerations"></a><span data-ttu-id="67187-102">融合列舉</span><span class="sxs-lookup"><span data-stu-id="67187-102">Fusion Enumerations</span></span>

<span data-ttu-id="67187-103">本節說明融合 API 所使用的非受控列舉。</span><span class="sxs-lookup"><span data-stu-id="67187-103">This section describes the unmanaged enumerations that the fusion API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="67187-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="67187-104">In This Section</span></span>  

 [<span data-ttu-id="67187-105">ASM_CACHE_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="67187-105">ASM_CACHE_FLAGS Enumeration</span></span>](asm-cache-flags-enumeration.md)  
 <span data-ttu-id="67187-106">指出全域組件快取中 [IAssemblyCacheItem](iassemblycacheitem-interface.md) 所代表之元件的來源。</span><span class="sxs-lookup"><span data-stu-id="67187-106">Indicates the source of an assembly represented by [IAssemblyCacheItem](iassemblycacheitem-interface.md) in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="67187-107">ASM_CMP_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="67187-107">ASM_CMP_FLAGS Enumeration</span></span>](asm-cmp-flags-enumeration.md)  
 <span data-ttu-id="67187-108">指出 [IAssemblyName：： IsEqual](iassemblyname-isequal-method.md) 方法要比較之兩個元件的版本、組建、文化特性、簽章等等。</span><span class="sxs-lookup"><span data-stu-id="67187-108">Indicates the version, build, culture, signature, and so on, of two assemblies to be compared by the [IAssemblyName::IsEqual](iassemblyname-isequal-method.md) method.</span></span>  
  
 [<span data-ttu-id="67187-109">ASM_DISPLAY_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="67187-109">ASM_DISPLAY_FLAGS Enumeration</span></span>](asm-display-flags-enumeration.md)  
 <span data-ttu-id="67187-110">指出 [IAssemblyName：： GetDisplayName](iassemblyname-getdisplayname-method.md) 方法將抓取其顯示名稱的元件版本、組建、文化特性、簽章等等。</span><span class="sxs-lookup"><span data-stu-id="67187-110">Indicates the version, build, culture, signature, and so on, of the assembly whose display name will be retrieved by the [IAssemblyName::GetDisplayName](iassemblyname-getdisplayname-method.md) method.</span></span>  
  
 [<span data-ttu-id="67187-111">ASM_NAME 列舉</span><span class="sxs-lookup"><span data-stu-id="67187-111">ASM_NAME Enumeration</span></span>](asm-name-enumeration.md)  
 <span data-ttu-id="67187-112">表示元件的版本、組建、文化特性、簽章等，其屬性將由 [IAssemblyName](iassemblyname-interface.md) 方法抓取或設定。</span><span class="sxs-lookup"><span data-stu-id="67187-112">Indicates the version, build, culture, signature, and so on, of the assembly whose properties will be retrieved or set by [IAssemblyName](iassemblyname-interface.md) methods.</span></span>  
  
 [<span data-ttu-id="67187-113">AssemblyComparisonResult 列舉</span><span class="sxs-lookup"><span data-stu-id="67187-113">AssemblyComparisonResult Enumeration</span></span>](assemblycomparisonresult-enumeration.md)  
 <span data-ttu-id="67187-114">指出兩個元件身分識別的相等（由 [CompareAssemblyIdentity](compareassemblyidentity-function.md) 函式所決定）。</span><span class="sxs-lookup"><span data-stu-id="67187-114">Indicates the equivalence of two assembly identities, as determined by the [CompareAssemblyIdentity](compareassemblyidentity-function.md) function.</span></span>  
  
 [<span data-ttu-id="67187-115">CREATE_ASM_NAME_OBJ_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="67187-115">CREATE_ASM_NAME_OBJ_FLAGS Enumeration</span></span>](create-asm-name-obj-flags-enumeration.md)  
 <span data-ttu-id="67187-116">指定當 CreateAssemblyNameObject 函式所建立 `IAssemblyName` 之物件的屬性時[CreateAssemblyNameObject](createassemblynameobject-function.md) 。</span><span class="sxs-lookup"><span data-stu-id="67187-116">Specifies the attributes of an `IAssemblyName` object when it is constructed by the [CreateAssemblyNameObject](createassemblynameobject-function.md) function.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="67187-117">相關章節</span><span class="sxs-lookup"><span data-stu-id="67187-117">Related Sections</span></span>  

 [<span data-ttu-id="67187-118">融合介面</span><span class="sxs-lookup"><span data-stu-id="67187-118">Fusion Interfaces</span></span>](fusion-interfaces.md)  
  
 [<span data-ttu-id="67187-119">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="67187-119">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)  
  
 [<span data-ttu-id="67187-120">融合結構</span><span class="sxs-lookup"><span data-stu-id="67187-120">Fusion Structures</span></span>](fusion-structures.md)
