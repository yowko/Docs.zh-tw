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
ms.openlocfilehash: ee44c89ec30edcb6233081f0757fa0f7b7191178
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449640"
---
# <a name="icorprofilerinfo3getthreadstaticaddress2-method"></a><span data-ttu-id="408d8-102">ICorProfilerInfo3::GetThreadStaticAddress2 方法</span><span class="sxs-lookup"><span data-stu-id="408d8-102">ICorProfilerInfo3::GetThreadStaticAddress2 Method</span></span>
<span data-ttu-id="408d8-103">取得指定執行緒靜態欄位的位址，這位於指定之執行緒和應用程式定義域的範圍內。</span><span class="sxs-lookup"><span data-stu-id="408d8-103">Gets the address of the specified thread-static field that is in the scope of the specified thread and application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="408d8-104">語法</span><span class="sxs-lookup"><span data-stu-id="408d8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadStaticAddress2(  
                [in] ClassID classId,  
                [in] mdFieldDef fieldToken,  
                [in] AppDomainID appDomainId,  
                [in] ThreadID threadId,  
                [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="408d8-105">參數</span><span class="sxs-lookup"><span data-stu-id="408d8-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="408d8-106">在包含所要求的執行緒靜態欄位之類別的識別碼。</span><span class="sxs-lookup"><span data-stu-id="408d8-106">[in] The ID of the class that contains the requested thread-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="408d8-107">在所要求之執行緒靜態欄位的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="408d8-107">[in] The metadata token for the requested thread-static field.</span></span>  
  
 `appDomainId`  
 <span data-ttu-id="408d8-108">[in] 應用程式定義域的 ID。</span><span class="sxs-lookup"><span data-stu-id="408d8-108">[in] The ID of the application domain.</span></span>  
  
 `threadId`  
 <span data-ttu-id="408d8-109">在做為要求的靜態欄位範圍之執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="408d8-109">[in] The ID of the thread that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="408d8-110">脫銷位於指定執行緒內之靜態欄位位址的指標。</span><span class="sxs-lookup"><span data-stu-id="408d8-110">[out] A pointer to the address of the static field that is within the specified thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="408d8-111">備註</span><span class="sxs-lookup"><span data-stu-id="408d8-111">Remarks</span></span>  
 <span data-ttu-id="408d8-112">`GetThreadStaticAddress2` 方法可能會傳回下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="408d8-112">The `GetThreadStaticAddress2` method may return one of the following:</span></span>  
  
- <span data-ttu-id="408d8-113">如果未在指定的內容中指派位址給給定的靜態欄位，CORPROF_E_DATAINCOMPLETE HRESULT。</span><span class="sxs-lookup"><span data-stu-id="408d8-113">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="408d8-114">可能位於垃圾收集堆積中之物件的位址。</span><span class="sxs-lookup"><span data-stu-id="408d8-114">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="408d8-115">這些位址在垃圾收集後可能會變成無效，因此在垃圾收集之後，分析工具不應假設它們是有效的。</span><span class="sxs-lookup"><span data-stu-id="408d8-115">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="408d8-116">在類別的類別的函式完成之前，`GetThreadStaticAddress2` 將會傳回其所有靜態欄位的 CORPROF_E_DATAINCOMPLETE，雖然某些靜態欄位可能已經初始化，並且會對垃圾收集物件進行根。</span><span class="sxs-lookup"><span data-stu-id="408d8-116">Before a class’s class constructor is completed, `GetThreadStaticAddress2` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
 <span data-ttu-id="408d8-117">[ICorProfilerInfo2：： GetThreadStaticAddress](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadstaticaddress-method.md)方法與 `GetThreadStaticAddress2` 方法類似，但不接受應用程式網域引數。</span><span class="sxs-lookup"><span data-stu-id="408d8-117">The [ICorProfilerInfo2::GetThreadStaticAddress](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadstaticaddress-method.md) method is similar to the `GetThreadStaticAddress2` method, but does not accept an application domain argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="408d8-118">需求</span><span class="sxs-lookup"><span data-stu-id="408d8-118">Requirements</span></span>  
 <span data-ttu-id="408d8-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="408d8-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="408d8-120">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="408d8-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="408d8-121">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="408d8-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="408d8-122">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="408d8-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="408d8-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="408d8-123">See also</span></span>

- [<span data-ttu-id="408d8-124">ICorProfilerInfo3 介面</span><span class="sxs-lookup"><span data-stu-id="408d8-124">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="408d8-125">分析介面</span><span class="sxs-lookup"><span data-stu-id="408d8-125">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="408d8-126">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="408d8-126">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
