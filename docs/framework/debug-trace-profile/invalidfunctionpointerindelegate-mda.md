---
title: invalidFunctionPointerInDelegate MDA
description: 請參閱 invalidFunctionPointerInDelegate managed 偵錯工具（MDA），如果傳入不正確函式指標以進行委派，則會叫用此功能。
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
ms.openlocfilehash: a17427d117c62ba782af3c9549c84623a3013b06
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051736"
---
# <a name="invalidfunctionpointerindelegate-mda"></a><span data-ttu-id="9b07b-103">invalidFunctionPointerInDelegate MDA</span><span class="sxs-lookup"><span data-stu-id="9b07b-103">invalidFunctionPointerInDelegate MDA</span></span>
<span data-ttu-id="9b07b-104">當無效的函式指標傳入，以建構取代原生函式指標的委派時，就會啟用 `invalidFunctionPointerInDelegate` Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="9b07b-104">The `invalidFunctionPointerInDelegate` managed debugging assistant (MDA) is activated when an invalid function pointer is passed in to construct a delegate over a native function pointer.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="9b07b-105">徵狀</span><span class="sxs-lookup"><span data-stu-id="9b07b-105">Symptoms</span></span>  
 <span data-ttu-id="9b07b-106">使用委派來取代函式指標時，發生存取違規或非預期的記憶體損毀。</span><span class="sxs-lookup"><span data-stu-id="9b07b-106">Access violations or unexpected memory corruption when using a delegate over a function pointer.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="9b07b-107">原因</span><span class="sxs-lookup"><span data-stu-id="9b07b-107">Cause</span></span>  
 <span data-ttu-id="9b07b-108">所指定的函式指標無效。</span><span class="sxs-lookup"><span data-stu-id="9b07b-108">An invalid function pointer was specified.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="9b07b-109">解決方案</span><span class="sxs-lookup"><span data-stu-id="9b07b-109">Resolution</span></span>  
 <span data-ttu-id="9b07b-110">指定有效的函式指標</span><span class="sxs-lookup"><span data-stu-id="9b07b-110">Specify a valid function pointer</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="9b07b-111">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="9b07b-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="9b07b-112">此 MDA 對 CLR 沒有影響。</span><span class="sxs-lookup"><span data-stu-id="9b07b-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="9b07b-113">輸出</span><span class="sxs-lookup"><span data-stu-id="9b07b-113">Output</span></span>  
 <span data-ttu-id="9b07b-114">無效的函式指標。</span><span class="sxs-lookup"><span data-stu-id="9b07b-114">The invalid function pointer.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="9b07b-115">組態</span><span class="sxs-lookup"><span data-stu-id="9b07b-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidFunctionPointerInDelegate />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9b07b-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b07b-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="9b07b-117">使用 Managed 偵錯助理診斷錯誤</span><span class="sxs-lookup"><span data-stu-id="9b07b-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="9b07b-118">Interop 封送處理</span><span class="sxs-lookup"><span data-stu-id="9b07b-118">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
