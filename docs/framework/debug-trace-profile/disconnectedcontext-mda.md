---
title: disconnectedContext MDA
description: 請參閱 .NET 中的 disconnectedCoNtext managed 偵錯工具，它是在 CLR 嘗試轉換成中斷連接的單元或內容時叫用。
ms.date: 03/30/2017
helpviewer_keywords:
- DisconnectedContext MDA
- MDAs (managed debugging assistants), disconnected context
- dead context
- transitioning disconnected apartment or context
- context disconnections
- managed debugging assistants (MDAs), disconnected context
ms.assetid: 1887d31d-7006-4491-93b3-68fd5b05f71d
ms.openlocfilehash: 0b24aadefab7a7cb2a5294f25e674d188beec814
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416079"
---
# <a name="disconnectedcontext-mda"></a><span data-ttu-id="22d48-103">disconnectedContext MDA</span><span class="sxs-lookup"><span data-stu-id="22d48-103">disconnectedContext MDA</span></span>
<span data-ttu-id="22d48-104">如果 CLR 在服務有關 COM 物件的要求時，試圖轉換至中斷連接的 Apartment 或內容，就會啟動 `disconnectedContext` Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="22d48-104">The `disconnectedContext` managed debugging assistant (MDA) is activated when the CLR attempts to transition into a disconnected apartment or context while servicing a request concerning a COM object.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="22d48-105">徵狀</span><span class="sxs-lookup"><span data-stu-id="22d48-105">Symptoms</span></span>  
 <span data-ttu-id="22d48-106">在[執行階段可呼叫包裝函式](../../standard/native-interop/runtime-callable-wrapper.md) (RCW) 上執行的呼叫會傳遞至目前 Apartment 或內容中的基礎 COM 元件，而不是其所在的 Apartment 或內容中。</span><span class="sxs-lookup"><span data-stu-id="22d48-106">Calls made on a [Runtime Callable Wrapper](../../standard/native-interop/runtime-callable-wrapper.md) (RCW) are delivered to the underlying COM component in the current apartment or context instead of the one in which they exist.</span></span> <span data-ttu-id="22d48-107">如果 COM 元件不是多執行緒，這可能會導致損毀及/或資料遺失，就像在單一執行緒 Apartment (STA) 元件的案例一樣。</span><span class="sxs-lookup"><span data-stu-id="22d48-107">This can cause corruption and or data loss if the COM component is not multithreaded, as in the case of single-threaded apartment (STA) components.</span></span> <span data-ttu-id="22d48-108">或者，如果 RCW 本身是 Proxy，則呼叫可能會導致擲回 <xref:System.Runtime.InteropServices.COMException>，且 HRESULT 為 RPC_E_WRONG_THREAD。</span><span class="sxs-lookup"><span data-stu-id="22d48-108">Alternatively, if the RCW is itself a proxy, the call might result in the throwing of a <xref:System.Runtime.InteropServices.COMException> with an HRESULT of RPC_E_WRONG_THREAD.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="22d48-109">原因</span><span class="sxs-lookup"><span data-stu-id="22d48-109">Cause</span></span>  
 <span data-ttu-id="22d48-110">當 CLR 試圖轉換至 OLE Apartment 或內容時，其已關閉。</span><span class="sxs-lookup"><span data-stu-id="22d48-110">The OLE apartment or context has been shut down when the CLR attempts to transition into it.</span></span> <span data-ttu-id="22d48-111">最常見的原因，就是在 Apartment 擁有的所有 COM 元件都完成發行之前，STA Apartment 即已關閉。從 RCW 上的使用者程式碼進行明確呼叫，或是 CLR 本身在操作 COM 元件時，就可能會導致這種情況發生，例如當相關聯的 RCW 已進行記憶體回收，而 CLR 還在發行 COM 元件時。</span><span class="sxs-lookup"><span data-stu-id="22d48-111">This is most commonly caused by STA apartments being shut down before all the COM components owned by the apartment were completely released This can occur as a result of an explicit call from user code on an RCW or while the CLR itself is manipulating the COM component, for example when the CLR is releasing the COM component when the associated RCW has been garbage collected.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="22d48-112">解決方案</span><span class="sxs-lookup"><span data-stu-id="22d48-112">Resolution</span></span>  
 <span data-ttu-id="22d48-113">若要避免此問題，請確定在應用程式完成 Apartment 中留存的所有物件之前，擁有 STA 的執行緒不會終止。</span><span class="sxs-lookup"><span data-stu-id="22d48-113">To avoid this problem, ensure the thread that owns the STA does not terminate before the application has finished with all the objects that live in the apartment.</span></span> <span data-ttu-id="22d48-114">對內容也是套用一樣的方式；請確定在應用程式完成內容中留存的任何 COM 元件之前，內容未關閉。</span><span class="sxs-lookup"><span data-stu-id="22d48-114">The same applies to contexts; ensure contexts are not shut down before the application is completely finished with any COM components that live inside the context.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="22d48-115">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="22d48-115">Effect on the Runtime</span></span>  
 <span data-ttu-id="22d48-116">此 MDA 對 CLR 沒有影響。</span><span class="sxs-lookup"><span data-stu-id="22d48-116">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="22d48-117">它只會提報中斷連接之內容的相關資料。</span><span class="sxs-lookup"><span data-stu-id="22d48-117">It only reports data about the disconnected context.</span></span>  
  
## <a name="output"></a><span data-ttu-id="22d48-118">輸出</span><span class="sxs-lookup"><span data-stu-id="22d48-118">Output</span></span>  
 <span data-ttu-id="22d48-119">提報中斷連接的 Apartment 或內容的內容 Cookie。</span><span class="sxs-lookup"><span data-stu-id="22d48-119">Reports the context cookie of the disconnected apartment or context.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="22d48-120">設定</span><span class="sxs-lookup"><span data-stu-id="22d48-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <disconnectedContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="22d48-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22d48-121">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="22d48-122">使用 Managed 偵錯助理診斷錯誤</span><span class="sxs-lookup"><span data-stu-id="22d48-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="22d48-123">Interop 封送處理</span><span class="sxs-lookup"><span data-stu-id="22d48-123">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
