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
ms.openlocfilehash: 3f840154d472dbcea7dfef7ba93e38c80b836734
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447556"
---
# <a name="imethodmalloc-interface"></a><span data-ttu-id="0f85b-102">IMethodMalloc 介面</span><span class="sxs-lookup"><span data-stu-id="0f85b-102">IMethodMalloc Interface</span></span>
<span data-ttu-id="0f85b-103">提供方法來為新的 Microsoft 中繼語言（MSIL）函數主體配置記憶體。</span><span class="sxs-lookup"><span data-stu-id="0f85b-103">Provides a method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0f85b-104">`IMethodMalloc` 介面是簡單的記憶體配置器。</span><span class="sxs-lookup"><span data-stu-id="0f85b-104">The `IMethodMalloc` interface is a simple memory allocator.</span></span> <span data-ttu-id="0f85b-105">它可讓您配置記憶體，但不能釋放它。</span><span class="sxs-lookup"><span data-stu-id="0f85b-105">It allows you to allocate memory, but not to free it.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0f85b-106">方法</span><span class="sxs-lookup"><span data-stu-id="0f85b-106">Methods</span></span>  
  
|<span data-ttu-id="0f85b-107">方法</span><span class="sxs-lookup"><span data-stu-id="0f85b-107">Method</span></span>|<span data-ttu-id="0f85b-108">描述</span><span class="sxs-lookup"><span data-stu-id="0f85b-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0f85b-109">Alloc 方法</span><span class="sxs-lookup"><span data-stu-id="0f85b-109">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)|<span data-ttu-id="0f85b-110">嘗試為新的 MSIL 函數主體配置指定的記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="0f85b-110">Attempts to allocate a specified amount of memory for a new MSIL function body.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f85b-111">備註</span><span class="sxs-lookup"><span data-stu-id="0f85b-111">Remarks</span></span>  
 <span data-ttu-id="0f85b-112">每個配置器都是模組特有的，並可確保函式主體會位於模組基底的正位移。</span><span class="sxs-lookup"><span data-stu-id="0f85b-112">Each allocator is module-specific and ensures that the function body will be at a positive offset from the base of the module.</span></span> <span data-ttu-id="0f85b-113">高於模組基底的記憶體可能非常寶貴，因此應該使用配置器只為函式主體配置記憶體。</span><span class="sxs-lookup"><span data-stu-id="0f85b-113">Memory above the base of a module can be precious, so the allocator should be used to allocate memory only for a function body.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f85b-114">需求</span><span class="sxs-lookup"><span data-stu-id="0f85b-114">Requirements</span></span>  
 <span data-ttu-id="0f85b-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0f85b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f85b-116">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0f85b-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0f85b-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0f85b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0f85b-118">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f85b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f85b-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="0f85b-119">See also</span></span>

- [<span data-ttu-id="0f85b-120">分析介面</span><span class="sxs-lookup"><span data-stu-id="0f85b-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
