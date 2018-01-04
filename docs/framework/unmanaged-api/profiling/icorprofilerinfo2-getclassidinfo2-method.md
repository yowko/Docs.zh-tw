---
title: "ICorProfilerInfo2::GetClassIDInfo2 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetClassIDInfo2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetClassIDInfo2
helpviewer_keywords:
- GetClassIDInfo2 method [.NET Framework profiling]
- ICorProfilerInfo2::GetClassIDInfo2 method [.NET Framework profiling]
ms.assetid: 0141d582-d066-4d49-8d1f-ae82129a1960
topic_type: apiref
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e0348462cdbff14486b31e1878f06b7565b47182
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getclassidinfo2-method"></a><span data-ttu-id="2e405-102">ICorProfilerInfo2::GetClassIDInfo2 方法</span><span class="sxs-lookup"><span data-stu-id="2e405-102">ICorProfilerInfo2::GetClassIDInfo2 Method</span></span>
<span data-ttu-id="2e405-103">取得父模組和中繼資料語彙基元的指定類別，開啟泛型定義`ClassID`其父類別，而`ClassID`如果有的話，類別的每個型別引數。</span><span class="sxs-lookup"><span data-stu-id="2e405-103">Gets the parent module and metadata token for the open generic definition of the specified class, the `ClassID` of its parent class, and the `ClassID` for each type argument, if present, of the class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e405-104">語法</span><span class="sxs-lookup"><span data-stu-id="2e405-104">Syntax</span></span>  
  
