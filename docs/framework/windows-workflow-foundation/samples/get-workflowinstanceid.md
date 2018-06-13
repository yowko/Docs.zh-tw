---
title: 取得 WorkflowInstanceId
ms.date: 03/30/2017
ms.assetid: bd7eea3b-1c28-4b84-9a67-003bc553aa81
ms.openlocfilehash: fbfaf52931345571e5125200fe467dcc098b9dc3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513902"
---
# <a name="get-workflowinstanceid"></a>取得 WorkflowInstanceId
這個範例示範如何使用 `GetWorkflowInstanceId` 自訂活動傳回工作流程執行個體識別碼。  
  
## <a name="demonstrates"></a>示範  
 自訂活動部署、如何存取工作流程執行個體。  
  
## <a name="discussion"></a>討論  
 取得執行中工作流程的執行個體識別碼，需要撰寫程式碼。 如果您想要撰寫完整宣告的工作流程，需要可傳回工作流程執行個體識別碼的活動，以便在工作流程中參考活動以提供完整宣告的工作流程撰寫經驗。 許多案例需要存取執行個體識別碼：一些範例包含記錄或稽核用途，或透過提供執行個體識別碼給用戶端供未來關聯 (例如在 SendReply 活動中使用這個活動) 來執行應用程式層級相互關聯。  
  
 `GetWorkflowInstanceId` 是實作為 <xref:System.Activities.CodeActivity%601>，因為它必須傳回 <xref:System.Guid> 類型的值，而且必須存取 <xref:System.Activities.CodeActivityContext> 以取得工作流程的執行個體識別碼。 這是相當基本的實作。  
  
```  
public sealed class GetWorkflowInstanceId : CodeActivity<Guid>  
{  
protected override Guid Execute(CodeActivityContext context)  
        {  
            return context.WorkflowInstanceId;  
        }  
}  
```  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\GetWorkflowInstanceId`
