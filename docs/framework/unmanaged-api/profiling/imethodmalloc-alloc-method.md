---
title: "IMethodMalloc::Alloc 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMethodMalloc.Alloc
api_location: mscorwks.dll
api_type: COM
f1_keywords: IMethodMalloc::Alloc
helpviewer_keywords:
- IMethodMalloc::Alloc method [.NET Framework profiling]
- Alloc method, IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8653bd4c-2290-43d2-a3e1-cbbd50033f4f
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 26998e8b2e8648b4fb175f188540e7bc33c580c2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imethodmallocalloc-method"></a><span data-ttu-id="b0754-102">IMethodMalloc::Alloc 方法</span><span class="sxs-lookup"><span data-stu-id="b0754-102">IMethodMalloc::Alloc Method</span></span>
<span data-ttu-id="b0754-103">嘗試為新的 Microsoft intermediate language (MSIL) 函式主體配置指定的記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="b0754-103">Attempts to allocate a specified amount of memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0754-104">語法</span><span class="sxs-lookup"><span data-stu-id="b0754-104">Syntax</span></span>  
  
```  
PVOID Alloc (  
    [in] ULONG   cb  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b0754-105">參數</span><span class="sxs-lookup"><span data-stu-id="b0754-105">Parameters</span></span>  
 `cb`  
 <span data-ttu-id="b0754-106">[in]方法主體所配置的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="b0754-106">[in] The number of bytes to allocate for the method body.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0754-107">備註</span><span class="sxs-lookup"><span data-stu-id="b0754-107">Remarks</span></span>  
 <span data-ttu-id="b0754-108">配置的記憶體會開始在大於這個配置器相關聯之模組的基底位址的位址。</span><span class="sxs-lookup"><span data-stu-id="b0754-108">The allocated memory will begin at an address greater than the base address of the module that is associated with this allocator.</span></span> <span data-ttu-id="b0754-109">換句話說，每個配置器建立特定的模組，並會嘗試從其基底的位址配置記憶體的正數的位移。</span><span class="sxs-lookup"><span data-stu-id="b0754-109">In other words, each allocator is created for a particular module, and will attempt to allocate memory at a positive offset from its base address.</span></span> <span data-ttu-id="b0754-110">如果`Alloc`無法配置所要求的位元組在大於模組的基底位址的位址數目會傳回 E_OUTOFMEMORY，不論實際可用的記憶體空間的數量。</span><span class="sxs-lookup"><span data-stu-id="b0754-110">If `Alloc` fails to allocate the requested number of bytes at an address greater than the base address of the module, it returns E_OUTOFMEMORY, regardless of the actual amount of memory space available.</span></span>  
  
 <span data-ttu-id="b0754-111">`Alloc`方法應用於搭配[icorprofilerinfo:: Setilfunctionbody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="b0754-111">The `Alloc` method should be used in conjunction with the [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0754-112">需求</span><span class="sxs-lookup"><span data-stu-id="b0754-112">Requirements</span></span>  
 <span data-ttu-id="b0754-113">**平台：** WindSee[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b0754-113">**Platforms:** WindSee [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0754-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b0754-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b0754-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b0754-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0754-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0754-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0754-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="b0754-117">See Also</span></span>  
 [<span data-ttu-id="b0754-118">IMethodMalloc 介面</span><span class="sxs-lookup"><span data-stu-id="b0754-118">IMethodMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)
