---
title: overlappedFreeError MDA
description: 請參閱 .NET 中的 overlappedFreeError managed 偵錯工具 (MDA) ，這可能會在存取違規或垃圾收集堆積損毀時啟動。
ms.date: 03/30/2017
helpviewer_keywords:
- OverlappedFreeError MDA
- overlapped free method call error
- managed debugging assistants (MDAs), overlapped structures
- overlapped structures
- MDAs (managed debugging assistants), overlapped structures
- freeing overlapped structures
ms.assetid: b6ab2d48-6eee-4bab-97a3-046b3b0a5470
ms.openlocfilehash: 1bedb8ad3b9801f0d235371a397c8951ff8723b1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96254528"
---
# <a name="overlappedfreeerror-mda"></a><span data-ttu-id="af734-103">overlappedFreeError MDA</span><span class="sxs-lookup"><span data-stu-id="af734-103">overlappedFreeError MDA</span></span>

<span data-ttu-id="af734-104">重疊作業完成之前，呼叫 <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> 方法時，會啟用 `overlappedFreeError` Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="af734-104">The `overlappedFreeError` managed debugging assistant (MDA) is activated when the <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> method is called before the overlapped operation has completed.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="af734-105">徵狀</span><span class="sxs-lookup"><span data-stu-id="af734-105">Symptoms</span></span>  

 <span data-ttu-id="af734-106">已進行記憶體回收之堆積的存取違規或損毀。</span><span class="sxs-lookup"><span data-stu-id="af734-106">Access violations or corruption of the garbage-collected heap.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="af734-107">原因</span><span class="sxs-lookup"><span data-stu-id="af734-107">Cause</span></span>  

 <span data-ttu-id="af734-108">作業完成之前，已釋放重疊結構。</span><span class="sxs-lookup"><span data-stu-id="af734-108">An overlapped structure was freed before the operation completed.</span></span> <span data-ttu-id="af734-109">使用重疊指標的函式稍後可能會在釋出之後寫入結構中。</span><span class="sxs-lookup"><span data-stu-id="af734-109">The function that is using the overlapped pointer might write to the structure later, after it has been freed.</span></span> <span data-ttu-id="af734-110">這可能會造成堆積損毀，因為另一個物件現在可能會佔用該區域。</span><span class="sxs-lookup"><span data-stu-id="af734-110">That can cause heap corruption because another object might now occupy that region.</span></span>  
  
 <span data-ttu-id="af734-111">如果未成功啟動重疊的作業，則此 MDA 可能不會呈現錯誤。</span><span class="sxs-lookup"><span data-stu-id="af734-111">This MDA might not represent an error if the overlapped operation did not start successfully.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="af734-112">解決方法</span><span class="sxs-lookup"><span data-stu-id="af734-112">Resolution</span></span>  

 <span data-ttu-id="af734-113">請確定使用重疊結構的 I/O 作業完成，再呼叫 <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> 方法。</span><span class="sxs-lookup"><span data-stu-id="af734-113">Ensure that the I/O operation using the overlapped structure has completed before calling the <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="af734-114">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="af734-114">Effect on the Runtime</span></span>  

 <span data-ttu-id="af734-115">此 MDA 對 CLR 沒有影響。</span><span class="sxs-lookup"><span data-stu-id="af734-115">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="af734-116">輸出</span><span class="sxs-lookup"><span data-stu-id="af734-116">Output</span></span>  

 <span data-ttu-id="af734-117">以下是此 MDA 的範例輸出。</span><span class="sxs-lookup"><span data-stu-id="af734-117">The following is sample output for this MDA.</span></span>  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlappedStructure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a><span data-ttu-id="af734-118">設定</span><span class="sxs-lookup"><span data-stu-id="af734-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <overlappedFreeError/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="af734-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af734-119">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="af734-120">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="af734-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="af734-121">Interop 封送處理</span><span class="sxs-lookup"><span data-stu-id="af734-121">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
