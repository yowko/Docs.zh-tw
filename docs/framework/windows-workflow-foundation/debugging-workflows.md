---
title: "偵錯工作流程"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b23b4814-ebb1-4c51-b7a9-469f4da7a96d
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 44814be3a21e9c0ca9ba2b09a5309661a939bbdd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-workflows"></a><span data-ttu-id="be40b-102">偵錯工作流程</span><span class="sxs-lookup"><span data-stu-id="be40b-102">Debugging Workflows</span></span>
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]<span data-ttu-id="be40b-103">提供一些從開發環境進行偵錯工作流程的選項。</span><span class="sxs-lookup"><span data-stu-id="be40b-103"> offers several options for debugging running workflows from the development environment.</span></span> <span data-ttu-id="be40b-104">可在設計工具、XAML 與程式碼中將工作流程偵錯。</span><span class="sxs-lookup"><span data-stu-id="be40b-104">Workflows can be debugged in the designer, in XAML, and in code.</span></span>  
  
## <a name="debugging-in-the-workflow-designer"></a><span data-ttu-id="be40b-105">在工作流程設計工具中偵錯</span><span class="sxs-lookup"><span data-stu-id="be40b-105">Debugging in the Workflow Designer</span></span>  
 <span data-ttu-id="be40b-106">可以在工作流程設計工具中的活動上設定中斷點，反白活動並按下**F9**或使用活動的內容功能表。</span><span class="sxs-lookup"><span data-stu-id="be40b-106">Breakpoints can be set on activities in the workflow designer by either highlighting the activity and pressing **F9** or by using the activity’s context menu.</span></span> <span data-ttu-id="be40b-107">執行工作流程，然後當工作流程主機正在偵錯模式中執行時中斷。</span><span class="sxs-lookup"><span data-stu-id="be40b-107">Execution of the workflow then breaks when the workflow host is run in debug mode.</span></span> <span data-ttu-id="be40b-108">在下列螢幕擷取畫面中，工作流程的執行已暫停於一個中斷點。</span><span class="sxs-lookup"><span data-stu-id="be40b-108">In the following screenshot, workflow execution is paused at a breakpoint.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="be40b-109">[偵錯工作流程與工作流程設計工具](/visualstudio/workflow-designer/debugging-workflows-with-the-workflow-designer)。</span><span class="sxs-lookup"><span data-stu-id="be40b-109"> [Debugging Workflows with the Workflow Designer](/visualstudio/workflow-designer/debugging-workflows-with-the-workflow-designer).</span></span>  
  
## <a name="debugging-in-xaml"></a><span data-ttu-id="be40b-110">在 XAML 中偵錯</span><span class="sxs-lookup"><span data-stu-id="be40b-110">Debugging in XAML</span></span>  
 <span data-ttu-id="be40b-111">如果工作流程在設計工具中的中斷點上暫停，即可在 XAML 中偵錯工作流程。</span><span class="sxs-lookup"><span data-stu-id="be40b-111">If a workflow has paused at a breakpoint in the designer, the workflow can also be debugged in XAML.</span></span> <span data-ttu-id="be40b-112">若要檢視執行點在 XAML 中，選取**XAML 檢視**暫停工作流程執行時，工作流程設計工具中。</span><span class="sxs-lookup"><span data-stu-id="be40b-112">To view the point of execution in XAML, select **XAML View** in the workflow designer when workflow execution is paused.</span></span> <span data-ttu-id="be40b-113">從解決方案總管的設計工具中重新開啟工作流程，即可將偵錯切換回設計工具。</span><span class="sxs-lookup"><span data-stu-id="be40b-113">Debugging can be switched back to the designer by re-opening the workflow in the designer from the solution explorer.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="be40b-114">[How to： 使用工作流程設計工具偵測 XAML](/visualstudio/workflow-designer/how-to-debug-xaml-with-the-workflow-designer)。</span><span class="sxs-lookup"><span data-stu-id="be40b-114"> [How to: Debug XAML with the Workflow Designer](/visualstudio/workflow-designer/how-to-debug-xaml-with-the-workflow-designer).</span></span>  
  
