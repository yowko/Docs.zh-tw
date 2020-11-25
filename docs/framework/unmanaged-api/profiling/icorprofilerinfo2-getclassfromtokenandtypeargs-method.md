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
ms.openlocfilehash: 62aad8339b34a4831211a45bd645906d73393d25
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727142"
---
# <a name="icorprofilerinfo2getclassfromtokenandtypeargs-method"></a><span data-ttu-id="bfdc7-102">ICorProfilerInfo2::GetClassFromTokenAndTypeArgs 方法</span><span class="sxs-lookup"><span data-stu-id="bfdc7-102">ICorProfilerInfo2::GetClassFromTokenAndTypeArgs Method</span></span>

<span data-ttu-id="bfdc7-103">`ClassID`使用指定的元資料標記和 `ClassID` 任何類型引數的值，取得型別的。</span><span class="sxs-lookup"><span data-stu-id="bfdc7-103">Gets the `ClassID` of a type by using the specified metadata token and the `ClassID` values of any type arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfdc7-104">語法</span><span class="sxs-lookup"><span data-stu-id="bfdc7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdTypeDef typeDef,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] ClassID* pClassID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bfdc7-105">參數</span><span class="sxs-lookup"><span data-stu-id="bfdc7-105">Parameters</span></span>  

 `moduleID`  
 <span data-ttu-id="bfdc7-106">在型別所在之模組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="bfdc7-106">[in] The ID of the module in which the type resides.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="bfdc7-107">在 `mdTypeDef` 參考該類型的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="bfdc7-107">[in] An `mdTypeDef` metadata token that references the type.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="bfdc7-108">在給定類型的型別參數數目。</span><span class="sxs-lookup"><span data-stu-id="bfdc7-108">[in] The number of type parameters for the given type.</span></span> <span data-ttu-id="bfdc7-109">非泛型型別的這個值必須為零。</span><span class="sxs-lookup"><span data-stu-id="bfdc7-109">This value must be zero for non-generic types.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="bfdc7-110">在值的陣列 `ClassID` ，每個值都是類型的引數。</span><span class="sxs-lookup"><span data-stu-id="bfdc7-110">[in] An array of `ClassID` values, each of which is an argument of the type.</span></span> <span data-ttu-id="bfdc7-111">如果設定為零，則的值 `typeArgs` 可以是 Null `cTypeArgs` 。</span><span class="sxs-lookup"><span data-stu-id="bfdc7-111">The value of `typeArgs` can be NULL if `cTypeArgs` is set to zero.</span></span>  
  
 `pClassID`  
 <span data-ttu-id="bfdc7-112">擴展 `ClassID` 指定之類型的指標。</span><span class="sxs-lookup"><span data-stu-id="bfdc7-112">[out] A pointer to the `ClassID` of the specified type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bfdc7-113">備註</span><span class="sxs-lookup"><span data-stu-id="bfdc7-113">Remarks</span></span>  

 <span data-ttu-id="bfdc7-114">`GetClassFromTokenAndTypeArgs`使用 `mdTypeRef` 取代元資料標記來呼叫方法， `mdTypeDef` 可能會產生無法預測的結果; 呼叫端應該 `mdTypeRef` `mdTypeDef` 在傳遞時將解析為。</span><span class="sxs-lookup"><span data-stu-id="bfdc7-114">Calling the `GetClassFromTokenAndTypeArgs` method with an `mdTypeRef` instead of an `mdTypeDef` metadata token can have unpredictable results; callers should resolve the `mdTypeRef` to an `mdTypeDef` when passing it.</span></span>  
  
 <span data-ttu-id="bfdc7-115">如果類型尚未載入，則呼叫 `GetClassFromTokenAndTypeArgs` 會觸發載入，這在許多內容中是危險的作業。</span><span class="sxs-lookup"><span data-stu-id="bfdc7-115">If the type is not already loaded, calling `GetClassFromTokenAndTypeArgs` will trigger loading, which is a dangerous operation in many contexts.</span></span> <span data-ttu-id="bfdc7-116">例如，在載入模組或其他類型期間呼叫這個方法，可能會導致無限迴圈，因為執行時間會嘗試迴圈載入專案。</span><span class="sxs-lookup"><span data-stu-id="bfdc7-116">For example, calling this method during loading of modules or other types could lead to an infinite loop as the runtime attempts to circularly load things.</span></span>  
  
 <span data-ttu-id="bfdc7-117">一般情況下， `GetClassFromTokenAndTypeArgs` 不建議使用。</span><span class="sxs-lookup"><span data-stu-id="bfdc7-117">In general, use of `GetClassFromTokenAndTypeArgs` is discouraged.</span></span> <span data-ttu-id="bfdc7-118">如果分析工具對特定類型的事件有興趣，則應該儲存該 `ModuleID` 類型的和 `mdTypeDef` ，並使用 [ICorProfilerInfo2：： GetClassIDInfo2](icorprofilerinfo2-getclassidinfo2-method.md) 來檢查給定的是否 `ClassID` 為所需類型的。</span><span class="sxs-lookup"><span data-stu-id="bfdc7-118">If profilers are interested in events for a particular type, they should store the `ModuleID` and `mdTypeDef` of that type, and use [ICorProfilerInfo2::GetClassIDInfo2](icorprofilerinfo2-getclassidinfo2-method.md) to check whether a given `ClassID` is that of the desired type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bfdc7-119">需求</span><span class="sxs-lookup"><span data-stu-id="bfdc7-119">Requirements</span></span>  

 <span data-ttu-id="bfdc7-120">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bfdc7-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bfdc7-121">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bfdc7-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bfdc7-122">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bfdc7-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bfdc7-123">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bfdc7-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfdc7-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bfdc7-124">See also</span></span>

- [<span data-ttu-id="bfdc7-125">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="bfdc7-125">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="bfdc7-126">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="bfdc7-126">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
