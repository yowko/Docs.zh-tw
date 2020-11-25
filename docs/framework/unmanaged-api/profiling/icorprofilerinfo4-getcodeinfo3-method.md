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
ms.openlocfilehash: 44454b87bb656d2a4ad6e597ae001f64222b905f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697762"
---
# <a name="icorprofilerinfo4getcodeinfo3-method"></a><span data-ttu-id="e4296-102">ICorProfilerInfo4::GetCodeInfo3 方法</span><span class="sxs-lookup"><span data-stu-id="e4296-102">ICorProfilerInfo4::GetCodeInfo3 Method</span></span>

<span data-ttu-id="e4296-103">取得與經過 JIT 重新編譯的指定函式版本關聯的機器碼範圍。</span><span class="sxs-lookup"><span data-stu-id="e4296-103">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4296-104">語法</span><span class="sxs-lookup"><span data-stu-id="e4296-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeInfo3(  
    [in]  FunctionID functionID,  
    [in]  ReJITID reJitId,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4296-105">參數</span><span class="sxs-lookup"><span data-stu-id="e4296-105">Parameters</span></span>  

 `functionID`  
 <span data-ttu-id="e4296-106">[in] 與機器碼關聯的函式識別碼。</span><span class="sxs-lookup"><span data-stu-id="e4296-106">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `reJitId`  
 <span data-ttu-id="e4296-107">[in] 經過 JIT 重新編譯的函式識別。</span><span class="sxs-lookup"><span data-stu-id="e4296-107">[in] The identity of the JIT-recompiled function.</span></span>  
  
 `cCodeInfos`  
 <span data-ttu-id="e4296-108">[in] `codeInfos` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="e4296-108">[in] The size of the `codeInfos` array.</span></span>  
  
 `pcCodeInfos`  
 <span data-ttu-id="e4296-109">擴展可用 [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) 結構總數的指標。</span><span class="sxs-lookup"><span data-stu-id="e4296-109">[out] A pointer to the total number of [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures available.</span></span>  
  
 `codeInfos`  
 <span data-ttu-id="e4296-110">[out] 呼叫者提供的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="e4296-110">[out] A caller-provided buffer.</span></span> <span data-ttu-id="e4296-111">方法傳回之後，它會包含 `COR_PRF_CODE_INFO` 結構的陣列，其中每個結構各描述一個機器碼區塊。</span><span class="sxs-lookup"><span data-stu-id="e4296-111">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4296-112">備註</span><span class="sxs-lookup"><span data-stu-id="e4296-112">Remarks</span></span>  

 <span data-ttu-id="e4296-113">`GetCodeInfo3`方法類似于[GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md)，不同之處在于它會取得包含指定 IP 位址的函式之 JIT 重新編譯的識別碼。</span><span class="sxs-lookup"><span data-stu-id="e4296-113">The `GetCodeInfo3` method is similar to [GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md), except that it will get the JIT-recompiled ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e4296-114">`GetCodeInfo3` 可以觸發垃圾收集，而 [GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md) 不會。</span><span class="sxs-lookup"><span data-stu-id="e4296-114">`GetCodeInfo3` can trigger a garbage collection, whereas [GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md) will not.</span></span> <span data-ttu-id="e4296-115">如需詳細資訊，請參閱 [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](corprof-e-unsupported-call-sequence-hresult.md) HRESULT。</span><span class="sxs-lookup"><span data-stu-id="e4296-115">For more information, see the [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](corprof-e-unsupported-call-sequence-hresult.md) HRESULT.</span></span>  
  
 <span data-ttu-id="e4296-116">範圍是以遞增的通用中繼語言 (CIL) 位移順序來排序。</span><span class="sxs-lookup"><span data-stu-id="e4296-116">The extents are sorted in order of increasing Common Intermediate Language (CIL) offset.</span></span>  
  
 <span data-ttu-id="e4296-117">傳回之後 `GetCodeInfo3` ，您必須確認 `codeInfos` 緩衝區夠大，足以容納所有的 [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) 結構。</span><span class="sxs-lookup"><span data-stu-id="e4296-117">After `GetCodeInfo3` returns, you must verify that the `codeInfos` buffer was large enough to contain all the [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures.</span></span> <span data-ttu-id="e4296-118">若要這樣做，請比較 `cCodeInfos` 的值與 `cchName` 參數的值。</span><span class="sxs-lookup"><span data-stu-id="e4296-118">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="e4296-119">如果 `cCodeInfos` 除以 [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) 結構的大小小於 `pcCodeInfos` ，請配置較大 `codeInfos` 的緩衝區， `cCodeInfos` 以新的、較大的大小進行更新，然後 `GetCodeInfo3` 再呼叫一次。</span><span class="sxs-lookup"><span data-stu-id="e4296-119">If `cCodeInfos` divided by the size of a [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo3` again.</span></span>  
  
 <span data-ttu-id="e4296-120">或者，您也可以先使用長度為零的 `codeInfos` 緩衝區來呼叫 `GetCodeInfo3`，以取得正確的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="e4296-120">Alternatively, you can first call `GetCodeInfo3` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="e4296-121">然後，您可以將 `codeInfos` 緩衝區大小設定為傳回的值 `pcCodeInfos` （乘以 [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) 結構的大小），然後再呼叫 `GetCodeInfo3` 一次。</span><span class="sxs-lookup"><span data-stu-id="e4296-121">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structure, and call `GetCodeInfo3` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4296-122">需求</span><span class="sxs-lookup"><span data-stu-id="e4296-122">Requirements</span></span>  

 <span data-ttu-id="e4296-123">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e4296-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4296-124">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e4296-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e4296-125">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e4296-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4296-126">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4296-126">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4296-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4296-127">See also</span></span>

- [<span data-ttu-id="e4296-128">GetCodeInfo2 方法</span><span class="sxs-lookup"><span data-stu-id="e4296-128">GetCodeInfo2 Method</span></span>](icorprofilerinfo2-getcodeinfo2-method.md)
- [<span data-ttu-id="e4296-129">ICorProfilerInfo4 介面</span><span class="sxs-lookup"><span data-stu-id="e4296-129">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="e4296-130">分析介面</span><span class="sxs-lookup"><span data-stu-id="e4296-130">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="e4296-131">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="e4296-131">Profiling</span></span>](index.md)
