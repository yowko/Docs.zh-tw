---
title: "ICorProfilerInfo3::GetThreadStaticAddress2 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.GetThreadStaticAddress2 Method
api_location: Mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::GetThreadStaticAddress2
helpviewer_keywords:
- ICorProfilerInfo3::GetThreadStaticAddress2 method [.NET Framework profiling]
- GetThreadStaticAddress2 method [.NET Framework profiling]
ms.assetid: a9608861-ae64-4467-8a73-be05ad34beac
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 136b68f886899430dbfc672b8e3e534d093bc617
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo3getthreadstaticaddress2-method"></a><span data-ttu-id="120dd-102">ICorProfilerInfo3::GetThreadStaticAddress2 方法</span><span class="sxs-lookup"><span data-stu-id="120dd-102">ICorProfilerInfo3::GetThreadStaticAddress2 Method</span></span>
<span data-ttu-id="120dd-103">取得指定執行緒靜態欄位的位址，這位於指定之執行緒和應用程式定義域的範圍內。</span><span class="sxs-lookup"><span data-stu-id="120dd-103">Gets the address of the specified thread-static field that is in the scope of the specified thread and application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="120dd-104">語法</span><span class="sxs-lookup"><span data-stu-id="120dd-104">Syntax</span></span>  
  
```  
HRESULT GetThreadStaticAddress2(  
                [in] ClassID classId,  
                [in] mdFieldDef fieldToken,  
                [in] AppDomainID appDomainId,  
                [in] ThreadID threadId,  
                [out] void **ppAddress);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="120dd-105">參數</span><span class="sxs-lookup"><span data-stu-id="120dd-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="120dd-106">[in]包含要求的執行緒靜態欄位的類別識別碼。</span><span class="sxs-lookup"><span data-stu-id="120dd-106">[in] The ID of the class that contains the requested thread-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="120dd-107">[in]要求的執行緒靜態欄位中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="120dd-107">[in] The metadata token for the requested thread-static field.</span></span>  
  
 `appDomainId`  
 <span data-ttu-id="120dd-108">[in] 應用程式定義域的 ID。</span><span class="sxs-lookup"><span data-stu-id="120dd-108">[in] The ID of the application domain.</span></span>  
  
 `threadId`  
 <span data-ttu-id="120dd-109">[in]要求的靜態欄位的資料範圍的執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="120dd-109">[in] The ID of the thread that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="120dd-110">[out]內指定執行緒靜態欄位的位址指標。</span><span class="sxs-lookup"><span data-stu-id="120dd-110">[out] A pointer to the address of the static field that is within the specified thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="120dd-111">備註</span><span class="sxs-lookup"><span data-stu-id="120dd-111">Remarks</span></span>  
 <span data-ttu-id="120dd-112">`GetThreadStaticAddress2`方法可能會傳回下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="120dd-112">The `GetThreadStaticAddress2` method may return one of the following:</span></span>  
  
-   <span data-ttu-id="120dd-113">如果在指定的靜態欄位指派指定的內容中的位址 CORPROF_E_DATAINCOMPLETE HRESULT。</span><span class="sxs-lookup"><span data-stu-id="120dd-113">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
-   <span data-ttu-id="120dd-114">可能會在記憶體回收堆積中之物件的位址。</span><span class="sxs-lookup"><span data-stu-id="120dd-114">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="120dd-115">這些位址可能會變成記憶體回收之後, 無效，所以記憶體回收之後, 程式碼剖析工具不應該假設都有效。</span><span class="sxs-lookup"><span data-stu-id="120dd-115">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="120dd-116">類別的類別建構函式完成之前，`GetThreadStaticAddress2`會針對其所有靜態欄位，傳回 CORPROF_E_DATAINCOMPLETE，雖然部分的靜態欄位可能已經初始化，而且為根建立記憶體回收物件。</span><span class="sxs-lookup"><span data-stu-id="120dd-116">Before a class’s class constructor is completed, `GetThreadStaticAddress2` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
 <span data-ttu-id="120dd-117">[Icorprofilerinfo2:: Getthreadstaticaddress](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadstaticaddress-method.md)方法很類似`GetThreadStaticAddress2`方法，但是不接受的應用程式網域引數。</span><span class="sxs-lookup"><span data-stu-id="120dd-117">The [ICorProfilerInfo2::GetThreadStaticAddress](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadstaticaddress-method.md) method is similar to the `GetThreadStaticAddress2` method, but does not accept an application domain argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="120dd-118">需求</span><span class="sxs-lookup"><span data-stu-id="120dd-118">Requirements</span></span>  
 <span data-ttu-id="120dd-119">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="120dd-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="120dd-120">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="120dd-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="120dd-121">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="120dd-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="120dd-122">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="120dd-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="120dd-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="120dd-123">See Also</span></span>  
 [<span data-ttu-id="120dd-124">ICorProfilerInfo3 介面</span><span class="sxs-lookup"><span data-stu-id="120dd-124">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="120dd-125">分析介面</span><span class="sxs-lookup"><span data-stu-id="120dd-125">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="120dd-126">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="120dd-126">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
