---
title: invalidApartmentStateChange MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid apartment state
- managed debugging assistants (MDAs), invalid apartment state
- InvalidApartmentStateChange MDA
- invalid apartment state changes
- threading [.NET Framework], apartment states
- apartment states
- threading [.NET Framework], managed debugging assistants
- COM apartment states
ms.assetid: e56fb9df-5286-4be7-b313-540c4d876cd7
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 864367e71f3ed05af87931b2a87f576df42dcbf5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33390688"
---
# <a name="invalidapartmentstatechange-mda"></a><span data-ttu-id="c621f-102">invalidApartmentStateChange MDA</span><span class="sxs-lookup"><span data-stu-id="c621f-102">invalidApartmentStateChange MDA</span></span>
<span data-ttu-id="c621f-103">`invalidApartmentStateChange` Managed 偵錯助理 (MDA) 是由下列兩個問題之一所啟動：</span><span class="sxs-lookup"><span data-stu-id="c621f-103">The `invalidApartmentStateChange` managed debugging assistant (MDS) is activated by either of two problems:</span></span>  
  
-   <span data-ttu-id="c621f-104">嘗試變更執行緒的 COM Apartment 狀態，該執行緒已被 COM 初始化成不同的 Apartment 狀態。</span><span class="sxs-lookup"><span data-stu-id="c621f-104">An attempt is made to change the COM apartment state of a thread that has already been initialized by COM to a different apartment state.</span></span>  
  
-   <span data-ttu-id="c621f-105">未預期的執行緒 COM Apartment 狀態變更。</span><span class="sxs-lookup"><span data-stu-id="c621f-105">The COM apartment state of a thread changes unexpectedly.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="c621f-106">徵兆</span><span class="sxs-lookup"><span data-stu-id="c621f-106">Symptoms</span></span>  
  
-   <span data-ttu-id="c621f-107">執行緒的 COM Apartment 狀態不是原來要求的。</span><span class="sxs-lookup"><span data-stu-id="c621f-107">A thread's COM apartment state is not what was requested.</span></span> <span data-ttu-id="c621f-108">這可能會導致 Proxy 用於執行緒模型和目前執行緒模型不同的 COM 元件。</span><span class="sxs-lookup"><span data-stu-id="c621f-108">This may cause proxies to be used for COM components that have a threading model different from the current one.</span></span> <span data-ttu-id="c621f-109">接著，在透過未設定跨 Apartment 封送處理的介面呼叫 COM 物件時，這可能會造成 <xref:System.InvalidCastException> 被擲回。</span><span class="sxs-lookup"><span data-stu-id="c621f-109">This in turn may cause an <xref:System.InvalidCastException> to be thrown when calling the COM object through interfaces that are not set up for cross-apartment marshaling.</span></span>  
  
-   <span data-ttu-id="c621f-110">執行緒的 COM Apartment 狀態與預期的不同。</span><span class="sxs-lookup"><span data-stu-id="c621f-110">The COM apartment state of the thread is different than expected.</span></span> <span data-ttu-id="c621f-111">在[執行階段可呼叫包裝函式](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) 上進行呼叫時，這會造成 <xref:System.Runtime.InteropServices.COMException> 具有 RPC_E_WRONG_THREAD 的 HRESULT 以及 <xref:System.InvalidCastException>。</span><span class="sxs-lookup"><span data-stu-id="c621f-111">This can cause a <xref:System.Runtime.InteropServices.COMException> with an HRESULT of RPC_E_WRONG_THREAD as well as a <xref:System.InvalidCastException> when making calls on a [Runtime Callable Wrapper](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW).</span></span> <span data-ttu-id="c621f-112">這也會造成多個執行緒同時存取某些單一執行緒的 COM 元件，導致損毀或資料遺失。</span><span class="sxs-lookup"><span data-stu-id="c621f-112">This can also cause some single-threaded COM components to be accessed by multiple threads at the same time, which can lead to corruption or data loss.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="c621f-113">原因</span><span class="sxs-lookup"><span data-stu-id="c621f-113">Cause</span></span>  
  
