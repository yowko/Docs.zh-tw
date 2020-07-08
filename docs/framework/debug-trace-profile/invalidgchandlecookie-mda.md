---
title: invalidGCHandleCookie MDA
description: 檢查 invalidGCHandleCookie managed 偵錯工具（MDA），這是在嘗試從不正確 IntPtr cookie 轉換到 GCHandle 時啟動的。
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid cookies
- cookies, invalid
- managed debugging assistants (MDAs), invalid cookies
- InvalidGCHandleCookie MDA
- invalid cookies
ms.assetid: 613ad742-3c11-401d-a6b3-893ceb8de4f8
ms.openlocfilehash: 1063b7be902d3063717b6639564d819ef3292c0e
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051294"
---
# <a name="invalidgchandlecookie-mda"></a><span data-ttu-id="01734-103">invalidGCHandleCookie MDA</span><span class="sxs-lookup"><span data-stu-id="01734-103">invalidGCHandleCookie MDA</span></span>
<span data-ttu-id="01734-104">當嘗試從無效的 <xref:System.IntPtr> Cookie 轉換成 <xref:System.Runtime.InteropServices.GCHandle> 時，就會啟動 `invalidGCHandleCookie` Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="01734-104">The `invalidGCHandleCookie` managed debugging assistant (MDA) is activated when a conversion from an invalid <xref:System.IntPtr> cookie to a <xref:System.Runtime.InteropServices.GCHandle> is attempted.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="01734-105">徵狀</span><span class="sxs-lookup"><span data-stu-id="01734-105">Symptoms</span></span>  
 <span data-ttu-id="01734-106">未定義的行為，例如嘗試使用或擷取 <xref:System.IntPtr> 的 <xref:System.Runtime.InteropServices.GCHandle> 時的存取違規與記憶體損毀。</span><span class="sxs-lookup"><span data-stu-id="01734-106">Undefined behavior such as access violations and memory corruption while attempting to use or retrieve a <xref:System.Runtime.InteropServices.GCHandle> from an <xref:System.IntPtr>.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="01734-107">原因</span><span class="sxs-lookup"><span data-stu-id="01734-107">Cause</span></span>  
 <span data-ttu-id="01734-108">Cookie 可能無效，因為它原本不是從代表已經釋放之 <xref:System.Runtime.InteropServices.GCHandle> 的 <xref:System.Runtime.InteropServices.GCHandle> 中建立的，它是不同應用程式網域中之 <xref:System.Runtime.InteropServices.GCHandle> 的 Cookie，或曾封送處理到原生程式碼當成 <xref:System.Runtime.InteropServices.GCHandle>，但傳遞回 CLR 當成在其中嘗試轉型的 <xref:System.IntPtr>，。</span><span class="sxs-lookup"><span data-stu-id="01734-108">The cookie is probably invalid because it was not originally created from a <xref:System.Runtime.InteropServices.GCHandle>, represents a <xref:System.Runtime.InteropServices.GCHandle> that has already been freed, is a cookie to a <xref:System.Runtime.InteropServices.GCHandle> in a different application domain, or was marshaled to native code as a <xref:System.Runtime.InteropServices.GCHandle> but passed back into the CLR as an <xref:System.IntPtr>, where a cast was attempted.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="01734-109">解決方案</span><span class="sxs-lookup"><span data-stu-id="01734-109">Resolution</span></span>  
 <span data-ttu-id="01734-110">為 <xref:System.Runtime.InteropServices.GCHandle> 指定有效的 <xref:System.IntPtr> Cookie。</span><span class="sxs-lookup"><span data-stu-id="01734-110">Specify a valid <xref:System.IntPtr> cookie for the <xref:System.Runtime.InteropServices.GCHandle>.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="01734-111">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="01734-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="01734-112">啟用此 MDA 時，偵錯工具即不再能夠追蹤回其物件的根，因為傳回的 Cookie 值和未啟用 MDA 時傳回的 Cookie 值不同。</span><span class="sxs-lookup"><span data-stu-id="01734-112">When this MDA is enabled, the debugger is no longer able to trace the roots back to their objects because the cookie values passed back are different from the ones returned when the MDA is not enabled.</span></span>  
  
## <a name="output"></a><span data-ttu-id="01734-113">輸出</span><span class="sxs-lookup"><span data-stu-id="01734-113">Output</span></span>  
 <span data-ttu-id="01734-114">已報告無效的 <xref:System.IntPtr> Cookie 值。</span><span class="sxs-lookup"><span data-stu-id="01734-114">The invalid <xref:System.IntPtr> cookie value is reported.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="01734-115">組態</span><span class="sxs-lookup"><span data-stu-id="01734-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidGCHandleCookie />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="01734-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01734-116">See also</span></span>

- <xref:System.Runtime.InteropServices.GCHandle.FromIntPtr%2A>
- <xref:System.Runtime.InteropServices.GCHandle>
- [<span data-ttu-id="01734-117">使用 Managed 偵錯助理診斷錯誤</span><span class="sxs-lookup"><span data-stu-id="01734-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
