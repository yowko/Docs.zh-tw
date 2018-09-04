---
title: 'How to: Create a Workflow'
ms.date: 03/30/2017
ms.assetid: 87234108-8e21-4cb3-9340-4a1a13f3f98c
ms.openlocfilehash: adaa322d4129f56abcad4fd848204ee373e907bd
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43502480"
---
# <a name="how-to-create-a-workflow"></a><span data-ttu-id="44e67-102">How to: Create a Workflow</span><span class="sxs-lookup"><span data-stu-id="44e67-102">How to: Create a Workflow</span></span>
<span data-ttu-id="44e67-103">工作流程可以從內建活動建構，也可以從自訂活動建構。</span><span class="sxs-lookup"><span data-stu-id="44e67-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="44e67-104">本主題中建立的工作流程會使用這兩個內建的活動時，例如，這一節逐步<xref:System.Activities.Statements.Flowchart>活動和自訂活動，從先前[How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)主題。</span><span class="sxs-lookup"><span data-stu-id="44e67-104">This topics in this section step through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Flowchart> activity, and the custom activities from the previous [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="44e67-105">此工作流程會以數字猜測遊戲為模型。</span><span class="sxs-lookup"><span data-stu-id="44e67-105">The workflow models a number guessing game.</span></span> <span data-ttu-id="44e67-106">只要閱讀本節其中一個主題即可完成教學課程；請選擇您感興趣的樣式並依照該步驟進行。</span><span class="sxs-lookup"><span data-stu-id="44e67-106">Only one of the topics in this section is required to complete the tutorial; you should pick the style that interests you and follow that step.</span></span> <span data-ttu-id="44e67-107">但是，您也可以完成所有的主題。</span><span class="sxs-lookup"><span data-stu-id="44e67-107">However, you may complete all of the topics if desired.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="44e67-108">「快速入門」教學課程中的每個主題都與之前的主題息息相關。</span><span class="sxs-lookup"><span data-stu-id="44e67-108">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="44e67-109">若要完成本主題，您必須先完成[How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)。</span><span class="sxs-lookup"><span data-stu-id="44e67-109">To complete this topic, you must first complete [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="44e67-110">若要下載教學課程的完整的版本，請參閱[Windows Workflow Foundation (WF45)-入門教學課程](https://go.microsoft.com/fwlink/?LinkID=248976)。</span><span class="sxs-lookup"><span data-stu-id="44e67-110">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="44e67-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="44e67-111">In This Section</span></span>  
 [<span data-ttu-id="44e67-112">如何：建立循序工作流程</span><span class="sxs-lookup"><span data-stu-id="44e67-112">How to: Create a Sequential Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-sequential-workflow.md)  
 <span data-ttu-id="44e67-113">說明如何使用 <xref:System.Activities.Statements.Sequence> 活動建立循序工作流程。</span><span class="sxs-lookup"><span data-stu-id="44e67-113">Describes how to create a sequential workflow using the <xref:System.Activities.Statements.Sequence> activity.</span></span>  
  
 [<span data-ttu-id="44e67-114">如何：建立流程圖工作流程</span><span class="sxs-lookup"><span data-stu-id="44e67-114">How to: Create a Flowchart Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-flowchart-workflow.md)  
 <span data-ttu-id="44e67-115">說明如何使用 <xref:System.Activities.Statements.Flowchart> 活動建立流程圖工作流程。</span><span class="sxs-lookup"><span data-stu-id="44e67-115">Describes how to create a flowchart workflow using the <xref:System.Activities.Statements.Flowchart> activity.</span></span>  
  
 [<span data-ttu-id="44e67-116">如何：建立狀態機器工作流程</span><span class="sxs-lookup"><span data-stu-id="44e67-116">How to: Create a State Machine Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-state-machine-workflow.md)  
 <span data-ttu-id="44e67-117">說明如何使用 <xref:System.Activities.Statements.StateMachine> 活動建立狀態電腦工作流程。</span><span class="sxs-lookup"><span data-stu-id="44e67-117">Describes how to create a state machine workflow using the <xref:System.Activities.Statements.StateMachine> activity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44e67-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44e67-118">See Also</span></span>  
 [<span data-ttu-id="44e67-119">Windows Workflow Foundation 程式設計</span><span class="sxs-lookup"><span data-stu-id="44e67-119">Windows Workflow Foundation Programming</span></span>](../../../docs/framework/windows-workflow-foundation/programming.md)
