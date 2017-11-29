---
title: "在工作流程中使用合約"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 939c64e9-e7cc-4abc-b41e-27cfce1d7e50
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1c84483b2ca18d63f20e64a62bb757e244db9b24
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="using-contracts-in-workflow"></a><span data-ttu-id="f695e-102">在工作流程中使用合約</span><span class="sxs-lookup"><span data-stu-id="f695e-102">Using Contracts in Workflow</span></span>
<span data-ttu-id="f695e-103">實作服務時，您會定義許多合約，這些合約會描述服務及服務傳送與接收的資料。</span><span class="sxs-lookup"><span data-stu-id="f695e-103">When implementing a service, you define a number of contracts that describe the service and the data that it sends and receives.</span></span> <span data-ttu-id="f695e-104">資料會以資料合約和訊息合約表示，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 和工作流程服務都會使用資料合約和訊息合約定義做為服務描述的一部分。</span><span class="sxs-lookup"><span data-stu-id="f695e-104">The data is represented as data contracts and message contracts; both [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] and workflow services use data contract and message contract definitions as part of service descriptions.</span></span> <span data-ttu-id="f695e-105">服務本身會公開中繼資料 (以 WSDL 的形式) 來描述服務的作業。</span><span class="sxs-lookup"><span data-stu-id="f695e-105">The service itself exposes metadata (in the form of WSDL) in order to describe the operations of the service.</span></span> <span data-ttu-id="f695e-106">在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中，服務合約和作業合約會定義所支援的服務及作業。</span><span class="sxs-lookup"><span data-stu-id="f695e-106">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], service contracts and operation contracts define the service and the operations it supports.</span></span> <span data-ttu-id="f695e-107">不過，在工作流程服務中，這些合約是商務程序本身的一部分，會由稱為「合約推斷」的處理序在中繼資料中公開。</span><span class="sxs-lookup"><span data-stu-id="f695e-107">However, in a workflow service, these contracts are part of the business process itself; they are exposed in metadata by a process called contract inference.</span></span>  
  
## <a name="contract-inference"></a><span data-ttu-id="f695e-108">合約推斷</span><span class="sxs-lookup"><span data-stu-id="f695e-108">Contract Inference</span></span>  
 <span data-ttu-id="f695e-109">使用 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 裝載工作流程服務時，會檢查該工作流程定義，並根據在工作流程中找到的傳訊活動集產生合約。</span><span class="sxs-lookup"><span data-stu-id="f695e-109">When a workflow service is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>, the workflow definition is examined and a contract is generated based on the set of messaging activities found in the workflow.</span></span> <span data-ttu-id="f695e-110">特別是，下列活動和屬性會用來產生合約：</span><span class="sxs-lookup"><span data-stu-id="f695e-110">In particular the following activities and properties are used to generate the contract:</span></span>  
  
 <span data-ttu-id="f695e-111"><xref:System.ServiceModel.Activities.Receive> 活動</span><span class="sxs-lookup"><span data-stu-id="f695e-111"><xref:System.ServiceModel.Activities.Receive> Activity</span></span>  
  
-   <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
-   <!--zz <xref:System.ServiceModel.Activities.Receive.OperationContractName%2A>  --> `System.ServiceModel.Activities.Receive.OperationContractName`
  
-   <xref:System.ServiceModel.Activities.Receive.Action%2A>  
  
-   <!--zz <xref:System.ServiceModel.Activities.Receive.ValueType%2A> --> `System.ServiceModel.Activities.Receive.ValueType`
  
 <span data-ttu-id="f695e-112"><xref:System.ServiceModel.Activities.SendReply> 活動</span><span class="sxs-lookup"><span data-stu-id="f695e-112"><xref:System.ServiceModel.Activities.SendReply> Activity</span></span>  
  
-   <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
-   <!--zz <xref:System.ServiceModel.Activities.SendReply.ValueType%2A>-->  `System.ServiceModel.Activities.SendReply.ValueType`
  
 <span data-ttu-id="f695e-113"><xref:System.ServiceModel.Activities.TransactedReceiveScope> 活動</span><span class="sxs-lookup"><span data-stu-id="f695e-113"><xref:System.ServiceModel.Activities.TransactedReceiveScope> Activity</span></span>  
  
 <span data-ttu-id="f695e-114">合約推斷的最終結果是與 WCF 服務和作業合約使用相同資料結構的服務描述。</span><span class="sxs-lookup"><span data-stu-id="f695e-114">The end result of contract inference is a description of the service using the same data structures as WCF service and operation contracts.</span></span> <span data-ttu-id="f695e-115">接著，這項資訊會用來公開工作流程服務的 WSDL。</span><span class="sxs-lookup"><span data-stu-id="f695e-115">This information is then used to expose WSDL for the workflow service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f695e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f695e-116">See Also</span></span>  
 [<span data-ttu-id="f695e-117">工作流程服務</span><span class="sxs-lookup"><span data-stu-id="f695e-117">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="f695e-118">傳訊活動</span><span class="sxs-lookup"><span data-stu-id="f695e-118">Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/messaging-activities.md)  
 [<span data-ttu-id="f695e-119">如何： 使用訊息活動建立工作流程服務</span><span class="sxs-lookup"><span data-stu-id="f695e-119">How to: Create a Workflow Service with Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)  
 [<span data-ttu-id="f695e-120">如何：建立會取用現有服務合約的工作流程服務</span><span class="sxs-lookup"><span data-stu-id="f695e-120">How to: Create a workflow service that consumes an existing service contract</span></span>](../../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)
