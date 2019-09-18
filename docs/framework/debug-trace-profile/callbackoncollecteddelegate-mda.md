---
title: callbackOnCollectedDelegate MDA
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- MDAs (managed debugging assistants), garbage collection
- managed debugging assistants (MDAs), callback on collected delegates
- MDAs (managed debugging assistants), callback on collected delegates
- callback on delegate after garbage collection
- callbackOnCollectedDelegate MDA
- managed debugging assistants (MDAs), garbage collection
- call back collected delegates
- garbage collection, run-time errors
- delegates [.NET Framework], garbage collection
ms.assetid: 398b0ce0-5cc9-4518-978d-b8263aa21e5b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f7f5a6ef2d4e8d4a987ed74a6a04e31f87cc46f3
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052940"
---
# <a name="callbackoncollecteddelegate-mda"></a><span data-ttu-id="0bb4c-102">callbackOnCollectedDelegate MDA</span><span class="sxs-lookup"><span data-stu-id="0bb4c-102">callbackOnCollectedDelegate MDA</span></span>
<span data-ttu-id="0bb4c-103">如果委派以函式指標形式從 Managed 程式碼封送處理至 Unmanaged 程式碼，而在對委派進行記憶體回收之後，將回呼放在該函式指標上，`callbackOnCollectedDelegate` Managed 偵錯助理 (MDA) 就會啟動。</span><span class="sxs-lookup"><span data-stu-id="0bb4c-103">The `callbackOnCollectedDelegate` managed debugging assistant (MDA) is activated if a delegate is marshaled from managed to unmanaged code as a function pointer and a callback is placed on that function pointer after the delegate has been garbage collected.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="0bb4c-104">徵兆</span><span class="sxs-lookup"><span data-stu-id="0bb4c-104">Symptoms</span></span>  
 <span data-ttu-id="0bb4c-105">嘗試透過從 Managed 委派取得的函式指標，呼叫至 Managed 程式碼中時，就會發生存取違規。</span><span class="sxs-lookup"><span data-stu-id="0bb4c-105">Access violations occur when attempting to call into managed code through function pointers that were obtained from managed delegates.</span></span> <span data-ttu-id="0bb4c-106">這些失敗雖然不是 Common Language Runtime (CLR) 錯誤，但看起來可能很像，因為 CLR 程式碼中發生存取違規。</span><span class="sxs-lookup"><span data-stu-id="0bb4c-106">These failures, while not common language runtime (CLR) bugs, may appear to be so because the access violation occurs in the CLR code.</span></span>  
  
 <span data-ttu-id="0bb4c-107">失敗情況不一致，有時在函式指標上呼叫成功，有時則失敗。</span><span class="sxs-lookup"><span data-stu-id="0bb4c-107">The failure is not consistent; sometimes the call on the function pointer succeeds and sometimes it fails.</span></span> <span data-ttu-id="0bb4c-108">只有在負載過重，或嘗試不定次數時，可能會發生失敗。</span><span class="sxs-lookup"><span data-stu-id="0bb4c-108">The failure might occur only under heavy load or on a random number of attempts.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="0bb4c-109">原因</span><span class="sxs-lookup"><span data-stu-id="0bb4c-109">Cause</span></span>  
 <span data-ttu-id="0bb4c-110">用來建立函式指標並向 Unmanaged 程式碼公開的委派被回收記憶體。</span><span class="sxs-lookup"><span data-stu-id="0bb4c-110">The delegate from which the function pointer was created and exposed to unmanaged code was garbage collected.</span></span> <span data-ttu-id="0bb4c-111">當 Unmanaged 元件嘗試在函式指標上呼叫時，會產生存取違規。</span><span class="sxs-lookup"><span data-stu-id="0bb4c-111">When the unmanaged component tries to call on the function pointer, it generates an access violation.</span></span>  
  
 <span data-ttu-id="0bb4c-112">此失敗會隨機發生，因為要視發生記憶體回收的時機而定。</span><span class="sxs-lookup"><span data-stu-id="0bb4c-112">The failure appears random because it depends on when garbage collection occurs.</span></span> <span data-ttu-id="0bb4c-113">如果委派符合記憶體回收資格，在回呼之後就會發生記憶體回收，且呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="0bb4c-113">If a delegate is eligible for collection, the garbage collection can occur after the callback and the call succeeds.</span></span> <span data-ttu-id="0bb4c-114">在其他時候，記憶體回收會發生在回呼之前，回呼會產生存取違規，而程式會停止。</span><span class="sxs-lookup"><span data-stu-id="0bb4c-114">At other times, the garbage collection occurs before the callback, the callback generates an access violation, and the program stops.</span></span>  
  
 <span data-ttu-id="0bb4c-115">失敗的機率取決於將委派封送處理與在函式指標上回呼之間的時間，以及記憶體回收的頻率。</span><span class="sxs-lookup"><span data-stu-id="0bb4c-115">The probability of the failure depends on the time between marshaling the delegate and the callback on the function pointer as well as the frequency of garbage collections.</span></span> <span data-ttu-id="0bb4c-116">如果將委派封送處理與後續回呼之間的時間很短，則偶爾會失敗。</span><span class="sxs-lookup"><span data-stu-id="0bb4c-116">The failure is sporadic if the time between marshaling the delegate and the ensuing callback is short.</span></span> <span data-ttu-id="0bb4c-117">如果接收函式指標的 Unmanaged 方法沒有儲存函式指標以供稍後使用，而是立即在函式指標上回呼，完成其作業後再返回，通常都會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="0bb4c-117">This is usually the case if the unmanaged method receiving the function pointer does not save the function pointer for later use but instead calls back on the function pointer immediately to complete its operation before returning.</span></span> <span data-ttu-id="0bb4c-118">同樣地，當系統負載過重時，會發生更多記憶體回收，這樣更有可能會在回呼之前發生記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="0bb4c-118">Similarly, more garbage collections occur when a system is under heavy load, which makes it more likely that a garbage collection will occur before the callback.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="0bb4c-119">解決方式</span><span class="sxs-lookup"><span data-stu-id="0bb4c-119">Resolution</span></span>  
 <span data-ttu-id="0bb4c-120">一旦將委派封送處理出去成為 Unmanaged 函式指標，記憶體回收行程即無法追蹤其存留期。</span><span class="sxs-lookup"><span data-stu-id="0bb4c-120">Once a delegate has been marshaled out as an unmanaged function pointer, the garbage collector cannot track its lifetime.</span></span> <span data-ttu-id="0bb4c-121">相反地，您的程式碼必須保留委派的參考，以供 Unmanaged 函式指標的存留期使用。</span><span class="sxs-lookup"><span data-stu-id="0bb4c-121">Instead, your code must keep a reference to the delegate for the lifetime of the unmanaged function pointer.</span></span> <span data-ttu-id="0bb4c-122">但是，您必須先識別已回收哪個委派，才能這麼做。</span><span class="sxs-lookup"><span data-stu-id="0bb4c-122">But before you can do that, you first must identify which delegate was collected.</span></span> <span data-ttu-id="0bb4c-123">當啟用 MDA 時，它會提供委派的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="0bb4c-123">When the MDA is activated, it provides the type name of the delegate.</span></span> <span data-ttu-id="0bb4c-124">使用此名稱，在您的程式碼中搜尋平台叫用，或是將該委派傳出至 Unmanaged 程式碼的 COM 簽章。</span><span class="sxs-lookup"><span data-stu-id="0bb4c-124">Use this name to search your code for platform invoke or COM signatures that pass that delegate out to unmanaged code.</span></span> <span data-ttu-id="0bb4c-125">違規的委派會透過其中一個呼叫位置傳遞出去。</span><span class="sxs-lookup"><span data-stu-id="0bb4c-125">The offending delegate is passed out through one of these call sites.</span></span> <span data-ttu-id="0bb4c-126">您也可以啟用 `gcUnmanagedToManaged` MDA，以在每次回呼至執行階段中之前，強制進行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="0bb4c-126">You can also enable the `gcUnmanagedToManaged` MDA to force a garbage collection before every callback into the runtime.</span></span> <span data-ttu-id="0bb4c-127">如此可以確保在回呼之前，一律會發生記憶體回收，進而消除因記憶體回收而產生的不確定性。</span><span class="sxs-lookup"><span data-stu-id="0bb4c-127">This will remove the uncertainty introduced by the garbage collection by ensuring that a garbage collection always occurs before the callback.</span></span> <span data-ttu-id="0bb4c-128">您知道哪些委派已回收之後，立即變更程式碼，以在已封送處理之 Unmanaged 函式指標的存留期間，將該委派的參考保留在 Managed 端。</span><span class="sxs-lookup"><span data-stu-id="0bb4c-128">Once you know what delegate was collected, change your code to keep a reference to that delegate on the managed side for the lifetime of the marshaled unmanaged function pointer.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="0bb4c-129">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="0bb4c-129">Effect on the Runtime</span></span>  
 <span data-ttu-id="0bb4c-130">當委派被封送處理為函式指標時，執行階段會配置從 Unmanaged 轉換到 Managed 的 Thunk。</span><span class="sxs-lookup"><span data-stu-id="0bb4c-130">When delegates are marshaled as function pointers, the runtime allocates a thunk that does the transition from unmanaged to managed.</span></span> <span data-ttu-id="0bb4c-131">這個 Thunk 是最後叫用 Managed 委派之前，Unmanaged 程式碼實際呼叫的項目。</span><span class="sxs-lookup"><span data-stu-id="0bb4c-131">This thunk is what the unmanaged code actually calls before the managed delegate is finally invoked.</span></span> <span data-ttu-id="0bb4c-132">若未啟用 `callbackOnCollectedDelegate` MDA，當委派被回收時，會刪除 Unmanaged 封送處理程式碼。</span><span class="sxs-lookup"><span data-stu-id="0bb4c-132">Without the `callbackOnCollectedDelegate` MDA enabled, the unmanaged marshaling code is deleted when the delegate is collected.</span></span> <span data-ttu-id="0bb4c-133">若已啟用 `callbackOnCollectedDelegate` MDA，當委派被回收時，就不會立即刪除 Unmanaged 封送處理程式碼。</span><span class="sxs-lookup"><span data-stu-id="0bb4c-133">With the `callbackOnCollectedDelegate` MDA enabled, the unmanaged marshaling code is not immediately deleted when the delegate is collected.</span></span> <span data-ttu-id="0bb4c-134">相反地，最後 1,000 個執行個體會依預設保持運作，並且在被呼叫時，變更為啟用 MDA。</span><span class="sxs-lookup"><span data-stu-id="0bb4c-134">Instead, the last 1,000 instances are kept alive by default and changed to activate the MDA when called.</span></span> <span data-ttu-id="0bb4c-135">在回收超過 1,001 個封送處理的委派之後，最後會刪除 Thunk。</span><span class="sxs-lookup"><span data-stu-id="0bb4c-135">The thunk is eventually deleted after 1,001 more marshaled delegates are collected.</span></span>  
  
