---
title: "WF 中的狀態機器活動"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 93312eaf-07e0-4a55-b4f7-4cdbbc4dee2d
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5056557c9fee74e9a16b235220c797e1f6356ce3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="state-machine-activities-in-wf"></a><span data-ttu-id="8f8b6-102">WF 中的狀態機器活動</span><span class="sxs-lookup"><span data-stu-id="8f8b6-102">State Machine Activities in WF</span></span>
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]<span data-ttu-id="8f8b6-103"> 提供數種系統提供的活動和活動設計工具，用於建立狀態機器工作流程。</span><span class="sxs-lookup"><span data-stu-id="8f8b6-103"> provides several system-provided activities and activity designers for creating state machine workflows.</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.StateMachine>|<span data-ttu-id="8f8b6-104">使用熟悉的狀態機器範例來執行包含的活動。</span><span class="sxs-lookup"><span data-stu-id="8f8b6-104">Executes contained activities using the familiar state machine paradigm.</span></span>|  
|<xref:System.Activities.Statements.State>|<span data-ttu-id="8f8b6-105">代表狀態機器中的狀態。</span><span class="sxs-lookup"><span data-stu-id="8f8b6-105">Represents a state in a state machine.</span></span>|  
|<xref:System.Activities.Core.Presentation.FinalState>|<span data-ttu-id="8f8b6-106">表示狀態機器中的終止狀態。</span><span class="sxs-lookup"><span data-stu-id="8f8b6-106">Represents a terminating state in a state machine.</span></span> <span data-ttu-id="8f8b6-107"><xref:System.Activities.Core.Presentation.FinalState> 是活動設計工具，使用時會建立預先設定為終止狀態的 <xref:System.Activities.Statements.State>。</span><span class="sxs-lookup"><span data-stu-id="8f8b6-107"><xref:System.Activities.Core.Presentation.FinalState> is an activity designer that when used creates a <xref:System.Activities.Statements.State> preconfigured as a terminating state.</span></span> <span data-ttu-id="8f8b6-108">如需詳細資訊，請參閱[FinalState 活動設計工具](/visualstudio/workflow-designer/finalstate-activity-designer)。</span><span class="sxs-lookup"><span data-stu-id="8f8b6-108">For more information, see [FinalState Activity Designer](/visualstudio/workflow-designer/finalstate-activity-designer).</span></span>|  
|<xref:System.Activities.Statements.Transition>|<span data-ttu-id="8f8b6-109">表示在兩個狀態之間轉換。</span><span class="sxs-lookup"><span data-stu-id="8f8b6-109">Represents the transition between two states.</span></span> <span data-ttu-id="8f8b6-110">沒有任何**工具箱**的項目<xref:System.Activities.Statements.Transition>; 轉換會藉由兩個狀態，之間拖放一條線建立工作流程設計工具或時出現的三角形上將狀態放一個狀態移至另.</span><span class="sxs-lookup"><span data-stu-id="8f8b6-110">There is no **Toolbox** item for <xref:System.Activities.Statements.Transition>; transitions are created on the workflow designer by dragging and dropping a line between two states, or by dropping a state on the triangles that appear when one state is hovered over another.</span></span> <span data-ttu-id="8f8b6-111">如需詳細資訊，請參閱[Transition 活動設計工具](/visualstudio/workflow-designer/transition-activity-designer)。</span><span class="sxs-lookup"><span data-stu-id="8f8b6-111">For more information, see [Transition Activity Designer](/visualstudio/workflow-designer/transition-activity-designer).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8f8b6-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f8b6-112">See Also</span></span>  
 [<span data-ttu-id="8f8b6-113">快速入門教學課程</span><span class="sxs-lookup"><span data-stu-id="8f8b6-113">Getting Started Tutorial</span></span>](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)
