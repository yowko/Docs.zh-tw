---
title: raceOnRCWCleanup MDA
ms.date: 03/30/2017
helpviewer_keywords:
- RCW
- managed debugging assistants (MDAs), RCWs
- race on RCW cleanup
- MDAs (managed debugging assistants), RCWs
- RaceOnRCWCleanup MDA
- runtime callable wrappers
ms.assetid: bee1e9b1-50a8-4c89-9cd9-7dd6b2458187
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 628790bb8229dc519589c122235f07a38ba57c1c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59100232"
---
# <a name="raceonrcwcleanup-mda"></a><span data-ttu-id="0f668-102">raceOnRCWCleanup MDA</span><span class="sxs-lookup"><span data-stu-id="0f668-102">raceOnRCWCleanup MDA</span></span>
<span data-ttu-id="0f668-103">當使用 <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> 方法這類命令呼叫釋放[執行階段可呼叫包裝函式](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) 時，如果 Common Language Runtime (CLR) 偵測到 RCW 正在使用中，則會啟動 `raceOnRCWCleanup` Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="0f668-103">The `raceOnRCWCleanup` managed debugging assistant (MDA) is activated when the common language runtime (CLR) detects that a [Runtime Callable Wrapper](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) is in use when a call to release it is made using a command such as the <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="0f668-104">徵兆</span><span class="sxs-lookup"><span data-stu-id="0f668-104">Symptoms</span></span>  
 <span data-ttu-id="0f668-105">使用 <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> 或類似方法釋放 RCW 期間或之後，發生存取違規或記憶體損毀的情況。</span><span class="sxs-lookup"><span data-stu-id="0f668-105">Access violations or memory corruption during or after freeing an RCW using <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> or a similar method.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="0f668-106">原因</span><span class="sxs-lookup"><span data-stu-id="0f668-106">Cause</span></span>  
 <span data-ttu-id="0f668-107">另一個執行緒正在使用這個 RCW，或釋放執行緒堆疊時正在使用這個 RCW。</span><span class="sxs-lookup"><span data-stu-id="0f668-107">The RCW is in use on another thread or on the freeing thread stack.</span></span>  <span data-ttu-id="0f668-108">無法釋放使用中的 RCW。</span><span class="sxs-lookup"><span data-stu-id="0f668-108">An RCW that is in use cannot be released.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="0f668-109">解決方式</span><span class="sxs-lookup"><span data-stu-id="0f668-109">Resolution</span></span>  
 <span data-ttu-id="0f668-110">請勿釋放目前執行緒或其他執行緒可能正在使用的 RCW。</span><span class="sxs-lookup"><span data-stu-id="0f668-110">Do not free an RCW that could be in use either in the current or in other threads.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="0f668-111">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="0f668-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="0f668-112">此 MDA 對 CLR 沒有影響。</span><span class="sxs-lookup"><span data-stu-id="0f668-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="0f668-113">Output</span><span class="sxs-lookup"><span data-stu-id="0f668-113">Output</span></span>  
 <span data-ttu-id="0f668-114">描述錯誤的訊息。</span><span class="sxs-lookup"><span data-stu-id="0f668-114">A message describing the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="0f668-115">組態</span><span class="sxs-lookup"><span data-stu-id="0f668-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <raceOnRCWCleanup/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0f668-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f668-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="0f668-117">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="0f668-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="0f668-118">Interop 封送處理</span><span class="sxs-lookup"><span data-stu-id="0f668-118">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
