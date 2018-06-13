---
title: 使用 Send 的通道快取
ms.date: 03/30/2017
ms.assetid: e69a2502-25cb-43bf-b8d2-95fbdecb41cb
ms.openlocfilehash: c26d81b9cd85ba75189fafddd82c3fb4673c7fae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514035"
---
# <a name="channel-caching-with-send"></a>使用 Send 的通道快取
<xref:System.ServiceModel.Activities.SendMessageChannelCache> 可讓使用者利用 <xref:System.ServiceModel.Activities.Send> 和 <xref:System.ServiceModel.Activities.SendParametersContent> 活動來擁有不同層級的通道快取。 預設會啟用執行個體層級的快取，而這個範例會示範下列功能：  
  
1.  跨應用程式定義域共用 <xref:System.ServiceModel.Activities.SendMessageChannelCache>。  
  
2.  停用通道快取。  
  
3.  在 <xref:System.ServiceModel.Activities.SendMessageChannelCache> 中的工作流程執行個體之間共用 <xref:System.ServiceModel.Activities.WorkflowServiceHost>。  
  
## <a name="demonstrates"></a>示範  
 <xref:System.ServiceModel.Activities.SendMessageChannelCache> 延伸、<xref:System.ServiceModel.Activities.Send>、<xref:System.ServiceModel.Activities.Receive>、<xref:System.ServiceModel.Activities.ReceiveContent> 和 <xref:System.ServiceModel.Activities.SendReply> 活動。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中載入專案方案，然後建立專案。  
  
2.  執行 \EchoWorkflowService\bin\debug 中產生的 EchoWorkflowService 應用程式。  
  
3.  執行 \EchoWorkflowClient\bin\debug 中產生的 EchoWorkflowClient 應用程式。  
  
4.  用戶端會在服務上呼叫 Echo 作業並列印結果。 當結果已經列印之後，按下 ENTER 結束用戶端，再結束服務。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\ChannelCache`
