---
title: OperationScope
ms.date: 03/30/2017
ms.assetid: 56206a21-1e63-422d-b92a-e5d8b713e707
ms.openlocfilehash: 562fd9c8ff964cb997012d49600bce73d4441465
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43554065"
---
# <a name="operationscope"></a>OperationScope
這個範例示範 <xref:System.ServiceModel.Activities.Receive> 和 <xref:System.ServiceModel.Activities.SendReply> 訊息活動如何用來將現有自訂活動公開成為工作流程服務中的作業。 這個範例包含一個名為 `OperationScope` 的新自訂活動。 它可讓使用者將作業主體分別撰寫成自訂活動，然後使用 `OperationScope` 活動，將它們輕鬆公開為服務作業，以便於開發工作流程服務。 例如，接收兩個 `Add` 引數並傳回一個 `in` 引數的自訂 `out` 活動，可以藉由放置在 `Add` 中，公開為工作流程服務的 `OperationScope` 作業。  
  
 範圍的運作方式是檢查當成主體提供的活動。 任何未繫結的 `in` 引數都會假定為傳入訊息中的輸入。 所有 `out` 引數，不論是否繫結，都會假定為後續回覆訊息中的輸出。 公開作業名稱是取自 `OperationScope` 活動的顯示名稱。 最終結果是主體活動包裝在 <xref:System.ServiceModel.Activities.Receive> 和 <xref:System.ServiceModel.Activities.SendReply> 中，其中來自訊息的參數繫結至活動的引數。  
  
 這個範例使用 HTTP 端點公開工作流程服務。 若要執行，必須加入 URL ACL。 如需詳細資訊，請參閱 <<c0> [ 設定 HTTP 和 HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353)。 執行下列命令，在提升權限提示字元中加入適當 Acl (請確定您的網域和使用者名稱取代 %網域 %\\%username%)。  
  
 **netsh http add urlacl =http://+:8000/使用者 = %網域 %\\%username%**  
  
### <a name="to-run-the-sample"></a>若要執行範例  
  
1.  在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 OperationScope.sln 方案。  
  
2.  設定多個啟始專案，以滑鼠右鍵按一下方案總管 中的方案，然後選取**設定啟始專案**。 加入 Scenario 和 Scenario_Client (依此順序) 做為多個啟始專案。  
  
3.  按下 CTRL+SHIFT+B 以建置方案。  
  
    > [!WARNING]
    >  由於自訂活動 `OperationScope`，需要這個步驟，才能檢視 BankService.xaml 工作流程。  
  
4.  按 CTRL+F5 執行應用程式。 Scenario_Client 主控台會提示您輸入，而且在 Scenario 主控台會顯示對應輸出。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\OperationScope`