---
title: ICorDebugILFrame3::GetReturnValueForILOffset 方法
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
api_name:
- ICorDebugILFrame3.GetReturnValueForILOffset
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 06522727-5f64-4391-9331-11386883c352
topic_type:
- apiref
ms.openlocfilehash: 0d1ef6c1369fd399f5b36b24a21c4b5d7f1e80fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178820"
---
# <a name="icordebugilframe3getreturnvalueforiloffset-method"></a><span data-ttu-id="a7e9e-102">ICorDebugILFrame3::GetReturnValueForILOffset 方法</span><span class="sxs-lookup"><span data-stu-id="a7e9e-102">ICorDebugILFrame3::GetReturnValueForILOffset Method</span></span>
<span data-ttu-id="a7e9e-103">獲取封裝函數傳回值的"ICorDebugValue"物件。</span><span class="sxs-lookup"><span data-stu-id="a7e9e-103">Gets an "ICorDebugValue" object that encapsulates the return value of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7e9e-104">語法</span><span class="sxs-lookup"><span data-stu-id="a7e9e-104">Syntax</span></span>  
  
```cpp
HRESULT GetReturnValueForILOffset(  
    ULONG32 ILoffset,
    [out] ICorDebugValue **ppReturnValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7e9e-105">參數</span><span class="sxs-lookup"><span data-stu-id="a7e9e-105">Parameters</span></span>  
 `ILOffset`  
 <span data-ttu-id="a7e9e-106">IL 偏移量。</span><span class="sxs-lookup"><span data-stu-id="a7e9e-106">The IL offset.</span></span> <span data-ttu-id="a7e9e-107">請參閱＜備註＞一節。</span><span class="sxs-lookup"><span data-stu-id="a7e9e-107">See the Remarks section.</span></span>  
  
 `ppReturnValue`  
 <span data-ttu-id="a7e9e-108">指向"ICorDebugValue"介面物件的位址的指標，該物件提供有關函式呼叫的傳回值的資訊。</span><span class="sxs-lookup"><span data-stu-id="a7e9e-108">A pointer to the address of an "ICorDebugValue" interface object that provides information about the return value of a function call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7e9e-109">備註</span><span class="sxs-lookup"><span data-stu-id="a7e9e-109">Remarks</span></span>  
 <span data-ttu-id="a7e9e-110">此方法與[ICorDebugCode3：：getReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md)方法一起使用，以獲得方法的傳回值。</span><span class="sxs-lookup"><span data-stu-id="a7e9e-110">This method is used along with the [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) method to get the return value of a method.</span></span> <span data-ttu-id="a7e9e-111">對於傳回值被忽略的方法，它特別有用，如下兩個代碼示例所示。</span><span class="sxs-lookup"><span data-stu-id="a7e9e-111">It is particularly useful in the case of methods whose return values are ignored, as in the following two code examples.</span></span> <span data-ttu-id="a7e9e-112">第一個示例調用<xref:System.Int32.TryParse%2A?displayProperty=nameWithType>方法，但忽略該方法的傳回值。</span><span class="sxs-lookup"><span data-stu-id="a7e9e-112">The first example calls the <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> method, but ignores the method's return value.</span></span>  
  
 [!code-csharp[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv1.cs#1)]
 [!code-vb[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv1.vb#1)]  
  
 <span data-ttu-id="a7e9e-113">第二個示例說明了調試中更常見的問題。</span><span class="sxs-lookup"><span data-stu-id="a7e9e-113">The second example illustrates a much more common problem in debugging.</span></span> <span data-ttu-id="a7e9e-114">由於方法在方法調用中用作參數，因此僅當調試器通過調用的方法時，才能訪問其傳回值。</span><span class="sxs-lookup"><span data-stu-id="a7e9e-114">Because a method is used as an argument in a method call, its return value is accessible only when the debugger steps through the called method.</span></span> <span data-ttu-id="a7e9e-115">在許多情況下，尤其是在外部庫中定義被調用的方法時，這是不可能的。</span><span class="sxs-lookup"><span data-stu-id="a7e9e-115">In many cases, particularly when the called method is defined in an external library, that is not possible.</span></span>  
  
 [!code-csharp[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv2.cs#2)]
 [!code-vb[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv2.vb#2)]  
  
 <span data-ttu-id="a7e9e-116">如果將[ICorDebugCode3：：獲取返回ValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md)方法 IL 偏移傳遞給函式呼叫網站，它將返回一個或多個本機偏移。</span><span class="sxs-lookup"><span data-stu-id="a7e9e-116">If you pass the [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) method an IL offset to a function call site, it returns one or more native offsets.</span></span> <span data-ttu-id="a7e9e-117">然後，調試器可以在函數中的這些本機偏移設置中斷點。</span><span class="sxs-lookup"><span data-stu-id="a7e9e-117">The debugger can then set breakpoints on these native offsets in the function.</span></span> <span data-ttu-id="a7e9e-118">當調試器到達其中一個中斷點時，可以傳遞傳遞給此方法的相同 IL 偏移量以獲得傳回值。</span><span class="sxs-lookup"><span data-stu-id="a7e9e-118">When the debugger hits one of the breakpoints, you can then pass the same IL offset that you passed to this method to get the return value.</span></span> <span data-ttu-id="a7e9e-119">然後，調試器應清除它設置的所有中斷點。</span><span class="sxs-lookup"><span data-stu-id="a7e9e-119">The debugger should then clear all the breakpoints that it set.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="a7e9e-120">[ICorDebugCode3：：獲取回歸價值即時偏移法](icordebugcode3-getreturnvalueliveoffset-method.md)和方法`ICorDebugILFrame3::GetReturnValueForILOffset`允許您僅獲取參考類型的傳回值資訊。</span><span class="sxs-lookup"><span data-stu-id="a7e9e-120">The [ICorDebugCode3::GetReturnValueLiveOffset Method](icordebugcode3-getreturnvalueliveoffset-method.md) and `ICorDebugILFrame3::GetReturnValueForILOffset` methods allow you to get return value information for reference types only.</span></span> <span data-ttu-id="a7e9e-121">不支援從數值型別（即派生自<xref:System.ValueType>的所有類型）檢索傳回值資訊。</span><span class="sxs-lookup"><span data-stu-id="a7e9e-121">Retrieving return value information from value types (that is, all types that derive from <xref:System.ValueType>) is not supported.</span></span>  
  
 <span data-ttu-id="a7e9e-122">`ILOffset`參數指定的 IL 偏移量應位於函式呼叫網站，調試器應在[ICorDebugCode3：getReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md)方法為同一 IL 偏移量返回的本機偏移器處的中斷點設置處停止。</span><span class="sxs-lookup"><span data-stu-id="a7e9e-122">The IL offset specified by the `ILOffset` parameter should be at a function call site, and the debuggee should be stopped at a breakpoint set at the native offset returned by the [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) method for the same IL offset.</span></span> <span data-ttu-id="a7e9e-123">如果調試器未停止在指定 IL 偏移的正確位置，則 API 將失敗。</span><span class="sxs-lookup"><span data-stu-id="a7e9e-123">If the debuggee is not stopped at the correct location for the specified IL offset, the API will fail.</span></span>  
  
 <span data-ttu-id="a7e9e-124">如果函式呼叫不傳回值，API 將失敗。</span><span class="sxs-lookup"><span data-stu-id="a7e9e-124">If the function call doesn't return a value, the API will fail.</span></span>  
  
 <span data-ttu-id="a7e9e-125">該方法`ICorDebugILFrame3::GetReturnValueForILOffset`僅適用于基於 x86 和 AMD64 的系統。</span><span class="sxs-lookup"><span data-stu-id="a7e9e-125">The `ICorDebugILFrame3::GetReturnValueForILOffset` method is available only on x86-based and AMD64 systems.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7e9e-126">需求</span><span class="sxs-lookup"><span data-stu-id="a7e9e-126">Requirements</span></span>  
 <span data-ttu-id="a7e9e-127">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a7e9e-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7e9e-128">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a7e9e-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a7e9e-129">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a7e9e-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7e9e-130">**.NET 框架版本：**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7e9e-130">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7e9e-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7e9e-131">See also</span></span>

- [<span data-ttu-id="a7e9e-132">GetReturnValueLiveOffset 方法</span><span class="sxs-lookup"><span data-stu-id="a7e9e-132">GetReturnValueLiveOffset Method</span></span>](icordebugcode3-getreturnvalueliveoffset-method.md)
- [<span data-ttu-id="a7e9e-133">ICorDebugILFrame3 介面</span><span class="sxs-lookup"><span data-stu-id="a7e9e-133">ICorDebugILFrame3 Interface</span></span>](icordebugilframe3-interface.md)
