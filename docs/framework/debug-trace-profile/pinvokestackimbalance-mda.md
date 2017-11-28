---
title: pInvokeStackImbalance MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- signatures, platform invoke
- stack depth
- platform invoke stack imbalance
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- PInvokeStackImbalance MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: 34ddc6bd-1675-4f35-86aa-de1645d5c631
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b33a3edc5780ecf07e7809ca327a304d748110f1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="pinvokestackimbalance-mda"></a><span data-ttu-id="3e5a6-102">pInvokeStackImbalance MDA</span><span class="sxs-lookup"><span data-stu-id="3e5a6-102">pInvokeStackImbalance MDA</span></span>
<span data-ttu-id="3e5a6-103">假設 <xref:System.Runtime.InteropServices.DllImportAttribute> 屬性中已指定呼叫慣例並已宣告Managed 簽章中的參數，當 CLR 在平台叫用呼叫之後偵測到有堆疊深度不符合預期的堆疊深度時，便會啟動 `pInvokeStackImbalance` Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="3e5a6-103">The `pInvokeStackImbalance` managed debugging assistant (MDA) is activated when the CLR detects that the stack depth after a platform invoke call does not match the expected stack depth, given the calling convention specified in the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute as well as the declaration of the parameters in the managed signature.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3e5a6-104">`pInvokeStackImbalance` MDA 只會在 32 位元 x86 平台上實作。</span><span class="sxs-lookup"><span data-stu-id="3e5a6-104">The `pInvokeStackImbalance` MDA is implemented only for 32-bit x86 platforms.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3e5a6-105">在 .NET Framework 3.5 版中，預設會停用 `pInvokeStackImbalance` MDA。</span><span class="sxs-lookup"><span data-stu-id="3e5a6-105">In the .NET Framework version 3.5, the `pInvokeStackImbalance` MDA is disabled by default.</span></span> <span data-ttu-id="3e5a6-106">當您搭配使用 .NET Framework 3.5 版與 Visual Studio 2005 時，`pInvokeStackImbalance` MDA 會出現在 [例外狀況] 對話方塊的 [Managed 偵錯助理] 清單中 (當您按一下 [偵錯] 功能表上的 [例外狀況] 時會顯示 [例外狀況] 對話方塊)。</span><span class="sxs-lookup"><span data-stu-id="3e5a6-106">When you use the .NET Framework version 3.5 with Visual Studio 2005, the `pInvokeStackImbalance` MDA will appear in the **Managed Debugging Assistants** list in the **Exceptions** dialog box (which is displayed when you click **Exceptions** on the **Debug** menu).</span></span> <span data-ttu-id="3e5a6-107">不過，選取或清除 `pInvokeStackImbalance` 的 [擲回] 核取方塊並不會啟用或停用 MDA，而只會控制 Visual Studio 是否在啟動 MDA 時擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3e5a6-107">However, selecting or clearing the **Thrown** check box for `pInvokeStackImbalance` does not enable or disable the MDA; it only controls whether Visual Studio throws an exception when the MDA is activated.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="3e5a6-108">徵兆</span><span class="sxs-lookup"><span data-stu-id="3e5a6-108">Symptoms</span></span>  
 <span data-ttu-id="3e5a6-109">應用程式在進行平台叫用呼叫期間或之後發生存取違規或記憶體損毀。</span><span class="sxs-lookup"><span data-stu-id="3e5a6-109">An application encounters an access violation or memory corruption when making or following a platform invoke call.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="3e5a6-110">原因</span><span class="sxs-lookup"><span data-stu-id="3e5a6-110">Cause</span></span>  
 <span data-ttu-id="3e5a6-111">平台叫用呼叫的 Managed 簽章可能與所呼叫之方法的 Unmanaged 簽章不符。</span><span class="sxs-lookup"><span data-stu-id="3e5a6-111">The managed signature of the platform invoke call might not match the unmanaged signature of the method being called.</span></span>  <span data-ttu-id="3e5a6-112">當 Managed 簽章未宣告正確的參數數目，或未指定適當的參數大小時，便會造成這種不相符狀況。</span><span class="sxs-lookup"><span data-stu-id="3e5a6-112">This mismatch can be caused by the managed signature not declaring the correct number of parameters or not specifying the appropriate size for the parameters.</span></span>  <span data-ttu-id="3e5a6-113">MDA 也可能由於呼叫慣例 (可能由 <xref:System.Runtime.InteropServices.DllImportAttribute> 屬性指定) 與 Unmanaged 呼叫慣例不符而啟動。</span><span class="sxs-lookup"><span data-stu-id="3e5a6-113">The MDA can also activate because the calling convention, possibly specified by the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute, does not match the unmanaged calling convention.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="3e5a6-114">解決方式</span><span class="sxs-lookup"><span data-stu-id="3e5a6-114">Resolution</span></span>  
 <span data-ttu-id="3e5a6-115">檢閱 Managed 平台叫用簽章和呼叫慣例，確認其與原生目標的簽章和呼叫慣例相符。</span><span class="sxs-lookup"><span data-stu-id="3e5a6-115">Review the managed platform invoke signature and calling convention to confirm it matches the signature and calling convention of the native target.</span></span>  <span data-ttu-id="3e5a6-116">嘗試明確指定 Managed 和 Unmanaged 端的呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="3e5a6-116">Try explicitly specifying the calling convention on both the managed and unmanaged sides.</span></span> <span data-ttu-id="3e5a6-117">Unmanaged 函式也可能 (雖然可能性不高) 因其他一些原因而使堆疊失去平衡，例如 Unmanaged 編譯器中的 Bug。</span><span class="sxs-lookup"><span data-stu-id="3e5a6-117">It is also possible, although not as likely, that the unmanaged function unbalanced the stack for some other reason, such as a bug in the unmanaged compiler.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="3e5a6-118">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="3e5a6-118">Effect on the Runtime</span></span>  
 <span data-ttu-id="3e5a6-119">強制所有平台叫用呼叫採用 CLR 中未最佳化的路徑。</span><span class="sxs-lookup"><span data-stu-id="3e5a6-119">Forces all platform invoke calls to take the nonoptimized path in the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="3e5a6-120">輸出</span><span class="sxs-lookup"><span data-stu-id="3e5a6-120">Output</span></span>  
 <span data-ttu-id="3e5a6-121">MDA 訊息會提供使堆疊失去平衡之平台叫用方法呼叫的名稱。</span><span class="sxs-lookup"><span data-stu-id="3e5a6-121">The MDA message gives the name of the platform invoke method call that is causing the stack imbalance.</span></span>  <span data-ttu-id="3e5a6-122">`SampleMethod` 方法之平台叫用呼叫的範例訊息為：</span><span class="sxs-lookup"><span data-stu-id="3e5a6-122">A sample message of a platform invoke call on method `SampleMethod` is:</span></span>  
  
```  
A call to PInvoke function 'SampleMethod' has unbalanced the stack.   
This is likely because the managed PInvoke signature does not match   
the unmanaged target signature. Check that the calling convention and   
parameters of the PInvoke signature match the target unmanaged signature.  
```  
  
## <a name="configuration"></a><span data-ttu-id="3e5a6-123">組態</span><span class="sxs-lookup"><span data-stu-id="3e5a6-123">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <pInvokeStackImbalance />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3e5a6-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e5a6-124">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="3e5a6-125">使用 Managed 偵錯助理診斷錯誤</span><span class="sxs-lookup"><span data-stu-id="3e5a6-125">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="3e5a6-126">Interop 封送處理</span><span class="sxs-lookup"><span data-stu-id="3e5a6-126">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
