---
title: overlappedFreeError MDA
ms.date: 03/30/2017
helpviewer_keywords:
- OverlappedFreeError MDA
- overlapped free method call error
- managed debugging assistants (MDAs), overlapped structures
- overlapped structures
- MDAs (managed debugging assistants), overlapped structures
- freeing overlapped structures
ms.assetid: b6ab2d48-6eee-4bab-97a3-046b3b0a5470
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 675e2e4d5022f0260450f9f0b2025f215b3ead7e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54708281"
---
# <a name="overlappedfreeerror-mda"></a><span data-ttu-id="2e6a2-102">overlappedFreeError MDA</span><span class="sxs-lookup"><span data-stu-id="2e6a2-102">overlappedFreeError MDA</span></span>
<span data-ttu-id="2e6a2-103">重疊作業完成之前，呼叫 <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> 方法時，會啟用 `overlappedFreeError` Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="2e6a2-103">The `overlappedFreeError` managed debugging assistant (MDA) is activated when the <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> method is called before the overlapped operation has completed.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="2e6a2-104">徵兆</span><span class="sxs-lookup"><span data-stu-id="2e6a2-104">Symptoms</span></span>  
 <span data-ttu-id="2e6a2-105">已進行記憶體回收之堆積的存取違規或損毀。</span><span class="sxs-lookup"><span data-stu-id="2e6a2-105">Access violations or corruption of the garbage-collected heap.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="2e6a2-106">原因</span><span class="sxs-lookup"><span data-stu-id="2e6a2-106">Cause</span></span>  
 <span data-ttu-id="2e6a2-107">作業完成之前，已釋放重疊結構。</span><span class="sxs-lookup"><span data-stu-id="2e6a2-107">An overlapped structure was freed before the operation completed.</span></span> <span data-ttu-id="2e6a2-108">使用重疊指標的函式稍後可能會在釋出之後寫入結構中。</span><span class="sxs-lookup"><span data-stu-id="2e6a2-108">The function that is using the overlapped pointer might write to the structure later, after it has been freed.</span></span> <span data-ttu-id="2e6a2-109">這可能會造成堆積損毀，因為另一個物件現在可能會佔用該區域。</span><span class="sxs-lookup"><span data-stu-id="2e6a2-109">That can cause heap corruption because another object might now occupy that region.</span></span>  
  
 <span data-ttu-id="2e6a2-110">如果未成功啟動重疊的作業，則此 MDA 可能不會呈現錯誤。</span><span class="sxs-lookup"><span data-stu-id="2e6a2-110">This MDA might not represent an error if the overlapped operation did not start successfully.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="2e6a2-111">解決方式</span><span class="sxs-lookup"><span data-stu-id="2e6a2-111">Resolution</span></span>  
 <span data-ttu-id="2e6a2-112">請確定使用重疊結構的 I/O 作業完成，再呼叫 <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> 方法。</span><span class="sxs-lookup"><span data-stu-id="2e6a2-112">Ensure that the I/O operation using the overlapped structure has completed before calling the <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="2e6a2-113">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="2e6a2-113">Effect on the Runtime</span></span>  
 <span data-ttu-id="2e6a2-114">此 MDA 對 CLR 沒有影響。</span><span class="sxs-lookup"><span data-stu-id="2e6a2-114">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="2e6a2-115">輸出</span><span class="sxs-lookup"><span data-stu-id="2e6a2-115">Output</span></span>  
 <span data-ttu-id="2e6a2-116">以下是此 MDA 的範例輸出。</span><span class="sxs-lookup"><span data-stu-id="2e6a2-116">The following is sample output for this MDA.</span></span>  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlappedStructure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a><span data-ttu-id="2e6a2-117">組態</span><span class="sxs-lookup"><span data-stu-id="2e6a2-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <overlappedFreeError/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2e6a2-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e6a2-118">See also</span></span>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="2e6a2-119">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="2e6a2-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="2e6a2-120">Interop 封送處理</span><span class="sxs-lookup"><span data-stu-id="2e6a2-120">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
