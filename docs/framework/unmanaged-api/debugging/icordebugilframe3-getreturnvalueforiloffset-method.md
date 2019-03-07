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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a01e2fcc7dc00d3a57272abb04ebcecc6d5f74a6
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57467063"
---
# <a name="icordebugilframe3getreturnvalueforiloffset-method"></a><span data-ttu-id="5d7b9-102">ICorDebugILFrame3::GetReturnValueForILOffset 方法</span><span class="sxs-lookup"><span data-stu-id="5d7b9-102">ICorDebugILFrame3::GetReturnValueForILOffset Method</span></span>
<span data-ttu-id="5d7b9-103">取得封裝函式的傳回值的"ICorDebugValue 」 物件。</span><span class="sxs-lookup"><span data-stu-id="5d7b9-103">Gets an "ICorDebugValue" object that encapsulates the return value of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d7b9-104">語法</span><span class="sxs-lookup"><span data-stu-id="5d7b9-104">Syntax</span></span>  
  
```cpp
HRESULT GetReturnValueForILOffset(  
    ULONG32 ILoffset,   
    [out] ICorDebugValue **ppReturnValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d7b9-105">參數</span><span class="sxs-lookup"><span data-stu-id="5d7b9-105">Parameters</span></span>  
 `ILOffset`  
 <span data-ttu-id="5d7b9-106">IL 位移。</span><span class="sxs-lookup"><span data-stu-id="5d7b9-106">The IL offset.</span></span> <span data-ttu-id="5d7b9-107">請參閱＜備註＞一節。</span><span class="sxs-lookup"><span data-stu-id="5d7b9-107">See the Remarks section.</span></span>  
  
 `ppReturnValue`  
 <span data-ttu-id="5d7b9-108">提供函式呼叫的傳回值的詳細資訊 」 ICorDebugValue 」 介面物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="5d7b9-108">A pointer to the address of an "ICorDebugValue" interface object that provides information about the return value of a function call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d7b9-109">備註</span><span class="sxs-lookup"><span data-stu-id="5d7b9-109">Remarks</span></span>  
 <span data-ttu-id="5d7b9-110">這個方法會用於[ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)方法來取得方法的傳回值。</span><span class="sxs-lookup"><span data-stu-id="5d7b9-110">This method is used along with the [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) method to get the return value of a method.</span></span> <span data-ttu-id="5d7b9-111">它是在方法的傳回值會被忽略，如下列兩個程式碼範例所示的情況下特別有用。</span><span class="sxs-lookup"><span data-stu-id="5d7b9-111">It is particularly useful in the case of methods whose return values are ignored, as in the following two code examples.</span></span> <span data-ttu-id="5d7b9-112">第一個範例會呼叫<xref:System.Int32.TryParse%2A?displayProperty=nameWithType>方法，但是忽略方法的傳回值。</span><span class="sxs-lookup"><span data-stu-id="5d7b9-112">The first example calls the <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> method, but ignores the method's return value.</span></span>  
  
 [!code-csharp[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv1.cs#1)]
 [!code-vb[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv1.vb#1)]  
  
 <span data-ttu-id="5d7b9-113">第二個範例說明一個更常見的問題，在偵錯。</span><span class="sxs-lookup"><span data-stu-id="5d7b9-113">The second example illustrates a much more common problem in debugging.</span></span> <span data-ttu-id="5d7b9-114">因為方法用來當做方法呼叫中引數，其傳回值只在偵錯工具逐步執行呼叫的方法時，才是可存取。</span><span class="sxs-lookup"><span data-stu-id="5d7b9-114">Because a method is used as an argument in a method call, its return value is accessible only when the debugger steps through the called method.</span></span> <span data-ttu-id="5d7b9-115">在許多情況下，特別是當被呼叫的方法定義在外部程式庫，這不可能。</span><span class="sxs-lookup"><span data-stu-id="5d7b9-115">In many cases, particularly when the called method is defined in an external library, that is not possible.</span></span>  
  
 [!code-csharp[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv2.cs#2)]
 [!code-vb[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv2.vb#2)]  
  
 <span data-ttu-id="5d7b9-116">如果您傳遞[ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) il 位移函式呼叫位置的方法，它會傳回一或多個原生位移。</span><span class="sxs-lookup"><span data-stu-id="5d7b9-116">If you pass the [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) method an IL offset to a function call site, it returns one or more native offsets.</span></span> <span data-ttu-id="5d7b9-117">偵錯工具則可以在這些函式中的原生位移上設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="5d7b9-117">The debugger can then set breakpoints on these native offsets in the function.</span></span> <span data-ttu-id="5d7b9-118">當偵錯工具叫用其中一個中斷點時，您可以將相同的 IL 位移傳遞給這個方法，以取得傳回值。</span><span class="sxs-lookup"><span data-stu-id="5d7b9-118">When the debugger hits one of the breakpoints, you can then pass the same IL offset that you passed to this method to get the return value.</span></span> <span data-ttu-id="5d7b9-119">偵錯工具應接著清除它所設定的所有中斷點。</span><span class="sxs-lookup"><span data-stu-id="5d7b9-119">The debugger should then clear all the breakpoints that it set.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="5d7b9-120">[ICorDebugCode3::GetReturnValueLiveOffset 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)和`ICorDebugILFrame3::GetReturnValueForILOffset`方法可讓您取得僅參考型別傳回值資訊。</span><span class="sxs-lookup"><span data-stu-id="5d7b9-120">The [ICorDebugCode3::GetReturnValueLiveOffset Method](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) and `ICorDebugILFrame3::GetReturnValueForILOffset` methods allow you to get return value information for reference types only.</span></span> <span data-ttu-id="5d7b9-121">傳回值資訊擷取實值型別 (也就是所有的型別衍生自<xref:System.ValueType>) 不支援。</span><span class="sxs-lookup"><span data-stu-id="5d7b9-121">Retrieving return value information from value types (that is, all types that derive from <xref:System.ValueType>) is not supported.</span></span>  
  
 <span data-ttu-id="5d7b9-122">所指定的 IL 位移`ILOffset`參數應該是在函式呼叫站台，以及偵錯項目應停止於中斷點，設定所傳回之原生位移[ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)方法相同的 IL 位移。</span><span class="sxs-lookup"><span data-stu-id="5d7b9-122">The IL offset specified by the `ILOffset` parameter should be at a function call site, and the debuggee should be stopped at a breakpoint set at the native offset returned by the [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) method for the same IL offset.</span></span> <span data-ttu-id="5d7b9-123">如果未在指定的 IL 位移的正確位置停止偵錯項目，則 API 將會失敗。</span><span class="sxs-lookup"><span data-stu-id="5d7b9-123">If the debuggee is not stopped at the correct location for the specified IL offset, the API will fail.</span></span>  
  
 <span data-ttu-id="5d7b9-124">如果函式呼叫沒有傳回值，則 API 將會失敗。</span><span class="sxs-lookup"><span data-stu-id="5d7b9-124">If the function call doesn't return a value, the API will fail.</span></span>  
  
 <span data-ttu-id="5d7b9-125">`ICorDebugILFrame3::GetReturnValueForILOffset`方法是僅適用於 x86 架構和 AMD64 系統。</span><span class="sxs-lookup"><span data-stu-id="5d7b9-125">The `ICorDebugILFrame3::GetReturnValueForILOffset` method is available only on x86-based and AMD64 systems.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d7b9-126">需求</span><span class="sxs-lookup"><span data-stu-id="5d7b9-126">Requirements</span></span>  
 <span data-ttu-id="5d7b9-127">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5d7b9-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d7b9-128">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5d7b9-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5d7b9-129">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5d7b9-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d7b9-130">**.NET framework 版本：**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d7b9-130">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d7b9-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d7b9-131">See also</span></span>
- [<span data-ttu-id="5d7b9-132">GetReturnValueLiveOffset 方法</span><span class="sxs-lookup"><span data-stu-id="5d7b9-132">GetReturnValueLiveOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)
- [<span data-ttu-id="5d7b9-133">ICorDebugILFrame3 介面</span><span class="sxs-lookup"><span data-stu-id="5d7b9-133">ICorDebugILFrame3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)
