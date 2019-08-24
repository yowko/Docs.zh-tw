---
title: ICorDebugCode3::GetReturnValueLiveOffset 方法
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugCode3.GetReturnValueLiveOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode3::GetReturnValueLiveOffset
helpviewer_keywords:
- ICorDebugCode3::GetReturnValueLiveOffset method [.NET Framework debugging]
- GetReturnValueLiveOffset method [.NET Framework debugging]
ms.assetid: 8c2ff5d8-8c04-4423-b1e1-e1c8764b36d3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5aa53d1c9d101544f532c51f43a8b47143117813
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988283"
---
# <a name="icordebugcode3getreturnvalueliveoffset-method"></a><span data-ttu-id="91d57-102">ICorDebugCode3::GetReturnValueLiveOffset 方法</span><span class="sxs-lookup"><span data-stu-id="91d57-102">ICorDebugCode3::GetReturnValueLiveOffset Method</span></span>
<span data-ttu-id="91d57-103">針對指定的 IL 位移, 取得應放置中斷點的原生位移, 讓偵錯工具可以從函數取得傳回值。</span><span class="sxs-lookup"><span data-stu-id="91d57-103">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91d57-104">語法</span><span class="sxs-lookup"><span data-stu-id="91d57-104">Syntax</span></span>  
  
