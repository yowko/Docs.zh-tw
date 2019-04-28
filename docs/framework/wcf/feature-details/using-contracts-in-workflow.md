---
title: 在工作流程中使用合約
ms.date: 03/30/2017
ms.assetid: 939c64e9-e7cc-4abc-b41e-27cfce1d7e50
ms.openlocfilehash: dd35766011c412acc937eed75d523a0574f6b9cb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61918537"
---
# <a name="using-contracts-in-workflow"></a>在工作流程中使用合約
實作服務時，您會定義許多合約，這些合約會描述服務及服務傳送與接收的資料。 資料被以資料合約與訊息合約。WCF 和工作流程服務會使用資料合約和訊息合約定義做為服務描述的一部分。 服務本身會公開中繼資料 (以 WSDL 的形式) 來描述服務的作業。 在 WCF 中，服務合約和作業合約會定義所支援的服務及作業。 不過，在工作流程服務中，這些合約是商務程序本身的一部分，會由稱為「合約推斷」的處理序在中繼資料中公開。  
  
## <a name="contract-inference"></a>合約推斷  
 使用 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 裝載工作流程服務時，會檢查該工作流程定義，並根據在工作流程中找到的傳訊活動集產生合約。 特別是，下列活動和屬性會用來產生合約：  
  
 <xref:System.ServiceModel.Activities.Receive> 活動  
  
- <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
- <xref:System.ServiceModel.Activities.Receive.OperationName%2A>
  
- <xref:System.ServiceModel.Activities.Receive.Action%2A>   
 
 <xref:System.ServiceModel.Activities.SendReply> 活動  
  
- <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 活動  
  
 合約推斷的最終結果是與 WCF 服務和作業合約使用相同資料結構的服務描述。 接著，這項資訊會用來公開工作流程服務的 WSDL。  
  
## <a name="see-also"></a>另請參閱

- [工作流程服務](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [傳訊活動](../../../../docs/framework/wcf/feature-details/messaging-activities.md)
- [如何：搭配訊息活動建立工作流程服務](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)
- [如何：建立會取用現有服務合約的工作流程服務](../../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)
