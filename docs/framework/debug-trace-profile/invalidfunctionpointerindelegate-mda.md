---
title: invalidFunctionPointerInDelegate MDA
ms.date: 03/30/2017
helpviewer_keywords:
- invalidFunctionPointerInDelegate MDA
- managed debugging assistants (MDAs), invalid function pointer to delegates
- MDAs (managed debugging assistants), invalid function pointer to delegates
- function pointers, invalid
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
- invalid function pointers
ms.assetid: 99ae44f1-783e-49a9-9009-24f54bbd0f09
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ff026ddd9f9dc7c1556c55b285958dad7139e8eb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54699307"
---
# <a name="invalidfunctionpointerindelegate-mda"></a><span data-ttu-id="0f7e5-102">invalidFunctionPointerInDelegate MDA</span><span class="sxs-lookup"><span data-stu-id="0f7e5-102">invalidFunctionPointerInDelegate MDA</span></span>
<span data-ttu-id="0f7e5-103">當無效的函式指標傳入，以建構取代原生函式指標的委派時，就會啟用 `invalidFunctionPointerInDelegate` Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="0f7e5-103">The `invalidFunctionPointerInDelegate` managed debugging assistant (MDA) is activated when an invalid function pointer is passed in to construct a delegate over a native function pointer.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="0f7e5-104">徵兆</span><span class="sxs-lookup"><span data-stu-id="0f7e5-104">Symptoms</span></span>  
 <span data-ttu-id="0f7e5-105">使用委派來取代函式指標時，發生存取違規或非預期的記憶體損毀。</span><span class="sxs-lookup"><span data-stu-id="0f7e5-105">Access violations or unexpected memory corruption when using a delegate over a function pointer.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="0f7e5-106">原因</span><span class="sxs-lookup"><span data-stu-id="0f7e5-106">Cause</span></span>  
 <span data-ttu-id="0f7e5-107">所指定的函式指標無效。</span><span class="sxs-lookup"><span data-stu-id="0f7e5-107">An invalid function pointer was specified.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="0f7e5-108">解決方式</span><span class="sxs-lookup"><span data-stu-id="0f7e5-108">Resolution</span></span>  
 <span data-ttu-id="0f7e5-109">指定有效的函式指標</span><span class="sxs-lookup"><span data-stu-id="0f7e5-109">Specify a valid function pointer</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="0f7e5-110">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="0f7e5-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="0f7e5-111">此 MDA 對 CLR 沒有影響。</span><span class="sxs-lookup"><span data-stu-id="0f7e5-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="0f7e5-112">輸出</span><span class="sxs-lookup"><span data-stu-id="0f7e5-112">Output</span></span>  
 <span data-ttu-id="0f7e5-113">無效的函式指標。</span><span class="sxs-lookup"><span data-stu-id="0f7e5-113">The invalid function pointer.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="0f7e5-114">組態</span><span class="sxs-lookup"><span data-stu-id="0f7e5-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidFunctionPointerInDelegate />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0f7e5-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f7e5-115">See also</span></span>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="0f7e5-116">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="0f7e5-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="0f7e5-117">Interop 封送處理</span><span class="sxs-lookup"><span data-stu-id="0f7e5-117">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
