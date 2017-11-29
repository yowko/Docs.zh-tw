---
title: "啟用 JIT 附加偵錯"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 107b47ba8abcbd1084bed6e043f5a648aa91cc91
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="enabling-jit-attach-debugging"></a><span data-ttu-id="bdae5-102">啟用 JIT 附加偵錯</span><span class="sxs-lookup"><span data-stu-id="bdae5-102">Enabling JIT-Attach Debugging</span></span>
<span data-ttu-id="bdae5-103">JIT 附加偵錯是當您將偵錯工具附加至處理序發生錯誤時，所使用的描述語句，或者可為特定的方法或函式所觸發。</span><span class="sxs-lookup"><span data-stu-id="bdae5-103">JIT-attach debugging is the phrase used to describe attaching a debugger to a process when you encounter errors, or it can be triggered by specific methods or functions.</span></span>  
  
 <span data-ttu-id="bdae5-104">下列錯誤條件下會使用 JIT 附加偵錯：</span><span class="sxs-lookup"><span data-stu-id="bdae5-104">JIT-attach debugging is used under the following fault conditions:</span></span>  
  
-   <span data-ttu-id="bdae5-105">未處理的例外狀況 (在原生和 Managed 程式碼中)。</span><span class="sxs-lookup"><span data-stu-id="bdae5-105">Unhandled exceptions (in both native and managed code).</span></span>  
  
-   <span data-ttu-id="bdae5-106"><xref:System.Environment.FailFast%2A?displayProperty=nameWithType> 方法或 [RaiseFailFastException](http://go.microsoft.com/fwlink/?LinkId=182107) 函式 (Windows 7 系列)。</span><span class="sxs-lookup"><span data-stu-id="bdae5-106"><xref:System.Environment.FailFast%2A?displayProperty=nameWithType> method or [RaiseFailFastException](http://go.microsoft.com/fwlink/?LinkId=182107) function (Windows 7 family).</span></span>  
  
-   <span data-ttu-id="bdae5-107">執行階段嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="bdae5-107">Runtime fatal errors.</span></span>  
  
 <span data-ttu-id="bdae5-108">呼叫下列方法和函式也會觸發 JIT 附加偵錯：</span><span class="sxs-lookup"><span data-stu-id="bdae5-108">JIT-attach debugging is also triggered by calls to the following methods and functions:</span></span>  
  
-   <span data-ttu-id="bdae5-109"><xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="bdae5-109"><xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> method.</span></span>  
  
-   <span data-ttu-id="bdae5-110"><xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="bdae5-110"><xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> method.</span></span>  
  
-   <span data-ttu-id="bdae5-111">[DebugBreak](http://go.microsoft.com/fwlink/?LinkId=182106) 函式 (Win32)。</span><span class="sxs-lookup"><span data-stu-id="bdae5-111">[DebugBreak](http://go.microsoft.com/fwlink/?LinkId=182106) function (Win32).</span></span>  
  
 <span data-ttu-id="bdae5-112">在 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 之前，.NET Framework 會提供不同的登錄機碼控制原生和 Managed 偵錯工具的行為。</span><span class="sxs-lookup"><span data-stu-id="bdae5-112">Before the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], the .NET Framework provided separate registry keys to control the behavior of native and managed debuggers.</span></span> <span data-ttu-id="bdae5-113">從 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 開始，控制會彙總在單一登錄機碼下：HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug。</span><span class="sxs-lookup"><span data-stu-id="bdae5-113">Starting with the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], control is consolidated under a single registry key: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug.</span></span> <span data-ttu-id="bdae5-114">您可為該機碼設定的值，會決定是否叫用偵錯工具；而如果決定叫用，是否使用需要使用者互動的對話方塊叫用。</span><span class="sxs-lookup"><span data-stu-id="bdae5-114">The values you can set for that key determine whether a debugger is invoked, and, if so, whether it is invoked with a dialog box that requires user interaction.</span></span> <span data-ttu-id="bdae5-115">如需設定此登錄機碼的資訊，請參閱[設定自動偵錯](http://go.microsoft.com/fwlink/?LinkId=181767)。</span><span class="sxs-lookup"><span data-stu-id="bdae5-115">For information about setting this registry key, see [Configuring Automatic Debugging](http://go.microsoft.com/fwlink/?LinkId=181767).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdae5-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bdae5-116">See Also</span></span>  
 [<span data-ttu-id="bdae5-117">偵錯、追蹤和程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="bdae5-117">Debugging, Tracing, and Profiling</span></span>](../../../docs/framework/debug-trace-profile/index.md)  
 [<span data-ttu-id="bdae5-118">使映像偵錯更容易</span><span class="sxs-lookup"><span data-stu-id="bdae5-118">Making an Image Easier to Debug</span></span>](../../../docs/framework/debug-trace-profile/making-an-image-easier-to-debug.md)  
 [<span data-ttu-id="bdae5-119">啟用分析</span><span class="sxs-lookup"><span data-stu-id="bdae5-119">Enabling Profiling</span></span>](http://msdn.microsoft.com/en-us/3b669676-f0e0-4ebf-8674-68986dd2020d)
