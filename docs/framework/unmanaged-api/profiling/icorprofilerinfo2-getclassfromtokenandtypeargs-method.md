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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0d4d5ec9119cdcf89e507f133288f569e6fb37ea
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59072515"
---
# <a name="icorprofilerinfo2getclassfromtokenandtypeargs-method"></a><span data-ttu-id="41e90-102">ICorProfilerInfo2::GetClassFromTokenAndTypeArgs 方法</span><span class="sxs-lookup"><span data-stu-id="41e90-102">ICorProfilerInfo2::GetClassFromTokenAndTypeArgs Method</span></span>
<span data-ttu-id="41e90-103">取得`ClassID`使用指定的中繼資料語彙基元型別和`ClassID`值的任何型別引數。</span><span class="sxs-lookup"><span data-stu-id="41e90-103">Gets the `ClassID` of a type by using the specified metadata token and the `ClassID` values of any type arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41e90-104">語法</span><span class="sxs-lookup"><span data-stu-id="41e90-104">Syntax</span></span>  
  
```  
HRESULT GetClassFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdTypeDef typeDef,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] ClassID* pClassID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41e90-105">參數</span><span class="sxs-lookup"><span data-stu-id="41e90-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="41e90-106">[in]型別所在之模組識別碼。</span><span class="sxs-lookup"><span data-stu-id="41e90-106">[in] The ID of the module in which the type resides.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="41e90-107">[in]`mdTypeDef`參考類型的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="41e90-107">[in] An `mdTypeDef` metadata token that references the type.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="41e90-108">[in]指定型別的型別參數的數目。</span><span class="sxs-lookup"><span data-stu-id="41e90-108">[in] The number of type parameters for the given type.</span></span> <span data-ttu-id="41e90-109">此值必須是非泛型型別為零。</span><span class="sxs-lookup"><span data-stu-id="41e90-109">This value must be zero for non-generic types.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="41e90-110">[in]陣列`ClassID`每一個都是類型的引數的值。</span><span class="sxs-lookup"><span data-stu-id="41e90-110">[in] An array of `ClassID` values, each of which is an argument of the type.</span></span> <span data-ttu-id="41e90-111">值`typeArgs`可以是 NULL，如果`cTypeArgs`設為零。</span><span class="sxs-lookup"><span data-stu-id="41e90-111">The value of `typeArgs` can be NULL if `cTypeArgs` is set to zero.</span></span>  
  
 `pClassID`  
 <span data-ttu-id="41e90-112">[out]指標`ClassID`指定的型別。</span><span class="sxs-lookup"><span data-stu-id="41e90-112">[out] A pointer to the `ClassID` of the specified type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41e90-113">備註</span><span class="sxs-lookup"><span data-stu-id="41e90-113">Remarks</span></span>  
 <span data-ttu-id="41e90-114">呼叫`GetClassFromTokenAndTypeArgs`方法`mdTypeRef`而不是`mdTypeDef`中繼資料語彙基元可能會有無法預期的結果，呼叫端應該解決`mdTypeRef`到`mdTypeDef`傳遞時。</span><span class="sxs-lookup"><span data-stu-id="41e90-114">Calling the `GetClassFromTokenAndTypeArgs` method with an `mdTypeRef` instead of an `mdTypeDef` metadata token can have unpredictable results; callers should resolve the `mdTypeRef` to an `mdTypeDef` when passing it.</span></span>  
  
 <span data-ttu-id="41e90-115">如果尚未載入的型別，則呼叫`GetClassFromTokenAndTypeArgs`會觸發載入，而這是危險的作業在許多內容中。</span><span class="sxs-lookup"><span data-stu-id="41e90-115">If the type is not already loaded, calling `GetClassFromTokenAndTypeArgs` will trigger loading, which is a dangerous operation in many contexts.</span></span> <span data-ttu-id="41e90-116">例如，在載入模組或其他類型期間呼叫這個方法可能會導致無限迴圈循環載入嘗試執行階段。</span><span class="sxs-lookup"><span data-stu-id="41e90-116">For example, calling this method during loading of modules or other types could lead to an infinite loop as the runtime attempts to circularly load things.</span></span>  
  
 <span data-ttu-id="41e90-117">一般情況下，使用`GetClassFromTokenAndTypeArgs`建議您不要使用。</span><span class="sxs-lookup"><span data-stu-id="41e90-117">In general, use of `GetClassFromTokenAndTypeArgs` is discouraged.</span></span> <span data-ttu-id="41e90-118">如果分析工具想要針對特定類型的事件，它們應該儲存`ModuleID`並`mdTypeDef`該類型，以及使用[ICorProfilerInfo2::GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md)來檢查是否指定`ClassID`，就是所需的類型。</span><span class="sxs-lookup"><span data-stu-id="41e90-118">If profilers are interested in events for a particular type, they should store the `ModuleID` and `mdTypeDef` of that type, and use [ICorProfilerInfo2::GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md) to check whether a given `ClassID` is that of the desired type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41e90-119">需求</span><span class="sxs-lookup"><span data-stu-id="41e90-119">Requirements</span></span>  
 <span data-ttu-id="41e90-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="41e90-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41e90-121">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="41e90-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="41e90-122">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="41e90-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41e90-123">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41e90-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41e90-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41e90-124">See also</span></span>

- [<span data-ttu-id="41e90-125">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="41e90-125">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="41e90-126">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="41e90-126">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
