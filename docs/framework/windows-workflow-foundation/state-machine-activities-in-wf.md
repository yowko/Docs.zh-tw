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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 62a211b51f37b306ffcc6b3b9a1ac65ccadd9db5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="state-machine-activities-in-wf"></a>WF 中的狀態機器活動
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 提供數種系統提供的活動和活動設計工具，用於建立狀態機器工作流程。  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.StateMachine>|使用熟悉的狀態機器範例來執行包含的活動。|  
|<xref:System.Activities.Statements.State>|代表狀態機器中的狀態。|  
|<xref:System.Activities.Core.Presentation.FinalState>|表示狀態機器中的終止狀態。 <xref:System.Activities.Core.Presentation.FinalState> 是活動設計工具，使用時會建立預先設定為終止狀態的 <xref:System.Activities.Statements.State>。 如需詳細資訊，請參閱[FinalState 活動設計工具](/visualstudio/workflow-designer/finalstate-activity-designer)。|  
|<xref:System.Activities.Statements.Transition>|表示在兩個狀態之間轉換。 沒有任何**工具箱**的項目<xref:System.Activities.Statements.Transition>; 轉換會藉由兩個狀態，之間拖放一條線建立工作流程設計工具或時出現的三角形上將狀態放一個狀態移至另. 如需詳細資訊，請參閱[Transition 活動設計工具](/visualstudio/workflow-designer/transition-activity-designer)。|  
  
## <a name="see-also"></a>請參閱  
 [快速入門教學課程](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)
