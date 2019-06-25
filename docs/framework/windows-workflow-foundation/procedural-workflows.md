---
title: 程序性工作流程
ms.date: 03/30/2017
ms.assetid: 52401de9-9115-472d-8fd9-047af6a072b9
ms.openlocfilehash: 15ff155fb057c4c10663d383a8942108c6e4375c
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348360"
---
# <a name="procedural-workflows"></a>程序性工作流程
程序式工作流程使用的流程控制方法類似於程序式語言中的流程控制方法。 這些建構包括 `While` 和 `If`。 使用其他流程控制活動 (例如 <xref:System.Activities.Statements.Flowchart> 和 <xref:System.Activities.Statements.Sequence>) 即可自由撰寫這些工作流程。  
  
## <a name="controlling-execution-flow"></a>控制執行流程  
 工作流程活動程式庫具有程序式語言中用於建立大多數流程控制方法之模型的活動， 它們包括：  
  
- <xref:System.Activities.Statements.While>  
  
- <xref:System.Activities.Statements.DoWhile>  
  
- <xref:System.Activities.Statements.ForEach%601>  
  
- <xref:System.Activities.Statements.Parallel>  
  
- <xref:System.Activities.Statements.ParallelForEach%601>  
  
- <xref:System.Activities.Statements.If>  
  
- <xref:System.Activities.Statements.Switch%601>  
  
- <xref:System.Activities.Statements.Pick>  
  
 若要使用流程控制活動，拖曳和卸除它們**活動**工具箱拖曳到設計工具視窗內的複合活動。  
  
> [!NOTE]
>  如果使用 Windows Server AppFabric 裝載功能，將工作流程裝載的 Web 伺服陣列，AppFabric 將不同的 AppFabric 伺服器之間移動執行個體。 所有節點必須能夠共用資源，才能這麼做。  所有預設的 NET 4 工作流程活動皆不包含任何存取本機資源的作業。 由於 AppFabric 沒有提供任何機制可將工作流程標記為不可移動，因此開發人員不得建立會在工作流程移動時失敗的自訂活動。  
  
## <a name="see-also"></a>另請參閱

- [流程圖工作流程](flowchart-workflows.md)
