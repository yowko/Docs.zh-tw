---
title: 活動程式庫
ms.date: 03/30/2017
ms.assetid: 5323e9d4-71d6-47eb-bfa6-31feac62044d
ms.openlocfilehash: ce65bf8e7adad6acefd7aac6d69c3f836b94be29
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094692"
---
# <a name="activity-library"></a>活動程式庫
本節包含的範例示範如何在 Windows Workflow Foundation （WF）中進行先進的自訂活動。  
  
## <a name="in-this-section"></a>本節內容

 [SendMail 自訂活動](sendmail-custom-activity.md)  
 示範如何建立衍生自 <xref:System.Activities.AsyncCodeActivity> 的自訂活動，以使用 SMTP 來傳送郵件，供工作流程應用程式使用。  
  
 [節流平行 ForEach](throttled-parallel-foreach.md)  
 示範 `ThrottleParallelForEach` 活動與 <xref:System.Activities.Statements.ParallelForEach%601> 活動如何類似，唯一的例外是它允許設定並行因數來限制同時執行的分支數目。
  
 [資料庫存取活動](database-access-activities.md)  
 示範如何建立活動，以允許存取資料庫來抓取或修改資訊，以及使用[ADO.NET](../../data/adonet/index.md)來存取資料庫。  
  
 [.NET Framework 4.5 中的外顯化原則活動](externalized-policy-activity-in-net-framework-4-5.md)  
 示範 ExternalizedPolicy4 活動如何使用 WF 3.5 中隨附的規則引擎，直接在 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] （WF 4.5） Windows Workflow Foundation 中的 .NET Framework 3.5 （WF 3.5）中執行現有的 Windows Workflow Foundation <xref:System.Workflow.Activities.Rules.RuleSet> 物件。 
  
 [非泛型 ForEach](non-generic-foreach.md)  
 示範如何建立非泛型 <xref:System.Activities.Statements.ForEach%601> 活動版本。  
  
 [非泛型 ParallelForEach](non-generic-parallelforeach.md)  
 示範如何建立非泛型 <xref:System.Activities.Statements.ParallelForEach%601> 活動版本。  
  
 [取得 WorkflowInstanceId](get-workflowinstanceid.md)  
 示範如何使用 `GetWorkflowInstanceId` 自訂活動傳回工作流程執行個體識別碼。
