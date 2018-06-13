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
ms.openlocfilehash: b11cf0fadc9142ee291115cf9f0d84e6429834fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455113"
---
# <a name="imethodmalloc-interface"></a><span data-ttu-id="6e533-102">IMethodMalloc 介面</span><span class="sxs-lookup"><span data-stu-id="6e533-102">IMethodMalloc Interface</span></span>
<span data-ttu-id="6e533-103">提供方法來為新的 Microsoft intermediate language (MSIL) 函式主體配置記憶體。</span><span class="sxs-lookup"><span data-stu-id="6e533-103">Provides a method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6e533-104">`IMethodMalloc`介面是簡單的記憶體配置器。</span><span class="sxs-lookup"><span data-stu-id="6e533-104">The `IMethodMalloc` interface is a simple memory allocator.</span></span> <span data-ttu-id="6e533-105">它可讓您配置記憶體，但不是將它釋放。</span><span class="sxs-lookup"><span data-stu-id="6e533-105">It allows you to allocate memory, but not to free it.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6e533-106">方法</span><span class="sxs-lookup"><span data-stu-id="6e533-106">Methods</span></span>  
  
|<span data-ttu-id="6e533-107">方法</span><span class="sxs-lookup"><span data-stu-id="6e533-107">Method</span></span>|<span data-ttu-id="6e533-108">描述</span><span class="sxs-lookup"><span data-stu-id="6e533-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6e533-109">Alloc 方法</span><span class="sxs-lookup"><span data-stu-id="6e533-109">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)|<span data-ttu-id="6e533-110">嘗試為新的 MSIL 函式主體配置指定的記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="6e533-110">Attempts to allocate a specified amount of memory for a new MSIL function body.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e533-111">備註</span><span class="sxs-lookup"><span data-stu-id="6e533-111">Remarks</span></span>  
 <span data-ttu-id="6e533-112">每個配置器為特定模組，並確保函式主體會在正的模組基底位移。</span><span class="sxs-lookup"><span data-stu-id="6e533-112">Each allocator is module-specific and ensures that the function body will be at a positive offset from the base of the module.</span></span> <span data-ttu-id="6e533-113">以上的模組基底的記憶體可以珍貴，因此配置器應該用來只針對函式主體配置記憶體。</span><span class="sxs-lookup"><span data-stu-id="6e533-113">Memory above the base of a module can be precious, so the allocator should be used to allocate memory only for a function body.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e533-114">需求</span><span class="sxs-lookup"><span data-stu-id="6e533-114">Requirements</span></span>  
 <span data-ttu-id="6e533-115">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6e533-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e533-116">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6e533-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6e533-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6e533-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e533-118">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e533-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e533-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e533-119">See Also</span></span>  
 [<span data-ttu-id="6e533-120">分析介面</span><span class="sxs-lookup"><span data-stu-id="6e533-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
