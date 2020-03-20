---
title: 活動程式庫
ms.date: 03/30/2017
ms.assetid: 5323e9d4-71d6-47eb-bfa6-31feac62044d
ms.openlocfilehash: fae2a94b5e5e776625aa7f26700980640b66afd4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142897"
---
# <a name="activity-library"></a>活動程式庫
本節包含演示 Windows 工作流基礎 （WF） 中高級自訂活動的示例。  
  
## <a name="in-this-section"></a>本節內容

 [SendMail 自訂活動](sendmail-custom-activity.md)  
 示範如何建立衍生自 <xref:System.Activities.AsyncCodeActivity> 的自訂活動，以使用 SMTP 來傳送郵件，供工作流程應用程式使用。  
  
 [節流平行 ForEach](throttled-parallel-foreach.md)  
 示範 `ThrottleParallelForEach` 活動與 <xref:System.Activities.Statements.ParallelForEach%601> 活動如何類似，唯一的例外是它允許設定並行因數來限制同時執行的分支數目。
  
 [資料庫存取活動](database-access-activities.md)  
 演示如何創建允許訪問資料庫以檢索或修改資訊並使用[ADO.NET](../../data/adonet/index.md)訪問資料庫的活動。  
  
 [.NET Framework 4.5 中的外顯化原則活動](externalized-policy-activity-in-net-framework-4-5.md)  
 演示外化策略4活動如何允許使用 WF 3.5 中隨附的規則引擎直接在 （WF 4.5） 中的 Windows 工作流基礎 （WF <xref:System.Workflow.Activities.Rules.RuleSet> 4.5） 中的[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]Windows 工作流基礎中執行現有的 Windows 工作流基礎。
  
 [非泛型 ForEach](non-generic-foreach.md)  
 示範如何建立非泛型 <xref:System.Activities.Statements.ForEach%601> 活動版本。  
  
 [非泛型 ParallelForEach](non-generic-parallelforeach.md)  
 示範如何建立非泛型 <xref:System.Activities.Statements.ParallelForEach%601> 活動版本。  
  
 [取得 WorkflowInstanceId](get-workflowinstanceid.md)  
 示範如何使用 `GetWorkflowInstanceId` 自訂活動傳回工作流程執行個體識別碼。
