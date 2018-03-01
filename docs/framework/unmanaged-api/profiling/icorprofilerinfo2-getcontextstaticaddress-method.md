---
title: "ICorProfilerInfo2::GetContextStaticAddress 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerInfo2.GetContextStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetContextStaticAddress
helpviewer_keywords:
- GetContextStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetContextStaticAddress method [.NET Framework profiling]
ms.assetid: 2b374116-0972-416a-8cf5-79213129be9a
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e92435927203bb2a75ff92d883470832126da080
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getcontextstaticaddress-method"></a><span data-ttu-id="3bf88-102">ICorProfilerInfo2::GetContextStaticAddress 方法</span><span class="sxs-lookup"><span data-stu-id="3bf88-102">ICorProfilerInfo2::GetContextStaticAddress Method</span></span>
<span data-ttu-id="3bf88-103">取得位於指定之內容的範圍內指定 context 靜態欄位的位址。</span><span class="sxs-lookup"><span data-stu-id="3bf88-103">Gets the address for the specified context-static field that is in the scope of the specified context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bf88-104">語法</span><span class="sxs-lookup"><span data-stu-id="3bf88-104">Syntax</span></span>  
  
```  
HRESULT GetContextStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] ContextID contextId,  
    [out] void **ppAddress);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3bf88-105">參數</span><span class="sxs-lookup"><span data-stu-id="3bf88-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="3bf88-106">[in]包含要求的內容靜態欄位的類別識別碼。</span><span class="sxs-lookup"><span data-stu-id="3bf88-106">[in] The ID of the class that contains the requested context-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="3bf88-107">[in]要求的內容靜態欄位中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="3bf88-107">[in] The metadata token for the requested context-static field.</span></span>  
  
 `contextId`  
 <span data-ttu-id="3bf88-108">[in]要求的內容靜態欄位的資料範圍的內容識別碼。</span><span class="sxs-lookup"><span data-stu-id="3bf88-108">[in] The ID of the context that is the scope for the requested context-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="3bf88-109">[out]會在指定的內容中的靜態欄位的位址指標。</span><span class="sxs-lookup"><span data-stu-id="3bf88-109">[out] A pointer to the address of the static field that is within the specified context.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3bf88-110">備註</span><span class="sxs-lookup"><span data-stu-id="3bf88-110">Remarks</span></span>  
 <span data-ttu-id="3bf88-111">`GetContextStaticAddress`方法可能會傳回下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="3bf88-111">The `GetContextStaticAddress` method may return one of the following:</span></span>  
  
-   <span data-ttu-id="3bf88-112">如果在指定的靜態欄位指派指定的內容中的位址 CORPROF_E_DATAINCOMPLETE HRESULT。</span><span class="sxs-lookup"><span data-stu-id="3bf88-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
-   <span data-ttu-id="3bf88-113">可能會在記憶體回收堆積中之物件的位址。</span><span class="sxs-lookup"><span data-stu-id="3bf88-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="3bf88-114">這些位址可能會變成記憶體回收之後, 無效，所以記憶體回收之後, 程式碼剖析工具不應該假設都有效。</span><span class="sxs-lookup"><span data-stu-id="3bf88-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="3bf88-115">類別的類別建構函式完成之前，`GetContextStaticAddress`會針對其所有靜態欄位，傳回 CORPROF_E_DATAINCOMPLETE，雖然部分的靜態欄位可能已經初始化，而且為根建立記憶體回收物件。</span><span class="sxs-lookup"><span data-stu-id="3bf88-115">Before a class’s class constructor is completed, `GetContextStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3bf88-116">需求</span><span class="sxs-lookup"><span data-stu-id="3bf88-116">Requirements</span></span>  
 <span data-ttu-id="3bf88-117">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3bf88-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3bf88-118">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3bf88-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3bf88-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3bf88-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3bf88-120">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3bf88-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bf88-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="3bf88-121">See Also</span></span>  
 [<span data-ttu-id="3bf88-122">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="3bf88-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="3bf88-123">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="3bf88-123">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
