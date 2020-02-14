---
title: exceptionSwallowedOnCallFromCom MDA
ms.date: 03/30/2017
helpviewer_keywords:
- messages, informational
- informational messages
- managed debugging assistants (MDAs), exceptions
- exception handling, managed debugging assistants
- MDAs (managed debugging assistants), exceptions
- ExceptionSwallowedOnCallFromCOM MDA
ms.assetid: 55d6ab12-f251-4aab-aa64-aacbe9d9f974
ms.openlocfilehash: 4ccb03c9a8a473c10f15b00e64810b04f21504c9
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217516"
---
# <a name="exceptionswallowedoncallfromcom-mda"></a><span data-ttu-id="d49be-102">exceptionSwallowedOnCallFromCom MDA</span><span class="sxs-lookup"><span data-stu-id="d49be-102">exceptionSwallowedOnCallFromCom MDA</span></span>
<span data-ttu-id="d49be-103">透過不含 Unmanaged HRESULT 傳回型別的方法，從 COM 呼叫的通用語言執行平台 (CLR) 擲回例外狀況時，就會啟用 `exceptionSwallowedOnCallFromCOM` Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="d49be-103">The `exceptionSwallowedOnCallFromCOM` managed debugging assistant (MDA) is activated when an exception is thrown from common language runtime (CLR) code called from COM via a method that does not have an unmanaged HRESULT return type.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="d49be-104">徵狀</span><span class="sxs-lookup"><span data-stu-id="d49be-104">Symptoms</span></span>  
 <span data-ttu-id="d49be-105">從 COM 呼叫 Managed 元件時，傳回的值為 FALSE 或 0。</span><span class="sxs-lookup"><span data-stu-id="d49be-105">A call to a managed component from COM returns with a value of FALSE or 0.</span></span> <span data-ttu-id="d49be-106">或者，如果方法具有 void 傳回型別，執行方法期間可能不會指出已擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d49be-106">Alternatively, if the method has a void return type, there may be no indication that an exception was thrown during the execution of the method.</span></span> <span data-ttu-id="d49be-107">在這種情況下，會以無訊息模式攔截例外狀況，而執行作業會返回 COM 呼叫端。</span><span class="sxs-lookup"><span data-stu-id="d49be-107">In this case, the exception will be silently caught and execution will return to the COM caller.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="d49be-108">原因</span><span class="sxs-lookup"><span data-stu-id="d49be-108">Cause</span></span>  
 <span data-ttu-id="d49be-109">已擲回例外狀況，但沒有有效的方式來進行提報。</span><span class="sxs-lookup"><span data-stu-id="d49be-109">An exception was thrown, but there is no valid way to report it.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="d49be-110">解決方案</span><span class="sxs-lookup"><span data-stu-id="d49be-110">Resolution</span></span>  
 <span data-ttu-id="d49be-111">僅供參考，不一定表示有 Bug。</span><span class="sxs-lookup"><span data-stu-id="d49be-111">Informational only, not necessarily indicative of a bug.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="d49be-112">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="d49be-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="d49be-113">此 MDA 對 CLR 沒有影響。</span><span class="sxs-lookup"><span data-stu-id="d49be-113">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="d49be-114">它只會提報以無訊息模式攔截例外狀況的相關資料。</span><span class="sxs-lookup"><span data-stu-id="d49be-114">It only reports data about silently caught exceptions.</span></span>  
  
## <a name="output"></a><span data-ttu-id="d49be-115">輸出</span><span class="sxs-lookup"><span data-stu-id="d49be-115">Output</span></span>  
 <span data-ttu-id="d49be-116">告知性訊息，包含方法名稱、類型名稱和例外狀況訊息。</span><span class="sxs-lookup"><span data-stu-id="d49be-116">Informational message containing the method name, type name, and exception message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="d49be-117">組態</span><span class="sxs-lookup"><span data-stu-id="d49be-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <exceptionSwallowedOnCallFromCom />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d49be-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d49be-118">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="d49be-119">使用 Managed 偵錯助理診斷錯誤</span><span class="sxs-lookup"><span data-stu-id="d49be-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="d49be-120">Interop 封送處理</span><span class="sxs-lookup"><span data-stu-id="d49be-120">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
