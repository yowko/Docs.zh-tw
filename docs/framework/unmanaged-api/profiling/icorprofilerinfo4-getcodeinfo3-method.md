---
title: ICorProfilerInfo4::GetCodeInfo3 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetCodeInfo3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetCodeInfo3
helpviewer_keywords:
- GetCodeInfo3 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetCodeInfo3 method [.NET Framework profiling]
ms.assetid: bb8c105e-4d9a-4684-8c05-ed6909cc1b8c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cb067d16ef7f8177f979a083707f8c6ef36750c0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59145804"
---
# <a name="icorprofilerinfo4getcodeinfo3-method"></a><span data-ttu-id="1ff59-102">ICorProfilerInfo4::GetCodeInfo3 方法</span><span class="sxs-lookup"><span data-stu-id="1ff59-102">ICorProfilerInfo4::GetCodeInfo3 Method</span></span>
<span data-ttu-id="1ff59-103">取得與經過 JIT 重新編譯的指定函式版本關聯的機器碼範圍。</span><span class="sxs-lookup"><span data-stu-id="1ff59-103">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ff59-104">語法</span><span class="sxs-lookup"><span data-stu-id="1ff59-104">Syntax</span></span>  
  
```  
HRESULT GetCodeInfo3(  
    [in]  FunctionID functionID,  
    [in]  ReJITID reJitId,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ff59-105">參數</span><span class="sxs-lookup"><span data-stu-id="1ff59-105">Parameters</span></span>  
 `functionID`  
 <span data-ttu-id="1ff59-106">[in] 與機器碼關聯的函式識別碼。</span><span class="sxs-lookup"><span data-stu-id="1ff59-106">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `reJitId`  
 <span data-ttu-id="1ff59-107">[in] 經過 JIT 重新編譯的函式識別。</span><span class="sxs-lookup"><span data-stu-id="1ff59-107">[in] The identity of the JIT-recompiled function.</span></span>  
  
 `cCodeInfos`  
 <span data-ttu-id="1ff59-108">[in] `codeInfos` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="1ff59-108">[in] The size of the `codeInfos` array.</span></span>  
  
 `pcCodeInfos`  
 <span data-ttu-id="1ff59-109">[out]總數的指標[COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md)可用的結構。</span><span class="sxs-lookup"><span data-stu-id="1ff59-109">[out] A pointer to the total number of [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures available.</span></span>  
  
 `codeInfos`  
 <span data-ttu-id="1ff59-110">[out] 呼叫者提供的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="1ff59-110">[out] A caller-provided buffer.</span></span> <span data-ttu-id="1ff59-111">方法傳回之後，它會包含 `COR_PRF_CODE_INFO` 結構的陣列，其中每個結構各描述一個機器碼區塊。</span><span class="sxs-lookup"><span data-stu-id="1ff59-111">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ff59-112">備註</span><span class="sxs-lookup"><span data-stu-id="1ff59-112">Remarks</span></span>  
 <span data-ttu-id="1ff59-113">`GetCodeInfo3`方法是類似[GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)，只不過它會取得 JIT 重新編譯函式的識別碼，其中包含指定的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="1ff59-113">The `GetCodeInfo3` method is similar to [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md), except that it will get the JIT-recompiled ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1ff59-114">`GetCodeInfo3` 可以觸發記憶體回收，而[GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)不會。</span><span class="sxs-lookup"><span data-stu-id="1ff59-114">`GetCodeInfo3` can trigger a garbage collection, whereas [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) will not.</span></span> <span data-ttu-id="1ff59-115">如需詳細資訊，請參閱 < [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md) HRESULT。</span><span class="sxs-lookup"><span data-stu-id="1ff59-115">For more information, see the [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md) HRESULT.</span></span>  
  
 <span data-ttu-id="1ff59-116">範圍是以遞增的通用中繼語言 (CIL) 位移順序來排序。</span><span class="sxs-lookup"><span data-stu-id="1ff59-116">The extents are sorted in order of increasing Common Intermediate Language (CIL) offset.</span></span>  
  
 <span data-ttu-id="1ff59-117">在後`GetCodeInfo3`傳回時，您必須確認`codeInfos`緩衝區的大小足以包含所有[COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md)結構。</span><span class="sxs-lookup"><span data-stu-id="1ff59-117">After `GetCodeInfo3` returns, you must verify that the `codeInfos` buffer was large enough to contain all the [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures.</span></span> <span data-ttu-id="1ff59-118">若要這樣做，請比較 `cCodeInfos` 的值與 `cchName` 參數的值。</span><span class="sxs-lookup"><span data-stu-id="1ff59-118">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="1ff59-119">如果`cCodeInfos`除以的大小[COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md)結構小於`pcCodeInfos`，配置較大`codeInfos`緩衝區，更新`cCodeInfos`新且較大的大小，與呼叫`GetCodeInfo3`一次。</span><span class="sxs-lookup"><span data-stu-id="1ff59-119">If `cCodeInfos` divided by the size of a [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo3` again.</span></span>  
  
 <span data-ttu-id="1ff59-120">或者，您也可以先使用長度為零的 `codeInfos` 緩衝區來呼叫 `GetCodeInfo3`，以取得正確的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="1ff59-120">Alternatively, you can first call `GetCodeInfo3` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="1ff59-121">然後您可以設定`codeInfos`緩衝區中傳回的值的大小`pcCodeInfos`大小乘以[COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md)結構，並呼叫`GetCodeInfo3`一次。</span><span class="sxs-lookup"><span data-stu-id="1ff59-121">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structure, and call `GetCodeInfo3` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ff59-122">需求</span><span class="sxs-lookup"><span data-stu-id="1ff59-122">Requirements</span></span>  
 <span data-ttu-id="1ff59-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1ff59-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ff59-124">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1ff59-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1ff59-125">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ff59-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ff59-126">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ff59-126">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ff59-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ff59-127">See also</span></span>

- [<span data-ttu-id="1ff59-128">GetCodeInfo2 方法</span><span class="sxs-lookup"><span data-stu-id="1ff59-128">GetCodeInfo2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)
- [<span data-ttu-id="1ff59-129">ICorProfilerInfo4 介面</span><span class="sxs-lookup"><span data-stu-id="1ff59-129">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="1ff59-130">分析介面</span><span class="sxs-lookup"><span data-stu-id="1ff59-130">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="1ff59-131">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="1ff59-131">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
