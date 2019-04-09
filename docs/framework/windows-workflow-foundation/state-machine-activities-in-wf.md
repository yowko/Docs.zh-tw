---
title: WF 中的狀態機器活動
ms.date: 03/30/2017
ms.assetid: 93312eaf-07e0-4a55-b4f7-4cdbbc4dee2d
ms.openlocfilehash: 5aee2a7cb078d9d62c9296f7dda9f28ff812a88a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59120909"
---
# <a name="state-machine-activities-in-wf"></a><span data-ttu-id="7fb1e-102">WF 中的狀態機器活動</span><span class="sxs-lookup"><span data-stu-id="7fb1e-102">State Machine Activities in WF</span></span>
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] <span data-ttu-id="7fb1e-103">提供數個系統提供的活動和活動設計工具建立狀態機器工作流程。</span><span class="sxs-lookup"><span data-stu-id="7fb1e-103">provides several system-provided activities and activity designers for creating state machine workflows.</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.StateMachine>|<span data-ttu-id="7fb1e-104">使用熟悉的狀態機器範例來執行包含的活動。</span><span class="sxs-lookup"><span data-stu-id="7fb1e-104">Executes contained activities using the familiar state machine paradigm.</span></span>|  
|<xref:System.Activities.Statements.State>|<span data-ttu-id="7fb1e-105">代表狀態機器中的狀態。</span><span class="sxs-lookup"><span data-stu-id="7fb1e-105">Represents a state in a state machine.</span></span>|  
|<xref:System.Activities.Core.Presentation.FinalState>|<span data-ttu-id="7fb1e-106">表示狀態機器中的終止狀態。</span><span class="sxs-lookup"><span data-stu-id="7fb1e-106">Represents a terminating state in a state machine.</span></span> <xref:System.Activities.Core.Presentation.FinalState> <span data-ttu-id="7fb1e-107">是活動設計工具，當使用建立<xref:System.Activities.Statements.State>預先設定為終止狀態。</span><span class="sxs-lookup"><span data-stu-id="7fb1e-107">is an activity designer that when used creates a <xref:System.Activities.Statements.State> preconfigured as a terminating state.</span></span> <span data-ttu-id="7fb1e-108">如需詳細資訊，請參閱 < [FinalState 活動設計工具](/visualstudio/workflow-designer/finalstate-activity-designer)。</span><span class="sxs-lookup"><span data-stu-id="7fb1e-108">For more information, see [FinalState Activity Designer](/visualstudio/workflow-designer/finalstate-activity-designer).</span></span>|  
|<xref:System.Activities.Statements.Transition>|<span data-ttu-id="7fb1e-109">表示在兩個狀態之間轉換。</span><span class="sxs-lookup"><span data-stu-id="7fb1e-109">Represents the transition between two states.</span></span> <span data-ttu-id="7fb1e-110">沒有任何**工具箱**的項目<xref:System.Activities.Statements.Transition>; 轉換時，會建立工作流程設計工具上，藉由兩個狀態，之間拖放一條線，或將狀態時顯示的三角形上放一個狀態停留另一個.</span><span class="sxs-lookup"><span data-stu-id="7fb1e-110">There is no **Toolbox** item for <xref:System.Activities.Statements.Transition>; transitions are created on the workflow designer by dragging and dropping a line between two states, or by dropping a state on the triangles that appear when one state is hovered over another.</span></span> <span data-ttu-id="7fb1e-111">如需詳細資訊，請參閱 < [Transition 活動設計工具](/visualstudio/workflow-designer/transition-activity-designer)。</span><span class="sxs-lookup"><span data-stu-id="7fb1e-111">For more information, see [Transition Activity Designer](/visualstudio/workflow-designer/transition-activity-designer).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7fb1e-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7fb1e-112">See also</span></span>

- [<span data-ttu-id="7fb1e-113">快速入門教學課程</span><span class="sxs-lookup"><span data-stu-id="7fb1e-113">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
