---
title: "IMethodMalloc 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMethodMalloc
api_location: mscorwks.dll
api_type: COM
f1_keywords: IMethodMalloc
helpviewer_keywords: IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8c8ab5dc-557c-473a-82f2-6e403eca7dac
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1941a46a60219d9dd56d162f89baf268f220c102
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imethodmalloc-interface"></a><span data-ttu-id="da11d-102">IMethodMalloc 介面</span><span class="sxs-lookup"><span data-stu-id="da11d-102">IMethodMalloc Interface</span></span>
<span data-ttu-id="da11d-103">提供方法來為新的 Microsoft intermediate language (MSIL) 函式主體配置記憶體。</span><span class="sxs-lookup"><span data-stu-id="da11d-103">Provides a method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da11d-104">`IMethodMalloc`介面是簡單的記憶體配置器。</span><span class="sxs-lookup"><span data-stu-id="da11d-104">The `IMethodMalloc` interface is a simple memory allocator.</span></span> <span data-ttu-id="da11d-105">它可讓您配置記憶體，但不是將它釋放。</span><span class="sxs-lookup"><span data-stu-id="da11d-105">It allows you to allocate memory, but not to free it.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="da11d-106">方法</span><span class="sxs-lookup"><span data-stu-id="da11d-106">Methods</span></span>  
  
|<span data-ttu-id="da11d-107">方法</span><span class="sxs-lookup"><span data-stu-id="da11d-107">Method</span></span>|<span data-ttu-id="da11d-108">描述</span><span class="sxs-lookup"><span data-stu-id="da11d-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="da11d-109">Alloc 方法</span><span class="sxs-lookup"><span data-stu-id="da11d-109">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)|<span data-ttu-id="da11d-110">嘗試為新的 MSIL 函式主體配置指定的記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="da11d-110">Attempts to allocate a specified amount of memory for a new MSIL function body.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da11d-111">備註</span><span class="sxs-lookup"><span data-stu-id="da11d-111">Remarks</span></span>  
 <span data-ttu-id="da11d-112">每個配置器為特定模組，並確保函式主體會在正的模組基底位移。</span><span class="sxs-lookup"><span data-stu-id="da11d-112">Each allocator is module-specific and ensures that the function body will be at a positive offset from the base of the module.</span></span> <span data-ttu-id="da11d-113">以上的模組基底的記憶體可以珍貴，因此配置器應該用來只針對函式主體配置記憶體。</span><span class="sxs-lookup"><span data-stu-id="da11d-113">Memory above the base of a module can be precious, so the allocator should be used to allocate memory only for a function body.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da11d-114">需求</span><span class="sxs-lookup"><span data-stu-id="da11d-114">Requirements</span></span>  
 <span data-ttu-id="da11d-115">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="da11d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da11d-116">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="da11d-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="da11d-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="da11d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da11d-118">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da11d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da11d-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="da11d-119">See Also</span></span>  
 [<span data-ttu-id="da11d-120">分析介面</span><span class="sxs-lookup"><span data-stu-id="da11d-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
