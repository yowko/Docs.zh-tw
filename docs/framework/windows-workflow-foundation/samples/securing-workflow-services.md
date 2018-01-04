---
title: "保護工作流程服務"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53f84ad5-1ed1-4114-8d0d-b12e8a021c6e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ba98ac3e64d7dcbf52ed6363d44487af54128437
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="securing-workflow-services"></a>保護工作流程服務
安全工作流程服務範例示範下列程序：  
  
-   使用 <xref:System.ServiceModel.Activities.Receive> 和 <xref:System.ServiceModel.Activities.SendReply> 活動建立基本工作流程服務。  
  
-   使用 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 組態，定義工作流程服務所用的安全端點。  
  
-   在自訂原則中建立宣告，並使用 <xref:System.ServiceModel.ServiceAuthorizationManager> 驗證宣告。  
  
## <a name="demonstrates"></a>示範  
 使用 WCF 安全性保護用戶端和工作流程服務之間的通訊、宣告架構的授權  
  
## <a name="discussion"></a>討論  
 這個範例示範如何使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 安全性基礎結構來保護工作流程服務，就像保護一般 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務一樣。 特別是對授權使用自訂宣告。 在這個範例中，會使用 <xref:System.ServiceModel.WSHttpBinding> 和訊息模式安全性搭配 Windows 認證。  
  
 自訂 <xref:System.IdentityModel.Policy.IAuthorizationPolicy> (`CustomNameCheckerPolicy`) 會檢查用戶端的 Windows 使用者名稱和特定字元。 如果該字元存在，則會建立宣告並將它加入至 <xref:System.IdentityModel.Policy.EvaluationContext>。 透過這種方式，自訂原則表示用戶端的使用者名稱中有這個字元。 在呼叫的存留期間，可以查詢這個宣告。 您可以在 `Constants.cs` 中找到該字元。  
  
 授權原則會在 `SecureWorkFlowAuthZManager` 中尋找宣告。 如果找到，會傳回 `true` 並允許工作流程繼續執行。 否則會傳回 `false`，導致「拒絕存取」訊息傳回至用戶端。 其他宣告存在於此內容中，也可以在 `SecureWorkFlowAuthZManager` 中進行檢查。  
  
#### <a name="to-run-this-sample"></a>若要執行這個範例  
  
1.  以系統管理員權限執行 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]。  
  
2.  在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中載入 SecuringWorkflowServices.sln。  
  
3.  按 CTRL+SHIFT+B 以編譯方案。  
  
4.  將 Service 專案設定為方案的啟始專案。  
  
5.  按 CTRL+F5 啟動服務但不偵錯。  
  
6.  將 Client 專案設定為方案的啟始專案。  
  
7.  按 CTRL+F5 啟動用戶端但不偵錯。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\SecuringWorkflowServices`