## <a name="output"></a><span data-ttu-id="0bb4c-136">Output</span><span class="sxs-lookup"><span data-stu-id="0bb4c-136">Output</span></span>  
 <span data-ttu-id="0bb4c-137">MDA 會報告在其 Unmanaged 函式指標上嘗試回呼之前，所回收之委派的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="0bb4c-137">The MDA reports the type name of the delegate that was collected before a callback was attempted on its unmanaged function pointer.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="0bb4c-138">組態</span><span class="sxs-lookup"><span data-stu-id="0bb4c-138">Configuration</span></span>  
 <span data-ttu-id="0bb4c-139">下列範例顯示應用程式組態選項。</span><span class="sxs-lookup"><span data-stu-id="0bb4c-139">The following example shows the application configuration options.</span></span> <span data-ttu-id="0bb4c-140">它將 MDA 保持運作的 Thunk 數目設為 1,500。</span><span class="sxs-lookup"><span data-stu-id="0bb4c-140">It sets the number of thunks the MDA keeps alive to 1,500.</span></span> <span data-ttu-id="0bb4c-141">預設的 `listSize` 值為 1,000，最小值為 50，最大值為  2,000。</span><span class="sxs-lookup"><span data-stu-id="0bb4c-141">The default `listSize` value is 1,000, the minimum is 50, and the maximum is 2,000.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <callbackOnCollectedDelegate listSize="1500" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="0bb4c-142">範例</span><span class="sxs-lookup"><span data-stu-id="0bb4c-142">Example</span></span>  
 <span data-ttu-id="0bb4c-143">下列範例示範可以啟動此 MDA 的情況：</span><span class="sxs-lookup"><span data-stu-id="0bb4c-143">The following example demonstrates a situation that can activate this MDA:</span></span>  
  
