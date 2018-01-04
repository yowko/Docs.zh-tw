---
title: "使用者入門課程 2"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WF [WF], getting started
- Windows Workflow Foundation [WF], getting started
ms.assetid: c2d3585f-6b1a-4d4f-9865-bd7cd31c5d42
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f25058071e041ac1e14de2c223750013c8ef1d30
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-tutorial"></a><span data-ttu-id="ca918-102">快速入門教學課程</span><span class="sxs-lookup"><span data-stu-id="ca918-102">Getting Started Tutorial</span></span>
<span data-ttu-id="ca918-103">本節包含逐步解說主題集，可引導您進行 [!INCLUDE[wf](../../../includes/wf-md.md)] 應用程式的程式設計。</span><span class="sxs-lookup"><span data-stu-id="ca918-103">This section contains a set of walkthrough topics that introduce you to programming [!INCLUDE[wf](../../../includes/wf-md.md)] applications.</span></span> <span data-ttu-id="ca918-104">您可以遵循這些主題的程序進行，建置一個數字猜測遊戲應用程式。</span><span class="sxs-lookup"><span data-stu-id="ca918-104">By following the procedures in these topics, you will build an application that is a number guessing game.</span></span> <span data-ttu-id="ca918-105">教學課程中的第一個主題會引導您透過步驟來建立工作流程所需的自訂活動。</span><span class="sxs-lookup"><span data-stu-id="ca918-105">The first topic in the tutorial leads you through the steps to create the custom activities required for the workflow.</span></span> <span data-ttu-id="ca918-106">在第二個主題中，這些活動會隨著內建工作流程活動組裝至流程圖工作流程。</span><span class="sxs-lookup"><span data-stu-id="ca918-106">In the second topic, these activities are assembled along with built-in workflow activities into a flowchart workflow.</span></span> <span data-ttu-id="ca918-107">在第三個主題中，會設定主應用程式執行工作流程，並在最後一個主題中介紹持續性。</span><span class="sxs-lookup"><span data-stu-id="ca918-107">In the third topic, the host application is configured to run the workflow, and in the final topic persistence is introduced.</span></span> <span data-ttu-id="ca918-108">這個程序中的每一個步驟都與之前的步驟息息相關，因此建議您最好依照順序完成。</span><span class="sxs-lookup"><span data-stu-id="ca918-108">Each step in this process depends on the previous steps, so we recommend that you complete them in order.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ca918-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="ca918-109">In This Section</span></span>  
 [<span data-ttu-id="ca918-110">如何：建立活動</span><span class="sxs-lookup"><span data-stu-id="ca918-110">How to: Create an Activity</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)  
 <span data-ttu-id="ca918-111">描述如何建立衍生自 <xref:System.Activities.NativeActivity%601> 的自訂活動，以及如何使用活動設計工具，將這個活動連同內建活動撰寫成複合活動。</span><span class="sxs-lookup"><span data-stu-id="ca918-111">Describes how to create a custom activity that derives from <xref:System.Activities.NativeActivity%601>, and how to compose this activity along with a built-in activity into a composite activity using the activity designer.</span></span>  
  
 [<span data-ttu-id="ca918-112">如何：建立工作流程</span><span class="sxs-lookup"><span data-stu-id="ca918-112">How to: Create a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md)  
 <span data-ttu-id="ca918-113">說明如何利用內建活動和前述教學課程的自訂活動，來建立流程圖、循序和狀態機器工作流程。</span><span class="sxs-lookup"><span data-stu-id="ca918-113">Describes how to create flowchart, sequential, and state machine workflows by using built-in activities and the custom activities from the preceding tutorial.</span></span>  
  
 [<span data-ttu-id="ca918-114">如何：執行工作流程</span><span class="sxs-lookup"><span data-stu-id="ca918-114">How to: Run a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)  
 <span data-ttu-id="ca918-115">描述如何從主機環境中叫用工作流程，在工作流程中來回傳遞資料，以及如何恢復書籤。</span><span class="sxs-lookup"><span data-stu-id="ca918-115">Describes how to invoke a workflow from a host environment, pass data into and out of a workflow, and how to resume bookmarks.</span></span>  
  
 [<span data-ttu-id="ca918-116">如何：建立及執行長時間執行的工作流程</span><span class="sxs-lookup"><span data-stu-id="ca918-116">How to: Create and Run a Long Running Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md)  
 <span data-ttu-id="ca918-117">說明如何將持續性加入工作流程應用程式。</span><span class="sxs-lookup"><span data-stu-id="ca918-117">Describes how to add persistence to a workflow application.</span></span>  
  
 [<span data-ttu-id="ca918-118">如何：建立自訂追蹤參與者</span><span class="sxs-lookup"><span data-stu-id="ca918-118">How to: Create a Custom Tracking Participant</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md)  
 <span data-ttu-id="ca918-119">說明如何建立自訂的追蹤參與者和追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="ca918-119">Describes how to create a custom tracking participant and tracking profile.</span></span>  
  
 [<span data-ttu-id="ca918-120">如何：並存裝載工作流程的多個版本</span><span class="sxs-lookup"><span data-stu-id="ca918-120">How to: Host Multiple Versions of a Workflow Side-by-Side</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md)  
 <span data-ttu-id="ca918-121">描述如何使用 `WorkflowIdentity` 裝載工作流程並存的多個版本。</span><span class="sxs-lookup"><span data-stu-id="ca918-121">Describes how to use `WorkflowIdentity` to host multiple versions of a workflow side-by-side.</span></span>  
  
 [<span data-ttu-id="ca918-122">如何：更新執行中工作流程執行個體的定義</span><span class="sxs-lookup"><span data-stu-id="ca918-122">How to: Update the Definition of a Running Workflow Instance</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md)  
 <span data-ttu-id="ca918-123">說明如何使用動態更新來修改執行中的工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="ca918-123">Describes how to use dynamic update to modify running workflow instances.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca918-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="ca918-124">See Also</span></span>  
 [<span data-ttu-id="ca918-125">Windows Workflow Foundation 程式設計</span><span class="sxs-lookup"><span data-stu-id="ca918-125">Windows Workflow Foundation Programming</span></span>](../../../docs/framework/windows-workflow-foundation/programming.md)
