---
title: "ICorDebugCode3::GetReturnValueLiveOffset 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorDebugCode3.GetReturnValueLiveOffset
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode3::GetReturnValueLiveOffset
helpviewer_keywords:
- ICorDebugCode3::GetReturnValueLiveOffset method [.NET Framework debugging]
- GetReturnValueLiveOffset method [.NET Framework debugging]
ms.assetid: 8c2ff5d8-8c04-4423-b1e1-e1c8764b36d3
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5d10d298a031e7146eaf6cf7988538e6f7020136
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcode3getreturnvalueliveoffset-method"></a><span data-ttu-id="9b136-102">ICorDebugCode3::GetReturnValueLiveOffset 方法</span><span class="sxs-lookup"><span data-stu-id="9b136-102">ICorDebugCode3::GetReturnValueLiveOffset Method</span></span>
<span data-ttu-id="9b136-103">針對指定的 IL 位移，取得原生位移中斷點放置的位置，讓偵錯工具可以從函式取得傳回值。</span><span class="sxs-lookup"><span data-stu-id="9b136-103">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b136-104">語法</span><span class="sxs-lookup"><span data-stu-id="9b136-104">Syntax</span></span>  
  
```cpp
HRESULT GetReturnValueLiveOffset(  
    [in] ULONG32 ILoffset,  
    [in] ULONG32 bufferSize,   
    [out] ULONG32 *pFetched,   
    [out, size_is(buffersize), length_is(*pFetched)] ULong32 pOffsets[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9b136-105">參數</span><span class="sxs-lookup"><span data-stu-id="9b136-105">Parameters</span></span>  
 `ILoffset`  
 <span data-ttu-id="9b136-106">IL 位移。</span><span class="sxs-lookup"><span data-stu-id="9b136-106">The IL offset.</span></span> <span data-ttu-id="9b136-107">它必須是函式呼叫位置或函式呼叫將會失敗。</span><span class="sxs-lookup"><span data-stu-id="9b136-107">It must be a function call site or the function call will fail.</span></span>  
  
 `bufferSize`  
 <span data-ttu-id="9b136-108">可用來儲存的位元組數目`pOffsets`。</span><span class="sxs-lookup"><span data-stu-id="9b136-108">The number of bytes available to store `pOffsets`.</span></span>  
  
 `pFetched`  
 <span data-ttu-id="9b136-109">實際傳回的位移數指標。</span><span class="sxs-lookup"><span data-stu-id="9b136-109">A pointer to the number of offsets actually returned.</span></span> <span data-ttu-id="9b136-110">通常，其值為 1，但是單一的 IL 指令可以對應至多個`CALL`組譯碼指令。</span><span class="sxs-lookup"><span data-stu-id="9b136-110">Usually, its value is 1, but a single IL instruction can map to multiple `CALL` assembly instructions.</span></span>  
  
 `pOffsets`  
 <span data-ttu-id="9b136-111">原生位移的陣列。</span><span class="sxs-lookup"><span data-stu-id="9b136-111">An array of native offsets.</span></span> <span data-ttu-id="9b136-112">一般而言，`pOffsets`包含單一的位移，但是單一的 IL 指令可以對應至多個對應至多個`CALL`組譯碼指令。</span><span class="sxs-lookup"><span data-stu-id="9b136-112">Typically, `pOffsets` contains a single offset, although a single IL instruction can map to multiple map to multiple `CALL` assembly instructions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b136-113">備註</span><span class="sxs-lookup"><span data-stu-id="9b136-113">Remarks</span></span>  
 <span data-ttu-id="9b136-114">這個方法會用於[icordebugilframe3:: Getreturnvalueforiloffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)方法來取得傳回參考類型的方法的傳回值。</span><span class="sxs-lookup"><span data-stu-id="9b136-114">This method is used along with the [ICorDebugILFrame3::GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) method to get the return value of a method that returns a reference type.</span></span> <span data-ttu-id="9b136-115">傳遞的 IL 位移站可將函式呼叫這個方法會傳回一或多個原生位移。</span><span class="sxs-lookup"><span data-stu-id="9b136-115">Passing an IL offset to a function call site to this method returns one or more native offsets.</span></span> <span data-ttu-id="9b136-116">偵錯工具然後可以在這些原生位移函式中設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="9b136-116">The debugger can then set breakpoints on these native offsets in the function.</span></span> <span data-ttu-id="9b136-117">當偵錯工具叫用的其中一個中斷點時，然後您可以傳遞相同的 IL 位移傳遞到此方法以[icordebugilframe3:: Getreturnvalueforiloffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)方法來取得傳回值。</span><span class="sxs-lookup"><span data-stu-id="9b136-117">When the debugger hits one of the breakpoints, you can then pass the same IL offset that you passed to this method to the [ICorDebugILFrame3::GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) method to get the return value.</span></span> <span data-ttu-id="9b136-118">偵錯工具應再清除它所設定的所有中斷點。</span><span class="sxs-lookup"><span data-stu-id="9b136-118">The debugger should then clear all the breakpoints that it set.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="9b136-119">`ICorDebugCode3::GetReturnValueLiveOffset`和[icordebugilframe3:: Getreturnvalueforiloffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)方法可讓您取得只參考類型的傳回值資訊。</span><span class="sxs-lookup"><span data-stu-id="9b136-119">The `ICorDebugCode3::GetReturnValueLiveOffset` and [ICorDebugILFrame3::GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) methods allow you to get return value information for reference types only.</span></span> <span data-ttu-id="9b136-120">傳回值的資訊擷取實值類型 (也就是所有的型別衍生自<xref:System.ValueType>) 不支援。</span><span class="sxs-lookup"><span data-stu-id="9b136-120">Retrieving return value information from value types (that is, all types that derive from <xref:System.ValueType>) is not supported.</span></span>  
  
 <span data-ttu-id="9b136-121">此函數會傳回`HRESULT`下表所示的值。</span><span class="sxs-lookup"><span data-stu-id="9b136-121">The function returns the `HRESULT` values shown in the following table.</span></span>  
  
|<span data-ttu-id="9b136-122">`HRESULT` 值</span><span class="sxs-lookup"><span data-stu-id="9b136-122">`HRESULT` value</span></span>|<span data-ttu-id="9b136-123">描述</span><span class="sxs-lookup"><span data-stu-id="9b136-123">Description</span></span>|  
|---------------------|-----------------|  
|`S_OK`|<span data-ttu-id="9b136-124">成功。</span><span class="sxs-lookup"><span data-stu-id="9b136-124">Success.</span></span>|  
|`CORDBG_E_INVALID_OPCODE`|<span data-ttu-id="9b136-125">給定的 IL 位移的網站不是呼叫的指示，或函式會傳回`void`。</span><span class="sxs-lookup"><span data-stu-id="9b136-125">The given IL offset site is not a call instruction, or the function returns `void`.</span></span>|  
|`CORDBG_E_UNSUPPORTED`|<span data-ttu-id="9b136-126">指定的 IL 位移有適當的呼叫，但傳回型別不支援以取得傳回值。</span><span class="sxs-lookup"><span data-stu-id="9b136-126">The given IL offset is a proper call, but the return type is unsupported for getting a return value.</span></span>|  
  
 <span data-ttu-id="9b136-127">`ICorDebugCode3::GetReturnValueLiveOffset`方法是僅可在 x86 型和 AMD64 系統。</span><span class="sxs-lookup"><span data-stu-id="9b136-127">The `ICorDebugCode3::GetReturnValueLiveOffset` method is available only on x86-based and AMD64 systems.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b136-128">需求</span><span class="sxs-lookup"><span data-stu-id="9b136-128">Requirements</span></span>  
 <span data-ttu-id="9b136-129">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9b136-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b136-130">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9b136-130">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9b136-131">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b136-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b136-132">**.NET framework 版本：**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b136-132">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b136-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="9b136-133">See Also</span></span>  
 [<span data-ttu-id="9b136-134">GetReturnValueForILOffset 方法</span><span class="sxs-lookup"><span data-stu-id="9b136-134">GetReturnValueForILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)  
 [<span data-ttu-id="9b136-135">ICorDebugCode3 介面</span><span class="sxs-lookup"><span data-stu-id="9b136-135">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
