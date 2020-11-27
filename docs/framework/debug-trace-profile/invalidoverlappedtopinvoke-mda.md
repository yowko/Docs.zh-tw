---
title: invalidOverlappedToPinvoke MDA
description: 請參閱 .NET 中的 invalidOverlappedToPinvoke managed 偵錯工具 (MDA) ，這可能會在損毀或無法解釋堆積損毀期間啟用。
ms.date: 03/30/2017
helpviewer_keywords:
- overlapped pointers
- managed debugging assistants (MDAs), overlapped pointers
- invalid overlapped pointer to platform invoke
- InvalidOverlappedToPinvoke MDA
- MDAs (managed debugging assistants), overlapped pointers
- pointers, overlapped
ms.assetid: 28876047-58bd-4fed-9452-c7da346d67c0
ms.openlocfilehash: 55b10af87130bd32410508cef2bc3e4e733549c0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96281319"
---
# <a name="invalidoverlappedtopinvoke-mda"></a><span data-ttu-id="20fd7-103">invalidOverlappedToPinvoke MDA</span><span class="sxs-lookup"><span data-stu-id="20fd7-103">invalidOverlappedToPinvoke MDA</span></span>

<span data-ttu-id="20fd7-104">當不是在記憶體回收堆積上建立的重疊指標傳遞至特定的 Win32 函式時，就會啟動 `invalidOverlappedToPinvoke` Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="20fd7-104">The `invalidOverlappedToPinvoke` managed debugging assistant (MDA) is activated when an overlapped pointer that was not created on the garbage collection heap is passed to specific Win32 functions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="20fd7-105">根據預設，只有在程式碼中定義了平台叫用呼叫，而且偵錯工具報告每一個方法的 JustMyCode 狀態時，才會啟用這個 MDA。</span><span class="sxs-lookup"><span data-stu-id="20fd7-105">By default, this MDA is activated only if the platform invoke call is defined in your code and the debugger reports the JustMyCode status of each method.</span></span> <span data-ttu-id="20fd7-106">不了解 JustMyCode (例如 MDbg.exe 沒有副檔名) 的偵錯工具，不會啟動此 MDA。</span><span class="sxs-lookup"><span data-stu-id="20fd7-106">A debugger that does not understand JustMyCode (such as MDbg.exe with no extensions) will not activate this MDA.</span></span> <span data-ttu-id="20fd7-107">使用組態檔和在 .mda.config 檔案 `(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>`) 中明確設定 `justMyCode="false"`，可針對這些偵錯工具啟用此 MDA。</span><span class="sxs-lookup"><span data-stu-id="20fd7-107">This MDA can be enabled for those debuggers by using a configuration file and explicitly settting `justMyCode="false"` in the .mda.config file `(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>`).</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="20fd7-108">徵狀</span><span class="sxs-lookup"><span data-stu-id="20fd7-108">Symptoms</span></span>  

 <span data-ttu-id="20fd7-109">當機或無法解釋的堆積損毀。</span><span class="sxs-lookup"><span data-stu-id="20fd7-109">Crashes or unexplainable heap corruptions.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="20fd7-110">原因</span><span class="sxs-lookup"><span data-stu-id="20fd7-110">Cause</span></span>  

 <span data-ttu-id="20fd7-111">不是在記憶體回收堆積建立的重疊指標，會傳遞給特定的作業系統函式。</span><span class="sxs-lookup"><span data-stu-id="20fd7-111">An overlapped pointer that was not created on the garbage collection heap is passed to specific operating system functions.</span></span>  
  
 <span data-ttu-id="20fd7-112">下表會顯示這個 MDA 追蹤的函式。</span><span class="sxs-lookup"><span data-stu-id="20fd7-112">The following table shows the functions that this MDA tracks.</span></span>  
  
