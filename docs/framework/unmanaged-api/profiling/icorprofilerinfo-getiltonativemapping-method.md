---
title: ICorProfilerInfo::GetILToNativeMapping 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetILToNativeMapping
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetILToNativeMapping
helpviewer_keywords:
- GetILToNativeMapping method, ICorProfilerInfo interface [.NET Framework profiling]
- ICorProfilerInfo::GetILToNativeMapping method [.NET Framework profiling]
ms.assetid: 6a5431ef-22fb-4e53-bac5-703986297eb1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ea471f5ebaab93c60847ad60ea0125baa01d8b3a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569020"
---
# <a name="icorprofilerinfogetiltonativemapping-method"></a><span data-ttu-id="fd837-102">ICorProfilerInfo::GetILToNativeMapping 方法</span><span class="sxs-lookup"><span data-stu-id="fd837-102">ICorProfilerInfo::GetILToNativeMapping Method</span></span>
<span data-ttu-id="fd837-103">針對指定的函式中所包含的程式碼，取得從 Microsoft Intermediate Language (MSIL) 位移到原生位移的對應。</span><span class="sxs-lookup"><span data-stu-id="fd837-103">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd837-104">語法</span><span class="sxs-lookup"><span data-stu-id="fd837-104">Syntax</span></span>  
  
```  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fd837-105">參數</span><span class="sxs-lookup"><span data-stu-id="fd837-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="fd837-106">[in] 包含程式碼的函式 ID。</span><span class="sxs-lookup"><span data-stu-id="fd837-106">[in] The ID of the function that contains the code.</span></span>  
  
 `cMap`  
 <span data-ttu-id="fd837-107">[in] `map` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="fd837-107">[in] The maximum size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="fd837-108">[out]可用的 COR_DEBUG_IL_TO_NATIVE_MAP 結構總數。</span><span class="sxs-lookup"><span data-stu-id="fd837-108">[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>  
  
 `map`  
 <span data-ttu-id="fd837-109">[out] `COR_DEBUG_IL_TO_NATIVE_MAP` 結構的陣列，每個結構都有指定位移。</span><span class="sxs-lookup"><span data-stu-id="fd837-109">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which specifies the offsets.</span></span> <span data-ttu-id="fd837-110">`GetILToNativeMapping` 方法傳回之後，`map` 將會包含部分或所有 `COR_DEBUG_IL_TO_NATIVE_MAP` 結構。</span><span class="sxs-lookup"><span data-stu-id="fd837-110">After the `GetILToNativeMapping` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd837-111">備註</span><span class="sxs-lookup"><span data-stu-id="fd837-111">Remarks</span></span>  
 <span data-ttu-id="fd837-112">`GetILToNativeMapping` 方法會傳回 `COR_DEBUG_IL_TO_NATIVE_MAP` 結構的陣列。</span><span class="sxs-lookup"><span data-stu-id="fd837-112">The `GetILToNativeMapping` method returns an array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="fd837-113">陣列中的項目可以有傳達原生指令的特定範圍對應至特殊的區域，程式碼 （例如，初構），其`ilOffset`欄位設定為值[CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="fd837-113">To convey that certain ranges of native instructions correspond to special regions of code (for example, the prolog), an entry in the array can have its `ilOffset` field set to a value of the [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="fd837-114">傳回 `GetILToNativeMapping` 之後，您必須確認 `map` 緩衝區夠大，足以包含所有 `COR_DEBUG_IL_TO_NATIVE_MAP` 結構。</span><span class="sxs-lookup"><span data-stu-id="fd837-114">After `GetILToNativeMapping` returns, you must verify that the `map` buffer was large enough to contain all the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="fd837-115">若要執行這項作業，請比較 `cMap` 的值和 `pcMap` 參數的值。</span><span class="sxs-lookup"><span data-stu-id="fd837-115">To do this, compare the value of `cMap` with the value of the `pcMap` parameter.</span></span> <span data-ttu-id="fd837-116">如果 `pcMap` 值乘以 `COR_DEBUG_IL_TO_NATIVE_MAP` 結構的大小之後大於 `cMap`，請配置較大的 `map` 緩衝區，以新的較大大小更新 `cMap`，然後重新呼叫 `GetILToNativeMapping`。</span><span class="sxs-lookup"><span data-stu-id="fd837-116">If the `pcMap` value, when it is multiplied by the size of a `COR_DEBUG_IL_TO_NATIVE_MAP` structure, is larger than `cMap`, allocate a larger `map` buffer, update `cMap` with the new, larger size, and call `GetILToNativeMapping` again.</span></span>  
  
 <span data-ttu-id="fd837-117">或者，您也可以先使用長度為零的 `map` 緩衝區來呼叫 `GetILToNativeMapping`，以取得正確的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="fd837-117">Alternatively, you can first call `GetILToNativeMapping` with a zero-length `map` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="fd837-118">接著您就可以將緩衝區大小設定為 `pcMap` 中傳回的值，並再次呼叫 `GetILToNativeMapping`。</span><span class="sxs-lookup"><span data-stu-id="fd837-118">You can then set the buffer size to the value returned in `pcMap` and call `GetILToNativeMapping` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd837-119">需求</span><span class="sxs-lookup"><span data-stu-id="fd837-119">Requirements</span></span>  
 <span data-ttu-id="fd837-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fd837-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd837-121">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fd837-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fd837-122">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fd837-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fd837-123">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd837-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd837-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd837-124">See also</span></span>
- [<span data-ttu-id="fd837-125">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="fd837-125">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="fd837-126">GetILToNativeMapping2 方法</span><span class="sxs-lookup"><span data-stu-id="fd837-126">GetILToNativeMapping2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)
- [<span data-ttu-id="fd837-127">分析介面</span><span class="sxs-lookup"><span data-stu-id="fd837-127">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="fd837-128">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="fd837-128">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
