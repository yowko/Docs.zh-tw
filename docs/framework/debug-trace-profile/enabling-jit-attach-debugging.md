---
title: 啟用 JIT 附加偵錯
ms.date: 03/30/2017
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7af34cf4bd3a2367eaf320990dbbc24f4e7a8bbf
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64660142"
---
# <a name="enabling-jit-attach-debugging"></a><span data-ttu-id="bafd7-102">啟用 JIT 附加偵錯</span><span class="sxs-lookup"><span data-stu-id="bafd7-102">Enabling JIT-Attach Debugging</span></span>
<span data-ttu-id="bafd7-103">JIT 附加偵錯是當您將偵錯工具附加至處理序發生錯誤時，所使用的描述語句，或者可為特定的方法或函式所觸發。</span><span class="sxs-lookup"><span data-stu-id="bafd7-103">JIT-attach debugging is the phrase used to describe attaching a debugger to a process when you encounter errors, or it can be triggered by specific methods or functions.</span></span>  
  
 <span data-ttu-id="bafd7-104">下列錯誤條件下會使用 JIT 附加偵錯：</span><span class="sxs-lookup"><span data-stu-id="bafd7-104">JIT-attach debugging is used under the following fault conditions:</span></span>  
  
- <span data-ttu-id="bafd7-105">未處理的例外狀況 (在原生和 Managed 程式碼中)。</span><span class="sxs-lookup"><span data-stu-id="bafd7-105">Unhandled exceptions (in both native and managed code).</span></span>  
  
- <span data-ttu-id="bafd7-106"><xref:System.Environment.FailFast%2A?displayProperty=nameWithType> 方法或 [RaiseFailFastException](https://go.microsoft.com/fwlink/?LinkId=182107) 函式 (Windows 7 系列)。</span><span class="sxs-lookup"><span data-stu-id="bafd7-106"><xref:System.Environment.FailFast%2A?displayProperty=nameWithType> method or [RaiseFailFastException](https://go.microsoft.com/fwlink/?LinkId=182107) function (Windows 7 family).</span></span>  
  
- <span data-ttu-id="bafd7-107">執行階段嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="bafd7-107">Runtime fatal errors.</span></span>  
  
 <span data-ttu-id="bafd7-108">呼叫下列方法和函式也會觸發 JIT 附加偵錯：</span><span class="sxs-lookup"><span data-stu-id="bafd7-108">JIT-attach debugging is also triggered by calls to the following methods and functions:</span></span>  
  
- <span data-ttu-id="bafd7-109"><xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="bafd7-109"><xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> method.</span></span>  
  
- <span data-ttu-id="bafd7-110"><xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="bafd7-110"><xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> method.</span></span>  
  
- <span data-ttu-id="bafd7-111">[DebugBreak](https://go.microsoft.com/fwlink/?LinkId=182106) 函式 (Win32)。</span><span class="sxs-lookup"><span data-stu-id="bafd7-111">[DebugBreak](https://go.microsoft.com/fwlink/?LinkId=182106) function (Win32).</span></span>  
  
 <span data-ttu-id="bafd7-112">在 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 之前，.NET Framework 會提供不同的登錄機碼控制原生和 Managed 偵錯工具的行為。</span><span class="sxs-lookup"><span data-stu-id="bafd7-112">Before the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], the .NET Framework provided separate registry keys to control the behavior of native and managed debuggers.</span></span> <span data-ttu-id="bafd7-113">從開始[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]，控制會彙總在單一登錄機碼下：HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug。</span><span class="sxs-lookup"><span data-stu-id="bafd7-113">Starting with the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], control is consolidated under a single registry key: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug.</span></span> <span data-ttu-id="bafd7-114">您可為該機碼設定的值，會決定是否叫用偵錯工具；而如果決定叫用，是否使用需要使用者互動的對話方塊叫用。</span><span class="sxs-lookup"><span data-stu-id="bafd7-114">The values you can set for that key determine whether a debugger is invoked, and, if so, whether it is invoked with a dialog box that requires user interaction.</span></span> <span data-ttu-id="bafd7-115">如需設定此登錄機碼的資訊，請參閱[設定自動偵錯](https://go.microsoft.com/fwlink/?LinkId=181767)。</span><span class="sxs-lookup"><span data-stu-id="bafd7-115">For information about setting this registry key, see [Configuring Automatic Debugging](https://go.microsoft.com/fwlink/?LinkId=181767).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bafd7-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bafd7-116">See also</span></span>

- [<span data-ttu-id="bafd7-117">偵錯、追蹤和程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="bafd7-117">Debugging, Tracing, and Profiling</span></span>](../../../docs/framework/debug-trace-profile/index.md)
- [<span data-ttu-id="bafd7-118">使映像偵錯更容易</span><span class="sxs-lookup"><span data-stu-id="bafd7-118">Making an Image Easier to Debug</span></span>](../../../docs/framework/debug-trace-profile/making-an-image-easier-to-debug.md)
