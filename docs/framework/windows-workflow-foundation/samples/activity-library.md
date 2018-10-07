---
title: 活動程式庫
ms.date: 03/30/2017
ms.assetid: 5323e9d4-71d6-47eb-bfa6-31feac62044d
ms.openlocfilehash: 7e8777d0068e6cca9c9324a6fd2668e6ff9e9da7
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2018
ms.locfileid: "48844016"
---
# <a name="activity-library"></a>活動程式庫
本節包含示範進階自訂活動中 Windows Workflow Foundation (WF) 範例。  
  
## <a name="in-this-section"></a>本節內容

 [SendMail 自訂活動](../../../../docs/framework/windows-workflow-foundation/samples/sendmail-custom-activity.md)  
 示範如何建立衍生自 <xref:System.Activities.AsyncCodeActivity> 的自訂活動，以使用 SMTP 來傳送郵件，供工作流程應用程式使用。  
  
 [節流平行 ForEach](../../../../docs/framework/windows-workflow-foundation/samples/throttled-parallel-foreach.md)  
 示範 `ThrottleParallelForEach` 活動與 <xref:System.Activities.Statements.ParallelForEach%601> 活動如何類似，唯一的例外是它允許設定並行因數來限制同時執行的分支數目。
  
 [資料庫存取活動](../../../../docs/framework/windows-workflow-foundation/samples/database-access-activities.md)  
 示範如何建立活動，可讓您存取資料庫以擷取或修改資訊以及使用[ADO.NET](https://go.microsoft.com/fwlink/?LinkId=166081)來存取資料庫。  
  
 [.NET Framework 4.5 中的外顯化原則活動](../../../../docs/framework/windows-workflow-foundation/samples/externalized-policy-activity-in-net-framework-4-5.md)  
 示範 ExternalizedPolicy4 活動如何讓執行中的現有 Windows Workflow Foundation [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF 3.5)<xref:System.Workflow.Activities.Rules.RuleSet>物件中的 Windows Workflow foundation [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF 4.5) 直接使用規則引擎也就是WF 3.5 隨附。 
  
 [非泛型 ForEach](../../../../docs/framework/windows-workflow-foundation/samples/non-generic-foreach.md)  
 示範如何建立非泛型 <xref:System.Activities.Statements.ForEach%601> 活動版本。  
  
 [非泛型 ParallelForEach](../../../../docs/framework/windows-workflow-foundation/samples/non-generic-parallelforeach.md)  
 示範如何建立非泛型 <xref:System.Activities.Statements.ParallelForEach%601> 活動版本。  
  
 [取得 WorkflowInstanceId](../../../../docs/framework/windows-workflow-foundation/samples/get-workflowinstanceid.md)  
 示範如何使用 `GetWorkflowInstanceId` 自訂活動傳回工作流程執行個體識別碼。
