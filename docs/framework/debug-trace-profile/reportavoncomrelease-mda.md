---
title: reportAvOnComRelease MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), reference counting errors
- exceptions, reference counting errors
- ReportAvOnComRelease MDA
- COM release access violations
- user reference counting errors
- managed debugging assistants (MDAs), reference counting errors
- report access violation on Com release
- reference counting errors
ms.assetid: a2b86b63-08b2-4943-b344-3c2cf46ccd31
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0bea73a30cb103f0e72caf73a633229a0719dc6c
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052320"
---
# <a name="reportavoncomrelease-mda"></a><span data-ttu-id="6c49f-102">reportAvOnComRelease MDA</span><span class="sxs-lookup"><span data-stu-id="6c49f-102">reportAvOnComRelease MDA</span></span>
<span data-ttu-id="6c49f-103">如果在執行 COM Interop 並使用與原始 COM 呼叫組合的 `reportAvOnComRelease` 或 <xref:System.Runtime.InteropServices.Marshal.Release%2A> 方法時，因為使用者參考計數錯誤而擲回例外狀況，就會啟用 <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="6c49f-103">The `reportAvOnComRelease` managed debugging assistant (MDA) is activated when exceptions are thrown due to user reference counting errors while performing COM interop and using the <xref:System.Runtime.InteropServices.Marshal.Release%2A> or <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> method combined with raw COM calls.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="6c49f-104">徵兆</span><span class="sxs-lookup"><span data-stu-id="6c49f-104">Symptoms</span></span>  
 <span data-ttu-id="6c49f-105">存取違規與記憶體損毀。</span><span class="sxs-lookup"><span data-stu-id="6c49f-105">Access violations and memory corruption.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="6c49f-106">原因</span><span class="sxs-lookup"><span data-stu-id="6c49f-106">Cause</span></span>  
 <span data-ttu-id="6c49f-107">有時候，在執行 COM Interop 並使用與原始 COM 呼叫組合的 <xref:System.Runtime.InteropServices.Marshal.Release%2A> 或 <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> 方法時，會因為使用者參考計數錯誤而擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6c49f-107">Occasionally, an exception is thrown due to user reference counting errors while performing COM interop and using the <xref:System.Runtime.InteropServices.Marshal.Release%2A> or <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> method combined with raw COM calls.</span></span> <span data-ttu-id="6c49f-108">通常會捨棄此例外狀況，因為如果不這麼做，就會導致 CLR 發生存取違規，而降低效能。</span><span class="sxs-lookup"><span data-stu-id="6c49f-108">Normally, this exception is discarded because not doing so would cause an access violation in the CLR, bringing it down.</span></span> <span data-ttu-id="6c49f-109">如果啟用此助理，就會偵測並提報這類例外狀況，而不是直接捨棄。</span><span class="sxs-lookup"><span data-stu-id="6c49f-109">When this assistant is enabled, such exceptions can be detected and reported instead of being simply discarded.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="6c49f-110">解決方式</span><span class="sxs-lookup"><span data-stu-id="6c49f-110">Resolution</span></span>  
 <span data-ttu-id="6c49f-111">檢查您的參考計數程式碼，並搜尋錯誤，另外也要檢查物件的原生用戶端，查看是否有參考計數錯誤。</span><span class="sxs-lookup"><span data-stu-id="6c49f-111">Examine your reference counting code and search for errors as well as examining the native clients of your object for reference counting errors.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="6c49f-112">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="6c49f-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="6c49f-113">有兩種模式可用。</span><span class="sxs-lookup"><span data-stu-id="6c49f-113">Two modes are available.</span></span> <span data-ttu-id="6c49f-114">如果 `allowAv` 屬性為 `true`，該助理會防止執行階段捨棄存取違規。</span><span class="sxs-lookup"><span data-stu-id="6c49f-114">If the `allowAv` attribute is `true`, the assistant prevents the runtime from discarding the access violation.</span></span> <span data-ttu-id="6c49f-115">如果 `allowAv` 為 `false` (預設值)，則執行階段會捨棄存取違規，但是會向使用者提報警告訊息，指出已擲回並捨棄例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6c49f-115">If `allowAv` is `false`, which is the default, the runtime discards the access violation, but a warning message is reported to the user to indicate that an exception was thrown and discarded.</span></span>  
  
## <a name="output"></a><span data-ttu-id="6c49f-116">Output</span><span class="sxs-lookup"><span data-stu-id="6c49f-116">Output</span></span>  
 <span data-ttu-id="6c49f-117">如果可能，輸出會包含 COM 介面指標的原始 vtable。</span><span class="sxs-lookup"><span data-stu-id="6c49f-117">If possible, the output contains the COM interface pointer's original vtable.</span></span> <span data-ttu-id="6c49f-118">否則，就會顯示告知性訊息。</span><span class="sxs-lookup"><span data-stu-id="6c49f-118">Otherwise, an informational message is displayed.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="6c49f-119">組態</span><span class="sxs-lookup"><span data-stu-id="6c49f-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reportAvOnComRelease />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6c49f-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c49f-120">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="6c49f-121">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="6c49f-121">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="6c49f-122">Interop 封送處理</span><span class="sxs-lookup"><span data-stu-id="6c49f-122">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
