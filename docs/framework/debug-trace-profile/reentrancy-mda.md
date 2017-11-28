---
title: "重新進入 MDA"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unmanaged code, debugging
- transitioning threads unmanaged to managed code
- reentrancy MDA
- reentrancy without an orderly transition
- managed debugging assistants (MDAs), reentrancy
- illegal reentrancy
- MDAs (managed debugging assistants), reentrancy
- threading [.NET Framework], managed debugging assistants
- managed code, debugging
- native debugging, MDAs
ms.assetid: 7240c3f3-7df8-4b03-bbf1-17cdce142d45
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a54a985abbc59aea0eeb46cc74560485e86b897d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="reentrancy-mda"></a><span data-ttu-id="21bf0-102">重新進入 MDA</span><span class="sxs-lookup"><span data-stu-id="21bf0-102">reentrancy MDA</span></span>
<span data-ttu-id="21bf0-103">如果未透過循序轉換執行先前從 Managed 程式碼到機器碼的切換時嘗試從機器碼轉換成 Managed 程式碼，啟用 `reentrancy` Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="21bf0-103">The `reentrancy` managed debugging assistant (MDA) is activated when an attempt is made to transition from native to managed code in cases where a prior switch from managed to native code was not performed through an orderly transition.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="21bf0-104">徵兆 </span><span class="sxs-lookup"><span data-stu-id="21bf0-104">Symptoms</span></span>  
 <span data-ttu-id="21bf0-105">物件堆積損毀，或從機器碼轉換成 Managed 程式碼時發生其他嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="21bf0-105">The object heap is corrupted or other serious errors are occurring when transitioning from native to managed code.</span></span>  
  
 <span data-ttu-id="21bf0-106">在機器碼與 Managed 程式碼之間依任一方向切換的執行緒，必須執行循序轉換。</span><span class="sxs-lookup"><span data-stu-id="21bf0-106">Threads that switch between native and managed code in either direction must perform an orderly transition.</span></span> <span data-ttu-id="21bf0-107">不過，作業系統中的特定低階擴充點 (例如向量化例外狀況處理常式) 允許從 Managed 程式碼切換成機器碼，而不需要執行循序轉換。</span><span class="sxs-lookup"><span data-stu-id="21bf0-107">However, certain low-level extensibility points in the operating system, such as the vectored exception handler, allow switches from managed to native code without performing an orderly transition.</span></span>  <span data-ttu-id="21bf0-108">這些參數是受作業系統控制，而不是受 Common Language Runtime (CLR) 控制。</span><span class="sxs-lookup"><span data-stu-id="21bf0-108">These switches are under operating system control, rather than under common language runtime (CLR) control.</span></span>  <span data-ttu-id="21bf0-109">任何在這些擴充點內執行的機器碼都必須避免回呼 Managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="21bf0-109">Any native code that executes inside these extensibility points must avoid calling back into managed code.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="21bf0-110">原因</span><span class="sxs-lookup"><span data-stu-id="21bf0-110">Cause</span></span>  
 <span data-ttu-id="21bf0-111">執行 Managed 程式碼時，已啟用低階作業系統擴充點 (例如向量化例外狀況處理常式)。</span><span class="sxs-lookup"><span data-stu-id="21bf0-111">A low-level operating system extensibility point, such as the vectored exception handler, has activated while executing managed code.</span></span>  <span data-ttu-id="21bf0-112">透過該擴充點叫用的應用程式碼將嘗試回呼至 Managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="21bf0-112">The application code that is invoked through that extensibility point is attempting to call back into managed code.</span></span>  
  
 <span data-ttu-id="21bf0-113">這個問題一律是由應用程式碼所造成。</span><span class="sxs-lookup"><span data-stu-id="21bf0-113">This problem is always caused by application code.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="21bf0-114">解決方式</span><span class="sxs-lookup"><span data-stu-id="21bf0-114">Resolution</span></span>  
 <span data-ttu-id="21bf0-115">檢查已啟用此 MDA 的執行緒堆疊追蹤。</span><span class="sxs-lookup"><span data-stu-id="21bf0-115">Examine the stack trace for the thread that has activated this MDA.</span></span>  <span data-ttu-id="21bf0-116">執行緒將會嘗試不合法地呼叫 Managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="21bf0-116">The thread is attempting to illegally call into managed code.</span></span>  <span data-ttu-id="21bf0-117">堆疊追蹤應該顯示使用此擴充點的應用程式碼、提供此擴充點的作業系統程式碼，以及擴充點已中斷的 Managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="21bf0-117">The stack trace should reveal the application code using this extensibility point, the operating system code that provides this extensibility point, and the managed code that was interrupted by the extensibility point.</span></span>  
  
 <span data-ttu-id="21bf0-118">例如，您會看到 MDA 已在嘗試從向量化例外狀況處理常式呼叫 Managed 程式碼時啟用。</span><span class="sxs-lookup"><span data-stu-id="21bf0-118">For example, you will see the MDA activated in an attempt to call managed code from inside a vectored exception handler.</span></span>  <span data-ttu-id="21bf0-119">在堆疊上，您會看到作業系統例外狀況處理程式碼，以及觸發例外狀況的某個 Managed 程式碼 (例如 <xref:System.DivideByZeroException> 或 <xref:System.AccessViolationException>)。</span><span class="sxs-lookup"><span data-stu-id="21bf0-119">On the stack you will see the operating system exception handling code and some managed code triggering an exception such as a <xref:System.DivideByZeroException> or an <xref:System.AccessViolationException>.</span></span>  
  
 <span data-ttu-id="21bf0-120">在此範例中，正確的解決方式是使用 Unmanaged 程式碼完全實作向量化例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="21bf0-120">In this example, the correct resolution is to implement the vectored exception handler completely in unmanaged code.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="21bf0-121">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="21bf0-121">Effect on the Runtime</span></span>  
 <span data-ttu-id="21bf0-122">此 MDA 對 CLR 沒有影響。</span><span class="sxs-lookup"><span data-stu-id="21bf0-122">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="21bf0-123">輸出</span><span class="sxs-lookup"><span data-stu-id="21bf0-123">Output</span></span>  
 <span data-ttu-id="21bf0-124">MDA 報告正在嘗試不合法的重新進入。</span><span class="sxs-lookup"><span data-stu-id="21bf0-124">The MDA reports that illegal reentrancy is being attempted.</span></span>  <span data-ttu-id="21bf0-125">檢查執行緒的堆疊，以判斷發生此問題的原因和其更正方式。</span><span class="sxs-lookup"><span data-stu-id="21bf0-125">Examine the thread's stack to determine why this is happening and how to correct the problem.</span></span> <span data-ttu-id="21bf0-126">以下是範例輸出。</span><span class="sxs-lookup"><span data-stu-id="21bf0-126">The following is sample output.</span></span>  
  
