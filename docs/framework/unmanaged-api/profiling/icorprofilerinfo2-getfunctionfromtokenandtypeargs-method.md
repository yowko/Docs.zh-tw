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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c069cb375e9cb6011e7e91041d13736f5ef88dfd
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57482440"
---
# <a name="icorprofilerinfo2getfunctionfromtokenandtypeargs-method"></a><span data-ttu-id="262be-102">ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs 方法</span><span class="sxs-lookup"><span data-stu-id="262be-102">ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs Method</span></span>
<span data-ttu-id="262be-103">取得`FunctionID`函式使用指定的中繼資料語彙基元，包含類別，和`ClassID`值的任何型別引數。</span><span class="sxs-lookup"><span data-stu-id="262be-103">Gets the `FunctionID` of a function by using the specified metadata token, containing class, and `ClassID` values of any type arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="262be-104">語法</span><span class="sxs-lookup"><span data-stu-id="262be-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdMethodDef funcDef,  
    [in] ClassID classId,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] FunctionID* pFunctionID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="262be-105">參數</span><span class="sxs-lookup"><span data-stu-id="262be-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="262be-106">[in]函數所在之模組識別碼。</span><span class="sxs-lookup"><span data-stu-id="262be-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `funcDef`  
 <span data-ttu-id="262be-107">[in]`mdMethodDef`參考函式的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="262be-107">[in] An `mdMethodDef` metadata token that references the function.</span></span>  
  
 `classId`  
 <span data-ttu-id="262be-108">[in]函式的包含類別的識別碼。</span><span class="sxs-lookup"><span data-stu-id="262be-108">[in] The ID of the function's containing class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="262be-109">[in]指定的函式的型別參數的數目。</span><span class="sxs-lookup"><span data-stu-id="262be-109">[in] The number of type parameters for the given function.</span></span> <span data-ttu-id="262be-110">此值必須是零的非泛型函式。</span><span class="sxs-lookup"><span data-stu-id="262be-110">This value must be zero for non-generic functions.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="262be-111">[in]陣列`ClassID`每一個都是函式的引數的值。</span><span class="sxs-lookup"><span data-stu-id="262be-111">[in] An array of `ClassID` values, each of which is an argument of the function.</span></span> <span data-ttu-id="262be-112">值`typeArgs`可以是 NULL，如果`cTypeArgs`設為零。</span><span class="sxs-lookup"><span data-stu-id="262be-112">The value of `typeArgs` can be NULL if `cTypeArgs` is set to zero.</span></span>  
  
 `pFunctionID`  
 <span data-ttu-id="262be-113">[out]指標`FunctionID`所指定函式。</span><span class="sxs-lookup"><span data-stu-id="262be-113">[out] A pointer to the `FunctionID` of the specified function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="262be-114">備註</span><span class="sxs-lookup"><span data-stu-id="262be-114">Remarks</span></span>  
 <span data-ttu-id="262be-115">呼叫`GetFunctionFromTokenAndTypeArgs`方法`mdMethodRef`中繼資料，而不是`mdMethodDef`中繼資料語彙基元可能會有無法預期的結果。</span><span class="sxs-lookup"><span data-stu-id="262be-115">Calling the `GetFunctionFromTokenAndTypeArgs` method with an `mdMethodRef` metadata instead of an `mdMethodDef` metadata token can have unpredictable results.</span></span> <span data-ttu-id="262be-116">呼叫端應該解決`mdMethodRef`至`mdMethodDef`傳遞時。</span><span class="sxs-lookup"><span data-stu-id="262be-116">Callers should resolve the `mdMethodRef` to an `mdMethodDef` when passing it.</span></span>  
  
 <span data-ttu-id="262be-117">如果尚未載入函式，呼叫`GetFunctionFromTokenAndTypeArgs`會導致發生，而這是危險的作業在許多內容中載入。</span><span class="sxs-lookup"><span data-stu-id="262be-117">If the function is not already loaded, calling `GetFunctionFromTokenAndTypeArgs` will cause loading to occur, which is a dangerous operation in many contexts.</span></span> <span data-ttu-id="262be-118">例如，在模組或類型載入期間呼叫這個方法可能會導致無限迴圈循環載入嘗試執行階段。</span><span class="sxs-lookup"><span data-stu-id="262be-118">For example, calling this method during loading of modules or types could lead to an infinite loop as the runtime attempts to circularly load things.</span></span>  
  
 <span data-ttu-id="262be-119">一般情況下，使用`GetFunctionFromTokenAndTypeArgs`建議您不要使用。</span><span class="sxs-lookup"><span data-stu-id="262be-119">In general, use of `GetFunctionFromTokenAndTypeArgs` is discouraged.</span></span> <span data-ttu-id="262be-120">如果程式碼剖析工具有興趣的特定函式的事件，它們應該儲存`ModuleID`並`mdMethodDef`該函式，並使用[ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)若要檢查是否指定`FunctionID`是所需的函式。</span><span class="sxs-lookup"><span data-stu-id="262be-120">If profilers are interested in events for a particular function, they should store the `ModuleID` and `mdMethodDef` of that function, and use [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) to check whether a given `FunctionID` is that of the desired function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="262be-121">需求</span><span class="sxs-lookup"><span data-stu-id="262be-121">Requirements</span></span>  
 <span data-ttu-id="262be-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="262be-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="262be-123">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="262be-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="262be-124">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="262be-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="262be-125">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="262be-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="262be-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="262be-126">See also</span></span>
- [<span data-ttu-id="262be-127">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="262be-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="262be-128">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="262be-128">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
