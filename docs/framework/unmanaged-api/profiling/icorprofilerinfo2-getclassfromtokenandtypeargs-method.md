---
title: "ICorProfilerInfo2::GetClassFromTokenAndTypeArgs 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5a459f8e9ec6d63dc42d6a0a8f752c129d278524
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getclassfromtokenandtypeargs-method"></a><span data-ttu-id="5d56a-102">ICorProfilerInfo2::GetClassFromTokenAndTypeArgs 方法</span><span class="sxs-lookup"><span data-stu-id="5d56a-102">ICorProfilerInfo2::GetClassFromTokenAndTypeArgs Method</span></span>
<span data-ttu-id="5d56a-103">取得`ClassID`使用指定的中繼資料語彙基元的類型和`ClassID`值的任何型別引數。</span><span class="sxs-lookup"><span data-stu-id="5d56a-103">Gets the `ClassID` of a type by using the specified metadata token and the `ClassID` values of any type arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d56a-104">語法</span><span class="sxs-lookup"><span data-stu-id="5d56a-104">Syntax</span></span>  
  
```  
HRESULT GetClassFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdTypeDef typeDef,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] ClassID* pClassID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5d56a-105">參數</span><span class="sxs-lookup"><span data-stu-id="5d56a-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="5d56a-106">[in]型別所在之模組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="5d56a-106">[in] The ID of the module in which the type resides.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="5d56a-107">[in]`mdTypeDef`參考該類型的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="5d56a-107">[in] An `mdTypeDef` metadata token that references the type.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="5d56a-108">[in]給定類型的型別參數數目。</span><span class="sxs-lookup"><span data-stu-id="5d56a-108">[in] The number of type parameters for the given type.</span></span> <span data-ttu-id="5d56a-109">此值必須是零的非泛型型別。</span><span class="sxs-lookup"><span data-stu-id="5d56a-109">This value must be zero for non-generic types.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="5d56a-110">[in]陣列`ClassID`每一個都是類型的引數的值。</span><span class="sxs-lookup"><span data-stu-id="5d56a-110">[in] An array of `ClassID` values, each of which is an argument of the type.</span></span> <span data-ttu-id="5d56a-111">值`typeArgs`可以是 NULL，如果`cTypeArgs`設為零。</span><span class="sxs-lookup"><span data-stu-id="5d56a-111">The value of `typeArgs` can be NULL if `cTypeArgs` is set to zero.</span></span>  
  
 `pClassID`  
 <span data-ttu-id="5d56a-112">[out]指標`ClassID`指定的型別。</span><span class="sxs-lookup"><span data-stu-id="5d56a-112">[out] A pointer to the `ClassID` of the specified type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d56a-113">備註</span><span class="sxs-lookup"><span data-stu-id="5d56a-113">Remarks</span></span>  
 <span data-ttu-id="5d56a-114">呼叫`GetClassFromTokenAndTypeArgs`方法`mdTypeRef`而不是`mdTypeDef`中繼資料語彙基元可以有無法預期的結果，呼叫端應該解決`mdTypeRef`至`mdTypeDef`時將傳遞給它。</span><span class="sxs-lookup"><span data-stu-id="5d56a-114">Calling the `GetClassFromTokenAndTypeArgs` method with an `mdTypeRef` instead of an `mdTypeDef` metadata token can have unpredictable results; callers should resolve the `mdTypeRef` to an `mdTypeDef` when passing it.</span></span>  
  
 <span data-ttu-id="5d56a-115">如果尚未載入的型別，則呼叫`GetClassFromTokenAndTypeArgs`將會觸發載入，這可能會有危險的作業，許多內容中。</span><span class="sxs-lookup"><span data-stu-id="5d56a-115">If the type is not already loaded, calling `GetClassFromTokenAndTypeArgs` will trigger loading, which is a dangerous operation in many contexts.</span></span> <span data-ttu-id="5d56a-116">例如，呼叫這個方法期間載入模組或其他類型可能會導致無限迴圈因為執行階段嘗試循環載入。</span><span class="sxs-lookup"><span data-stu-id="5d56a-116">For example, calling this method during loading of modules or other types could lead to an infinite loop as the runtime attempts to circularly load things.</span></span>  
  
 <span data-ttu-id="5d56a-117">一般情況下，使用`GetClassFromTokenAndTypeArgs`不建議使用。</span><span class="sxs-lookup"><span data-stu-id="5d56a-117">In general, use of `GetClassFromTokenAndTypeArgs` is discouraged.</span></span> <span data-ttu-id="5d56a-118">如果分析工具想要特定類型的事件中，它們應該儲存`ModuleID`和`mdTypeDef`該型別，且使用[icorprofilerinfo2:: Getclassidinfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md)來檢查是否指定`ClassID`，就是所需的類型。</span><span class="sxs-lookup"><span data-stu-id="5d56a-118">If profilers are interested in events for a particular type, they should store the `ModuleID` and `mdTypeDef` of that type, and use [ICorProfilerInfo2::GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md) to check whether a given `ClassID` is that of the desired type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d56a-119">需求</span><span class="sxs-lookup"><span data-stu-id="5d56a-119">Requirements</span></span>  
 <span data-ttu-id="5d56a-120">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5d56a-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d56a-121">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5d56a-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5d56a-122">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5d56a-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d56a-123">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d56a-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d56a-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="5d56a-124">See Also</span></span>  
 [<span data-ttu-id="5d56a-125">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="5d56a-125">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="5d56a-126">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="5d56a-126">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
