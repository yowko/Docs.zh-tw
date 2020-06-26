---
title: failedQI MDA
description: 請參閱 .NET 中的 failedQI managed 偵錯工具（MDA），這可能會在執行時間可呼叫包裝函式（RCW）中的轉型或 COM 呼叫失敗時啟用。
ms.date: 03/30/2017
helpviewer_keywords:
- failed QueryInterface
- FailedQI MDA
- QueryInterface call failures
- MDAs (managed debugging assistants), failed QueryInterface
- managed debugging assistants (MDAs), failed QueryInterface
ms.assetid: 902dc863-34b3-477c-b433-b8a6bb6133c6
ms.openlocfilehash: 2d7f14c67d47e58bcb88eab4621df63d7c598a7a
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415936"
---
# <a name="failedqi-mda"></a><span data-ttu-id="cfe7f-103">failedQI MDA</span><span class="sxs-lookup"><span data-stu-id="cfe7f-103">failedQI MDA</span></span>
<span data-ttu-id="cfe7f-104">當執行階段代表執行階段可呼叫包裝函式 (RCW)，在 COM 介面指標上呼叫 `QueryInterface`，而 `QueryInterface` 呼叫失敗時，就會啟動 `failedQI` Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="cfe7f-104">The `failedQI` managed debugging assistant (MDA) is activated when the runtime calls `QueryInterface` on a COM interface pointer on behalf of a runtime callable wrapper (RCW), and the `QueryInterface` call fails.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="cfe7f-105">徵狀</span><span class="sxs-lookup"><span data-stu-id="cfe7f-105">Symptoms</span></span>  
 <span data-ttu-id="cfe7f-106">在 RCW 上轉換失敗，或從 RCW 呼叫 COM 時意外失敗。</span><span class="sxs-lookup"><span data-stu-id="cfe7f-106">A cast on an RCW fails, or a call to COM from an RCW fails unexpectedly.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="cfe7f-107">原因</span><span class="sxs-lookup"><span data-stu-id="cfe7f-107">Cause</span></span>  
  
- <span data-ttu-id="cfe7f-108">從錯誤的內容進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="cfe7f-108">The call is made from the wrong context.</span></span>  
  
- <span data-ttu-id="cfe7f-109">所註冊的 Proxy 導致 `QueryInterface` 呼叫失敗，因為是嘗試在錯誤的內容中呼叫。</span><span class="sxs-lookup"><span data-stu-id="cfe7f-109">The registered proxy is failing the `QueryInterface` call because the call was attempted in the wrong context.</span></span>  
  
- <span data-ttu-id="cfe7f-110">OLE 擁有的 Proxy 傳回失敗 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="cfe7f-110">An OLE-owned proxy returned a failure HRESULT.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="cfe7f-111">解決方案</span><span class="sxs-lookup"><span data-stu-id="cfe7f-111">Resolution</span></span>  
 <span data-ttu-id="cfe7f-112">請參閱有關 COM 規則的 MSDN 文件。</span><span class="sxs-lookup"><span data-stu-id="cfe7f-112">See the MSDN documentation on COM rules.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="cfe7f-113">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="cfe7f-113">Effect on the Runtime</span></span>  
 <span data-ttu-id="cfe7f-114">如果 `QueryInterface` 呼叫失敗，內容就會切換，然後重新嘗試 `QueryInterface` 呼叫，以查看是否有不正確的內容出錯。</span><span class="sxs-lookup"><span data-stu-id="cfe7f-114">If a `QueryInterface` call fails, the context is switched and the `QueryInterface` call is attempted again to see if an incorrect context was at fault.</span></span>  
  
## <a name="output"></a><span data-ttu-id="cfe7f-115">輸出</span><span class="sxs-lookup"><span data-stu-id="cfe7f-115">Output</span></span>  
 <span data-ttu-id="cfe7f-116">介面的 Managed 名稱、介面的 GUID，以及失敗的 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="cfe7f-116">The managed name of the interface, the GUID of the interface, and the HRESULT of the failure.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="cfe7f-117">設定</span><span class="sxs-lookup"><span data-stu-id="cfe7f-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <failedQI/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cfe7f-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cfe7f-118">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="cfe7f-119">使用 Managed 偵錯助理診斷錯誤</span><span class="sxs-lookup"><span data-stu-id="cfe7f-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="cfe7f-120">Interop 封送處理</span><span class="sxs-lookup"><span data-stu-id="cfe7f-120">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
