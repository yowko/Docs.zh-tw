---
title: WF 中的狀態機器活動
ms.date: 03/30/2017
ms.assetid: 93312eaf-07e0-4a55-b4f7-4cdbbc4dee2d
ms.openlocfilehash: 64af2698c878066464e2ca3f32d4522d99999aec
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/30/2019
ms.locfileid: "66378043"
---
# <a name="state-machine-activities-in-wf"></a><span data-ttu-id="abc96-102">WF 中的狀態機器活動</span><span class="sxs-lookup"><span data-stu-id="abc96-102">State Machine Activities in WF</span></span>
<span data-ttu-id="abc96-103">.NET framework 4.5 提供數個系統提供的活動和活動設計工具用於建立狀態機器工作流程。</span><span class="sxs-lookup"><span data-stu-id="abc96-103">.NET Framework 4.5 provides several system-provided activities and activity designers for creating state machine workflows.</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.StateMachine>|<span data-ttu-id="abc96-104">使用熟悉的狀態機器範例來執行包含的活動。</span><span class="sxs-lookup"><span data-stu-id="abc96-104">Executes contained activities using the familiar state machine paradigm.</span></span>|  
|<xref:System.Activities.Statements.State>|<span data-ttu-id="abc96-105">代表狀態機器中的狀態。</span><span class="sxs-lookup"><span data-stu-id="abc96-105">Represents a state in a state machine.</span></span>|  
|<xref:System.Activities.Core.Presentation.FinalState>|<span data-ttu-id="abc96-106">表示狀態機器中的終止狀態。</span><span class="sxs-lookup"><span data-stu-id="abc96-106">Represents a terminating state in a state machine.</span></span> <span data-ttu-id="abc96-107"><xref:System.Activities.Core.Presentation.FinalState> 是活動設計工具，使用時會建立預先設定為終止狀態的 <xref:System.Activities.Statements.State>。</span><span class="sxs-lookup"><span data-stu-id="abc96-107"><xref:System.Activities.Core.Presentation.FinalState> is an activity designer that when used creates a <xref:System.Activities.Statements.State> preconfigured as a terminating state.</span></span> <span data-ttu-id="abc96-108">如需詳細資訊，請參閱 < [FinalState 活動設計工具](/visualstudio/workflow-designer/finalstate-activity-designer)。</span><span class="sxs-lookup"><span data-stu-id="abc96-108">For more information, see [FinalState Activity Designer](/visualstudio/workflow-designer/finalstate-activity-designer).</span></span>|  
|<xref:System.Activities.Statements.Transition>|<span data-ttu-id="abc96-109">表示在兩個狀態之間轉換。</span><span class="sxs-lookup"><span data-stu-id="abc96-109">Represents the transition between two states.</span></span> <span data-ttu-id="abc96-110">沒有任何**工具箱**的項目<xref:System.Activities.Statements.Transition>; 轉換時，會建立工作流程設計工具上，藉由兩個狀態，之間拖放一條線，或將狀態時顯示的三角形上放一個狀態停留另一個.</span><span class="sxs-lookup"><span data-stu-id="abc96-110">There is no **Toolbox** item for <xref:System.Activities.Statements.Transition>; transitions are created on the workflow designer by dragging and dropping a line between two states, or by dropping a state on the triangles that appear when one state is hovered over another.</span></span> <span data-ttu-id="abc96-111">如需詳細資訊，請參閱 < [Transition 活動設計工具](/visualstudio/workflow-designer/transition-activity-designer)。</span><span class="sxs-lookup"><span data-stu-id="abc96-111">For more information, see [Transition Activity Designer](/visualstudio/workflow-designer/transition-activity-designer).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="abc96-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="abc96-112">See also</span></span>

- [<span data-ttu-id="abc96-113">快速入門教學課程</span><span class="sxs-lookup"><span data-stu-id="abc96-113">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
