---
title: ICorProfilerInfo3::GetThreadStaticAddress2 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetThreadStaticAddress2 Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetThreadStaticAddress2
helpviewer_keywords:
- ICorProfilerInfo3::GetThreadStaticAddress2 method [.NET Framework profiling]
- GetThreadStaticAddress2 method [.NET Framework profiling]
ms.assetid: a9608861-ae64-4467-8a73-be05ad34beac
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f62dadf4f21022f8f425596cf5957891ed39effe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59189179"
---
# <a name="icorprofilerinfo3getthreadstaticaddress2-method"></a><span data-ttu-id="ba8ce-102">ICorProfilerInfo3::GetThreadStaticAddress2 方法</span><span class="sxs-lookup"><span data-stu-id="ba8ce-102">ICorProfilerInfo3::GetThreadStaticAddress2 Method</span></span>
<span data-ttu-id="ba8ce-103">取得指定執行緒靜態欄位的位址，這位於指定之執行緒和應用程式定義域的範圍內。</span><span class="sxs-lookup"><span data-stu-id="ba8ce-103">Gets the address of the specified thread-static field that is in the scope of the specified thread and application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba8ce-104">語法</span><span class="sxs-lookup"><span data-stu-id="ba8ce-104">Syntax</span></span>  
  
```  
HRESULT GetThreadStaticAddress2(  
                [in] ClassID classId,  
                [in] mdFieldDef fieldToken,  
                [in] AppDomainID appDomainId,  
                [in] ThreadID threadId,  
                [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba8ce-105">參數</span><span class="sxs-lookup"><span data-stu-id="ba8ce-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="ba8ce-106">[in]包含要求的執行緒靜態欄位的類別識別碼。</span><span class="sxs-lookup"><span data-stu-id="ba8ce-106">[in] The ID of the class that contains the requested thread-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="ba8ce-107">[in]要求的執行緒靜態欄位的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="ba8ce-107">[in] The metadata token for the requested thread-static field.</span></span>  
  
 `appDomainId`  
 <span data-ttu-id="ba8ce-108">[in] 應用程式定義域的 ID。</span><span class="sxs-lookup"><span data-stu-id="ba8ce-108">[in] The ID of the application domain.</span></span>  
  
 `threadId`  
 <span data-ttu-id="ba8ce-109">[in]要求的靜態欄位的範圍的執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="ba8ce-109">[in] The ID of the thread that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="ba8ce-110">[out]位於指定的執行緒靜態欄位的位址指標。</span><span class="sxs-lookup"><span data-stu-id="ba8ce-110">[out] A pointer to the address of the static field that is within the specified thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba8ce-111">備註</span><span class="sxs-lookup"><span data-stu-id="ba8ce-111">Remarks</span></span>  
 <span data-ttu-id="ba8ce-112">`GetThreadStaticAddress2`方法可能會傳回下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="ba8ce-112">The `GetThreadStaticAddress2` method may return one of the following:</span></span>  
  
-   <span data-ttu-id="ba8ce-113">如果指定的靜態欄位尚未指派指定的內容中的地址 CORPROF_E_DATAINCOMPLETE HRESULT。</span><span class="sxs-lookup"><span data-stu-id="ba8ce-113">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
-   <span data-ttu-id="ba8ce-114">可能在記憶體回收堆積中物件的位址。</span><span class="sxs-lookup"><span data-stu-id="ba8ce-114">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="ba8ce-115">這些位址可能會變成無效記憶體回收之後，讓記憶體回收之後, 程式碼剖析工具不應該假設其有效。</span><span class="sxs-lookup"><span data-stu-id="ba8ce-115">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="ba8ce-116">類別的類別建構函式完成之前，`GetThreadStaticAddress2`雖然靜態欄位的一些可能已經初始化，將會傳回 CORPROF_E_DATAINCOMPLETE 所有其靜態欄位，及根廢棄項目集合物件。</span><span class="sxs-lookup"><span data-stu-id="ba8ce-116">Before a class’s class constructor is completed, `GetThreadStaticAddress2` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
 <span data-ttu-id="ba8ce-117">[ICorProfilerInfo2::GetThreadStaticAddress](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadstaticaddress-method.md)方式類似於`GetThreadStaticAddress2`方法，但不是接受應用程式網域引數。</span><span class="sxs-lookup"><span data-stu-id="ba8ce-117">The [ICorProfilerInfo2::GetThreadStaticAddress](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadstaticaddress-method.md) method is similar to the `GetThreadStaticAddress2` method, but does not accept an application domain argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba8ce-118">需求</span><span class="sxs-lookup"><span data-stu-id="ba8ce-118">Requirements</span></span>  
 <span data-ttu-id="ba8ce-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ba8ce-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba8ce-120">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ba8ce-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ba8ce-121">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ba8ce-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba8ce-122">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba8ce-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba8ce-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ba8ce-123">See also</span></span>

- [<span data-ttu-id="ba8ce-124">ICorProfilerInfo3 介面</span><span class="sxs-lookup"><span data-stu-id="ba8ce-124">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="ba8ce-125">分析介面</span><span class="sxs-lookup"><span data-stu-id="ba8ce-125">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="ba8ce-126">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="ba8ce-126">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