```  
Additional Information: Attempting to call into managed code without   
transitioning out first.  Do not attempt to run managed code inside   
low-level native extensibility points. Managed Debugging Assistant   
'Reentrancy' has detected a problem in 'D:\ConsoleApplication1\  
ConsoleApplication1\bin\Debug\ConsoleApplication1.vshost.exe'.  
```  
  
## <a name="configuration"></a><span data-ttu-id="21bf0-127">組態</span><span class="sxs-lookup"><span data-stu-id="21bf0-127">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reentrancy />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="21bf0-128">範例</span><span class="sxs-lookup"><span data-stu-id="21bf0-128">Example</span></span>  
 <span data-ttu-id="21bf0-129">下列程式碼範例會導致擲回 <xref:System.AccessViolationException>。</span><span class="sxs-lookup"><span data-stu-id="21bf0-129">The following code example causes an <xref:System.AccessViolationException> to be thrown.</span></span>  <span data-ttu-id="21bf0-130">在支援向量化例外狀況處理的 Windows 版本上，這會呼叫 Managed 向量化例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="21bf0-130">On versions of Windows that support vectored exception handling, this will cause the managed vectored exception handler to be called.</span></span>  <span data-ttu-id="21bf0-131">如果啟用 `reentrancy` MDA，則會在透過作業系統的向量化例外狀況處理支援程式碼嘗試呼叫 `MyHandler` 期間啟用 MDA。</span><span class="sxs-lookup"><span data-stu-id="21bf0-131">If the `reentrancy` MDA is enabled, the MDA will activate during the attempted call to `MyHandler` from the operating system's vectored exception handling support code.</span></span>  
  
```  
using System;  
public delegate int ExceptionHandler(IntPtr ptrExceptionInfo);  
  
public class Reenter   
{  
    public static ExceptionHandler keepAlive;  
  
    [System.Runtime.InteropServices.DllImport("kernel32", ExactSpelling=true,   
        CharSet=System.Runtime.InteropServices.CharSet.Auto)]  
    public static extern IntPtr AddVectoredExceptionHandler(int bFirst,   
        ExceptionHandler handler);  
  
    static int MyHandler(IntPtr ptrExceptionInfo)   
    {  
        // EXCEPTION_CONTINUE_SEARCH  
        return 0;  
    }  
    void Run() {}  
  
    static void Main()   
    {  
        keepAlive = new ExceptionHandler(Reenter.MyHandler);  
        IntPtr ret = AddVectoredExceptionHandler(1, keepAlive);  
        try   
        {  
            // Dispatch on null should AV.  
            Reenter r = null;   
            r.Run();  
        }   
        catch { }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="21bf0-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21bf0-132">See Also</span></span>  
 [<span data-ttu-id="21bf0-133">使用 Managed 偵錯助理診斷錯誤</span><span class="sxs-lookup"><span data-stu-id="21bf0-133">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
