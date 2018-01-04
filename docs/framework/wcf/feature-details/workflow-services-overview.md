---
title: "工作流程服務概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e536dda3-e286-441e-99a7-49ddc004b646
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0c38abe8ab0ac99a7e5bd0499ff826a00730b211
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="workflow-services-overview"></a>工作流程服務概觀
工作流程服務是以 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 為主的服務，這些服務是使用工作流程實作的。 工作流程服務是使用傳訊活動傳送及接收 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 訊息的工作流程。 .NET Framework 4.5 引入了許多傳訊活動，可讓您從工作流程內傳送及接收訊息。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]傳訊活動，以及如何使用它們來實作不同訊息交換模式，請參閱[傳訊活動](../../../../docs/framework/wcf/feature-details/messaging-activities.md)。  
  
## <a name="benefits-of-using-workflow-services"></a>使用工作流程服務的好處  
 當應用程式的散發範圍越來越廣時，就必須由個別服務負責呼叫其他服務來卸載部分工作。 實作這些呼叫做為非同步作業會為程式碼增添少許複雜性。 錯誤處理會增加額外的複雜性，因為它需要處理例外狀況及提供詳細的追蹤資訊。 部分服務經常需要長時間執行，等待輸入時可能會佔用重要的系統資源。 由於這些問題，分散式應用程式通常非常複雜，而且難以撰寫及維護。 工作流程是表達非同步工作 (特別是呼叫外部服務) 協調性的自然方式。 工作流程也能有效地表示長期執行的商務程序。 這些特質使得工作流程成為在分散式環境中建置服務的重要資產。  
  
## <a name="implementing-a-workflow-service"></a>實作工作流程服務  
 實作 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務時，您會定義許多合約，這些合約會描述服務及服務傳送與接收的資料。 資料會以資料合約及訊息合約表示。 WCF 和工作流程服務都使用資料合約和訊息合約定義做為部分服務描述。 服務本身會公開中繼資料 (以 WSDL 的形式) 來描述服務的作業。 在 WCF 中，服務合約和作業合約會定義所支援的服務及作業。 不過，在工作流程服務中，這些合約是商務程序的一部分。 它們會藉由名為合約推斷的程序在中繼資料中公布。 使用 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 裝載工作流程服務時，會檢查該工作流程定義，並根據在工作流程中找到的傳訊活動集產生合約。 特別是，下列活動和屬性會用來產生合約：  
  
 <xref:System.ServiceModel.Activities.Receive> 活動  
  
-   <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
-   <!--zz <xref:System.ServiceModel.Activities.Receive.OperationContractName%2A>  --> `System.ServiceModel.Activities.Receive.OperationContractName`
  
-   <xref:System.ServiceModel.Activities.Receive.Action%2A>  
  
-   <!--zz <xref:System.ServiceModel.Activities.Receive.ValueType%2A>  --> `System.ServiceModel.Activities.Receive.ValueType`
  
 <xref:System.ServiceModel.Activities.SendReply> 活動  
  
-   <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
-   <!--zz <xref:System.ServiceModel.Activities.SendReply.ValueType%2A> -->
`xref:System.ServiceModel.Activities.SendReply.ValueType`
  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 活動  
  
 合約推斷的最終結果是與 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務和作業合約使用相同資料結構的服務描述。 接著，這項資訊會用來公開工作流程服務的 WSDL。  
  
> [!NOTE]
>  [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] 不允許您使用現有的合約定義而不使用其他工具撰寫工作流程服務。 工作流程服務合約是由上述合約推斷程序所建立的， 但可以完全支援訊息合約和資料合約。  
  
## <a name="workflow-services-and-msmq-based-bindings"></a>工作流程服務與以 MSMQ 為主的繫結  
 WCF 定義兩種以 MSMQ 為主的繫結：<xref:System.ServiceModel.NetMsmqBinding> 與 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>。  由於工作流程服務的長期執行特性，以 MSMQ 為主的繫結通常會與此類服務搭配使用。 以 MSMQ 為主的繫結具有 `ValidityDuration` 屬性，該屬性會指定可以假設 MSMQ 訊息有效的時間長短。 由於工作流程服務的長期執行特性，因此 MSMQ 訊息的有效性持續時間可能會在工作流程服務能夠處理該訊息之前結束。 因此，將 MSMQ 繫結的有效性持續時間設定為適當的值相當重要。 您必須根據工作流程和工作流程處理訊息的方式選擇這個值。 例如，如果您的工作流程含有 <xref:System.ServiceModel.Activities.Receive> 活動加上需要執行 10 分鐘的自訂活動，接著是另一個 <xref:System.ServiceModel.Activities.Receive> 活動，正確的 `ValidityDuration` 值便會大於 10 分鐘。  
  
## <a name="hosting-a-workflow-service"></a>裝載工作流程服務  
 如同 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務，工作流程服務必須經過裝載。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務會使用 <xref:System.ServiceModel.ServiceHost> 類別來裝載服務，而工作流程服務則會使用 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 來裝載服務。 如同 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務，工作流程服務可透過許多不同的方式進行裝載，例如：  
  
-   在 Managed [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 應用程式中。  
  
-   在網際網路資訊服務 (IIS) 中。  
  
-   在 Windows 處理序啟用服務 (WAS) 中。  
  
-   在 Managed Windows 服務中。  
  
 裝載於 Managed [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 應用程式或 Managed Windows 服務中的工作流程服務會建立 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 類別的執行個體，並將該執行個體傳遞至 <xref:System.ServiceModel.Activities.WorkflowService> 的執行個體 (此執行個體包含 <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> 屬性中的工作流程定義)。 包含傳訊活動的工作流程定義會公開為工作流程服務。  
  
 若要將工作流程服務裝載於 IIS 或 WAS 中，請將包含工作流程服務定義的 .xamlx 檔案置入虛擬目錄中。 預設端點 (使用<xref:System.ServiceModel.BasicHttpBinding>) 會自動建立[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][簡化的組態](../../../../docs/framework/wcf/simplified-configuration.md)。 您也可以將 Web.config 檔案置於虛擬目錄中，指定您自己的端點。 如果工作流程定義位於組件中，您可以將 .svc 檔案置於虛擬目錄內，並將工作流程組件置於 App_Code 目錄中。 .svc 檔案必須指定服務主機處理站，以及實作工作流程服務的類別。 下列範例示範如何指定服務主機處理站，以及指定實作工作流程服務的類別。  
  
```  
<%@ServiceHost Factory=" System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory  
Service="EchoService"%>  
```
