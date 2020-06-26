---
title: 啟用 JIT 附加偵錯
description: 當您遇到錯誤時，請啟用即時（JIT）附加偵錯工具，以將偵錯工具附加至進程。 它可以由特定方法或函式觸發。
ms.date: 03/30/2017
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
ms.openlocfilehash: d1190c51a9cc6b5322ec832e0d35bc01dc855b12
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416040"
---
# <a name="enabling-jit-attach-debugging"></a><span data-ttu-id="ba4d3-104">啟用 JIT 附加偵錯</span><span class="sxs-lookup"><span data-stu-id="ba4d3-104">Enabling JIT-Attach Debugging</span></span>
<span data-ttu-id="ba4d3-105">JIT 附加偵錯是當您將偵錯工具附加至處理序發生錯誤時，所使用的描述語句，或者可為特定的方法或函式所觸發。</span><span class="sxs-lookup"><span data-stu-id="ba4d3-105">JIT-attach debugging is the phrase used to describe attaching a debugger to a process when you encounter errors, or it can be triggered by specific methods or functions.</span></span>  
  
 <span data-ttu-id="ba4d3-106">下列錯誤條件下會使用 JIT 附加偵錯：</span><span class="sxs-lookup"><span data-stu-id="ba4d3-106">JIT-attach debugging is used under the following fault conditions:</span></span>  
  
- <span data-ttu-id="ba4d3-107">未處理的例外狀況 (在原生和 Managed 程式碼中)。</span><span class="sxs-lookup"><span data-stu-id="ba4d3-107">Unhandled exceptions (in both native and managed code).</span></span>  
  
- <span data-ttu-id="ba4d3-108"><xref:System.Environment.FailFast%2A?displayProperty=nameWithType> 方法或 [RaiseFailFastException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raisefailfastexception) 函式 (Windows 7 系列)。</span><span class="sxs-lookup"><span data-stu-id="ba4d3-108"><xref:System.Environment.FailFast%2A?displayProperty=nameWithType> method or [RaiseFailFastException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raisefailfastexception) function (Windows 7 family).</span></span>  
  
- <span data-ttu-id="ba4d3-109">執行階段嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="ba4d3-109">Runtime fatal errors.</span></span>  
  
 <span data-ttu-id="ba4d3-110">呼叫下列方法和函式也會觸發 JIT 附加偵錯：</span><span class="sxs-lookup"><span data-stu-id="ba4d3-110">JIT-attach debugging is also triggered by calls to the following methods and functions:</span></span>  
  
- <span data-ttu-id="ba4d3-111"><xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="ba4d3-111"><xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> method.</span></span>  
  
- <span data-ttu-id="ba4d3-112"><xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="ba4d3-112"><xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> method.</span></span>  
  
- <span data-ttu-id="ba4d3-113">[DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) 函式 (Win32)。</span><span class="sxs-lookup"><span data-stu-id="ba4d3-113">[DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) function (Win32).</span></span>  
  
 <span data-ttu-id="ba4d3-114">在 .NET Framework 4 之前，.NET Framework 提供個別的登錄機碼來控制原生和 managed 偵錯工具的行為。</span><span class="sxs-lookup"><span data-stu-id="ba4d3-114">Before the .NET Framework 4, the .NET Framework provided separate registry keys to control the behavior of native and managed debuggers.</span></span> <span data-ttu-id="ba4d3-115">從 .NET Framework 4 開始，控制權會合並在單一登入機碼底下： HKEY_LOCAL_MACHINE \Software\microsoft\windows server\ NT\Current Version\AeDebug。</span><span class="sxs-lookup"><span data-stu-id="ba4d3-115">Starting with the .NET Framework 4, control is consolidated under a single registry key: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug.</span></span> <span data-ttu-id="ba4d3-116">您可為該機碼設定的值，會決定是否叫用偵錯工具；而如果決定叫用，是否使用需要使用者互動的對話方塊叫用。</span><span class="sxs-lookup"><span data-stu-id="ba4d3-116">The values you can set for that key determine whether a debugger is invoked, and, if so, whether it is invoked with a dialog box that requires user interaction.</span></span> <span data-ttu-id="ba4d3-117">如需設定此登錄機碼的相關資訊，請參閱設定[自動的調試](/windows/win32/debug/configuring-automatic-debugging)程式。</span><span class="sxs-lookup"><span data-stu-id="ba4d3-117">For information about setting this registry key, see [Configuring Automatic Debugging](/windows/win32/debug/configuring-automatic-debugging).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba4d3-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ba4d3-118">See also</span></span>

- [<span data-ttu-id="ba4d3-119">偵錯工具、追蹤和程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="ba4d3-119">Debugging, Tracing, and Profiling</span></span>](index.md)
- [<span data-ttu-id="ba4d3-120">使映像偵錯更容易</span><span class="sxs-lookup"><span data-stu-id="ba4d3-120">Making an Image Easier to Debug</span></span>](making-an-image-easier-to-debug.md)
