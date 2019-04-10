---
title: 建立與執行工作流程執行個體
ms.date: 03/30/2017
ms.assetid: 19d27f47-0491-4569-8f53-51bc1d940e80
ms.openlocfilehash: f2bdfce0b311da6dd20aac5e0fe4f5fbcd14f68a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59210089"
---
# <a name="creating-and-running-a-workflow-instance"></a>建立與執行工作流程執行個體
這個範例示範如何執行工作流程執行個體。 範例中會示範如何以同步和非同步方式執行。  
  
## <a name="demonstrates"></a>示範  
 <xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.  
  
## <a name="discussion"></a>討論  
 範例的第一個部分會使用 <xref:System.Activities.WorkflowInvoker.Invoke%2A>。 這是執行工作流程的最基本方式。 使用 <xref:System.Activities.WorkflowInvoker.Invoke%2A> 執行的工作流程會以同步方式執行。  
  
 範例的第二部分使用 <xref:System.Activities.WorkflowApplication> 類別。 <xref:System.Activities.WorkflowApplication> 可讓您更充分掌控每個執行個體，包括執行中工作流程進行互動，並以非同步方式執行工作流程的能力。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreatingWorkflowInstances`  
  
## <a name="see-also"></a>另請參閱

- [使用 WorkflowInvoker 與 WorkflowApplication](../using-workflowinvoker-and-workflowapplication.md)