## <a name="debugging-in-code"></a><span data-ttu-id="be40b-115">在程式碼中偵錯</span><span class="sxs-lookup"><span data-stu-id="be40b-115">Debugging in Code</span></span>  
 <span data-ttu-id="be40b-116">在 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 中使用程式碼中斷點的方式與用於其他命令式應用程式相同。</span><span class="sxs-lookup"><span data-stu-id="be40b-116">Code breakpoints can be used in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] in the same way that they can be used in other imperative applications.</span></span> <span data-ttu-id="be40b-117">按一下左邊的界的程式碼 窗格建立程式碼中斷點，或按**F9**將中斷點放置的游標位置。</span><span class="sxs-lookup"><span data-stu-id="be40b-117">Click the left margin of the code pane to create a code breakpoint, or press **F9** to place a breakpoint at the cursor location.</span></span>  
  
## <a name="attaching-to-a-workflow-process"></a><span data-ttu-id="be40b-118">附加至工作流程處理序</span><span class="sxs-lookup"><span data-stu-id="be40b-118">Attaching to a Workflow Process</span></span>  
 <span data-ttu-id="be40b-119">工作流程偵錯也支援使用 Visual Studio 的基礎結構來附加至處理序。</span><span class="sxs-lookup"><span data-stu-id="be40b-119">Workflow debugging also supports using Visual Studio’s infrastructure to attach to a process.</span></span> <span data-ttu-id="be40b-120">這可讓工作流程的作者在不同的主機環境中 (例如 Internet Information Services (IIS) 7.0) 執行時偵錯工作流程。</span><span class="sxs-lookup"><span data-stu-id="be40b-120">This enables the workflow author to debug a workflow running in a different host environment such as Internet Information Services (IIS) 7.0.</span></span>  
  
## <a name="remote-debugging"></a><span data-ttu-id="be40b-121">遠端偵錯</span><span class="sxs-lookup"><span data-stu-id="be40b-121">Remote Debugging</span></span>  
 [!INCLUDE[wf](../../../includes/wf-md.md)]<span data-ttu-id="be40b-122"> 遠端偵錯的運作方式與其他 [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] 元件的遠端偵錯功能相同。</span><span class="sxs-lookup"><span data-stu-id="be40b-122"> remote debugging functions the same as remote debugging for other [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] components.</span></span> <span data-ttu-id="be40b-123">如需使用遠端偵錯資訊，請參閱[How to： 啟用遠端偵錯](http://go.microsoft.com/fwlink/?LinkId=196257)。</span><span class="sxs-lookup"><span data-stu-id="be40b-123">For information on using remote debugging, see [How to: Enable Remote Debugging](http://go.microsoft.com/fwlink/?LinkId=196257).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="be40b-124">如果工作流程應用程式以 x86 為目標架構，而執行 64 位元作業系統的電腦上裝載，則遠端偵錯將不會運作，除非[!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)]變更工作流程應用程式，會安裝在遠端電腦或目標若要**任何 CPU**。</span><span class="sxs-lookup"><span data-stu-id="be40b-124">If the workflow application targets the x86 architecture and is hosted on a computer running a 64 bit operating system, then remote debugging will not work unless [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] is installed on the remote computer or the target for the workflow application is changed to **Any CPU**.</span></span>  
  
## <a name="extending-the-workflow-debugging-service"></a><span data-ttu-id="be40b-125">擴充工作流程偵錯服務</span><span class="sxs-lookup"><span data-stu-id="be40b-125">Extending the Workflow Debugging Service</span></span>  
 <span data-ttu-id="be40b-126">現在已公開工作流程偵錯程式服務，且可用於建立自訂應用程式，例如在重新裝載的設計工具中監控、模擬和偵錯。</span><span class="sxs-lookup"><span data-stu-id="be40b-126">The workflow debugger service is now public and can be used to create custom applications such as monitoring, simulation, and debugging in a re-hosted designer.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="be40b-127"> <xref:System.Activities.Presentation.Debug.DebuggerService> 主題。</span><span class="sxs-lookup"><span data-stu-id="be40b-127"> the <xref:System.Activities.Presentation.Debug.DebuggerService> topic.</span></span>
