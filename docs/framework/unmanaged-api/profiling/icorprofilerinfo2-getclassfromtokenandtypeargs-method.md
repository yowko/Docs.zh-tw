---
title: ICorProfilerInfo2::GetClassFromTokenAndTypeArgs 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassFromTokenAndTypeArgs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassFromTokenAndTypeArgs
helpviewer_keywords:
- GetClassFromTokenAndTypeArgs method [.NET Framework profiling]
- ICorProfilerInfo2::GetClassFromTokenAndTypeArgs method [.NET Framework profiling]
ms.assetid: b25c88f0-71b9-443b-8eea-1c94db0a44b9
topic_type:
- apiref
ms.openlocfilehash: 702c5f9f2bc08c824bdc0607741a6afd65a3e89b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497253"
---
# <a name="icorprofilerinfo2getclassfromtokenandtypeargs-method"></a><span data-ttu-id="07bae-102">ICorProfilerInfo2::GetClassFromTokenAndTypeArgs 方法</span><span class="sxs-lookup"><span data-stu-id="07bae-102">ICorProfilerInfo2::GetClassFromTokenAndTypeArgs Method</span></span>
<span data-ttu-id="07bae-103">`ClassID`使用指定的元資料標記和 `ClassID` 任何類型引數的值，取得類型的。</span><span class="sxs-lookup"><span data-stu-id="07bae-103">Gets the `ClassID` of a type by using the specified metadata token and the `ClassID` values of any type arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07bae-104">語法</span><span class="sxs-lookup"><span data-stu-id="07bae-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdTypeDef typeDef,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] ClassID* pClassID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07bae-105">參數</span><span class="sxs-lookup"><span data-stu-id="07bae-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="07bae-106">在類型所在之模組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="07bae-106">[in] The ID of the module in which the type resides.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="07bae-107">在`mdTypeDef`參考類型的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="07bae-107">[in] An `mdTypeDef` metadata token that references the type.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="07bae-108">在給定類型的類型參數數目。</span><span class="sxs-lookup"><span data-stu-id="07bae-108">[in] The number of type parameters for the given type.</span></span> <span data-ttu-id="07bae-109">非泛型型別的這個值必須是零。</span><span class="sxs-lookup"><span data-stu-id="07bae-109">This value must be zero for non-generic types.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="07bae-110">在值的陣列 `ClassID` ，其中每一個都是類型的引數。</span><span class="sxs-lookup"><span data-stu-id="07bae-110">[in] An array of `ClassID` values, each of which is an argument of the type.</span></span> <span data-ttu-id="07bae-111">如果設定為零，則的值 `typeArgs` 可以是 Null `cTypeArgs` 。</span><span class="sxs-lookup"><span data-stu-id="07bae-111">The value of `typeArgs` can be NULL if `cTypeArgs` is set to zero.</span></span>  
  
 `pClassID`  
 <span data-ttu-id="07bae-112">脫銷`ClassID`指定之類型的指標。</span><span class="sxs-lookup"><span data-stu-id="07bae-112">[out] A pointer to the `ClassID` of the specified type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07bae-113">備註</span><span class="sxs-lookup"><span data-stu-id="07bae-113">Remarks</span></span>  
 <span data-ttu-id="07bae-114">`GetClassFromTokenAndTypeArgs`使用 `mdTypeRef` 而不是 `mdTypeDef` 元資料標記呼叫方法，可能會產生無法預期的結果; 呼叫端應 `mdTypeRef` `mdTypeDef` 在傳遞時將解析為。</span><span class="sxs-lookup"><span data-stu-id="07bae-114">Calling the `GetClassFromTokenAndTypeArgs` method with an `mdTypeRef` instead of an `mdTypeDef` metadata token can have unpredictable results; callers should resolve the `mdTypeRef` to an `mdTypeDef` when passing it.</span></span>  
  
 <span data-ttu-id="07bae-115">如果尚未載入類型，呼叫 `GetClassFromTokenAndTypeArgs` 將會觸發載入，這在許多內容中是危險的作業。</span><span class="sxs-lookup"><span data-stu-id="07bae-115">If the type is not already loaded, calling `GetClassFromTokenAndTypeArgs` will trigger loading, which is a dangerous operation in many contexts.</span></span> <span data-ttu-id="07bae-116">例如，在載入模組或其他類型期間呼叫這個方法，可能會導致無限迴圈，因為執行時間會嘗試迴圈載入專案。</span><span class="sxs-lookup"><span data-stu-id="07bae-116">For example, calling this method during loading of modules or other types could lead to an infinite loop as the runtime attempts to circularly load things.</span></span>  
  
 <span data-ttu-id="07bae-117">一般而言， `GetClassFromTokenAndTypeArgs` 不建議使用。</span><span class="sxs-lookup"><span data-stu-id="07bae-117">In general, use of `GetClassFromTokenAndTypeArgs` is discouraged.</span></span> <span data-ttu-id="07bae-118">如果分析工具對特定類型的事件有興趣，則應該儲存 `ModuleID` `mdTypeDef` 該類型的和，並使用[ICorProfilerInfo2：： GetClassIDInfo2](icorprofilerinfo2-getclassidinfo2-method.md)來檢查給定的 `ClassID` 是否為所需類型的。</span><span class="sxs-lookup"><span data-stu-id="07bae-118">If profilers are interested in events for a particular type, they should store the `ModuleID` and `mdTypeDef` of that type, and use [ICorProfilerInfo2::GetClassIDInfo2](icorprofilerinfo2-getclassidinfo2-method.md) to check whether a given `ClassID` is that of the desired type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07bae-119">規格需求</span><span class="sxs-lookup"><span data-stu-id="07bae-119">Requirements</span></span>  
 <span data-ttu-id="07bae-120">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="07bae-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07bae-121">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="07bae-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="07bae-122">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="07bae-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07bae-123">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07bae-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07bae-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07bae-124">See also</span></span>

- [<span data-ttu-id="07bae-125">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="07bae-125">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="07bae-126">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="07bae-126">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
