---
title: "ICorProfilerInfo::SetILFunctionBody 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.SetILFunctionBody
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerInfo::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method [.NET Framework profiling]
ms.assetid: b159c712-00f4-4fc7-a990-40bf9f642e8f
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c44fa89ba66a306792f1ffed162447a6305a0347
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfosetilfunctionbody-method"></a><span data-ttu-id="755ee-102">ICorProfilerInfo::SetILFunctionBody 方法</span><span class="sxs-lookup"><span data-stu-id="755ee-102">ICorProfilerInfo::SetILFunctionBody Method</span></span>
<span data-ttu-id="755ee-103">取代指定的模組中的指定函式的主體。</span><span class="sxs-lookup"><span data-stu-id="755ee-103">Replaces the body of the specified function in the specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="755ee-104">語法</span><span class="sxs-lookup"><span data-stu-id="755ee-104">Syntax</span></span>  
  
```  
HRESULT SetILFunctionBody(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodid,  
    [in] LPCBYTE     pbNewILMethodHeader);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="755ee-105">參數</span><span class="sxs-lookup"><span data-stu-id="755ee-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="755ee-106">[in]此函式所在模組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="755ee-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `methodid`  
 <span data-ttu-id="755ee-107">[in]用來取代主體的函式語彙基元。</span><span class="sxs-lookup"><span data-stu-id="755ee-107">[in] The token of the function for which to replace the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="755ee-108">[in]函式的新標頭。</span><span class="sxs-lookup"><span data-stu-id="755ee-108">[in] The new header for the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="755ee-109">備註</span><span class="sxs-lookup"><span data-stu-id="755ee-109">Remarks</span></span>  
 <span data-ttu-id="755ee-110">`SetILFunctionBody`方法會取代函式的中繼資料中的相對虛擬位址，使其指向新的函式主體，然後調整所需的任何內部資料結構。</span><span class="sxs-lookup"><span data-stu-id="755ee-110">The `SetILFunctionBody` method replaces the relative virtual address of the function in the metadata so that it points to the new function body, and adjusts any internal data structures as required.</span></span>  
  
 <span data-ttu-id="755ee-111">`SetILFunctionBody`永遠不會在 just-in-time (JIT) 編譯器所編譯的函式上呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="755ee-111">The `SetILFunctionBody` method can be called on only those functions that have never been compiled by a just-in-time (JIT) compiler.</span></span>  
  
 <span data-ttu-id="755ee-112">使用[icorprofilerinfo:: Getilfunctionbodyallocator](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md)配置空間給新的方法，以確保緩衝區相容的方法。</span><span class="sxs-lookup"><span data-stu-id="755ee-112">Use the [ICorProfilerInfo::GetILFunctionBodyAllocator](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md) method to allocate space for the new method to ensure that the buffer is compatible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="755ee-113">需求</span><span class="sxs-lookup"><span data-stu-id="755ee-113">Requirements</span></span>  
 <span data-ttu-id="755ee-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="755ee-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="755ee-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="755ee-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="755ee-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="755ee-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="755ee-117">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="755ee-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="755ee-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="755ee-118">See Also</span></span>  
 [<span data-ttu-id="755ee-119">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="755ee-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
