---
title: gcUnmanagedToManaged MDA
description: 請參閱 .NET 中的 gcManagedToUnmanaged managed 偵錯工具。 此 MDA 可能會因為轉換至 managed 程式碼期間的垃圾堆積損毀而啟用。
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), garbage collection
- GC unmanaged to managed
- transitioning threads unmanaged to managed code
- GcUnmanagedToManaged MDA
- threading [.NET Framework], garbage collection
- managed debugging assistants (MDAs), garbage collection
- threading [.NET Framework], managed debugging assistants
- garbage collection, run-time errors
- unmanaged to managed garbage collection
ms.assetid: 103eb3a3-1cf0-4406-8a9a-a7798fdc22d1
ms.openlocfilehash: 61fbdbf0d3941aa3e876748ae4d76cd7ad0c0977
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244219"
---
# <a name="gcunmanagedtomanaged-mda"></a><span data-ttu-id="1acf2-104">gcUnmanagedToManaged MDA</span><span class="sxs-lookup"><span data-stu-id="1acf2-104">gcUnmanagedToManaged MDA</span></span>

<span data-ttu-id="1acf2-105">每當執行緒從 Unmanaged 轉換到 Managed 程式碼時，`gcUnmanagedToManaged` Managed 偵錯助理 (MDA) 會造成記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="1acf2-105">The `gcUnmanagedToManaged` managed debugging assistant (MDA) causes a garbage collection whenever a thread transitions from unmanaged to managed code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="1acf2-106">徵狀</span><span class="sxs-lookup"><span data-stu-id="1acf2-106">Symptoms</span></span>  

 <span data-ttu-id="1acf2-107">使用 COM 和平台叫用執行 Unmanaged 使用者元件的應用程式在 CLR 中造成不具決定性的存取違規。</span><span class="sxs-lookup"><span data-stu-id="1acf2-107">An application running unmanaged user components using COM and platform invoke is causing a nondeterministic access violation in the CLR.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="1acf2-108">原因</span><span class="sxs-lookup"><span data-stu-id="1acf2-108">Cause</span></span>  

 <span data-ttu-id="1acf2-109">如果應用程式正在執行 Unmanaged 使用者元件，那麼這些元件可能已損毀記憶體回收的堆積。</span><span class="sxs-lookup"><span data-stu-id="1acf2-109">If an application is running unmanaged user components, then those components might have corrupted the garbage-collected heap.</span></span> <span data-ttu-id="1acf2-110">在 CLR 中，當記憶體回收行程嘗試查核物件圖形時，這會造成存取違規。</span><span class="sxs-lookup"><span data-stu-id="1acf2-110">This causes an access violation in the CLR when the garbage collector tries to walk the object graph.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="1acf2-111">解決方法</span><span class="sxs-lookup"><span data-stu-id="1acf2-111">Resolution</span></span>  

 <span data-ttu-id="1acf2-112">在每次 Managed 轉換之前，啟用此助理會減少從 Unmanaged 元件損毀記憶體回收的堆積到強制執行記憶體回收而發生存取違規的間隔時間。</span><span class="sxs-lookup"><span data-stu-id="1acf2-112">Enabling this assistant reduces the time between when the unmanaged component corrupts the garbage-collected heap and when the access violation happens by forcing a garbage collection to occur before every managed transition.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="1acf2-113">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="1acf2-113">Effect on the Runtime</span></span>  

 <span data-ttu-id="1acf2-114">每當執行緒從 Unmanaged 轉換到 Managed 程式碼時，會造成記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="1acf2-114">Causes a garbage collection whenever a thread transitions from unmanaged to managed code.</span></span>  
  
## <a name="output"></a><span data-ttu-id="1acf2-115">輸出</span><span class="sxs-lookup"><span data-stu-id="1acf2-115">Output</span></span>  

 <span data-ttu-id="1acf2-116">此 MDA 不會產生輸出。</span><span class="sxs-lookup"><span data-stu-id="1acf2-116">This MDA produces no output.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="1acf2-117">設定</span><span class="sxs-lookup"><span data-stu-id="1acf2-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcUnmanagedToManaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1acf2-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1acf2-118">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="1acf2-119">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="1acf2-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="1acf2-120">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="1acf2-120">gcManagedToUnmanaged</span></span>](gcmanagedtounmanaged-mda.md)
- [<span data-ttu-id="1acf2-121">Interop 封送處理</span><span class="sxs-lookup"><span data-stu-id="1acf2-121">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
