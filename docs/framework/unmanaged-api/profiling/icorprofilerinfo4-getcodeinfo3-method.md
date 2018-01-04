---
title: "ICorProfilerInfo4::GetCodeInfo3 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4.GetCodeInfo3
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::GetCodeInfo3
helpviewer_keywords:
- GetCodeInfo3 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetCodeInfo3 method [.NET Framework profiling]
ms.assetid: bb8c105e-4d9a-4684-8c05-ed6909cc1b8c
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b669714774ecfccad436f064350569d27ef13883
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo4getcodeinfo3-method"></a><span data-ttu-id="026b5-102">ICorProfilerInfo4::GetCodeInfo3 方法</span><span class="sxs-lookup"><span data-stu-id="026b5-102">ICorProfilerInfo4::GetCodeInfo3 Method</span></span>
<span data-ttu-id="026b5-103">取得與經過 JIT 重新編譯的指定函式版本關聯的機器碼範圍。</span><span class="sxs-lookup"><span data-stu-id="026b5-103">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="026b5-104">語法</span><span class="sxs-lookup"><span data-stu-id="026b5-104">Syntax</span></span>  
  
```  
HRESULT GetCodeInfo3(  
    [in]  FunctionID functionID,  
    [in]  ReJITID reJitId,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="026b5-105">參數</span><span class="sxs-lookup"><span data-stu-id="026b5-105">Parameters</span></span>  
 `functionID`  
 <span data-ttu-id="026b5-106">[in] 與機器碼關聯的函式識別碼。</span><span class="sxs-lookup"><span data-stu-id="026b5-106">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `reJitId`  
 <span data-ttu-id="026b5-107">[in] 經過 JIT 重新編譯的函式識別。</span><span class="sxs-lookup"><span data-stu-id="026b5-107">[in] The identity of the JIT-recompiled function.</span></span>  
  
 `cCodeInfos`  
 <span data-ttu-id="026b5-108">[in] `codeInfos` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="026b5-108">[in] The size of the `codeInfos` array.</span></span>  
  
 `pcCodeInfos`  
 <span data-ttu-id="026b5-109">[out]總數的指標[COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md)可用結構。</span><span class="sxs-lookup"><span data-stu-id="026b5-109">[out] A pointer to the total number of [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures available.</span></span>  
  
 `codeInfos`  
 <span data-ttu-id="026b5-110">[out] 呼叫者提供的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="026b5-110">[out] A caller-provided buffer.</span></span> <span data-ttu-id="026b5-111">方法傳回之後，它會包含 `COR_PRF_CODE_INFO` 結構的陣列，其中每個結構各描述一個機器碼區塊。</span><span class="sxs-lookup"><span data-stu-id="026b5-111">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="026b5-112">備註</span><span class="sxs-lookup"><span data-stu-id="026b5-112">Remarks</span></span>  
 <span data-ttu-id="026b5-113">`GetCodeInfo3`方法很類似[GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)，只不過它會取得包含指定的 IP 位址的函式的 JIT 重新編譯識別碼。</span><span class="sxs-lookup"><span data-stu-id="026b5-113">The `GetCodeInfo3` method is similar to [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md), except that it will get the JIT-recompiled ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="026b5-114">`GetCodeInfo3`可能觸發記憶體回收，而[GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)則不會。</span><span class="sxs-lookup"><span data-stu-id="026b5-114">`GetCodeInfo3` can trigger a garbage collection, whereas [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) will not.</span></span> <span data-ttu-id="026b5-115">如需詳細資訊，請參閱[CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md) HRESULT。</span><span class="sxs-lookup"><span data-stu-id="026b5-115">For more information, see the [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md) HRESULT.</span></span>  
  
 <span data-ttu-id="026b5-116">範圍是以遞增的通用中繼語言 (CIL) 位移順序來排序。</span><span class="sxs-lookup"><span data-stu-id="026b5-116">The extents are sorted in order of increasing Common Intermediate Language (CIL) offset.</span></span>  
  
 <span data-ttu-id="026b5-117">之後`GetCodeInfo3`傳回時，您必須確認`codeInfos`緩衝區的大小足以包含所有[COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md)結構。</span><span class="sxs-lookup"><span data-stu-id="026b5-117">After `GetCodeInfo3` returns, you must verify that the `codeInfos` buffer was large enough to contain all the [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures.</span></span> <span data-ttu-id="026b5-118">若要執行這項作業，請比較 `cCodeInfos` 的值和 `cchName` 參數的值。</span><span class="sxs-lookup"><span data-stu-id="026b5-118">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="026b5-119">如果`cCodeInfos`除以大小[COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md)結構小於`pcCodeInfos`，配置較大`codeInfos`緩衝區，更新`cCodeInfos`以新、 較大的大小和呼叫`GetCodeInfo3`一次。</span><span class="sxs-lookup"><span data-stu-id="026b5-119">If `cCodeInfos` divided by the size of a [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo3` again.</span></span>  
  
 <span data-ttu-id="026b5-120">此外，您也可以先使用長度為零的 `codeInfos` 緩衝區來呼叫 `GetCodeInfo3`，以取得正確的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="026b5-120">Alternatively, you can first call `GetCodeInfo3` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="026b5-121">然後您可以設定`codeInfos`緩衝區大小中傳回的值為`pcCodeInfos`大小乘以[COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md)結構，並呼叫`GetCodeInfo3`一次。</span><span class="sxs-lookup"><span data-stu-id="026b5-121">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structure, and call `GetCodeInfo3` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="026b5-122">需求</span><span class="sxs-lookup"><span data-stu-id="026b5-122">Requirements</span></span>  
 <span data-ttu-id="026b5-123">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="026b5-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="026b5-124">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="026b5-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="026b5-125">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="026b5-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="026b5-126">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="026b5-126">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="026b5-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="026b5-127">See Also</span></span>  
 [<span data-ttu-id="026b5-128">GetCodeInfo2 方法</span><span class="sxs-lookup"><span data-stu-id="026b5-128">GetCodeInfo2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)  
 [<span data-ttu-id="026b5-129">ICorProfilerInfo4 介面</span><span class="sxs-lookup"><span data-stu-id="026b5-129">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [<span data-ttu-id="026b5-130">分析介面</span><span class="sxs-lookup"><span data-stu-id="026b5-130">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="026b5-131">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="026b5-131">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
