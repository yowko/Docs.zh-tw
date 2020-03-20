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
ms.openlocfilehash: 34d543dd76de05bdf55d8187cf192455d1387a9f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178946"
---
# <a name="icordebugcode3getreturnvalueliveoffset-method"></a><span data-ttu-id="4948d-102">ICorDebugCode3::GetReturnValueLiveOffset 方法</span><span class="sxs-lookup"><span data-stu-id="4948d-102">ICorDebugCode3::GetReturnValueLiveOffset Method</span></span>
<span data-ttu-id="4948d-103">對於指定的 IL 偏移量，獲取應放置中斷點的本機偏移，以便調試器可以從函數獲取傳回值。</span><span class="sxs-lookup"><span data-stu-id="4948d-103">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4948d-104">語法</span><span class="sxs-lookup"><span data-stu-id="4948d-104">Syntax</span></span>  
  
```cpp
HRESULT GetReturnValueLiveOffset(  
    [in] ULONG32 ILoffset,  
    [in] ULONG32 bufferSize,
    [out] ULONG32 *pFetched,
    [out, size_is(buffersize), length_is(*pFetched)] ULong32 pOffsets[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4948d-105">參數</span><span class="sxs-lookup"><span data-stu-id="4948d-105">Parameters</span></span>  
 `ILoffset`  
 <span data-ttu-id="4948d-106">IL 偏移量。</span><span class="sxs-lookup"><span data-stu-id="4948d-106">The IL offset.</span></span> <span data-ttu-id="4948d-107">它必須是函式呼叫網站，否則函式呼叫將失敗。</span><span class="sxs-lookup"><span data-stu-id="4948d-107">It must be a function call site or the function call will fail.</span></span>  
  
 `bufferSize`  
 <span data-ttu-id="4948d-108">可用於存儲`pOffsets`的位元組數。</span><span class="sxs-lookup"><span data-stu-id="4948d-108">The number of bytes available to store `pOffsets`.</span></span>  
  
 `pFetched`  
 <span data-ttu-id="4948d-109">指向實際返回的偏移量數的指標。</span><span class="sxs-lookup"><span data-stu-id="4948d-109">A pointer to the number of offsets actually returned.</span></span> <span data-ttu-id="4948d-110">通常，其值為 1，但單個 IL 指令可以映射到`CALL`多個程式集指令。</span><span class="sxs-lookup"><span data-stu-id="4948d-110">Usually, its value is 1, but a single IL instruction can map to multiple `CALL` assembly instructions.</span></span>  
  
 `pOffsets`  
 <span data-ttu-id="4948d-111">本機偏移的陣列。</span><span class="sxs-lookup"><span data-stu-id="4948d-111">An array of native offsets.</span></span> <span data-ttu-id="4948d-112">通常，`pOffsets`包含單個偏移量，儘管單個 IL 指令可以映射到多個映射到多個`CALL`程式集指令。</span><span class="sxs-lookup"><span data-stu-id="4948d-112">Typically, `pOffsets` contains a single offset, although a single IL instruction can map to multiple map to multiple `CALL` assembly instructions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4948d-113">備註</span><span class="sxs-lookup"><span data-stu-id="4948d-113">Remarks</span></span>  
 <span data-ttu-id="4948d-114">此方法與[ICorDebugILFrame3：：getReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md)方法一起使用，以獲取返回參考型別的方法的傳回值。</span><span class="sxs-lookup"><span data-stu-id="4948d-114">This method is used along with the [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) method to get the return value of a method that returns a reference type.</span></span> <span data-ttu-id="4948d-115">將 IL 偏移傳遞到函式呼叫網站到此方法返回一個或多個本機偏移。</span><span class="sxs-lookup"><span data-stu-id="4948d-115">Passing an IL offset to a function call site to this method returns one or more native offsets.</span></span> <span data-ttu-id="4948d-116">然後，調試器可以在函數中的這些本機偏移設置中斷點。</span><span class="sxs-lookup"><span data-stu-id="4948d-116">The debugger can then set breakpoints on these native offsets in the function.</span></span> <span data-ttu-id="4948d-117">當調試器到達其中一個中斷點時，您可以將傳遞給此方法的相同 IL 偏移傳遞給[ICorDebugILFrame3：：：：getReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md)方法以獲得傳回值。</span><span class="sxs-lookup"><span data-stu-id="4948d-117">When the debugger hits one of the breakpoints, you can then pass the same IL offset that you passed to this method to the [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) method to get the return value.</span></span> <span data-ttu-id="4948d-118">然後，調試器應清除它設置的所有中斷點。</span><span class="sxs-lookup"><span data-stu-id="4948d-118">The debugger should then clear all the breakpoints that it set.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="4948d-119">和`ICorDebugCode3::GetReturnValueLiveOffset` [ICorDebugILFrame3：：獲取回歸價值ForIL偏移](icordebugilframe3-getreturnvalueforiloffset-method.md)方法允許您僅獲取參考類型的傳回值資訊。</span><span class="sxs-lookup"><span data-stu-id="4948d-119">The `ICorDebugCode3::GetReturnValueLiveOffset` and [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) methods allow you to get return value information for reference types only.</span></span> <span data-ttu-id="4948d-120">不支援從數值型別（即派生自<xref:System.ValueType>的所有類型）檢索傳回值資訊。</span><span class="sxs-lookup"><span data-stu-id="4948d-120">Retrieving return value information from value types (that is, all types that derive from <xref:System.ValueType>) is not supported.</span></span>  
  
 <span data-ttu-id="4948d-121">函數返回下表中顯示的`HRESULT`值。</span><span class="sxs-lookup"><span data-stu-id="4948d-121">The function returns the `HRESULT` values shown in the following table.</span></span>  
  
|<span data-ttu-id="4948d-122">`HRESULT` 值</span><span class="sxs-lookup"><span data-stu-id="4948d-122">`HRESULT` value</span></span>|<span data-ttu-id="4948d-123">描述</span><span class="sxs-lookup"><span data-stu-id="4948d-123">Description</span></span>|  
|---------------------|-----------------|  
|`S_OK`|<span data-ttu-id="4948d-124">成功。</span><span class="sxs-lookup"><span data-stu-id="4948d-124">Success.</span></span>|  
|`CORDBG_E_INVALID_OPCODE`|<span data-ttu-id="4948d-125">給定的 IL 偏移網站不是呼叫指令，或函數返回`void`。</span><span class="sxs-lookup"><span data-stu-id="4948d-125">The given IL offset site is not a call instruction, or the function returns `void`.</span></span>|  
|`CORDBG_E_UNSUPPORTED`|<span data-ttu-id="4948d-126">給定的 IL 偏移量是適當的調用，但返回類型對於獲取傳回值不受支援。</span><span class="sxs-lookup"><span data-stu-id="4948d-126">The given IL offset is a proper call, but the return type is unsupported for getting a return value.</span></span>|  
  
 <span data-ttu-id="4948d-127">該方法`ICorDebugCode3::GetReturnValueLiveOffset`僅適用于基於 x86 和 AMD64 的系統。</span><span class="sxs-lookup"><span data-stu-id="4948d-127">The `ICorDebugCode3::GetReturnValueLiveOffset` method is available only on x86-based and AMD64 systems.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4948d-128">需求</span><span class="sxs-lookup"><span data-stu-id="4948d-128">Requirements</span></span>  
 <span data-ttu-id="4948d-129">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4948d-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4948d-130">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4948d-130">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4948d-131">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4948d-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4948d-132">**.NET 框架版本：**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4948d-132">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4948d-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4948d-133">See also</span></span>

- [<span data-ttu-id="4948d-134">GetReturnValueForILOffset 方法</span><span class="sxs-lookup"><span data-stu-id="4948d-134">GetReturnValueForILOffset Method</span></span>](icordebugilframe3-getreturnvalueforiloffset-method.md)
- [<span data-ttu-id="4948d-135">ICorDebugCode3 介面</span><span class="sxs-lookup"><span data-stu-id="4948d-135">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
