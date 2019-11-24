---
title: ICorProfilerInfo2::GetContextStaticAddress 方法
ms.date: 03/30/2017
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
ms.openlocfilehash: d5d7da343148d5f1c2aa9b2b639b094f8269199b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433197"
---
# <a name="icorprofilerinfo2getcontextstaticaddress-method"></a><span data-ttu-id="7f13e-102">ICorProfilerInfo2::GetContextStaticAddress 方法</span><span class="sxs-lookup"><span data-stu-id="7f13e-102">ICorProfilerInfo2::GetContextStaticAddress Method</span></span>
<span data-ttu-id="7f13e-103">Gets the address for the specified context-static field that is in the scope of the specified context.</span><span class="sxs-lookup"><span data-stu-id="7f13e-103">Gets the address for the specified context-static field that is in the scope of the specified context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f13e-104">語法</span><span class="sxs-lookup"><span data-stu-id="7f13e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContextStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] ContextID contextId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f13e-105">參數</span><span class="sxs-lookup"><span data-stu-id="7f13e-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="7f13e-106">[in] The ID of the class that contains the requested context-static field.</span><span class="sxs-lookup"><span data-stu-id="7f13e-106">[in] The ID of the class that contains the requested context-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="7f13e-107">[in] The metadata token for the requested context-static field.</span><span class="sxs-lookup"><span data-stu-id="7f13e-107">[in] The metadata token for the requested context-static field.</span></span>  
  
 `contextId`  
 <span data-ttu-id="7f13e-108">[in] The ID of the context that is the scope for the requested context-static field.</span><span class="sxs-lookup"><span data-stu-id="7f13e-108">[in] The ID of the context that is the scope for the requested context-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="7f13e-109">[out] A pointer to the address of the static field that is within the specified context.</span><span class="sxs-lookup"><span data-stu-id="7f13e-109">[out] A pointer to the address of the static field that is within the specified context.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f13e-110">備註</span><span class="sxs-lookup"><span data-stu-id="7f13e-110">Remarks</span></span>  
 <span data-ttu-id="7f13e-111">The `GetContextStaticAddress` method may return one of the following:</span><span class="sxs-lookup"><span data-stu-id="7f13e-111">The `GetContextStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="7f13e-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span><span class="sxs-lookup"><span data-stu-id="7f13e-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="7f13e-113">The addresses of objects that may be in the garbage collection heap.</span><span class="sxs-lookup"><span data-stu-id="7f13e-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="7f13e-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span><span class="sxs-lookup"><span data-stu-id="7f13e-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="7f13e-115">Before a class’s class constructor is completed, `GetContextStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span><span class="sxs-lookup"><span data-stu-id="7f13e-115">Before a class’s class constructor is completed, `GetContextStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f13e-116">需求</span><span class="sxs-lookup"><span data-stu-id="7f13e-116">Requirements</span></span>  
 <span data-ttu-id="7f13e-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7f13e-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f13e-118">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7f13e-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7f13e-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7f13e-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7f13e-120">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f13e-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f13e-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="7f13e-121">See also</span></span>

- [<span data-ttu-id="7f13e-122">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="7f13e-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="7f13e-123">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="7f13e-123">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