```  
HRESULT GetClassIDInfo2(  
    [in]  ClassID classId,  
    [out] ModuleID *pModuleId,  
    [out] mdTypeDef *pTypeDefToken,  
    [out] ClassID *pParentClassId,  
    [in]  ULONG32 cNumTypeArgs,  
    [out] ULONG32 *pcNumTypeArgs,  
    [out] ClassID typeArgs[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2e405-105">參數</span><span class="sxs-lookup"><span data-stu-id="2e405-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="2e405-106">[in] 要擷取資訊的類別 ID。</span><span class="sxs-lookup"><span data-stu-id="2e405-106">[in] The ID of the class for which information will be retrieved.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="2e405-107">[out]適用於開啟的泛型定義指定類別的父模組 ID 的指標。</span><span class="sxs-lookup"><span data-stu-id="2e405-107">[out] Pointer to the ID of the parent module for the open generic definition of the specified class.</span></span>  
  
 `pTypeDefToken`  
 <span data-ttu-id="2e405-108">[out]如需開啟泛型定義指定類別的中繼資料語彙基元指標。</span><span class="sxs-lookup"><span data-stu-id="2e405-108">[out] Pointer to the metadata token for the open generic definition of the specified class.</span></span>  
  
 `pParentClassId`  
 <span data-ttu-id="2e405-109">[out] 父類別 ID 的指標。</span><span class="sxs-lookup"><span data-stu-id="2e405-109">[out] Pointer to the ID of the parent class.</span></span>  
  
 `cNumTypeArgs`  
 <span data-ttu-id="2e405-110">[in] `typeArgs` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="2e405-110">[in] The size of the `typeArgs` array.</span></span>  
  
 `pcNumTypeArgs`  
 <span data-ttu-id="2e405-111">[out] 可用的項目總數之指標。</span><span class="sxs-lookup"><span data-stu-id="2e405-111">[out] Pointer to the total number of available elements.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="2e405-112">[out] 一組 `ClassID` 值的陣列，其中每一項各代表此類別之類型引數的 ID。</span><span class="sxs-lookup"><span data-stu-id="2e405-112">[out] An array of `ClassID` values, each of which represents the ID of a type argument of the class.</span></span> <span data-ttu-id="2e405-113">方法傳回時， `typeArgs` 將包含部分或所有可用的 `ClassID` 值。</span><span class="sxs-lookup"><span data-stu-id="2e405-113">When the method returns, `typeArgs` will contain some or all the available `ClassID` values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e405-114">備註</span><span class="sxs-lookup"><span data-stu-id="2e405-114">Remarks</span></span>  
 <span data-ttu-id="2e405-115">`GetClassIDInfo2`方法很類似[icorprofilerinfo:: Getclassidinfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md)方法，但`GetClassIDInfo2`取得泛型類型的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="2e405-115">The `GetClassIDInfo2` method is similar to the [ICorProfilerInfo::GetClassIDInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md) method, but `GetClassIDInfo2` obtains additional information about a generic type.</span></span>  
  
 <span data-ttu-id="2e405-116">分析工具程式碼可以呼叫[icorprofilerinfo:: Getmodulemetadata](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md)取得[中繼資料](../../../../docs/framework/unmanaged-api/metadata/index.md)提供之模組的介面。</span><span class="sxs-lookup"><span data-stu-id="2e405-116">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a [metadata](../../../../docs/framework/unmanaged-api/metadata/index.md) interface for a given module.</span></span> <span data-ttu-id="2e405-117">然後，傳回至 `pTypeDefToken` 所參考位置的中繼資料語彙基元可以用來存取此類別的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="2e405-117">The metadata token that is returned to the location referenced by `pTypeDefToken` can then be used to access the metadata for the class.</span></span>  
  
 <span data-ttu-id="2e405-118">`GetClassIDInfo2` 傳回之後，您必須確認 `typeArgs` 緩衝區夠大，以包含所有 `ClassID` 的值。</span><span class="sxs-lookup"><span data-stu-id="2e405-118">After `GetClassIDInfo2` returns, you must verify that the `typeArgs` buffer was large enough to contain all the `ClassID` values.</span></span> <span data-ttu-id="2e405-119">若要這樣做，請比對 `pcNumTypeArgs` 指向的值和 `cNumTypeArgs` 參數。</span><span class="sxs-lookup"><span data-stu-id="2e405-119">To do this, compare the value that `pcNumTypeArgs` points to with the value of the `cNumTypeArgs` parameter.</span></span> <span data-ttu-id="2e405-120">如果 `pcNumTypeArgs` 指向大於 `cNumTypeArgs` 的值，請配置較大的 `typeArgs` 緩衝區，並以較大的大小來更新 `cNumTypeArgs`，然後再次呼叫 `GetClassIDInfo2`。</span><span class="sxs-lookup"><span data-stu-id="2e405-120">If `pcNumTypeArgs` points to a value that is larger than `cNumTypeArgs`, allocate a larger `typeArgs` buffer, update `cNumTypeArgs` with the new, larger size, and call `GetClassIDInfo2` again.</span></span>  
  
 <span data-ttu-id="2e405-121">此外，您可以先使用長度為零的 `typeArgs` 緩衝區來呼叫 `GetClassIDInfo2`，以取得正確的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="2e405-121">Alternatively, you can first call `GetClassIDInfo2` with a zero-length `typeArgs` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="2e405-122">然後您可以設定 `typeArgs` 緩衝區大小為在 `pcNumTypeArgs` 中傳回的值，並且再呼叫 `GetClassIDInfo2` 一次。</span><span class="sxs-lookup"><span data-stu-id="2e405-122">You can then set the `typeArgs` buffer size to the value returned in `pcNumTypeArgs` and call `GetClassIDInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e405-123">需求</span><span class="sxs-lookup"><span data-stu-id="2e405-123">Requirements</span></span>  
 <span data-ttu-id="2e405-124">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2e405-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e405-125">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2e405-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2e405-126">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2e405-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e405-127">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e405-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e405-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="2e405-128">See Also</span></span>  
 [<span data-ttu-id="2e405-129">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="2e405-129">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="2e405-130">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="2e405-130">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [<span data-ttu-id="2e405-131">分析介面</span><span class="sxs-lookup"><span data-stu-id="2e405-131">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="2e405-132">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="2e405-132">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
