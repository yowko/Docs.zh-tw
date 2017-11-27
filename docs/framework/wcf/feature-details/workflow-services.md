---
title: "工作流程服務"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7b05c766-f181-425d-9a3d-2a5e150c85f7
caps.latest.revision: "20"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8eeb446687b2aa75c90ec02995319fc5a0cbebf3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="workflow-services"></a><span data-ttu-id="10682-102">工作流程服務</span><span class="sxs-lookup"><span data-stu-id="10682-102">Workflow Services</span></span>
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="10682-103"> 可讓您在 XAML 中以宣告方式完整描述以工作流程為基礎的服務。</span><span class="sxs-lookup"><span data-stu-id="10682-103"> allows you to fully describe a workflow-based service declaratively in XAML.</span></span> <span data-ttu-id="10682-104">您可以定義實作服務的工作流程並且描述服務所公開的端點，這些作業都可在 XAML 中完成。</span><span class="sxs-lookup"><span data-stu-id="10682-104">You can define a workflow that implements your service and describe endpoints the service exposes, all entirely in XAML.</span></span> <span data-ttu-id="10682-105">本節中的主題會詳細說明，可支援以宣告方式撰寫服務的程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="10682-105">The topics in this section describe, in detail, the programming model that supports writing services declaratively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="10682-106">本章節內容</span><span class="sxs-lookup"><span data-stu-id="10682-106">In This Section</span></span>  
 [<span data-ttu-id="10682-107">工作流程服務概觀</span><span class="sxs-lookup"><span data-stu-id="10682-107">Workflow Services Overview</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services-overview.md)  
 <span data-ttu-id="10682-108">說明建立和裝載工作流程服務相關的元件。</span><span class="sxs-lookup"><span data-stu-id="10682-108">Describes the components involved in creating and hosting a workflow service.</span></span>  
  
 [<span data-ttu-id="10682-109">傳訊活動</span><span class="sxs-lookup"><span data-stu-id="10682-109">Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/messaging-activities.md)  
 <span data-ttu-id="10682-110">討論可讓工作流程傳送和接收訊息的活動。</span><span class="sxs-lookup"><span data-stu-id="10682-110">Discusses activities that allow workflows to send and receive messages.</span></span>  
  
 [<span data-ttu-id="10682-111">如何： 使用訊息活動建立工作流程服務</span><span class="sxs-lookup"><span data-stu-id="10682-111">How to: Create a Workflow Service with Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)  
 <span data-ttu-id="10682-112">說明如何使用訊息活動建立工作流程服務。</span><span class="sxs-lookup"><span data-stu-id="10682-112">Describes how to use messaging activities to create a workflow service.</span></span>  
  
 [<span data-ttu-id="10682-113">如何： 從工作流程應用程式存取服務</span><span class="sxs-lookup"><span data-stu-id="10682-113">How To: Access a Service From a Workflow Application</span></span>](../../../../docs/framework/wcf/feature-details/how-to-access-a-service-from-a-workflow-application.md)  
 <span data-ttu-id="10682-114">討論如何從工作流程應用程式呼叫服務。</span><span class="sxs-lookup"><span data-stu-id="10682-114">Discusses how to call a service from a workflow application.</span></span>  
  
 [<span data-ttu-id="10682-115">相互關聯</span><span class="sxs-lookup"><span data-stu-id="10682-115">Correlation</span></span>](../../../../docs/framework/wcf/feature-details/correlation.md)  
 <span data-ttu-id="10682-116">討論相互關聯如何讓訊息相互對應以及對應至執行個體。</span><span class="sxs-lookup"><span data-stu-id="10682-116">Discusses how correlation maps messages to each other and to instances.</span></span>  
  
 [<span data-ttu-id="10682-117">次序不對的訊息處理</span><span class="sxs-lookup"><span data-stu-id="10682-117">Out-of-Order Message Processing</span></span>](../../../../docs/framework/wcf/feature-details/out-of-order-message-processing.md)  
 <span data-ttu-id="10682-118">說明如何設定服務以接受順序錯誤的訊息。</span><span class="sxs-lookup"><span data-stu-id="10682-118">Describes configuring a service to accept out of order messages.</span></span>  
  
 [<span data-ttu-id="10682-119">如何： 建立呼叫另一個工作流程服務的工作流程服務</span><span class="sxs-lookup"><span data-stu-id="10682-119">How to: Create a Workflow Service That Calls Another Workflow Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-that-calls-another-workflow-service.md)  
 <span data-ttu-id="10682-120">說明如何以同步方式從某個工作流程服務內部呼叫另一個工作流程服務。</span><span class="sxs-lookup"><span data-stu-id="10682-120">Describes how to synchronously call a workflow service from within another workflow service.</span></span>  
  
 [<span data-ttu-id="10682-121">合約優先工作流程服務開發</span><span class="sxs-lookup"><span data-stu-id="10682-121">Contract First Workflow Service Development</span></span>](../../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md)  
 <span data-ttu-id="10682-122">說明依據現有服務合約建立的工作流程服務。</span><span class="sxs-lookup"><span data-stu-id="10682-122">Describes creating a workflow service based on an existing service contract.</span></span>  
  
 [<span data-ttu-id="10682-123">如何：建立會取用現有服務合約的工作流程服務</span><span class="sxs-lookup"><span data-stu-id="10682-123">How to: Create a workflow service that consumes an existing service contract</span></span>](../../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)  
 <span data-ttu-id="10682-124">提供使用現有服務合約建立工作流程服務的逐步範例。</span><span class="sxs-lookup"><span data-stu-id="10682-124">Provides a step-by-step example of creating a workflow service using an existing service contract.</span></span>  
  
 [<span data-ttu-id="10682-125">裝載工作流程服務概觀</span><span class="sxs-lookup"><span data-stu-id="10682-125">Hosting Workflow Services Overview</span></span>](../../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md)  
 <span data-ttu-id="10682-126">說明裝載工作流程服務的不同層面。</span><span class="sxs-lookup"><span data-stu-id="10682-126">Describes the different aspects of hosting a workflow service.</span></span>  
  
 [<span data-ttu-id="10682-127">工作流程中使用合約</span><span class="sxs-lookup"><span data-stu-id="10682-127">Using Contracts in Workflow</span></span>](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md)  
 <span data-ttu-id="10682-128">說明不同型別的合約和合約推斷。</span><span class="sxs-lookup"><span data-stu-id="10682-128">Describes the different types of contracts and contract inference.</span></span>
