---
title: raceOnRCWCleanup MDA
description: 檢查 raceOnRCWCleanup managed 偵錯工具（MDA），這是在另一個執行緒上或在 .NET 的釋放執行緒堆疊上使用 RCW 時啟動的。
ms.date: 03/30/2017
helpviewer_keywords:
- RCW
- managed debugging assistants (MDAs), RCWs
- race on RCW cleanup
- MDAs (managed debugging assistants), RCWs
- RaceOnRCWCleanup MDA
- runtime callable wrappers
ms.assetid: bee1e9b1-50a8-4c89-9cd9-7dd6b2458187
ms.openlocfilehash: e86ef96bebb648c7927ae5fec8b68fc4429b268b
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803647"
---
# <a name="raceonrcwcleanup-mda"></a><span data-ttu-id="ffce1-103">raceOnRCWCleanup MDA</span><span class="sxs-lookup"><span data-stu-id="ffce1-103">raceOnRCWCleanup MDA</span></span>
<span data-ttu-id="ffce1-104">當使用 <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> 方法這類命令呼叫釋放[執行階段可呼叫包裝函式](../../standard/native-interop/runtime-callable-wrapper.md) (RCW) 時，如果 Common Language Runtime (CLR) 偵測到 RCW 正在使用中，則會啟動 `raceOnRCWCleanup` Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="ffce1-104">The `raceOnRCWCleanup` managed debugging assistant (MDA) is activated when the common language runtime (CLR) detects that a [Runtime Callable Wrapper](../../standard/native-interop/runtime-callable-wrapper.md) (RCW) is in use when a call to release it is made using a command such as the <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="ffce1-105">徵狀</span><span class="sxs-lookup"><span data-stu-id="ffce1-105">Symptoms</span></span>  
 <span data-ttu-id="ffce1-106">使用 <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> 或類似方法釋放 RCW 期間或之後，發生存取違規或記憶體損毀的情況。</span><span class="sxs-lookup"><span data-stu-id="ffce1-106">Access violations or memory corruption during or after freeing an RCW using <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> or a similar method.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="ffce1-107">原因</span><span class="sxs-lookup"><span data-stu-id="ffce1-107">Cause</span></span>  
 <span data-ttu-id="ffce1-108">另一個執行緒正在使用這個 RCW，或釋放執行緒堆疊時正在使用這個 RCW。</span><span class="sxs-lookup"><span data-stu-id="ffce1-108">The RCW is in use on another thread or on the freeing thread stack.</span></span>  <span data-ttu-id="ffce1-109">無法釋放使用中的 RCW。</span><span class="sxs-lookup"><span data-stu-id="ffce1-109">An RCW that is in use cannot be released.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="ffce1-110">解決方案</span><span class="sxs-lookup"><span data-stu-id="ffce1-110">Resolution</span></span>  
 <span data-ttu-id="ffce1-111">請勿釋放目前執行緒或其他執行緒可能正在使用的 RCW。</span><span class="sxs-lookup"><span data-stu-id="ffce1-111">Do not free an RCW that could be in use either in the current or in other threads.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="ffce1-112">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="ffce1-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="ffce1-113">此 MDA 對 CLR 沒有影響。</span><span class="sxs-lookup"><span data-stu-id="ffce1-113">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="ffce1-114">輸出</span><span class="sxs-lookup"><span data-stu-id="ffce1-114">Output</span></span>  
 <span data-ttu-id="ffce1-115">描述錯誤的訊息。</span><span class="sxs-lookup"><span data-stu-id="ffce1-115">A message describing the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="ffce1-116">組態</span><span class="sxs-lookup"><span data-stu-id="ffce1-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <raceOnRCWCleanup/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ffce1-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ffce1-117">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="ffce1-118">使用 Managed 偵錯助理診斷錯誤</span><span class="sxs-lookup"><span data-stu-id="ffce1-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="ffce1-119">Interop 封送處理</span><span class="sxs-lookup"><span data-stu-id="ffce1-119">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
