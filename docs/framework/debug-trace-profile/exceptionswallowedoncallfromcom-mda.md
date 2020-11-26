---
title: exceptionSwallowedOnCallFromCom MDA
description: 請參閱 .NET 中的 exceptionSwallowedOnCallFromCOM managed 偵錯工具。 如果擲回例外狀況，就會發生此 MDA，但無法報告它。
ms.date: 03/30/2017
helpviewer_keywords:
- messages, informational
- informational messages
- managed debugging assistants (MDAs), exceptions
- exception handling, managed debugging assistants
- MDAs (managed debugging assistants), exceptions
- ExceptionSwallowedOnCallFromCOM MDA
ms.assetid: 55d6ab12-f251-4aab-aa64-aacbe9d9f974
ms.openlocfilehash: 11daccb4d1e757bf2fae25858d706eee5921c509
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244349"
---
# <a name="exceptionswallowedoncallfromcom-mda"></a><span data-ttu-id="453f3-104">exceptionSwallowedOnCallFromCom MDA</span><span class="sxs-lookup"><span data-stu-id="453f3-104">exceptionSwallowedOnCallFromCom MDA</span></span>

<span data-ttu-id="453f3-105">透過不含 Unmanaged HRESULT 傳回型別的方法，從 COM 呼叫的通用語言執行平台 (CLR) 擲回例外狀況時，就會啟用 `exceptionSwallowedOnCallFromCOM` Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="453f3-105">The `exceptionSwallowedOnCallFromCOM` managed debugging assistant (MDA) is activated when an exception is thrown from common language runtime (CLR) code called from COM via a method that does not have an unmanaged HRESULT return type.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="453f3-106">徵狀</span><span class="sxs-lookup"><span data-stu-id="453f3-106">Symptoms</span></span>  

 <span data-ttu-id="453f3-107">從 COM 呼叫 Managed 元件時，傳回的值為 FALSE 或 0。</span><span class="sxs-lookup"><span data-stu-id="453f3-107">A call to a managed component from COM returns with a value of FALSE or 0.</span></span> <span data-ttu-id="453f3-108">或者，如果方法具有 void 傳回型別，執行方法期間可能不會指出已擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="453f3-108">Alternatively, if the method has a void return type, there may be no indication that an exception was thrown during the execution of the method.</span></span> <span data-ttu-id="453f3-109">在這種情況下，會以無訊息模式攔截例外狀況，而執行作業會返回 COM 呼叫端。</span><span class="sxs-lookup"><span data-stu-id="453f3-109">In this case, the exception will be silently caught and execution will return to the COM caller.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="453f3-110">原因</span><span class="sxs-lookup"><span data-stu-id="453f3-110">Cause</span></span>  

 <span data-ttu-id="453f3-111">已擲回例外狀況，但沒有有效的方式來進行提報。</span><span class="sxs-lookup"><span data-stu-id="453f3-111">An exception was thrown, but there is no valid way to report it.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="453f3-112">解決方法</span><span class="sxs-lookup"><span data-stu-id="453f3-112">Resolution</span></span>  

 <span data-ttu-id="453f3-113">僅供參考，不一定表示有 Bug。</span><span class="sxs-lookup"><span data-stu-id="453f3-113">Informational only, not necessarily indicative of a bug.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="453f3-114">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="453f3-114">Effect on the Runtime</span></span>  

 <span data-ttu-id="453f3-115">此 MDA 對 CLR 沒有影響。</span><span class="sxs-lookup"><span data-stu-id="453f3-115">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="453f3-116">它只會提報以無訊息模式攔截例外狀況的相關資料。</span><span class="sxs-lookup"><span data-stu-id="453f3-116">It only reports data about silently caught exceptions.</span></span>  
  
## <a name="output"></a><span data-ttu-id="453f3-117">輸出</span><span class="sxs-lookup"><span data-stu-id="453f3-117">Output</span></span>  

 <span data-ttu-id="453f3-118">告知性訊息，包含方法名稱、類型名稱和例外狀況訊息。</span><span class="sxs-lookup"><span data-stu-id="453f3-118">Informational message containing the method name, type name, and exception message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="453f3-119">設定</span><span class="sxs-lookup"><span data-stu-id="453f3-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <exceptionSwallowedOnCallFromCom />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="453f3-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="453f3-120">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="453f3-121">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="453f3-121">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="453f3-122">Interop 封送處理</span><span class="sxs-lookup"><span data-stu-id="453f3-122">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