```cpp
HRESULT GetReturnValueLiveOffset(  
    [in] ULONG32 ILoffset,  
    [in] ULONG32 bufferSize,   
    [out] ULONG32 *pFetched,   
    [out, size_is(buffersize), length_is(*pFetched)] ULong32 pOffsets[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91d57-105">參數</span><span class="sxs-lookup"><span data-stu-id="91d57-105">Parameters</span></span>  
 `ILoffset`  
 <span data-ttu-id="91d57-106">IL 位移。</span><span class="sxs-lookup"><span data-stu-id="91d57-106">The IL offset.</span></span> <span data-ttu-id="91d57-107">它必須是函式呼叫網站, 否則函式呼叫將會失敗。</span><span class="sxs-lookup"><span data-stu-id="91d57-107">It must be a function call site or the function call will fail.</span></span>  
  
 `bufferSize`  
 <span data-ttu-id="91d57-108">可供儲存`pOffsets`的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="91d57-108">The number of bytes available to store `pOffsets`.</span></span>  
  
 `pFetched`  
 <span data-ttu-id="91d57-109">實際傳回之位移數目的指標。</span><span class="sxs-lookup"><span data-stu-id="91d57-109">A pointer to the number of offsets actually returned.</span></span> <span data-ttu-id="91d57-110">通常, 其值為 1, 但單一 IL 指令可以對應到多個`CALL`元件指令。</span><span class="sxs-lookup"><span data-stu-id="91d57-110">Usually, its value is 1, but a single IL instruction can map to multiple `CALL` assembly instructions.</span></span>  
  
 `pOffsets`  
 <span data-ttu-id="91d57-111">原生位移的陣列。</span><span class="sxs-lookup"><span data-stu-id="91d57-111">An array of native offsets.</span></span> <span data-ttu-id="91d57-112">通常會`CALL`包含單一位移, 雖然單一 IL 指令可對應至多個對應至多個元件指令。 `pOffsets`</span><span class="sxs-lookup"><span data-stu-id="91d57-112">Typically, `pOffsets` contains a single offset, although a single IL instruction can map to multiple map to multiple `CALL` assembly instructions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91d57-113">備註</span><span class="sxs-lookup"><span data-stu-id="91d57-113">Remarks</span></span>  
 <span data-ttu-id="91d57-114">這個方法會與[ICorDebugILFrame3:: GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)方法搭配使用, 以取得傳回參考型別之方法的傳回值。</span><span class="sxs-lookup"><span data-stu-id="91d57-114">This method is used along with the [ICorDebugILFrame3::GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) method to get the return value of a method that returns a reference type.</span></span> <span data-ttu-id="91d57-115">將 IL 位移傳遞給這個方法的函式呼叫網站, 會傳回一或多個原生位移。</span><span class="sxs-lookup"><span data-stu-id="91d57-115">Passing an IL offset to a function call site to this method returns one or more native offsets.</span></span> <span data-ttu-id="91d57-116">然後偵錯工具可以在函式中的這些原生位移上設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="91d57-116">The debugger can then set breakpoints on these native offsets in the function.</span></span> <span data-ttu-id="91d57-117">當偵錯工具到達其中一個中斷點時, 您就可以將傳遞給這個方法的相同 IL 位移傳遞給[ICorDebugILFrame3:: GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)方法, 以取得傳回值。</span><span class="sxs-lookup"><span data-stu-id="91d57-117">When the debugger hits one of the breakpoints, you can then pass the same IL offset that you passed to this method to the [ICorDebugILFrame3::GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) method to get the return value.</span></span> <span data-ttu-id="91d57-118">偵錯工具應該會清除它所設定的所有中斷點。</span><span class="sxs-lookup"><span data-stu-id="91d57-118">The debugger should then clear all the breakpoints that it set.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="91d57-119">和 ICorDebugILFrame3 [:: GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)方法可讓您只取得參考型別的傳回值資訊。 `ICorDebugCode3::GetReturnValueLiveOffset`</span><span class="sxs-lookup"><span data-stu-id="91d57-119">The `ICorDebugCode3::GetReturnValueLiveOffset` and [ICorDebugILFrame3::GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) methods allow you to get return value information for reference types only.</span></span> <span data-ttu-id="91d57-120">不支援從實數值型別 (也就是衍生自<xref:System.ValueType>的所有類型) 中抓取傳回值資訊。</span><span class="sxs-lookup"><span data-stu-id="91d57-120">Retrieving return value information from value types (that is, all types that derive from <xref:System.ValueType>) is not supported.</span></span>  
  
 <span data-ttu-id="91d57-121">函數會傳回下`HRESULT`表所示的值。</span><span class="sxs-lookup"><span data-stu-id="91d57-121">The function returns the `HRESULT` values shown in the following table.</span></span>  
  
|<span data-ttu-id="91d57-122">`HRESULT` 值</span><span class="sxs-lookup"><span data-stu-id="91d57-122">`HRESULT` value</span></span>|<span data-ttu-id="91d57-123">說明</span><span class="sxs-lookup"><span data-stu-id="91d57-123">Description</span></span>|  
|---------------------|-----------------|  
|`S_OK`|<span data-ttu-id="91d57-124">成功。</span><span class="sxs-lookup"><span data-stu-id="91d57-124">Success.</span></span>|  
|`CORDBG_E_INVALID_OPCODE`|<span data-ttu-id="91d57-125">給定的 IL 位移網站不是呼叫指示, 或函數`void`傳回。</span><span class="sxs-lookup"><span data-stu-id="91d57-125">The given IL offset site is not a call instruction, or the function returns `void`.</span></span>|  
|`CORDBG_E_UNSUPPORTED`|<span data-ttu-id="91d57-126">給定的 IL 位移是適當的呼叫, 但不支援傳回類型來取得傳回值。</span><span class="sxs-lookup"><span data-stu-id="91d57-126">The given IL offset is a proper call, but the return type is unsupported for getting a return value.</span></span>|  
  
 <span data-ttu-id="91d57-127">`ICorDebugCode3::GetReturnValueLiveOffset`方法僅適用于 x86 型和 AMD64 系統。</span><span class="sxs-lookup"><span data-stu-id="91d57-127">The `ICorDebugCode3::GetReturnValueLiveOffset` method is available only on x86-based and AMD64 systems.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91d57-128">需求</span><span class="sxs-lookup"><span data-stu-id="91d57-128">Requirements</span></span>  
 <span data-ttu-id="91d57-129">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="91d57-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91d57-130">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="91d57-130">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="91d57-131">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91d57-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91d57-132">**.NET framework 版本：** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91d57-132">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91d57-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91d57-133">See also</span></span>

- [<span data-ttu-id="91d57-134">GetReturnValueForILOffset 方法</span><span class="sxs-lookup"><span data-stu-id="91d57-134">GetReturnValueForILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)
- [<span data-ttu-id="91d57-135">ICorDebugCode3 介面</span><span class="sxs-lookup"><span data-stu-id="91d57-135">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
