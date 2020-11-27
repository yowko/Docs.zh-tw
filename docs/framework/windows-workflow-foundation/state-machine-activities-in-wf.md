---
title: WF 中的狀態機器活動
ms.date: 03/30/2017
ms.assetid: 93312eaf-07e0-4a55-b4f7-4cdbbc4dee2d
ms.openlocfilehash: dd0bfae1f24ecd9f98c0a2f04265581f880202a7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96261718"
---
# <a name="state-machine-activities-in-wf"></a>WF 中的狀態機器活動

.NET Framework 4.5 提供數種系統提供的活動和活動設計工具，可用來建立狀態機器工作流程。  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.StateMachine>|使用熟悉的狀態機器範例來執行包含的活動。|  
|<xref:System.Activities.Statements.State>|代表狀態機器中的狀態。|  
|<xref:System.Activities.Core.Presentation.FinalState>|表示狀態機器中的終止狀態。 <xref:System.Activities.Core.Presentation.FinalState> 是活動設計工具，使用時會建立預先設定為終止狀態的 <xref:System.Activities.Statements.State>。 如需詳細資訊，請參閱 [FinalState 活動設計](/visualstudio/workflow-designer/finalstate-activity-designer)工具。|  
|<xref:System.Activities.Statements.Transition>|表示在兩個狀態之間轉換。 沒有的 [ **工具箱** ] 專案 <xref:System.Activities.Statements.Transition> ; 您可以在工作流程設計工具上，藉由在兩個狀態之間拖放線條來建立轉換，或在某個狀態停留在另一個狀態時，將狀態放置在出現的三角形上。 如需詳細資訊，請參閱 [轉換活動設計](/visualstudio/workflow-designer/transition-activity-designer)工具。|  
  
## <a name="see-also"></a>另請參閱

- [快速入門教學課程](getting-started-tutorial.md)