-   <span data-ttu-id="c621f-114">執行緒先前已初始化成不同的 COM Apartment 狀態。</span><span class="sxs-lookup"><span data-stu-id="c621f-114">The thread was previously initialized to a different COM apartment state.</span></span> <span data-ttu-id="c621f-115">請注意，可以明確或隱含方式設定執行緒的 Apartment 狀態。</span><span class="sxs-lookup"><span data-stu-id="c621f-115">Note that the apartment state of a thread can be set either explicitly or implicitly.</span></span> <span data-ttu-id="c621f-116">明確的作業包括 <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> 屬性以及 <xref:System.Threading.Thread.SetApartmentState%2A> 和 <xref:System.Threading.Thread.TrySetApartmentState%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="c621f-116">The explicit operations include the <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> property and the <xref:System.Threading.Thread.SetApartmentState%2A> and <xref:System.Threading.Thread.TrySetApartmentState%2A> methods.</span></span> <span data-ttu-id="c621f-117">使用 <xref:System.Threading.Thread.Start%2A> 方法建立的執行緒，會以隱含方式設成 <xref:System.Threading.ApartmentState.MTA>，除非啟動執行緒之前呼叫 <xref:System.Threading.Thread.SetApartmentState%2A>。</span><span class="sxs-lookup"><span data-stu-id="c621f-117">A thread created using the <xref:System.Threading.Thread.Start%2A> method is implicitly set to <xref:System.Threading.ApartmentState.MTA> unless <xref:System.Threading.Thread.SetApartmentState%2A> is called before the thread is started.</span></span> <span data-ttu-id="c621f-118">應用程式的主執行緒也會以隱含方式初始化為 <xref:System.Threading.ApartmentState.MTA>，除非在 Main 方法上指定 <xref:System.STAThreadAttribute> 屬性。</span><span class="sxs-lookup"><span data-stu-id="c621f-118">The main thread of the application is also implicitly initialized to <xref:System.Threading.ApartmentState.MTA> unless the <xref:System.STAThreadAttribute> attribute is specified on the main method.</span></span>  
  
-   <span data-ttu-id="c621f-119">在執行緒上呼叫具有不同並行模型的 `CoUninitialize` 方法 (或 `CoInitializeEx` 方法)。</span><span class="sxs-lookup"><span data-stu-id="c621f-119">The `CoUninitialize` method (or the `CoInitializeEx` method) with a different concurrency model is called on the thread.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="c621f-120">解決方式</span><span class="sxs-lookup"><span data-stu-id="c621f-120">Resolution</span></span>  
 <span data-ttu-id="c621f-121">請先設定執行緒的 Apartment 狀態再開始執行，或將 <xref:System.STAThreadAttribute> 屬性或 <xref:System.MTAThreadAttribute> 屬性套用到應用程式的 Main 方法。</span><span class="sxs-lookup"><span data-stu-id="c621f-121">Set the apartment state of the thread before it begins executing, or apply either the <xref:System.STAThreadAttribute> attribute or the <xref:System.MTAThreadAttribute> attribute to the main method of the application.</span></span>  
  
 <span data-ttu-id="c621f-122">第二個原因，在理想情況下，應該修改呼叫 `CoUninitialize` 方法的程式碼以延遲呼叫，直到執行緒即將終止且沒有任何 RCW 為止，執行緒仍繼續使用它們的基礎 COM 元件。</span><span class="sxs-lookup"><span data-stu-id="c621f-122">For the second cause, ideally, the code that calls the `CoUninitialize` method should be modified to delay the call until the thread is about to terminate and there are no RCWs and their underlying COM components still in use by the thread.</span></span> <span data-ttu-id="c621f-123">不過，如果不可能修改呼叫 `CoUninitialize` 方法的程式碼，則不應從未以此方式初始化的執行緒中使用任何 RCW。</span><span class="sxs-lookup"><span data-stu-id="c621f-123">However, if it is not possible to modify the code that calls the `CoUninitialize` method, then no RCWs should be used from threads that are uninitialized in this way.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="c621f-124">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="c621f-124">Effect on the Runtime</span></span>  
 <span data-ttu-id="c621f-125">此 MDA 對 CLR 沒有影響。</span><span class="sxs-lookup"><span data-stu-id="c621f-125">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="c621f-126">輸出</span><span class="sxs-lookup"><span data-stu-id="c621f-126">Output</span></span>  
 <span data-ttu-id="c621f-127">目前執行緒的 COM Apartment 狀態和程式碼之前嘗試套用的狀態。</span><span class="sxs-lookup"><span data-stu-id="c621f-127">The COM apartment state of the current thread, and the state that the code was attempting to apply.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="c621f-128">組態</span><span class="sxs-lookup"><span data-stu-id="c621f-128">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidApartmentStateChange />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="c621f-129">範例</span><span class="sxs-lookup"><span data-stu-id="c621f-129">Example</span></span>  
 <span data-ttu-id="c621f-130">下列程式碼範例示範可以啟動此 MDA 的情況。</span><span class="sxs-lookup"><span data-stu-id="c621f-130">The following code example demonstrates a situation that can activate this MDA.</span></span>  
  
```  
using System.Threading;  
namespace ApartmentStateMDA  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Thread.CurrentThread.SetApartmentState(ApartmentState.STA);  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="c621f-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c621f-131">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="c621f-132">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="c621f-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="c621f-133">Interop 封送處理</span><span class="sxs-lookup"><span data-stu-id="c621f-133">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
