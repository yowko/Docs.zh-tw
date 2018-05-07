---
title: 使用 TryCatch 錯誤處理流程圖活動
ms.date: 03/30/2017
ms.assetid: 50922964-bfe0-4ba8-9422-0e7220d514fd
ms.openlocfilehash: cc7630be868a5bdc1a07e8d935e5dd3269b4ae22
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="fault-handling-in-a-flowchart-activity-using-trycatch"></a>使用 TryCatch 錯誤處理流程圖活動
這個範例示範 <xref:System.Activities.Statements.TryCatch> 活動在複雜控制流程活動中的使用方式。  
  
 在這個範例中，促銷碼和小孩人數會當做變數傳遞至 <xref:System.Activities.Statements.Flowchart> 活動，根據對應於促銷碼的公式來計算折扣。 此範例包含命令式程式碼和工作流程設計工具的範例版本。  
  
 下表詳細說明 `CreateFlowchartWithFaults` 活動的變數。  
  
|參數|描述|  
|----------------|-----------------|  
|promoCode|促銷碼。 類型：String<br /><br /> 可能的值，說明放在括號中：<br /><br /> -單一 （單一）<br />-MNK （已婚，沒有小孩）。<br />-MWK （已婚，有小孩）|  
|numKids|小孩人數。 類型：int|  
  
 `CreateFlowchartWithFaults` 活動使用 <xref:System.Activities.Statements.FlowSwitch%601> 活動，在 `promoCode` 引數上切換，並透過下列公式計算折扣。  
  
|`promoCode` 的值|折扣 (%)|  
|--------------------------|--------------------|  
|Single|10|  
|MNK|15|  
|MWK|15 + (1 – 1 /`numberOfKids`)\*10**附註：**可能需要的這項計算可能會擲回<xref:System.DivideByZeroException>。 因此，折扣計算是包裝在 <xref:System.Activities.Statements.TryCatch> 活動中，以攔截 <xref:System.DivideByZeroException> 例外狀況並將折扣設為零。|  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 FlowchartWithFaultHandling.sln 方案檔案。  
  
2.  若要建置此方案，請按 CTRL+SHIFT+B。  
  
3.  若要執行此方案，請按 F5。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\FlowChartWithFaultHandling`  
  
## <a name="see-also"></a>另請參閱  
 [流程圖工作流程](../../../../docs/framework/windows-workflow-foundation/flowchart-workflows.md)  
 [例外狀況](../../../../docs/framework/windows-workflow-foundation/exceptions.md)
