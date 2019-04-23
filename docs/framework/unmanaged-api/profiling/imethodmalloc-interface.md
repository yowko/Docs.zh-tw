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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ee825da1f3f0fd72a3b47b48783f0f344af99b65
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59077765"
---
# <a name="imethodmalloc-interface"></a><span data-ttu-id="63c60-102">IMethodMalloc 介面</span><span class="sxs-lookup"><span data-stu-id="63c60-102">IMethodMalloc Interface</span></span>
<span data-ttu-id="63c60-103">提供方法來為新的 Microsoft intermediate language (MSIL) 函式主體配置記憶體。</span><span class="sxs-lookup"><span data-stu-id="63c60-103">Provides a method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="63c60-104">`IMethodMalloc`介面是簡單的記憶體配置器。</span><span class="sxs-lookup"><span data-stu-id="63c60-104">The `IMethodMalloc` interface is a simple memory allocator.</span></span> <span data-ttu-id="63c60-105">它可讓您配置記憶體，但不是能釋放它。</span><span class="sxs-lookup"><span data-stu-id="63c60-105">It allows you to allocate memory, but not to free it.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="63c60-106">方法</span><span class="sxs-lookup"><span data-stu-id="63c60-106">Methods</span></span>  
  
|<span data-ttu-id="63c60-107">方法</span><span class="sxs-lookup"><span data-stu-id="63c60-107">Method</span></span>|<span data-ttu-id="63c60-108">描述</span><span class="sxs-lookup"><span data-stu-id="63c60-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="63c60-109">Alloc 方法</span><span class="sxs-lookup"><span data-stu-id="63c60-109">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)|<span data-ttu-id="63c60-110">嘗試為新的 MSIL 函式主體配置指定的記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="63c60-110">Attempts to allocate a specified amount of memory for a new MSIL function body.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63c60-111">備註</span><span class="sxs-lookup"><span data-stu-id="63c60-111">Remarks</span></span>  
 <span data-ttu-id="63c60-112">每個配置器為特定模組，並確保函式主體會從模組的基底的正面位移。</span><span class="sxs-lookup"><span data-stu-id="63c60-112">Each allocator is module-specific and ensures that the function body will be at a positive offset from the base of the module.</span></span> <span data-ttu-id="63c60-113">以上的模組基底的記憶體可能寶貴，因此配置器應該用來只為函式主體配置記憶體。</span><span class="sxs-lookup"><span data-stu-id="63c60-113">Memory above the base of a module can be precious, so the allocator should be used to allocate memory only for a function body.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63c60-114">需求</span><span class="sxs-lookup"><span data-stu-id="63c60-114">Requirements</span></span>  
 <span data-ttu-id="63c60-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="63c60-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63c60-116">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="63c60-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="63c60-117">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="63c60-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63c60-118">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63c60-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63c60-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63c60-119">See also</span></span>

- [<span data-ttu-id="63c60-120">分析介面</span><span class="sxs-lookup"><span data-stu-id="63c60-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
