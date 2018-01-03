---
title: "ICorDebugILFrame3::GetReturnValueForILOffset 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- csharp
- vb
api_name: ICorDebugILFrame3.GetReturnValueForILOffset
api_location: mscordbi.dll
api_type: COM
ms.assetid: 06522727-5f64-4391-9331-11386883c352
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c58319de99bdd8d7cce0ea55ccb3140a31a39bd0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframe3getreturnvalueforiloffset-method"></a><span data-ttu-id="c96de-102">ICorDebugILFrame3::GetReturnValueForILOffset 方法</span><span class="sxs-lookup"><span data-stu-id="c96de-102">ICorDebugILFrame3::GetReturnValueForILOffset Method</span></span>
<span data-ttu-id="c96de-103">取得封裝函式的傳回值的"ICorDebugValue 」 物件。</span><span class="sxs-lookup"><span data-stu-id="c96de-103">Gets an "ICorDebugValue" object that encapsulates the return value of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c96de-104">語法</span><span class="sxs-lookup"><span data-stu-id="c96de-104">Syntax</span></span>  
  
```cpp
HRESULT GetReturnValueForILOffset(  
    ULONG32 ILoffset,   
    [out] ICorDebugValue **ppReturnValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c96de-105">參數</span><span class="sxs-lookup"><span data-stu-id="c96de-105">Parameters</span></span>  
 `ILOffset`  
 <span data-ttu-id="c96de-106">IL 位移。</span><span class="sxs-lookup"><span data-stu-id="c96de-106">The IL offset.</span></span> <span data-ttu-id="c96de-107">請參閱＜備註＞一節。</span><span class="sxs-lookup"><span data-stu-id="c96de-107">See the Remarks section.</span></span>  
  
 `ppReturnValue`  
 <span data-ttu-id="c96de-108">「 ICorDebugValue 」 介面物件，提供函式呼叫的傳回值的相關資訊的位址指標。</span><span class="sxs-lookup"><span data-stu-id="c96de-108">A pointer to the address of an "ICorDebugValue" interface object that provides information about the return value of a function call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c96de-109">備註</span><span class="sxs-lookup"><span data-stu-id="c96de-109">Remarks</span></span>  
 <span data-ttu-id="c96de-110">這個方法會用於[icordebugcode3:: Getreturnvalueliveoffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)方法來取得方法的傳回值。</span><span class="sxs-lookup"><span data-stu-id="c96de-110">This method is used along with the [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) method to get the return value of a method.</span></span> <span data-ttu-id="c96de-111">它是在其傳回值會被忽略，如下列兩個程式碼範例所示的方法的情況下特別有用。</span><span class="sxs-lookup"><span data-stu-id="c96de-111">It is particularly useful in the case of methods whose return values are ignored, as in the following two code examples.</span></span> <span data-ttu-id="c96de-112">第一個範例會呼叫<xref:System.Int32.TryParse%2A?displayProperty=nameWithType>方法，但會忽略方法的傳回值。</span><span class="sxs-lookup"><span data-stu-id="c96de-112">The first example calls the <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> method, but ignores the method's return value.</span></span>  
  
 [!code-csharp[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv1.cs#1)]
 [!code-vb[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv1.vb#1)]  
  
 <span data-ttu-id="c96de-113">第二個範例說明如何在偵錯更常見的問題。</span><span class="sxs-lookup"><span data-stu-id="c96de-113">The second example illustrates a much more common problem in debugging.</span></span> <span data-ttu-id="c96de-114">當做方法呼叫中引數使用的方法，因為它的傳回值存取。 只有在偵錯工具逐步執行呼叫的方法時，才</span><span class="sxs-lookup"><span data-stu-id="c96de-114">Because a method is used as an argument in a method call, its return value is accessible only when the debugger steps through the called method.</span></span> <span data-ttu-id="c96de-115">在許多情況下，特別是當外部程式庫中定義呼叫的方法不可行。</span><span class="sxs-lookup"><span data-stu-id="c96de-115">In many cases, particularly when the called method is defined in an external library, that is not possible.</span></span>  
  
 [!code-csharp[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv2.cs#2)]
 [!code-vb[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv2.vb#2)]  
  
 <span data-ttu-id="c96de-116">如果您要傳入[icordebugcode3:: Getreturnvalueliveoffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) IL 位移函式呼叫位置的方法，它會傳回一或多個原生位移。</span><span class="sxs-lookup"><span data-stu-id="c96de-116">If you pass the [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) method an IL offset to a function call site, it returns one or more native offsets.</span></span> <span data-ttu-id="c96de-117">偵錯工具然後可以在這些原生位移函式中設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="c96de-117">The debugger can then set breakpoints on these native offsets in the function.</span></span> <span data-ttu-id="c96de-118">當偵錯工具叫用的其中一個中斷點時，然後您可以傳遞相同的 IL 位移傳遞到這個方法，以取得傳回值。</span><span class="sxs-lookup"><span data-stu-id="c96de-118">When the debugger hits one of the breakpoints, you can then pass the same IL offset that you passed to this method to get the return value.</span></span> <span data-ttu-id="c96de-119">偵錯工具應再清除它所設定的所有中斷點。</span><span class="sxs-lookup"><span data-stu-id="c96de-119">The debugger should then clear all the breakpoints that it set.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="c96de-120">[Icordebugcode3:: Getreturnvalueliveoffset 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)和`ICorDebugILFrame3::GetReturnValueForILOffset`方法可讓您取得只參考類型的傳回值資訊。</span><span class="sxs-lookup"><span data-stu-id="c96de-120">The [ICorDebugCode3::GetReturnValueLiveOffset Method](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) and `ICorDebugILFrame3::GetReturnValueForILOffset` methods allow you to get return value information for reference types only.</span></span> <span data-ttu-id="c96de-121">傳回值的資訊擷取實值類型 (也就是所有的型別衍生自<xref:System.ValueType>) 不支援。</span><span class="sxs-lookup"><span data-stu-id="c96de-121">Retrieving return value information from value types (that is, all types that derive from <xref:System.ValueType>) is not supported.</span></span>  
  
 <span data-ttu-id="c96de-122">所指定的 IL 位移`ILOffset`參數應該是位於函式呼叫位置，以及偵錯項目應該停止於中斷點，在所傳回的原生位移設定[icordebugcode3:: Getreturnvalueliveoffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)方法針對相同的 IL 位移。</span><span class="sxs-lookup"><span data-stu-id="c96de-122">The IL offset specified by the `ILOffset` parameter should be at a function call site, and the debuggee should be stopped at a breakpoint set at the native offset returned by the [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) method for the same IL offset.</span></span> <span data-ttu-id="c96de-123">如果指定的 IL 位移的正確位置在不停止偵錯項目時，API 將會失敗。</span><span class="sxs-lookup"><span data-stu-id="c96de-123">If the debuggee is not stopped at the correct location for the specified IL offset, the API will fail.</span></span>  
  
 <span data-ttu-id="c96de-124">如果函式呼叫不會傳回值，此 API 將會失敗。</span><span class="sxs-lookup"><span data-stu-id="c96de-124">If the function call doesn't return a value, the API will fail.</span></span>  
  
 <span data-ttu-id="c96de-125">`ICorDebugILFrame3::GetReturnValueForILOffset`方法是僅可在 x86 型和 AMD64 系統。</span><span class="sxs-lookup"><span data-stu-id="c96de-125">The `ICorDebugILFrame3::GetReturnValueForILOffset` method is available only on x86-based and AMD64 systems.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c96de-126">需求</span><span class="sxs-lookup"><span data-stu-id="c96de-126">Requirements</span></span>  
 <span data-ttu-id="c96de-127">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c96de-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c96de-128">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c96de-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c96de-129">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c96de-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c96de-130">**.NET framework 版本：**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c96de-130">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c96de-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="c96de-131">See Also</span></span>  
 [<span data-ttu-id="c96de-132">GetReturnValueLiveOffset 方法</span><span class="sxs-lookup"><span data-stu-id="c96de-132">GetReturnValueLiveOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)  
 [<span data-ttu-id="c96de-133">ICorDebugILFrame3 介面</span><span class="sxs-lookup"><span data-stu-id="c96de-133">ICorDebugILFrame3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)
