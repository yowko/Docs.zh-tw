---
title: "程序性工作流程"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52401de9-9115-472d-8fd9-047af6a072b9
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cd879d138a95c003ca0ffb12b3ce010534c3e158
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="procedural-workflows"></a><span data-ttu-id="4ab83-102">程序性工作流程</span><span class="sxs-lookup"><span data-stu-id="4ab83-102">Procedural Workflows</span></span>
<span data-ttu-id="4ab83-103">程序式工作流程使用的流程控制方法類似於程序式語言中的流程控制方法。</span><span class="sxs-lookup"><span data-stu-id="4ab83-103">Procedural workflows use flow-control methods similar to those found in procedural languages.</span></span> <span data-ttu-id="4ab83-104">這些建構包括 `While` 和 `If`。</span><span class="sxs-lookup"><span data-stu-id="4ab83-104">These constructs include `While` and `If`.</span></span> <span data-ttu-id="4ab83-105">使用其他流程控制活動 (例如 <xref:System.Activities.Statements.Flowchart> 和 <xref:System.Activities.Statements.Sequence>) 即可自由撰寫這些工作流程。</span><span class="sxs-lookup"><span data-stu-id="4ab83-105">These workflows can be freely composed using other flow control activities such as <xref:System.Activities.Statements.Flowchart> and <xref:System.Activities.Statements.Sequence>.</span></span>  
  
## <a name="controlling-execution-flow"></a><span data-ttu-id="4ab83-106">控制執行流程</span><span class="sxs-lookup"><span data-stu-id="4ab83-106">Controlling Execution Flow</span></span>  
 <span data-ttu-id="4ab83-107">工作流程活動程式庫具有程序式語言中用於建立大多數流程控制方法之模型的活動，</span><span class="sxs-lookup"><span data-stu-id="4ab83-107">The workflow activity library has activities for modeling most flow-control methods used in procedural languages.</span></span> <span data-ttu-id="4ab83-108">這些活動包括：</span><span class="sxs-lookup"><span data-stu-id="4ab83-108">These include:</span></span>  
  
-   <xref:System.Activities.Statements.While>  
  
-   <xref:System.Activities.Statements.DoWhile>  
  
-   <xref:System.Activities.Statements.ForEach%601>  
  
-   <xref:System.Activities.Statements.Parallel>  
  
-   <xref:System.Activities.Statements.ParallelForEach%601>  
  
-   <xref:System.Activities.Statements.If>  
  
-   <xref:System.Activities.Statements.Switch%601>  
  
-   <xref:System.Activities.Statements.Pick>  
  
 <span data-ttu-id="4ab83-109">若要使用流程控制活動，拖曳和卸除從**活動**工具箱拖曳到的複合活動設計工具視窗中。</span><span class="sxs-lookup"><span data-stu-id="4ab83-109">To use flow control activities, drag and drop them from the **Activity** toolbox into a composite activity inside the designer window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4ab83-110">如果使用 [!INCLUDE[dublin](../../../includes/dublin-md.md)]將工作流程裝載到 Web 伺服陣列，AppFabric 會在不同的 AppFabric 伺服器之間移動執行個體。</span><span class="sxs-lookup"><span data-stu-id="4ab83-110">If using the [!INCLUDE[dublin](../../../includes/dublin-md.md)] to host workflows on a Web farm, AppFabric will move instances between different AppFabric servers.</span></span> <span data-ttu-id="4ab83-111">所有節點必須能夠共用資源，才能這麼做。</span><span class="sxs-lookup"><span data-stu-id="4ab83-111">This requires that the resources are able to be shared between all nodes.</span></span>  <span data-ttu-id="4ab83-112">所有預設的 NET 4 工作流程活動皆不包含任何存取本機資源的作業。</span><span class="sxs-lookup"><span data-stu-id="4ab83-112">None of the default NET 4 workflow activities contain any operations that access local resources.</span></span> <span data-ttu-id="4ab83-113">由於 AppFabric 沒有提供任何機制可將工作流程標記為不可移動，因此開發人員不得建立會在工作流程移動時失敗的自訂活動。</span><span class="sxs-lookup"><span data-stu-id="4ab83-113">Since AppFabric does not offer any mechanism to mark a workflow as immovable, a developer must not create custom activities that fail when a workflow is moved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ab83-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ab83-114">See Also</span></span>  
 [<span data-ttu-id="4ab83-115">流程圖工作流程</span><span class="sxs-lookup"><span data-stu-id="4ab83-115">Flowchart Workflows</span></span>](../../../docs/framework/windows-workflow-foundation/flowchart-workflows.md)
