---
title: 在工作流程中使用合約
ms.date: 03/30/2017
ms.assetid: 939c64e9-e7cc-4abc-b41e-27cfce1d7e50
ms.openlocfilehash: dd35766011c412acc937eed75d523a0574f6b9cb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150055"
---
# <a name="using-contracts-in-workflow"></a><span data-ttu-id="4182c-102">在工作流程中使用合約</span><span class="sxs-lookup"><span data-stu-id="4182c-102">Using Contracts in Workflow</span></span>
<span data-ttu-id="4182c-103">實作服務時，您會定義許多合約，這些合約會描述服務及服務傳送與接收的資料。</span><span class="sxs-lookup"><span data-stu-id="4182c-103">When implementing a service, you define a number of contracts that describe the service and the data that it sends and receives.</span></span> <span data-ttu-id="4182c-104">資料被以資料合約與訊息合約。WCF 和工作流程服務會使用資料合約和訊息合約定義做為服務描述的一部分。</span><span class="sxs-lookup"><span data-stu-id="4182c-104">The data is represented as data contracts and message contracts; both WCF and workflow services use data contract and message contract definitions as part of service descriptions.</span></span> <span data-ttu-id="4182c-105">服務本身會公開中繼資料 (以 WSDL 的形式) 來描述服務的作業。</span><span class="sxs-lookup"><span data-stu-id="4182c-105">The service itself exposes metadata (in the form of WSDL) in order to describe the operations of the service.</span></span> <span data-ttu-id="4182c-106">在 WCF 中，服務合約和作業合約會定義所支援的服務及作業。</span><span class="sxs-lookup"><span data-stu-id="4182c-106">In WCF, service contracts and operation contracts define the service and the operations it supports.</span></span> <span data-ttu-id="4182c-107">不過，在工作流程服務中，這些合約是商務程序本身的一部分，會由稱為「合約推斷」的處理序在中繼資料中公開。</span><span class="sxs-lookup"><span data-stu-id="4182c-107">However, in a workflow service, these contracts are part of the business process itself; they are exposed in metadata by a process called contract inference.</span></span>  
  
## <a name="contract-inference"></a><span data-ttu-id="4182c-108">合約推斷</span><span class="sxs-lookup"><span data-stu-id="4182c-108">Contract Inference</span></span>  
 <span data-ttu-id="4182c-109">使用 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 裝載工作流程服務時，會檢查該工作流程定義，並根據在工作流程中找到的傳訊活動集產生合約。</span><span class="sxs-lookup"><span data-stu-id="4182c-109">When a workflow service is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>, the workflow definition is examined and a contract is generated based on the set of messaging activities found in the workflow.</span></span> <span data-ttu-id="4182c-110">特別是，下列活動和屬性會用來產生合約：</span><span class="sxs-lookup"><span data-stu-id="4182c-110">In particular the following activities and properties are used to generate the contract:</span></span>  
  
 <xref:System.ServiceModel.Activities.Receive> <span data-ttu-id="4182c-111">活動</span><span class="sxs-lookup"><span data-stu-id="4182c-111">Activity</span></span>  
  
-   <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
-   <xref:System.ServiceModel.Activities.Receive.OperationName%2A>
  
-   <xref:System.ServiceModel.Activities.Receive.Action%2A>   
 
 <xref:System.ServiceModel.Activities.SendReply> <span data-ttu-id="4182c-112">活動</span><span class="sxs-lookup"><span data-stu-id="4182c-112">Activity</span></span>  
  
-   <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope> <span data-ttu-id="4182c-113">活動</span><span class="sxs-lookup"><span data-stu-id="4182c-113">Activity</span></span>  
  
 <span data-ttu-id="4182c-114">合約推斷的最終結果是與 WCF 服務和作業合約使用相同資料結構的服務描述。</span><span class="sxs-lookup"><span data-stu-id="4182c-114">The end result of contract inference is a description of the service using the same data structures as WCF service and operation contracts.</span></span> <span data-ttu-id="4182c-115">接著，這項資訊會用來公開工作流程服務的 WSDL。</span><span class="sxs-lookup"><span data-stu-id="4182c-115">This information is then used to expose WSDL for the workflow service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4182c-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4182c-116">See also</span></span>

- [<span data-ttu-id="4182c-117">工作流程服務</span><span class="sxs-lookup"><span data-stu-id="4182c-117">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="4182c-118">傳訊活動</span><span class="sxs-lookup"><span data-stu-id="4182c-118">Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/messaging-activities.md)
- [<span data-ttu-id="4182c-119">HOW TO：使用傳訊活動建立工作流程服務</span><span class="sxs-lookup"><span data-stu-id="4182c-119">How to: Create a Workflow Service with Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)
- [<span data-ttu-id="4182c-120">HOW TO：建立會取用現有服務合約的工作流程服務</span><span class="sxs-lookup"><span data-stu-id="4182c-120">How to: Create a workflow service that consumes an existing service contract</span></span>](../../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)
