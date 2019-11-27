---
title: ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetFunctionFromTokenAndTypeArgs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs
helpviewer_keywords:
- ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
- GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
ms.assetid: ce8f6aa6-4ebf-4a86-b429-4bbc8af41a8f
topic_type:
- apiref
ms.openlocfilehash: 41021a524142afe34727584265aee578e31a64b3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433219"
---
# <a name="icorprofilerinfo2getfunctionfromtokenandtypeargs-method"></a><span data-ttu-id="3084c-102">ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs 方法</span><span class="sxs-lookup"><span data-stu-id="3084c-102">ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs Method</span></span>
<span data-ttu-id="3084c-103">使用指定的元資料標記、包含類別，以及任何類型引數的 `ClassID` 值，取得函式的 `FunctionID`。</span><span class="sxs-lookup"><span data-stu-id="3084c-103">Gets the `FunctionID` of a function by using the specified metadata token, containing class, and `ClassID` values of any type arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3084c-104">語法</span><span class="sxs-lookup"><span data-stu-id="3084c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdMethodDef funcDef,  
    [in] ClassID classId,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] FunctionID* pFunctionID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3084c-105">參數</span><span class="sxs-lookup"><span data-stu-id="3084c-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="3084c-106">在函數所在模組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="3084c-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `funcDef`  
 <span data-ttu-id="3084c-107">在參考函數的 `mdMethodDef` 中繼資料 token。</span><span class="sxs-lookup"><span data-stu-id="3084c-107">[in] An `mdMethodDef` metadata token that references the function.</span></span>  
  
 `classId`  
 <span data-ttu-id="3084c-108">在函式之包含類別的識別碼。</span><span class="sxs-lookup"><span data-stu-id="3084c-108">[in] The ID of the function's containing class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="3084c-109">在指定函數的類型參數數目。</span><span class="sxs-lookup"><span data-stu-id="3084c-109">[in] The number of type parameters for the given function.</span></span> <span data-ttu-id="3084c-110">非泛型函數的這個值必須是零。</span><span class="sxs-lookup"><span data-stu-id="3084c-110">This value must be zero for non-generic functions.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="3084c-111">在`ClassID` 值的陣列，其中每一個都是函數的引數。</span><span class="sxs-lookup"><span data-stu-id="3084c-111">[in] An array of `ClassID` values, each of which is an argument of the function.</span></span> <span data-ttu-id="3084c-112">如果 `cTypeArgs` 設定為零，`typeArgs` 的值可以是 Null。</span><span class="sxs-lookup"><span data-stu-id="3084c-112">The value of `typeArgs` can be NULL if `cTypeArgs` is set to zero.</span></span>  
  
 `pFunctionID`  
 <span data-ttu-id="3084c-113">脫銷所指定函式之 `FunctionID` 的指標。</span><span class="sxs-lookup"><span data-stu-id="3084c-113">[out] A pointer to the `FunctionID` of the specified function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3084c-114">備註</span><span class="sxs-lookup"><span data-stu-id="3084c-114">Remarks</span></span>  
 <span data-ttu-id="3084c-115">使用 `mdMethodRef` 中繼資料來呼叫 `GetFunctionFromTokenAndTypeArgs` 方法，而不是 `mdMethodDef` 元資料標記，可能會有無法預期的結果。</span><span class="sxs-lookup"><span data-stu-id="3084c-115">Calling the `GetFunctionFromTokenAndTypeArgs` method with an `mdMethodRef` metadata instead of an `mdMethodDef` metadata token can have unpredictable results.</span></span> <span data-ttu-id="3084c-116">呼叫端應該在傳遞時，將 `mdMethodRef` 解析成 `mdMethodDef`。</span><span class="sxs-lookup"><span data-stu-id="3084c-116">Callers should resolve the `mdMethodRef` to an `mdMethodDef` when passing it.</span></span>  
  
 <span data-ttu-id="3084c-117">如果尚未載入函式，呼叫 `GetFunctionFromTokenAndTypeArgs` 將會造成載入，這在許多內容中是危險的作業。</span><span class="sxs-lookup"><span data-stu-id="3084c-117">If the function is not already loaded, calling `GetFunctionFromTokenAndTypeArgs` will cause loading to occur, which is a dangerous operation in many contexts.</span></span> <span data-ttu-id="3084c-118">例如，在載入模組或類型期間呼叫這個方法可能會導致無限迴圈，因為執行時間會嘗試迴圈載入專案。</span><span class="sxs-lookup"><span data-stu-id="3084c-118">For example, calling this method during loading of modules or types could lead to an infinite loop as the runtime attempts to circularly load things.</span></span>  
  
 <span data-ttu-id="3084c-119">一般而言，不建議使用 `GetFunctionFromTokenAndTypeArgs`。</span><span class="sxs-lookup"><span data-stu-id="3084c-119">In general, use of `GetFunctionFromTokenAndTypeArgs` is discouraged.</span></span> <span data-ttu-id="3084c-120">如果分析工具對特定函式的事件有興趣，則應該儲存該函式的 `ModuleID` 和 `mdMethodDef`，並使用[ICorProfilerInfo2：： GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)來檢查給定的 `FunctionID` 是否為所需函式的。</span><span class="sxs-lookup"><span data-stu-id="3084c-120">If profilers are interested in events for a particular function, they should store the `ModuleID` and `mdMethodDef` of that function, and use [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) to check whether a given `FunctionID` is that of the desired function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3084c-121">需求</span><span class="sxs-lookup"><span data-stu-id="3084c-121">Requirements</span></span>  
 <span data-ttu-id="3084c-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3084c-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3084c-123">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3084c-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3084c-124">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3084c-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3084c-125">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3084c-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3084c-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3084c-126">See also</span></span>

- [<span data-ttu-id="3084c-127">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="3084c-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="3084c-128">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="3084c-128">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