```cpp
// Library.cpp : Defines the unmanaged entry point for the DLL application.  
#include "windows.h"  
#include "stdio.h"  
  
void (__stdcall *g_pfTarget)();  
  
void __stdcall Initialize(void __stdcall pfTarget())  
{  
    g_pfTarget = pfTarget;  
}  
  
void __stdcall Callback()  
{  
    g_pfTarget();  
}
```

```csharp
// C# Client  
using System;  
using System.Runtime.InteropServices;  
  
public class Entry  
{  
    public delegate void DCallback();  
  
    public static void Main()  
    {  
        new Entry();  
        Initialize(Target);  
        GC.Collect();  
        GC.WaitForPendingFinalizers();  
        Callback();  
    }  
  
    public static void Target()  
    {          
    }  
  
    [DllImport("Library", CallingConvention = CallingConvention.StdCall)]  
    public static extern void Initialize(DCallback pfDelegate);  
  
    [DllImport ("Library", CallingConvention = CallingConvention.StdCall)]  
    public static extern void Callback();  
  
    ~Entry() { Console.Error.WriteLine("Entry Collected"); }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="0bb4c-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0bb4c-144">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="0bb4c-145">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="0bb4c-145">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="0bb4c-146">Interop 封送處理</span><span class="sxs-lookup"><span data-stu-id="0bb4c-146">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
- [<span data-ttu-id="0bb4c-147">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="0bb4c-147">gcUnmanagedToManaged</span></span>](gcunmanagedtomanaged-mda.md)
