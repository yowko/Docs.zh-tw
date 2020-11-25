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
ms.openlocfilehash: 17a6220598010c0bee9c3f0485860aa0b2dc5f3a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727103"
---
# <a name="icorprofilerinfo2getfunctionfromtokenandtypeargs-method"></a><span data-ttu-id="3c9f2-102">ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs 方法</span><span class="sxs-lookup"><span data-stu-id="3c9f2-102">ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs Method</span></span>

<span data-ttu-id="3c9f2-103">`FunctionID`使用指定的元資料標記、包含類別以及 `ClassID` 任何類型引數的值，取得函數的。</span><span class="sxs-lookup"><span data-stu-id="3c9f2-103">Gets the `FunctionID` of a function by using the specified metadata token, containing class, and `ClassID` values of any type arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c9f2-104">語法</span><span class="sxs-lookup"><span data-stu-id="3c9f2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdMethodDef funcDef,  
    [in] ClassID classId,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] FunctionID* pFunctionID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c9f2-105">參數</span><span class="sxs-lookup"><span data-stu-id="3c9f2-105">Parameters</span></span>  

 `moduleID`  
 <span data-ttu-id="3c9f2-106">在函數所在之模組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="3c9f2-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `funcDef`  
 <span data-ttu-id="3c9f2-107">在 `mdMethodDef` 參考函數的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="3c9f2-107">[in] An `mdMethodDef` metadata token that references the function.</span></span>  
  
 `classId`  
 <span data-ttu-id="3c9f2-108">在函數包含類別的識別碼。</span><span class="sxs-lookup"><span data-stu-id="3c9f2-108">[in] The ID of the function's containing class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="3c9f2-109">在指定函式的型別參數數目。</span><span class="sxs-lookup"><span data-stu-id="3c9f2-109">[in] The number of type parameters for the given function.</span></span> <span data-ttu-id="3c9f2-110">非泛型函數的這個值必須為零。</span><span class="sxs-lookup"><span data-stu-id="3c9f2-110">This value must be zero for non-generic functions.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="3c9f2-111">在值的陣列 `ClassID` ，每個值都是函數的引數。</span><span class="sxs-lookup"><span data-stu-id="3c9f2-111">[in] An array of `ClassID` values, each of which is an argument of the function.</span></span> <span data-ttu-id="3c9f2-112">如果設定為零，則的值 `typeArgs` 可以是 Null `cTypeArgs` 。</span><span class="sxs-lookup"><span data-stu-id="3c9f2-112">The value of `typeArgs` can be NULL if `cTypeArgs` is set to zero.</span></span>  
  
 `pFunctionID`  
 <span data-ttu-id="3c9f2-113">擴展指定之函式的指標 `FunctionID` 。</span><span class="sxs-lookup"><span data-stu-id="3c9f2-113">[out] A pointer to the `FunctionID` of the specified function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c9f2-114">備註</span><span class="sxs-lookup"><span data-stu-id="3c9f2-114">Remarks</span></span>  

 <span data-ttu-id="3c9f2-115">`GetFunctionFromTokenAndTypeArgs`使用 `mdMethodRef` 中繼資料來呼叫方法，而不是使用 `mdMethodDef` 元資料標記，可能會產生無法預測的結果。</span><span class="sxs-lookup"><span data-stu-id="3c9f2-115">Calling the `GetFunctionFromTokenAndTypeArgs` method with an `mdMethodRef` metadata instead of an `mdMethodDef` metadata token can have unpredictable results.</span></span> <span data-ttu-id="3c9f2-116">當呼叫端傳遞時，呼叫端應該將解析 `mdMethodRef` 為 `mdMethodDef` 。</span><span class="sxs-lookup"><span data-stu-id="3c9f2-116">Callers should resolve the `mdMethodRef` to an `mdMethodDef` when passing it.</span></span>  
  
 <span data-ttu-id="3c9f2-117">如果尚未載入此函式，呼叫 `GetFunctionFromTokenAndTypeArgs` 會導致載入發生，這在許多內容中是危險的作業。</span><span class="sxs-lookup"><span data-stu-id="3c9f2-117">If the function is not already loaded, calling `GetFunctionFromTokenAndTypeArgs` will cause loading to occur, which is a dangerous operation in many contexts.</span></span> <span data-ttu-id="3c9f2-118">例如，在載入模組或類型期間呼叫這個方法，可能會導致無限迴圈，因為執行時間會嘗試迴圈載入專案。</span><span class="sxs-lookup"><span data-stu-id="3c9f2-118">For example, calling this method during loading of modules or types could lead to an infinite loop as the runtime attempts to circularly load things.</span></span>  
  
 <span data-ttu-id="3c9f2-119">一般情況下， `GetFunctionFromTokenAndTypeArgs` 不建議使用。</span><span class="sxs-lookup"><span data-stu-id="3c9f2-119">In general, use of `GetFunctionFromTokenAndTypeArgs` is discouraged.</span></span> <span data-ttu-id="3c9f2-120">如果分析工具對特定函式的事件有興趣，則應該儲存該函式的 `ModuleID` 和 `mdMethodDef` ，並使用 [ICorProfilerInfo2：： GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) 檢查給定的是否為所需函式的 `FunctionID` 。</span><span class="sxs-lookup"><span data-stu-id="3c9f2-120">If profilers are interested in events for a particular function, they should store the `ModuleID` and `mdMethodDef` of that function, and use [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) to check whether a given `FunctionID` is that of the desired function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c9f2-121">需求</span><span class="sxs-lookup"><span data-stu-id="3c9f2-121">Requirements</span></span>  

 <span data-ttu-id="3c9f2-122">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3c9f2-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c9f2-123">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3c9f2-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3c9f2-124">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c9f2-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c9f2-125">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c9f2-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c9f2-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c9f2-126">See also</span></span>

- [<span data-ttu-id="3c9f2-127">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="3c9f2-127">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="3c9f2-128">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="3c9f2-128">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
