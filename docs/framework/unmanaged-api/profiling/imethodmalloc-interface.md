---
title: IMethodMalloc 介面
ms.date: 03/30/2017
api_name:
- IMethodMalloc
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- IMethodMalloc
helpviewer_keywords:
- IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8c8ab5dc-557c-473a-82f2-6e403eca7dac
topic_type:
- apiref
ms.openlocfilehash: 8eccdba75b59df505ae72d74cfcd2bc83de2b45a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688168"
---
# <a name="imethodmalloc-interface"></a><span data-ttu-id="459fb-102">IMethodMalloc 介面</span><span class="sxs-lookup"><span data-stu-id="459fb-102">IMethodMalloc Interface</span></span>

<span data-ttu-id="459fb-103">提供方法，為新的 Microsoft 中繼語言 (MSIL) 函式主體中配置記憶體。</span><span class="sxs-lookup"><span data-stu-id="459fb-103">Provides a method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="459fb-104">`IMethodMalloc`介面是簡單的記憶體配置器。</span><span class="sxs-lookup"><span data-stu-id="459fb-104">The `IMethodMalloc` interface is a simple memory allocator.</span></span> <span data-ttu-id="459fb-105">它可讓您配置記憶體，但無法釋放記憶體。</span><span class="sxs-lookup"><span data-stu-id="459fb-105">It allows you to allocate memory, but not to free it.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="459fb-106">方法</span><span class="sxs-lookup"><span data-stu-id="459fb-106">Methods</span></span>  
  
|<span data-ttu-id="459fb-107">方法</span><span class="sxs-lookup"><span data-stu-id="459fb-107">Method</span></span>|<span data-ttu-id="459fb-108">描述</span><span class="sxs-lookup"><span data-stu-id="459fb-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="459fb-109">Alloc 方法</span><span class="sxs-lookup"><span data-stu-id="459fb-109">Alloc Method</span></span>](imethodmalloc-alloc-method.md)|<span data-ttu-id="459fb-110">嘗試為新的 MSIL 函數主體配置指定的記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="459fb-110">Attempts to allocate a specified amount of memory for a new MSIL function body.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="459fb-111">備註</span><span class="sxs-lookup"><span data-stu-id="459fb-111">Remarks</span></span>  

 <span data-ttu-id="459fb-112">每個配置器都是模組專屬的，可確保函式主體會與模組基底的正位移。</span><span class="sxs-lookup"><span data-stu-id="459fb-112">Each allocator is module-specific and ensures that the function body will be at a positive offset from the base of the module.</span></span> <span data-ttu-id="459fb-113">在模組基底之上的記憶體可能很寶貴，因此配置器只能用來配置函數主體的記憶體。</span><span class="sxs-lookup"><span data-stu-id="459fb-113">Memory above the base of a module can be precious, so the allocator should be used to allocate memory only for a function body.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="459fb-114">需求</span><span class="sxs-lookup"><span data-stu-id="459fb-114">Requirements</span></span>  

 <span data-ttu-id="459fb-115">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="459fb-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="459fb-116">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="459fb-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="459fb-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="459fb-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="459fb-118">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="459fb-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="459fb-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="459fb-119">See also</span></span>

- [<span data-ttu-id="459fb-120">分析介面</span><span class="sxs-lookup"><span data-stu-id="459fb-120">Profiling Interfaces</span></span>](profiling-interfaces.md)
