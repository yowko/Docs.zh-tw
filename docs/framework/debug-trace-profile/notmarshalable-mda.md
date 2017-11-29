---
title: notMarshalable MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed debugging assistants (MDAs), interface pointer not marshalable
- interface pointer not marshalable MDA
- MDAs (managed debugging assistants), interface pointer not marshalable
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- marshalable interface pointers
- MDAs (managed debugging assistants), marshaling
- notMarshalable MDA
ms.assetid: 96e7b2c1-843f-4d64-b519-740c3a18b50a
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c5de75130acab30c4f73522728c00b69c1c3e8d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="notmarshalable-mda"></a><span data-ttu-id="4c1c5-102">notMarshalable MDA</span><span class="sxs-lookup"><span data-stu-id="4c1c5-102">notMarshalable MDA</span></span>
<span data-ttu-id="4c1c5-103">在跨內容封送處理介面時，當 Common Language Runtime (CLR) 遇到 COM 介面指標，卻無有效已登錄的 Proxy/Stub 或 `IMarshal` 界面實作不正確，則會啟動 `notMarshalable` Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="4c1c5-103">The `notMarshalable` managed debugging assistant (MDA) is activated when the common language runtime (CLR) encounters a COM interface pointer without a valid registered proxy/stub or an incorrect `IMarshal` interface implementation while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="4c1c5-104">徵兆 </span><span class="sxs-lookup"><span data-stu-id="4c1c5-104">Symptoms</span></span>  
 <span data-ttu-id="4c1c5-105">未服務呼叫，或呼叫在錯誤的 COM 介面指標的內容中發生。</span><span class="sxs-lookup"><span data-stu-id="4c1c5-105">Calls are not serviced, or calls occur in the wrong context for COM interface pointers.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="4c1c5-106">原因</span><span class="sxs-lookup"><span data-stu-id="4c1c5-106">Cause</span></span>  
 <span data-ttu-id="4c1c5-107">嘗試跨內容封送處理介面時，沒有有效的已登錄 Proxy/Stub 或 `IMarshal` 不正確。</span><span class="sxs-lookup"><span data-stu-id="4c1c5-107">No valid registered proxy/stub or an incorrect `IMarshal` while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="4c1c5-108">解決方式</span><span class="sxs-lookup"><span data-stu-id="4c1c5-108">Resolution</span></span>  
 <span data-ttu-id="4c1c5-109">請確定您已註冊 Proxy 虛設常式，並確定 `IMarshal` 實作是否有效。</span><span class="sxs-lookup"><span data-stu-id="4c1c5-109">Make sure you have a proxy stub registered and that the `IMarshal` implementation is valid.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="4c1c5-110">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="4c1c5-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="4c1c5-111">此 MDA 對執行階段沒有影響。</span><span class="sxs-lookup"><span data-stu-id="4c1c5-111">This MDA has no effect on the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="4c1c5-112">輸出</span><span class="sxs-lookup"><span data-stu-id="4c1c5-112">Output</span></span>  
 <span data-ttu-id="4c1c5-113">描述問題的訊息。</span><span class="sxs-lookup"><span data-stu-id="4c1c5-113">A message describing the problem.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="4c1c5-114">組態</span><span class="sxs-lookup"><span data-stu-id="4c1c5-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <notMarshalable/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4c1c5-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c1c5-115">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="4c1c5-116">使用 Managed 偵錯助理診斷錯誤</span><span class="sxs-lookup"><span data-stu-id="4c1c5-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="4c1c5-117">Interop 封送處理</span><span class="sxs-lookup"><span data-stu-id="4c1c5-117">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
