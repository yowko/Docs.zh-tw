---
title: 偵錯、追蹤和程式碼剖析
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [.NET Framework]
- .NET Framework application configuration, debugging
- debugging [.NET Framework], .NET Framework application debugging
- troubleshooting applications [.NET Framework], profiling
- application development [.NET Framework], debugging
- .NET Framework application configuration, profiling
- profiling applications
- troubleshooting applications [.NET Framework], debugging
- troubleshooting applications [.NET Framework]
- application development [.NET Framework], profiling
ms.assetid: 4a04863e-2475-46f4-bc3f-3c11510c2a4b
caps.latest.revision: 28
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4368ce1256e1e0637907768b3698ca7dab97c5f9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-tracing-and-profiling"></a><span data-ttu-id="0664d-102">偵錯、追蹤和程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="0664d-102">Debugging, Tracing, and Profiling</span></span>
<span data-ttu-id="0664d-103">若要偵錯 .NET Framework 應用程式，必須設定編譯器和執行階段環境，讓偵錯工具能夠附加至應用程式，並針對應用程式及其相對應的 Microsoft 中繼語言 (MSIL) 產生符號和字行對應 (可能的話)。</span><span class="sxs-lookup"><span data-stu-id="0664d-103">To debug a .NET Framework application, the compiler and runtime environment must be configured to enable a debugger to attach to the application and to produce both symbols and line maps, if possible, for the application and its corresponding Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="0664d-104">在偵錯 Managed 應用程式後，可將其剖析以提高效能。</span><span class="sxs-lookup"><span data-stu-id="0664d-104">After a managed application has been debugged, it can be profiled to boost performance.</span></span> <span data-ttu-id="0664d-105">程式碼剖析會評估和描述產生最常執行之程式碼的原始程式碼字行，以及花費多少時間執行。</span><span class="sxs-lookup"><span data-stu-id="0664d-105">Profiling evaluates and describes the lines of source code that generate the most frequently executed code, and how much time it takes to execute them.</span></span>  
  
 <span data-ttu-id="0664d-106">使用 Visual Studio 可輕易偵錯 .NET Framework 應用程式，它會處理許多組態詳細資料。</span><span class="sxs-lookup"><span data-stu-id="0664d-106">.NET Framework applications are easily debugged by using Visual Studio, which handles many of the configuration details.</span></span> <span data-ttu-id="0664d-107">如果未安裝 Visual Studio，您可以使用 .NET Framework <xref:System.Diagnostics> 命名空間中的偵錯類別，來檢查並改善 .NET Framework 應用程式的效能。</span><span class="sxs-lookup"><span data-stu-id="0664d-107">If Visual Studio is not installed, you can examine and improve the performance of .NET Framework applications by using the debugging classes in the .NET Framework <xref:System.Diagnostics> namespace.</span></span> <span data-ttu-id="0664d-108">此命名空間包含用來追蹤執行流程的 <xref:System.Diagnostics.Trace><xref:System.Diagnostics.Debug> 和 <xref:System.Diagnostics.TraceSource> 類別，以及用來剖析程式碼的 <xref:System.Diagnostics.Process>、<xref:System.Diagnostics.EventLog> 和 <xref:System.Diagnostics.PerformanceCounter> 類別。</span><span class="sxs-lookup"><span data-stu-id="0664d-108">This namespace includes the <xref:System.Diagnostics.Trace>, <xref:System.Diagnostics.Debug>, and <xref:System.Diagnostics.TraceSource> classes for tracing execution flow, and the <xref:System.Diagnostics.Process>, <xref:System.Diagnostics.EventLog>, and <xref:System.Diagnostics.PerformanceCounter> classes for profiling code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0664d-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="0664d-109">In This Section</span></span>  
 [<span data-ttu-id="0664d-110">啟用 JIT 附加偵錯</span><span class="sxs-lookup"><span data-stu-id="0664d-110">Enabling JIT-Attach Debugging</span></span>](../../../docs/framework/debug-trace-profile/enabling-jit-attach-debugging.md)  
 <span data-ttu-id="0664d-111">示範如何設定登錄，以將偵錯引擎 JIT 附加至 .NET Framework 應用程式。</span><span class="sxs-lookup"><span data-stu-id="0664d-111">Shows how to configure the registry to JIT-attach a debug engine to a .NET Framework application.</span></span>  
  
 [<span data-ttu-id="0664d-112">使映像偵錯更容易</span><span class="sxs-lookup"><span data-stu-id="0664d-112">Making an Image Easier to Debug</span></span>](../../../docs/framework/debug-trace-profile/making-an-image-easier-to-debug.md)  
 <span data-ttu-id="0664d-113">示範如何開啟 JIT 追蹤並關閉最佳化，使組件偵錯更容易。</span><span class="sxs-lookup"><span data-stu-id="0664d-113">Shows how to turn JIT tracking on and optimization off to make an assembly easier to debug.</span></span>  
  
 [<span data-ttu-id="0664d-114">追蹤和檢測應用程式</span><span class="sxs-lookup"><span data-stu-id="0664d-114">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 <span data-ttu-id="0664d-115">描述當應用程式執行時，如何監視其執行狀況，以及如何加以檢測，以顯示其執行效能如何，或是否有哪裡發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="0664d-115">Describes how to monitor the execution of your application while it is running, and how to instrument it to display how well it is performing or whether something has gone wrong.</span></span>  
  
 [<span data-ttu-id="0664d-116">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="0664d-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 <span data-ttu-id="0664d-117">描述 Managed 偵錯助理 (MDA)，其為偵錯輔助程式，可與 Common Language Runtime (CLR) 合作提供執行階段狀態的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="0664d-117">Describes managed debugging assistants (MDAs), which are debugging aids that work in conjunction with the common language runtime (CLR) to provide information on runtime state.</span></span>  
  
 [<span data-ttu-id="0664d-118">使用偵錯工具顯示屬性增強偵錯功能</span><span class="sxs-lookup"><span data-stu-id="0664d-118">Enhancing Debugging with the Debugger Display Attributes</span></span>](../../../docs/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes.md)  
 <span data-ttu-id="0664d-119">描述類型的開發人員要如何指定當類型顯示在偵錯工具中時，看起來是什麼樣子。</span><span class="sxs-lookup"><span data-stu-id="0664d-119">Describes how the developer of a type can specify what that type will look like when it is displayed in a debugger.</span></span>  
  
 [<span data-ttu-id="0664d-120">效能計數器</span><span class="sxs-lookup"><span data-stu-id="0664d-120">Performance Counters</span></span>](../../../docs/framework/debug-trace-profile/performance-counters.md)  
 <span data-ttu-id="0664d-121">描述您可以用來追蹤應用程式效能的計數器。</span><span class="sxs-lookup"><span data-stu-id="0664d-121">Describes the counters that you can use to track the performance of an application.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0664d-122">相關章節</span><span class="sxs-lookup"><span data-stu-id="0664d-122">Related Sections</span></span>  
 [<span data-ttu-id="0664d-123">偵錯 ASP.NET 和 AJAX 應用程式</span><span class="sxs-lookup"><span data-stu-id="0664d-123">Debugging ASP.NET and AJAX Applications</span></span>](http://msdn.microsoft.com/library/9d531913-541b-47b8-864d-138021fca0c6)  
 <span data-ttu-id="0664d-124">提供如何在開發期間或部署之後偵錯 ASP.NET 應用程式的先決條件與指示。</span><span class="sxs-lookup"><span data-stu-id="0664d-124">Provides prerequisites and instructions for how to debug an ASP.NET application during development or after deployment.</span></span>  
  
 [<span data-ttu-id="0664d-125">開發指南</span><span class="sxs-lookup"><span data-stu-id="0664d-125">Development Guide</span></span>](../../../docs/framework/development-guide.md)  
 <span data-ttu-id="0664d-126">提供應用程式開發所有主要技術領域和工作的指引，包括建立、設定、偵錯、保護及部署您的應用程式，以及有關動態程式設計、互通性、擴充性、記憶體管理和執行緒的資訊。</span><span class="sxs-lookup"><span data-stu-id="0664d-126">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>
