---
title: 'How to: Create a Workflow'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 87234108-8e21-4cb3-9340-4a1a13f3f98c
caps.latest.revision: "34"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8e619fa7fa6437b60b1d3cd6b50a2a68229899f5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-workflow"></a><span data-ttu-id="e88d3-102">How to: Create a Workflow</span><span class="sxs-lookup"><span data-stu-id="e88d3-102">How to: Create a Workflow</span></span>
<span data-ttu-id="e88d3-103">工作流程可以從內建活動建構，也可以從自訂活動建構。</span><span class="sxs-lookup"><span data-stu-id="e88d3-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="e88d3-104">此區段步驟，完成建立這類使用這兩個內建活動的工作流程中的主題<xref:System.Activities.Statements.Flowchart>活動，並從先前的自訂活動[How to： 建立活動](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)主題。</span><span class="sxs-lookup"><span data-stu-id="e88d3-104">This topics in this section step through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Flowchart> activity, and the custom activities from the previous [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="e88d3-105">此工作流程會以數字猜測遊戲為模型。</span><span class="sxs-lookup"><span data-stu-id="e88d3-105">The workflow models a number guessing game.</span></span> <span data-ttu-id="e88d3-106">只要閱讀本節其中一個主題即可完成教學課程；請選擇您感興趣的樣式並依照該步驟進行。</span><span class="sxs-lookup"><span data-stu-id="e88d3-106">Only one of the topics in this section is required to complete the tutorial; you should pick the style that interests you and follow that step.</span></span> <span data-ttu-id="e88d3-107">但是，您也可以完成所有的主題。</span><span class="sxs-lookup"><span data-stu-id="e88d3-107">However, you may complete all of the topics if desired.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e88d3-108">「快速入門」教學課程中的每個主題都與之前的主題息息相關。</span><span class="sxs-lookup"><span data-stu-id="e88d3-108">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="e88d3-109">若要完成本主題，您必須先完成[How to： 建立活動](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)。</span><span class="sxs-lookup"><span data-stu-id="e88d3-109">To complete this topic, you must first complete [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e88d3-110">若要下載教學課程的完整版本，請參閱 [Windows Workflow Foundation (WF45) - 快速入門教學課程](http://go.microsoft.com/fwlink/?LinkID=248976)。</span><span class="sxs-lookup"><span data-stu-id="e88d3-110">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e88d3-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="e88d3-111">In This Section</span></span>  
 [<span data-ttu-id="e88d3-112">如何：建立循序工作流程</span><span class="sxs-lookup"><span data-stu-id="e88d3-112">How to: Create a Sequential Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-sequential-workflow.md)  
 <span data-ttu-id="e88d3-113">說明如何使用 <xref:System.Activities.Statements.Sequence> 活動建立循序工作流程。</span><span class="sxs-lookup"><span data-stu-id="e88d3-113">Describes how to create a sequential workflow using the <xref:System.Activities.Statements.Sequence> activity.</span></span>  
  
 [<span data-ttu-id="e88d3-114">如何：建立流程圖工作流程</span><span class="sxs-lookup"><span data-stu-id="e88d3-114">How to: Create a Flowchart Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-flowchart-workflow.md)  
 <span data-ttu-id="e88d3-115">說明如何使用 <xref:System.Activities.Statements.Flowchart> 活動建立流程圖工作流程。</span><span class="sxs-lookup"><span data-stu-id="e88d3-115">Describes how to create a flowchart workflow using the <xref:System.Activities.Statements.Flowchart> activity.</span></span>  
  
 [<span data-ttu-id="e88d3-116">如何：建立狀態機器工作流程</span><span class="sxs-lookup"><span data-stu-id="e88d3-116">How to: Create a State Machine Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-state-machine-workflow.md)  
 <span data-ttu-id="e88d3-117">說明如何使用 <xref:System.Activities.Statements.StateMachine> 活動建立狀態電腦工作流程。</span><span class="sxs-lookup"><span data-stu-id="e88d3-117">Describes how to create a state machine workflow using the <xref:System.Activities.Statements.StateMachine> activity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e88d3-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="e88d3-118">See Also</span></span>  
 [<span data-ttu-id="e88d3-119">Windows Workflow Foundation 程式設計</span><span class="sxs-lookup"><span data-stu-id="e88d3-119">Windows Workflow Foundation Programming</span></span>](../../../docs/framework/windows-workflow-foundation/programming.md)
