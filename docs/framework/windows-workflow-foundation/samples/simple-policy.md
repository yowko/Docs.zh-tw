---
title: 簡單原則
ms.date: 03/30/2017
ms.assetid: 6a94c834-2e32-4bed-9f47-ae5845eef6ff
ms.openlocfilehash: dff3979d75fdeb5a45be3940af3568c26f5e8f98
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515892"
---
# <a name="simple-policy"></a>簡單原則
這個範例會示範如何在工作流程中使用 <xref:System.Workflow.Activities.PolicyActivity> 活動。  
  
 這個範例中的循序工作流程是使用 <xref:System.Workflow.Activities.PolicyActivity> 活動所建立的。 該工作流程會定義用來定義產品折扣工作流程的 `orderValue`、`customerType` 及 `discount` 欄位。 定義在規則檔案中的規則會根據 `orderValue` 和 `customerType` 來設定折扣值。 `orderValue` 和 `customerType` 會定義於 `SimplePolicyWorkflow` 類別定義，而且可以加以變更來改變行為。 結果產生的折扣將透過已定義於 <xref:System.Workflow.Runtime.WorkflowRuntime.WorkflowCompleted> 類別中的 `SimplePolicyWorkflow` 事件處理常式來寫入到主控台。  
  
### <a name="to-build-the-sample"></a>若要建置範例  
  
1.  在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟方案。  
  
2.  按 CTRL+SHIFT+B 建置此方案。  
  
3.  按 CTRL+F5 執行方案，但不進行偵錯。  
  
### <a name="to-run-the-sample"></a>若要執行範例  
  
-   在 [SDK 命令提示字元] 視窗中，執行 SimplePolicy\bin\debug 資料夾 (若是範例的 Visual Basic 版本，則是 SimplePolicy\bin 資料夾) 中的 .exe 檔案，該資料夾位於此範例的主要資料夾下方。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續：  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄：  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\SimplePolicy`  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Workflow.Activities.Rules.RuleSet>  
 <xref:System.Workflow.Activities.PolicyActivity>  
 [進階原則](../../../../docs/framework/windows-workflow-foundation/samples/advanced-policy.md)
