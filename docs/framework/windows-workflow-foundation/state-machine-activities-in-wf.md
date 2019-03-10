---
title: WF 中的狀態機器活動
ms.date: 03/30/2017
ms.assetid: 93312eaf-07e0-4a55-b4f7-4cdbbc4dee2d
ms.openlocfilehash: eee507f873cde3aabce09c9b3fdb1620cd79fdab
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57710312"
---
# <a name="state-machine-activities-in-wf"></a>WF 中的狀態機器活動
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 提供數種系統提供的活動和活動設計工具，用於建立狀態機器工作流程。  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.StateMachine>|使用熟悉的狀態機器範例來執行包含的活動。|  
|<xref:System.Activities.Statements.State>|代表狀態機器中的狀態。|  
|<xref:System.Activities.Core.Presentation.FinalState>|表示狀態機器中的終止狀態。 <xref:System.Activities.Core.Presentation.FinalState> 是活動設計工具，使用時會建立預先設定為終止狀態的 <xref:System.Activities.Statements.State>。 如需詳細資訊，請參閱 < [FinalState 活動設計工具](/visualstudio/workflow-designer/finalstate-activity-designer)。|  
|<xref:System.Activities.Statements.Transition>|表示在兩個狀態之間轉換。 沒有任何**工具箱**的項目<xref:System.Activities.Statements.Transition>; 轉換時，會建立工作流程設計工具上，藉由兩個狀態，之間拖放一條線，或將狀態時顯示的三角形上放一個狀態停留另一個. 如需詳細資訊，請參閱 < [Transition 活動設計工具](/visualstudio/workflow-designer/transition-activity-designer)。|  
  
## <a name="see-also"></a>另請參閱
- [快速入門教學課程](getting-started-tutorial.md)