|<span data-ttu-id="20fd7-113">模組</span><span class="sxs-lookup"><span data-stu-id="20fd7-113">Module</span></span>|<span data-ttu-id="20fd7-114">函式</span><span class="sxs-lookup"><span data-stu-id="20fd7-114">Function</span></span>|  
|------------|--------------|  
|<span data-ttu-id="20fd7-115">HttpApi.dll</span><span class="sxs-lookup"><span data-stu-id="20fd7-115">HttpApi.dll</span></span>|`HttpReceiveHttpRequest`|  
|<span data-ttu-id="20fd7-116">IpHlpApi.dll</span><span class="sxs-lookup"><span data-stu-id="20fd7-116">IpHlpApi.dll</span></span>|`NotifyAddrChange`|  
|<span data-ttu-id="20fd7-117">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="20fd7-117">kernel32.dll</span></span>|`ReadFile`|  
|<span data-ttu-id="20fd7-118">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="20fd7-118">kernel32.dll</span></span>|`ReadFileEx`|  
|<span data-ttu-id="20fd7-119">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="20fd7-119">kernel32.dll</span></span>|`WriteFile`|  
|<span data-ttu-id="20fd7-120">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="20fd7-120">kernel32.dll</span></span>|`WriteFileEx`|  
|<span data-ttu-id="20fd7-121">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="20fd7-121">kernel32.dll</span></span>|`ReadDirectoryChangesW`|  
|<span data-ttu-id="20fd7-122">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="20fd7-122">kernel32.dll</span></span>|`PostQueuedCompletionStatus`|  
|<span data-ttu-id="20fd7-123">MSWSock.dll</span><span class="sxs-lookup"><span data-stu-id="20fd7-123">MSWSock.dll</span></span>|`ConnectEx`|  
|<span data-ttu-id="20fd7-124">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="20fd7-124">WS2_32.dll</span></span>|`WSASend`|  
|<span data-ttu-id="20fd7-125">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="20fd7-125">WS2_32.dll</span></span>|`WSASendTo`|  
|<span data-ttu-id="20fd7-126">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="20fd7-126">WS2_32.dll</span></span>|`WSARecv`|  
|<span data-ttu-id="20fd7-127">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="20fd7-127">WS2_32.dll</span></span>|`WSARecvFrom`|  
|<span data-ttu-id="20fd7-128">MQRT.dll</span><span class="sxs-lookup"><span data-stu-id="20fd7-128">MQRT.dll</span></span>|`MQReceiveMessage`|  
  
 <span data-ttu-id="20fd7-129">這種狀況的堆積損毀可能性很高，因為可能會卸載 <xref:System.AppDomain> 進行的呼叫。</span><span class="sxs-lookup"><span data-stu-id="20fd7-129">The potential for heap corruption is high for this condition because the <xref:System.AppDomain> making the call might unload.</span></span> <span data-ttu-id="20fd7-130">如果 <xref:System.AppDomain> 卸載，則應用程式程式碼會釋放重疊指標的記憶體，在作業完成時導致損毀，或程式碼將流失記憶體，造成後來的問題。</span><span class="sxs-lookup"><span data-stu-id="20fd7-130">If the <xref:System.AppDomain> unloads, the application code will either free the memory for the overlapped pointer, causing corruption when the operation finishes, or the code will leak the memory, causing difficulties later.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="20fd7-131">解決方法</span><span class="sxs-lookup"><span data-stu-id="20fd7-131">Resolution</span></span>  

 <span data-ttu-id="20fd7-132">使用 <xref:System.Threading.Overlapped> 物件，呼叫 <xref:System.Threading.Overlapped.Pack%2A> 方法以取得可以傳遞至函式的 <xref:System.Threading.NativeOverlapped> 結構。</span><span class="sxs-lookup"><span data-stu-id="20fd7-132">Use an <xref:System.Threading.Overlapped> object, calling the <xref:System.Threading.Overlapped.Pack%2A> method to get a <xref:System.Threading.NativeOverlapped> structure that can be passed to the function.</span></span> <span data-ttu-id="20fd7-133">如果 <xref:System.AppDomain> 卸載，CLR 會等到非同步作業完成後再釋放指標。</span><span class="sxs-lookup"><span data-stu-id="20fd7-133">If the <xref:System.AppDomain> unloads, the CLR waits until the asynchronous operation completes before freeing the pointer.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="20fd7-134">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="20fd7-134">Effect on the Runtime</span></span>  

 <span data-ttu-id="20fd7-135">此 MDA 以前對 CLR 沒有影響。</span><span class="sxs-lookup"><span data-stu-id="20fd7-135">This MDA had no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="20fd7-136">輸出</span><span class="sxs-lookup"><span data-stu-id="20fd7-136">Output</span></span>  

 <span data-ttu-id="20fd7-137">以下是此 MDA 輸出的範例。</span><span class="sxs-lookup"><span data-stu-id="20fd7-137">The following is an example of output from this MDA.</span></span>  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the Win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlapped structure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a><span data-ttu-id="20fd7-138">設定</span><span class="sxs-lookup"><span data-stu-id="20fd7-138">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidOverlappedToPinvoke/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="20fd7-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="20fd7-139">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="20fd7-140">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="20fd7-140">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="20fd7-141">Interop 封送處理</span><span class="sxs-lookup"><span data-stu-id="20fd7-141">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
