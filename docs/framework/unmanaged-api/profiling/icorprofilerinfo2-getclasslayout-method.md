---
title: ICorProfilerInfo2::GetClassLayout 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassLayout
helpviewer_keywords:
- ICorProfilerInfo2::GetClassLayout method [.NET Framework profiling]
- GetClassLayout method, ICorProfilerInfo2 interface [.NET Framework profiling]
ms.assetid: a3a36987-5666-4e2f-95b5-d0cb246502ec
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f5995eac780241b5d0a01b99b23ec91c2f325e2a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478800"
---
# <a name="icorprofilerinfo2getclasslayout-method"></a><span data-ttu-id="969d1-102">ICorProfilerInfo2::GetClassLayout 方法</span><span class="sxs-lookup"><span data-stu-id="969d1-102">ICorProfilerInfo2::GetClassLayout Method</span></span>
<span data-ttu-id="969d1-103">取得在記憶體中指定類別所定義欄位的配置相關資訊。</span><span class="sxs-lookup"><span data-stu-id="969d1-103">Gets information about the layout, in memory, of the fields defined by the specified class.</span></span> <span data-ttu-id="969d1-104">也就是說，這個方法會取得此類別的欄位之位移。</span><span class="sxs-lookup"><span data-stu-id="969d1-104">That is, this method gets the offsets of the class's fields.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="969d1-105">語法</span><span class="sxs-lookup"><span data-stu-id="969d1-105">Syntax</span></span>  
  
```  
HRESULT GetClassLayout(  
    [in]  ClassID classID,  
    [in, out] COR_FIELD_OFFSET rFieldOffset[],  
    [in]  ULONG cFieldOffset,  
    [out] ULONG *pcFieldOffset,  
    [out] ULONG *pulClassSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="969d1-106">參數</span><span class="sxs-lookup"><span data-stu-id="969d1-106">Parameters</span></span>  
 `classID`  
 <span data-ttu-id="969d1-107">[in] 要擷取配置的類別 ID。</span><span class="sxs-lookup"><span data-stu-id="969d1-107">[in] The ID of the class for which the layout will be retrieved.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="969d1-108">[in、 out]陣列[COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md)結構，每個均包含語彙基元和位移類別的欄位。</span><span class="sxs-lookup"><span data-stu-id="969d1-108">[in, out] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) structures, each of which contains the tokens and offsets of the class's fields.</span></span>  
  
 `cFieldOffset`  
 <span data-ttu-id="969d1-109">[in] `rFieldOffset` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="969d1-109">[in] The size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="969d1-110">[out] 可用的項目總數之指標。</span><span class="sxs-lookup"><span data-stu-id="969d1-110">[out] A pointer to the total number of available elements.</span></span> <span data-ttu-id="969d1-111">如果 `cFieldOffset` 是 0，則這個值表示所需的項目數目。</span><span class="sxs-lookup"><span data-stu-id="969d1-111">If `cFieldOffset` is 0, this value indicates the number of elements needed.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="969d1-112">[out] 位置指標，其中包含此類別的大小，以位元組為單位。</span><span class="sxs-lookup"><span data-stu-id="969d1-112">[out] A pointer to a location that contains the size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="969d1-113">備註</span><span class="sxs-lookup"><span data-stu-id="969d1-113">Remarks</span></span>  
 <span data-ttu-id="969d1-114">
  `GetClassLayout\` 方法僅傳回類別本身所定義的欄位。</span><span class="sxs-lookup"><span data-stu-id="969d1-114">The `GetClassLayout` method returns only the fields defined by the class itself.</span></span> <span data-ttu-id="969d1-115">如果類別的父類別也已經定義欄位，則分析工具必須呼叫父類別上的 `GetClassLayout` 來取得那些欄位。</span><span class="sxs-lookup"><span data-stu-id="969d1-115">If the class's parent class has defined fields as well, the profiler must call `GetClassLayout` on the parent class to obtain those fields.</span></span>  
  
 <span data-ttu-id="969d1-116">如果您搭配字串類別使用 `GetClassLayout`，則該方法會失敗，伴隨錯誤碼 E_INVALIDARG。</span><span class="sxs-lookup"><span data-stu-id="969d1-116">If you use `GetClassLayout` with string classes, the method will fail with error code E_INVALIDARG.</span></span> <span data-ttu-id="969d1-117">使用[ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md)取得版面配置資訊的字串。</span><span class="sxs-lookup"><span data-stu-id="969d1-117">Use [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) to get information about the layout of a string.</span></span> <span data-ttu-id="969d1-118">以陣列類別呼叫 `GetClassLayout` 時也會失敗。</span><span class="sxs-lookup"><span data-stu-id="969d1-118">`GetClassLayout` will also fail when called with an array class.</span></span>  
  
 <span data-ttu-id="969d1-119">`GetClassLayout` 傳回之後，您必須確認 `rFieldOffset` 緩衝區夠大，可以包含所有可用的 `COR_FIELD_OFFSET` 結構。</span><span class="sxs-lookup"><span data-stu-id="969d1-119">After `GetClassLayout` returns, you must verify that the `rFieldOffset` buffer was large enough to contain all the available `COR_FIELD_OFFSET` structures.</span></span> <span data-ttu-id="969d1-120">若要這樣做，比對 `pcFieldOffset` 指向的值和 `rFieldOffset` 的大小除以 `COR_FIELD_OFFSET` 的結構大小。</span><span class="sxs-lookup"><span data-stu-id="969d1-120">To do this, compare the value that `pcFieldOffset` points to with the size of `rFieldOffset` divided by the size of a `COR_FIELD_OFFSET` structure.</span></span> <span data-ttu-id="969d1-121">如果 `rFieldOffset` 不夠大，則請配置一個更大的 `rFieldOffset` 緩衝區，以新的、較大的大小來更新 `cFieldOffset`，然後再呼叫 `GetClassLayout` 一次。</span><span class="sxs-lookup"><span data-stu-id="969d1-121">If `rFieldOffset` is not large enough, allocate a larger `rFieldOffset` buffer, update `cFieldOffset` with the new, larger size, and call `GetClassLayout` again.</span></span>  
  
 <span data-ttu-id="969d1-122">此外，您可以先使用長度為零的 `rFieldOffset` 緩衝區來呼叫 `GetClassLayout`，以取得正確的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="969d1-122">Alternatively, you can first call `GetClassLayout` with a zero-length `rFieldOffset` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="969d1-123">接著您就可以將緩衝區大小設定為 `pcFieldOffset` 中傳回的值，並再次呼叫 `GetClassLayout`。</span><span class="sxs-lookup"><span data-stu-id="969d1-123">You can then set the buffer size to the value returned in `pcFieldOffset` and call `GetClassLayout` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="969d1-124">需求</span><span class="sxs-lookup"><span data-stu-id="969d1-124">Requirements</span></span>  
 <span data-ttu-id="969d1-125">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="969d1-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="969d1-126">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="969d1-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="969d1-127">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="969d1-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="969d1-128">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="969d1-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="969d1-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="969d1-129">See also</span></span>
- [<span data-ttu-id="969d1-130">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="969d1-130">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="969d1-131">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="969d1-131">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [<span data-ttu-id="969d1-132">分析介面</span><span class="sxs-lookup"><span data-stu-id="969d1-132">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="969d1-133">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="969d1-133">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
