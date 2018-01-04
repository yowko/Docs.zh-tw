---
title: "Windows Workflow Foundation 功能內容"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e84d12da-a055-45f6-b4d1-878d127b46b6
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6943a7eaeaecf8f11de7c10237979067c83c24d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="windows-workflow-foundation-feature-specifics"></a><span data-ttu-id="98e8d-102">Windows Workflow Foundation 功能內容</span><span class="sxs-lookup"><span data-stu-id="98e8d-102">Windows Workflow Foundation Feature Specifics</span></span>
[!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)]<span data-ttu-id="98e8d-103"> 在 Windows Workflow Foundation 中加入一些功能。</span><span class="sxs-lookup"><span data-stu-id="98e8d-103"> adds a number of features to Windows Workflow Foundation.</span></span> <span data-ttu-id="98e8d-104">本文件將描述一些新功能，並且詳細說明適合使用這些功能的案例。</span><span class="sxs-lookup"><span data-stu-id="98e8d-104">This document describes a number of the new features, and gives details about scenarios in which they may be useful.</span></span>  
  
## <a name="messaging-activities"></a><span data-ttu-id="98e8d-105">傳訊活動</span><span class="sxs-lookup"><span data-stu-id="98e8d-105">Messaging Activities</span></span>  
 <span data-ttu-id="98e8d-106">傳訊活動 (<xref:System.ServiceModel.Activities.Receive>， <xref:System.ServiceModel.Activities.SendReply>， <xref:System.ServiceModel.Activities.Send>， <xref:System.ServiceModel.Activities.ReceiveReply>) 用來傳送和接收[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]與工作流程的訊息。</span><span class="sxs-lookup"><span data-stu-id="98e8d-106">The messaging activities (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.ReceiveReply>) are used to send and receive [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] messages from your workflow.</span></span>  <span data-ttu-id="98e8d-107"><xref:System.ServiceModel.Activities.Receive>和<xref:System.ServiceModel.Activities.SendReply>活動是用來表單[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]服務作業是透過 WSDL 公開，就像標準[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]web 服務。</span><span class="sxs-lookup"><span data-stu-id="98e8d-107"><xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply> activities are used to form a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service operation that is exposed via WSDL just like standard [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] web services.</span></span>  <span data-ttu-id="98e8d-108"><xref:System.ServiceModel.Activities.Send>和<xref:System.ServiceModel.Activities.ReceiveReply>用來取用 web 服務與 WCF <xref:System.ServiceModel.ChannelFactory>;**加入服務參考**經驗也有會產生預先設定的活動的 Workflow Foundation。</span><span class="sxs-lookup"><span data-stu-id="98e8d-108"><xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.ReceiveReply> are used to consume a web service similar to a WCF <xref:System.ServiceModel.ChannelFactory>; an **Add Service Reference** experience also exists for Workflow Foundation that generates pre-configured activities.</span></span>  
  
### <a name="getting-started-with-messaging-activities"></a><span data-ttu-id="98e8d-109">傳訊活動使用者入門</span><span class="sxs-lookup"><span data-stu-id="98e8d-109">Getting Started with Messaging Activities</span></span>  
  
-   <span data-ttu-id="98e8d-110">在 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 中，建立 WCF 工作流程服務應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="98e8d-110">In [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], create a WCF Workflow Service Application project.</span></span> <span data-ttu-id="98e8d-111">一組 <xref:System.ServiceModel.Activities.Receive> 和 <xref:System.ServiceModel.Activities.SendReply> 將置於畫布上。</span><span class="sxs-lookup"><span data-stu-id="98e8d-111">A <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply> pair will be placed on your canvas.</span></span>  
  
-   <span data-ttu-id="98e8d-112">以滑鼠右鍵按一下專案，然後選取**加入服務參考**。</span><span class="sxs-lookup"><span data-stu-id="98e8d-112">Right-click on the project and select **Add Service Reference**.</span></span>  <span data-ttu-id="98e8d-113">指向現有的 web 服務 WSDL，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="98e8d-113">Point to an existing web service WSDL and click **OK**.</span></span>  <span data-ttu-id="98e8d-114">建置專案，以顯示所產生的活動 (使用實作<xref:System.ServiceModel.Activities.Send>和<xref:System.ServiceModel.Activities.ReceiveReply>) 在工具箱中。</span><span class="sxs-lookup"><span data-stu-id="98e8d-114">Build your project to show the generated activities (implemented using <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.ReceiveReply>) in your toolbox.</span></span>  
  
-   <span data-ttu-id="98e8d-115">您可以在下列章節中找到這些活動的範例：</span><span class="sxs-lookup"><span data-stu-id="98e8d-115">Samples for these activities can be found in the following sections:</span></span>  
  
    -   <span data-ttu-id="98e8d-116">Basic:[服務](../../../docs/framework/windows-workflow-foundation/samples/services.md)</span><span class="sxs-lookup"><span data-stu-id="98e8d-116">Basic: [Services](../../../docs/framework/windows-workflow-foundation/samples/services.md)</span></span>  
  
    -   <span data-ttu-id="98e8d-117">案例：[服務](../../../docs/framework/windows-workflow-foundation/samples/services.md)</span><span class="sxs-lookup"><span data-stu-id="98e8d-117">Scenarios: [Services](../../../docs/framework/windows-workflow-foundation/samples/services.md)</span></span>  
  
-   [<span data-ttu-id="98e8d-118">概念文件</span><span class="sxs-lookup"><span data-stu-id="98e8d-118">Conceptual documentation</span></span>](http://go.microsoft.com/fwlink/?LinkId=204801)  
  
-   [<span data-ttu-id="98e8d-119">傳訊活動設計工具文件</span><span class="sxs-lookup"><span data-stu-id="98e8d-119">Messaging activities designer documentation</span></span>](http://go.microsoft.com/fwlink/?LinkId=204802)  
  
### <a name="messaging-activities-example-scenario"></a><span data-ttu-id="98e8d-120">傳訊活動範例案例</span><span class="sxs-lookup"><span data-stu-id="98e8d-120">Messaging Activities Example Scenario</span></span>  
 <span data-ttu-id="98e8d-121">A`BestPriceFinder`服務呼叫以尋找最佳的票證價格特定路由的多個 airline 服務。</span><span class="sxs-lookup"><span data-stu-id="98e8d-121">A `BestPriceFinder` service calls out to multiple airline services to find the best ticket price for a particular route.</span></span>  <span data-ttu-id="98e8d-122">實作此案例會要求您使用訊息活動來接收價格要求、 擷取後端服務的價格和價格的價格要求回覆。</span><span class="sxs-lookup"><span data-stu-id="98e8d-122">Implementing this scenario would require you to use the message activities to receive the price request, retrieve the prices from the back-end services, and reply to the price request with the best price.</span></span>  <span data-ttu-id="98e8d-123">它也會要求您使用其他現成的活動，以建立計算最佳的價格的商務邏輯。</span><span class="sxs-lookup"><span data-stu-id="98e8d-123">It would also require you to use other out-of-box activities to create the business logic for calculating the best price.</span></span>  
  
## <a name="workflowservicehost"></a><span data-ttu-id="98e8d-124">WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="98e8d-124">WorkflowServiceHost</span></span>  
 <span data-ttu-id="98e8d-125"><xref:System.ServiceModel.WorkflowServiceHost>支援多個執行個體，預設的工作流程主機組態和[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]傳訊 （雖然工作流程不需要使用訊息，就能夠裝載）。</span><span class="sxs-lookup"><span data-stu-id="98e8d-125">The <xref:System.ServiceModel.WorkflowServiceHost> is the out-of-box workflow host that supports multiple instances, configuration, and [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] messaging (although the workflows aren’t required to use messaging in order to be hosted).</span></span>  <span data-ttu-id="98e8d-126">此外，它也會透過一組服務行為，與持續性、追蹤和執行個體控制項整合。</span><span class="sxs-lookup"><span data-stu-id="98e8d-126">It also integrates with persistence, tracking, and instance control through a set of service behaviors.</span></span>  <span data-ttu-id="98e8d-127">就像[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]的<xref:System.ServiceModel.ServiceHost>、<xref:System.ServiceModel.WorkflowServiceHost>可以自行裝載於主控台/WinForms/WPF 應用程式或 Windows 服務或 web 裝載 （成為.xamlx 檔案） 在 IIS 或 WAS。</span><span class="sxs-lookup"><span data-stu-id="98e8d-127">Just like [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]’s <xref:System.ServiceModel.ServiceHost>, the <xref:System.ServiceModel.WorkflowServiceHost> can be self-hosted in a console/WinForms/WPF application or Windows service, or web-hosted (as a .xamlx file) in IIS or WAS.</span></span>  
  
### <a name="getting-started-with-workflow-service-host"></a><span data-ttu-id="98e8d-128">工作流程服務主機使用者入門</span><span class="sxs-lookup"><span data-stu-id="98e8d-128">Getting Started with Workflow Service Host</span></span>  
  
-   <span data-ttu-id="98e8d-129">在 Visual Studio 2010 中，建立 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 工作流程服務應用程式專案：這個專案將設定為使用 Web 主機環境中的 <xref:System.ServiceModel.WorkflowServiceHost>。</span><span class="sxs-lookup"><span data-stu-id="98e8d-129">In Visual Studio 2010, create a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Workflow Service Application project: this project will be set up to use <xref:System.ServiceModel.WorkflowServiceHost> in a web-host environment.</span></span>  
  
-   <span data-ttu-id="98e8d-130">若要裝載非傳訊工作流程，請加入會根據訊息建立執行個體的自訂 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>。</span><span class="sxs-lookup"><span data-stu-id="98e8d-130">In order to host a non-messaging workflow, add a custom <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> that will create the instance based on a message.</span></span>  
  
-   <span data-ttu-id="98e8d-131">您可以將 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> 加入至 <xref:System.ServiceModel.WorkflowServiceHost>，然後使用 <xref:System.ServiceModel.Activities.WorkflowControlClient>，藉以控制工作流程執行個體 (例如暫停或終止)。</span><span class="sxs-lookup"><span data-stu-id="98e8d-131">Workflow instances can be controlled (e.g. suspended or terminated) by adding a <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> to the <xref:System.ServiceModel.WorkflowServiceHost> and then using a <xref:System.ServiceModel.Activities.WorkflowControlClient>.</span></span>  
  
-   <span data-ttu-id="98e8d-132">您可以在下列章節中找到 <xref:System.ServiceModel.WorkflowServiceHost> 的範例：</span><span class="sxs-lookup"><span data-stu-id="98e8d-132">Samples for the <xref:System.ServiceModel.WorkflowServiceHost> can be found in the following sections:</span></span>  
  
    -   [<span data-ttu-id="98e8d-133">執行</span><span class="sxs-lookup"><span data-stu-id="98e8d-133">Execution</span></span>](../../../docs/framework/windows-workflow-foundation/samples/execution.md)  
  
    -   <span data-ttu-id="98e8d-134">Basic:[服務](../../../docs/framework/windows-workflow-foundation/samples/services.md)</span><span class="sxs-lookup"><span data-stu-id="98e8d-134">Basic: [Services](../../../docs/framework/windows-workflow-foundation/samples/services.md)</span></span>  
  
    -   <span data-ttu-id="98e8d-135">案例：[服務](../../../docs/framework/windows-workflow-foundation/samples/services.md)</span><span class="sxs-lookup"><span data-stu-id="98e8d-135">Scenarios: [Services](../../../docs/framework/windows-workflow-foundation/samples/services.md)</span></span>  
  
    -   <span data-ttu-id="98e8d-136">應用程式：[暫止執行個體管理](../../../docs/framework/windows-workflow-foundation/samples/suspended-instance-management.md)</span><span class="sxs-lookup"><span data-stu-id="98e8d-136">Application: [Suspended Instance Management](../../../docs/framework/windows-workflow-foundation/samples/suspended-instance-management.md)</span></span>  
  
-   [<span data-ttu-id="98e8d-137">WorkflowServiceHost 概念文件</span><span class="sxs-lookup"><span data-stu-id="98e8d-137">WorkflowServiceHost Conceptual Documentation</span></span>](http://go.microsoft.com/fwlink/?LinkId=204807)  
  
### <a name="workflowservicehost-scenario"></a><span data-ttu-id="98e8d-138">WorkflowServiceHost 案例</span><span class="sxs-lookup"><span data-stu-id="98e8d-138">WorkflowServiceHost Scenario</span></span>  
 <span data-ttu-id="98e8d-139">BestPriceFinder 服務呼叫以尋找最佳的票證價格特定路由的多個 airline 服務。</span><span class="sxs-lookup"><span data-stu-id="98e8d-139">A BestPriceFinder service calls out to multiple airline services to find the best ticket price for a particular route.</span></span>  <span data-ttu-id="98e8d-140">實作此案例會需要您裝載中的工作流程<xref:System.ServiceModel.WorkflowServiceHost>。</span><span class="sxs-lookup"><span data-stu-id="98e8d-140">Implementing this scenario would require you to host the workflow in <xref:System.ServiceModel.WorkflowServiceHost>.</span></span>  <span data-ttu-id="98e8d-141">它也會使用訊息活動來接收價格要求、 擷取後端服務的價格和價格的價格要求回覆。</span><span class="sxs-lookup"><span data-stu-id="98e8d-141">It would also use the message activities to receive the price request, retrieve the prices from the back-end services, and reply to the price request with the best price.</span></span>  
  
## <a name="correlation"></a><span data-ttu-id="98e8d-142">相互關聯</span><span class="sxs-lookup"><span data-stu-id="98e8d-142">Correlation</span></span>  
 <span data-ttu-id="98e8d-143">相互關聯是指下列其中一種情況：</span><span class="sxs-lookup"><span data-stu-id="98e8d-143">A correlation is one of two things:</span></span>  
  
-   <span data-ttu-id="98e8d-144">群組訊息的方式。亦即，要求訊息與其回覆之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="98e8d-144">A way of grouping messages together; that is, the relationship between a request message and its reply.</span></span>  
  
-   <span data-ttu-id="98e8d-145">將資料片段對應至服務執行個體的方式。</span><span class="sxs-lookup"><span data-stu-id="98e8d-145">A way of mapping a piece of data to a service instance</span></span>  
  
### <a name="getting-started"></a><span data-ttu-id="98e8d-146">快速入門</span><span class="sxs-lookup"><span data-stu-id="98e8d-146">Getting Started</span></span>  
  
-   <span data-ttu-id="98e8d-147">若要開始使用相互關聯，請在 Visual Studio 中建立新的專案。</span><span class="sxs-lookup"><span data-stu-id="98e8d-147">To get started with correlation, create a new project in Visual Studio.</span></span> <span data-ttu-id="98e8d-148">建立型別為 <xref:System.ServiceModel.Activities.CorrelationHandle> 的變數。</span><span class="sxs-lookup"><span data-stu-id="98e8d-148">Create a variable of type <xref:System.ServiceModel.Activities.CorrelationHandle>.</span></span>  
  
-   <span data-ttu-id="98e8d-149">用來將訊息群組在一起之相互關聯的範例就是，將訊息群組在一起的要求-回覆相互關聯。</span><span class="sxs-lookup"><span data-stu-id="98e8d-149">An example of correlation used to group messages together is a Request-Reply correlation that groups messages together.</span></span>  
  
    -   <span data-ttu-id="98e8d-150">在<xref:System.ServiceModel.Activities.Receive>活動，請按一下 <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A>屬性並新增<xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>使用 CorrelationHandle 在上述第一個步驟中建立。</span><span class="sxs-lookup"><span data-stu-id="98e8d-150">On a <xref:System.ServiceModel.Activities.Receive> activity, click on the <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> property and add a <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> using the CorrelationHandle created in the first step above.</span></span>  
  
    -   <span data-ttu-id="98e8d-151">建立<xref:System.ServiceModel.Activities.SendReply>活動，以滑鼠右鍵按一下<xref:System.ServiceModel.Activities.Receive>，然後按一下 [建立 SendReply]。</span><span class="sxs-lookup"><span data-stu-id="98e8d-151">Create a <xref:System.ServiceModel.Activities.SendReply> activity by right-clicking on the <xref:System.ServiceModel.Activities.Receive> and clicking "Create SendReply".</span></span> <span data-ttu-id="98e8d-152">接著，將它貼入工作流程中 <xref:System.ServiceModel.Activities.Receive> 活動的後面。</span><span class="sxs-lookup"><span data-stu-id="98e8d-152">Paste it into your workflow after the <xref:System.ServiceModel.Activities.Receive> activity.</span></span>  
  
-   <span data-ttu-id="98e8d-153">將資料片段對應至服務執行個體的範例就是內容架構的相互關聯，它會將資料片段 (例如訂單 ID) 對應至特定工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="98e8d-153">An example of mapping a piece of data to a service instance is content-based correlation which maps a piece of data (for example, an order ID) to a particular workflow instance.</span></span>  
  
    -   <span data-ttu-id="98e8d-154">在任何傳訊活動上，按一下 `CorrelationInitializers` 屬性，然後使用您在上述步驟中建立的 <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> 變數來加入 <xref:System.ServiceModel.Activities.CorrelationHandle>。</span><span class="sxs-lookup"><span data-stu-id="98e8d-154">On any messaging activity, click on the `CorrelationInitializers` property and add a <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> using the <xref:System.ServiceModel.Activities.CorrelationHandle> variable created above.</span></span> <span data-ttu-id="98e8d-155">在下拉式功能表中，按兩下所需的訊息屬性 (例如 OrderID)。</span><span class="sxs-lookup"><span data-stu-id="98e8d-155">Double-click on the desired property on the message (e.g. OrderID) from the drop-down menu.</span></span> <span data-ttu-id="98e8d-156">接著，將 `CorrelatesWith` 屬性設定為上述使用的 <xref:System.ServiceModel.Activities.CorrelationHandle> 變數。</span><span class="sxs-lookup"><span data-stu-id="98e8d-156">Set the `CorrelatesWith` property to the <xref:System.ServiceModel.Activities.CorrelationHandle> variable used above.</span></span>  
  
-   <span data-ttu-id="98e8d-157">範例：</span><span class="sxs-lookup"><span data-stu-id="98e8d-157">Samples:</span></span>  
  
    -   <span data-ttu-id="98e8d-158">Basic:[服務](../../../docs/framework/windows-workflow-foundation/samples/services.md)</span><span class="sxs-lookup"><span data-stu-id="98e8d-158">Basic: [Services](../../../docs/framework/windows-workflow-foundation/samples/services.md)</span></span>  
  
    -   <span data-ttu-id="98e8d-159">案例：[服務](../../../docs/framework/windows-workflow-foundation/samples/services.md)</span><span class="sxs-lookup"><span data-stu-id="98e8d-159">Scenarios: [Services](../../../docs/framework/windows-workflow-foundation/samples/services.md)</span></span>  
  
    -   [<span data-ttu-id="98e8d-160">相互關聯概念文件</span><span class="sxs-lookup"><span data-stu-id="98e8d-160">Correlation Conceptual Documentation</span></span>](http://go.microsoft.com/fwlink/?LinkId=204939)  
  
### <a name="correlation-scenario"></a><span data-ttu-id="98e8d-161">相互關聯案例</span><span class="sxs-lookup"><span data-stu-id="98e8d-161">Correlation Scenario</span></span>  
 <span data-ttu-id="98e8d-162">訂單處理工作流程用來處理新的順序建立及更新程序中之現有訂單。</span><span class="sxs-lookup"><span data-stu-id="98e8d-162">An order-processing workflow is used to handle new order creation and updating existing orders that are in process.</span></span>  <span data-ttu-id="98e8d-163">實作此案例會需要您裝載中的工作流程<xref:System.ServiceModel.WorkflowServiceHost>和使用訊息活動。</span><span class="sxs-lookup"><span data-stu-id="98e8d-163">Implementing this scenario would require you to host the workflow in <xref:System.ServiceModel.WorkflowServiceHost> and use the messaging activities.</span></span>  <span data-ttu-id="98e8d-164">它也會需要為基礎的相互關聯`orderId`以確保正確的工作流程進行更新。</span><span class="sxs-lookup"><span data-stu-id="98e8d-164">It would also require correlation based on the `orderId` to ensure that updates are made to the correct workflow.</span></span>  
  
## <a name="simplified-configuration"></a><span data-ttu-id="98e8d-165">簡化的組態</span><span class="sxs-lookup"><span data-stu-id="98e8d-165">Simplified Configuration</span></span>  
 <span data-ttu-id="98e8d-166">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 組態結構描述很複雜，而且為使用者提供了許多難以找到的功能。</span><span class="sxs-lookup"><span data-stu-id="98e8d-166">The [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] configuration schema is complex and provides users with many hard to find features.</span></span> <span data-ttu-id="98e8d-167">在 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 中，我們已經著重於協助 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 使用者使用下列功能來設定其服務：</span><span class="sxs-lookup"><span data-stu-id="98e8d-167">In [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], we have focused on helping [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] users configure their services with the following features:</span></span>  
  
-   <span data-ttu-id="98e8d-168">移除每項服務明確組態的需求。</span><span class="sxs-lookup"><span data-stu-id="98e8d-168">Removing the need for explicit per-service configuration.</span></span> <span data-ttu-id="98e8d-169">如果您未設定任何\<服務 > 項目，為您的服務，而且您的服務不會定義任何端點以程式設計的方式，則一組端點將會自動加入至您的服務，其中每個服務基底位址和每個合約實作您的服務。</span><span class="sxs-lookup"><span data-stu-id="98e8d-169">If you do not configure any \<service> elements for your service, and your service does not define programmatically any endpoint, then a set of endpoints will be automatically added to your service, one per service base address and per contract implemented by your service.</span></span>  
  
-   <span data-ttu-id="98e8d-170">讓使用者定義 WCF 繫結和行為的預設值，以便套用至沒有明確組態的服務。</span><span class="sxs-lookup"><span data-stu-id="98e8d-170">Enables the user to define default values for WCF bindings and behaviors, which will be applied to services with no explicit configuration.</span></span>  
  
-   <span data-ttu-id="98e8d-171">標準端點會定義可重複使用的預先設定端點，其中一個或多個端點屬性 (位址、繫結和合約) 具有固定的值，而且允許定義自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="98e8d-171">Standard endpoints define reusable preconfigured endpoints, which have fixed values for one or more of the endpoint properties (address, binding and contract), and allow defining custom properties.</span></span>  
  
-   <span data-ttu-id="98e8d-172">最後，<xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> 可讓您集中管理 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端組態，這在應用程式定義域載入時間之後選取或變更組態的案例中很有用。</span><span class="sxs-lookup"><span data-stu-id="98e8d-172">Finally, the <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> allows you to do central management of [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client configuration, useful in scenarios in which configuration is selected or changed after the application domain load time.</span></span>  
  
### <a name="getting-started"></a><span data-ttu-id="98e8d-173">快速入門</span><span class="sxs-lookup"><span data-stu-id="98e8d-173">Getting Started</span></span>  
  
-   [<span data-ttu-id="98e8d-174">Wcf 4.0 開發人員指南</span><span class="sxs-lookup"><span data-stu-id="98e8d-174">A Developer's Guide to WCF 4.0</span></span>](http://go.microsoft.com/fwlink/?LinkId=204940)  
  
-   [<span data-ttu-id="98e8d-175">組態通道處理站</span><span class="sxs-lookup"><span data-stu-id="98e8d-175">Configuration Channel Factory</span></span>](http://go.microsoft.com/fwlink/?LinkId=204941)  
  
-   [<span data-ttu-id="98e8d-176">標準端點項目</span><span class="sxs-lookup"><span data-stu-id="98e8d-176">Standard Endpoint Element</span></span>](http://go.microsoft.com/fwlink/?LinkId=204942)  
  
-   [<span data-ttu-id="98e8d-177">服務組態改良在.Net Framework 4</span><span class="sxs-lookup"><span data-stu-id="98e8d-177">Service configuration improvements in .Net Framework 4</span></span>](http://go.microsoft.com/fwlink/?LinkId=204943)  
  
-   [<span data-ttu-id="98e8d-178">.NET 4 中的常見使用者錯誤： //go.microsoft.com/fwlink/？ Linkid WF/WCF 服務組態名稱</span><span class="sxs-lookup"><span data-stu-id="98e8d-178">Common User Mistake in .NET 4: Mistyping the WF/WCF Service Configuration Name</span></span>](http://go.microsoft.com/fwlink/?LinkId=204944)  
  
### <a name="simplified-configuration-scenarios"></a><span data-ttu-id="98e8d-179">簡化的組態案例</span><span class="sxs-lookup"><span data-stu-id="98e8d-179">Simplified Configuration Scenarios</span></span>  
  
-   <span data-ttu-id="98e8d-180">有經驗的 ASMX 開發人員想要開始使用 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="98e8d-180">An experienced ASMX developer wants to start using [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="98e8d-181">不過，[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 看起來太複雜！</span><span class="sxs-lookup"><span data-stu-id="98e8d-181">However, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] seems way too complicated!</span></span> <span data-ttu-id="98e8d-182">我需要在組態檔中寫入哪些資訊？</span><span class="sxs-lookup"><span data-stu-id="98e8d-182">What is all that information that I need to write in a configuration file?</span></span> <span data-ttu-id="98e8d-183">在 .NET 4 中，您甚至可以決定完全不使用組態檔。</span><span class="sxs-lookup"><span data-stu-id="98e8d-183">In .NET 4, you can even decide to not have a configuration file at all.</span></span>  
  
-   <span data-ttu-id="98e8d-184">現有的 WCF 服務集非常難以設定和維護。</span><span class="sxs-lookup"><span data-stu-id="98e8d-184">An existing set of WCF services are very difficult to configure and maintain.</span></span> <span data-ttu-id="98e8d-185">組態檔具有數千行 XML 程式碼，任意修改可能會非常危險。</span><span class="sxs-lookup"><span data-stu-id="98e8d-185">The configuration file has thousands of lines of XML code that are extremely dangerous to touch.</span></span> <span data-ttu-id="98e8d-186">因此需要相關協助，以便將程式碼數量減少至較容易管理的數量。</span><span class="sxs-lookup"><span data-stu-id="98e8d-186">Help is needed to reduce that amount of code to something more manageable.</span></span>  
  
## <a name="data-contract-resolver"></a><span data-ttu-id="98e8d-187">資料合約解析程式</span><span class="sxs-lookup"><span data-stu-id="98e8d-187">Data Contract Resolver</span></span>  
 <span data-ttu-id="98e8d-188">在 .NET 3.5 中，已知型別的設計具有一些限制：</span><span class="sxs-lookup"><span data-stu-id="98e8d-188">In .NET 3.5, there were a few limitations in the design of known types:</span></span>  
  
-   <span data-ttu-id="98e8d-189">您無法在序列化或還原序列化期間，以動態方式加入已知型別。</span><span class="sxs-lookup"><span data-stu-id="98e8d-189">Adding known types dynamically, during serialization or deserialization, was not possible.</span></span>  
  
-   <span data-ttu-id="98e8d-190">序列化程式無法處理不明的 xsi:type 資訊。</span><span class="sxs-lookup"><span data-stu-id="98e8d-190">Serializers could not deal with unknown xsi:type information.</span></span>  
  
-   <span data-ttu-id="98e8d-191">使用者無法指定想要顯示在 Wire 上的 xsi:type，以便降低 Wire 上序列化執行個體的大小。</span><span class="sxs-lookup"><span data-stu-id="98e8d-191">It was not possible for users to specify what xsi:type they would like to have appear on the wire to, for instance, make the size of a serialization instance on the wire smaller.</span></span>  
  
 <span data-ttu-id="98e8d-192">[DataContractResolver](../../../docs/framework/wcf/samples/datacontractresolver.md)解決這些問題，在.NET 4.5。</span><span class="sxs-lookup"><span data-stu-id="98e8d-192">The [DataContractResolver](../../../docs/framework/wcf/samples/datacontractresolver.md) solves these issues in .NET 4.5.</span></span>  
  
### <a name="getting-started"></a><span data-ttu-id="98e8d-193">快速入門</span><span class="sxs-lookup"><span data-stu-id="98e8d-193">Getting Started</span></span>  
  
-   [<span data-ttu-id="98e8d-194">資料合約解析程式 API 文件</span><span class="sxs-lookup"><span data-stu-id="98e8d-194">Data Contract Resolver API documentation</span></span>](http://go.microsoft.com/fwlink/?LinkId=204946)  
  
-   [<span data-ttu-id="98e8d-195">導入的資料合約解析程式</span><span class="sxs-lookup"><span data-stu-id="98e8d-195">Introducing the Data Contract Resolver</span></span>](http://go.microsoft.com/fwlink/?LinkId=204947)  
  
-   <span data-ttu-id="98e8d-196">範例：</span><span class="sxs-lookup"><span data-stu-id="98e8d-196">Samples:</span></span>  
  
    -   [<span data-ttu-id="98e8d-197">DataContractResolver</span><span class="sxs-lookup"><span data-stu-id="98e8d-197">DataContractResolver</span></span>](../../../docs/framework/wcf/samples/datacontractresolver.md)  
  
    -   [<span data-ttu-id="98e8d-198">KnownAssemblyAttribute</span><span class="sxs-lookup"><span data-stu-id="98e8d-198">KnownAssemblyAttribute</span></span>](../../../docs/framework/wcf/samples/knownassemblyattribute.md)  
  
### <a name="data-contract-resolver-scenarios"></a><span data-ttu-id="98e8d-199">資料合約解析程式案例</span><span class="sxs-lookup"><span data-stu-id="98e8d-199">Data Contract Resolver Scenarios</span></span>  
  
-   <span data-ttu-id="98e8d-200">避免在服務中宣告數十個 <xref:System.Runtime.Serialization.KnownTypeAttribute> 物件。</span><span class="sxs-lookup"><span data-stu-id="98e8d-200">Avoiding having to declare tens of <xref:System.Runtime.Serialization.KnownTypeAttribute> objects in a service.</span></span>  
  
-   <span data-ttu-id="98e8d-201">減少 XML BLOB 的大小。</span><span class="sxs-lookup"><span data-stu-id="98e8d-201">Reducing the size of the XML blob.</span></span>  
  
## <a name="flowchart"></a><span data-ttu-id="98e8d-202">流程圖</span><span class="sxs-lookup"><span data-stu-id="98e8d-202">Flowchart</span></span>  
 <span data-ttu-id="98e8d-203">流程圖是已知的開發架構，可以視覺化方式表示網域問題。</span><span class="sxs-lookup"><span data-stu-id="98e8d-203">Flowchart is a well-known paradigm to visually represent domain problems.</span></span> <span data-ttu-id="98e8d-204">它是我們在 .NET 4 中導入的新控制流程樣式。</span><span class="sxs-lookup"><span data-stu-id="98e8d-204">It is a new control flow style we’re introducing in .NET 4.</span></span> <span data-ttu-id="98e8d-205">流程圖的核心特性在於，一次只能執行一項活動。</span><span class="sxs-lookup"><span data-stu-id="98e8d-205">A core characteristic of Flowchart is that only one activity is executed at any given time.</span></span> <span data-ttu-id="98e8d-206">流程圖可以表達迴圈和替代的結果，但本身無法表示同時執行的多個節點。</span><span class="sxs-lookup"><span data-stu-id="98e8d-206">Flowcharts can express loops and alternative outcomes, but cannot natively express concurrent execution of multiple nodes.</span></span>  
  
### <a name="getting-started"></a><span data-ttu-id="98e8d-207">快速入門</span><span class="sxs-lookup"><span data-stu-id="98e8d-207">Getting Started</span></span>  
  
-   <span data-ttu-id="98e8d-208">在 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 中，建立工作流程主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="98e8d-208">In [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], create a workflow console application.</span></span> <span data-ttu-id="98e8d-209">在工作流程設計工具中加入流程圖。</span><span class="sxs-lookup"><span data-stu-id="98e8d-209">Add a Flowchart in the workflow designer.</span></span>  
  
-   <span data-ttu-id="98e8d-210">流程圖功能會使用下列類別：</span><span class="sxs-lookup"><span data-stu-id="98e8d-210">The flowchart feature uses the following classes:</span></span>  
  
    -   <xref:System.Activities.Statements.Flowchart>  
  
    -   <xref:System.Activities.Statements.FlowNode>  
  
    -   <xref:System.Activities.Statements.FlowDecision>  
  
    -   <xref:System.Activities.Statements.FlowStep>  
  
    -   <xref:System.Activities.Statements.FlowSwitch%601>  
  
-   <span data-ttu-id="98e8d-211">範例：</span><span class="sxs-lookup"><span data-stu-id="98e8d-211">Samples:</span></span>  
  
    -   [<span data-ttu-id="98e8d-212">使用 TryCatch 錯誤處理流程圖活動</span><span class="sxs-lookup"><span data-stu-id="98e8d-212">Fault Handling in a Flowchart Activity Using TryCatch</span></span>](../../../docs/framework/windows-workflow-foundation/samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)  
  
    -   [<span data-ttu-id="98e8d-213">使用 FlowChart 及 Pick 組合的 StateMachine 案例</span><span class="sxs-lookup"><span data-stu-id="98e8d-213">StateMachine Scenario Using a Combination of FlowChart and Pick</span></span>](../../../docs/framework/windows-workflow-foundation/samples/statemachine-scenario-using-a-combination-of-flowchart-and-pick.md)  
  
    -   [<span data-ttu-id="98e8d-214">招聘程序</span><span class="sxs-lookup"><span data-stu-id="98e8d-214">Hiring Process</span></span>](../../../docs/framework/windows-workflow-foundation/samples/hiring-process.md)  
  
-   <span data-ttu-id="98e8d-215">設計工具文件：</span><span class="sxs-lookup"><span data-stu-id="98e8d-215">Designer Documentation:</span></span>  
  
    -   [<span data-ttu-id="98e8d-216">Flowchart 活動設計工具</span><span class="sxs-lookup"><span data-stu-id="98e8d-216">Flowchart Activity Designers</span></span>](/visualstudio/workflow-designer/flowchart-activity-designers)  
  
### <a name="flowchart-scenarios"></a><span data-ttu-id="98e8d-217">流程圖案例</span><span class="sxs-lookup"><span data-stu-id="98e8d-217">Flowchart Scenarios</span></span>  
 <span data-ttu-id="98e8d-218">流程圖活動可用來實作猜測遊戲。</span><span class="sxs-lookup"><span data-stu-id="98e8d-218">A flowchart activity can be used to implement a guessing game.</span></span> <span data-ttu-id="98e8d-219">猜測遊戲非常簡單：電腦會選取一個隨機數字，而玩家必須猜測該數字。</span><span class="sxs-lookup"><span data-stu-id="98e8d-219">The guessing game is very simple: the computer selects a random number and the player has to guess that number.</span></span> <span data-ttu-id="98e8d-220">當玩家送出每項猜測時，電腦會顯示一個提示 （也就是 「 再一次低的數字 」）。</span><span class="sxs-lookup"><span data-stu-id="98e8d-220">When the player submits each guess, the computer shows him a hint (i.e. "try a lower number").</span></span> <span data-ttu-id="98e8d-221">如果玩家在 7 次內猜到數字，電腦會對使用者顯示特別的恭賀畫面。</span><span class="sxs-lookup"><span data-stu-id="98e8d-221">If the player finds the number in less than 7 attempts, he receives a special congratulation from the computer.</span></span> <span data-ttu-id="98e8d-222">您可以透過組合下列程序性活動來實作此遊戲：</span><span class="sxs-lookup"><span data-stu-id="98e8d-222">This game can be implemented with a combination of the following procedural activities:</span></span>  
  
-   <xref:System.Activities.Statements.Sequence>  
  
-   <xref:System.Activities.Statements.While>  
  
-   <xref:System.Activities.Statements.Switch%601>  
  
-   <xref:System.Activities.Statements.TryCatch>  
  
-   <xref:System.Activities.Statements.Assign%601>  
  
-   <xref:System.Activities.Statements.If>  
  
## <a name="procedural-activities-sequence-if-foreach-switch-assign-dowhile-while"></a><span data-ttu-id="98e8d-223">程序性活動 (Sequence、If、ForEach、Switch、Assign、DoWhile 和 While)</span><span class="sxs-lookup"><span data-stu-id="98e8d-223">Procedural activities (Sequence, If, ForEach, Switch, Assign, DoWhile, While)</span></span>  
 <span data-ttu-id="98e8d-224">程序性活動會使用程式設計人員所熟悉的概念來提供模型循序控制流程的機制。</span><span class="sxs-lookup"><span data-stu-id="98e8d-224">Procedural activities provide a mechanism to model sequential control flow using concepts that are familiar to programmers.</span></span> <span data-ttu-id="98e8d-225">這些活動會啟用傳統結構的程式語言建構，並且在適當的情況下，提供一般程序性語言 (例如 C#/VB) 的語言同位項目。</span><span class="sxs-lookup"><span data-stu-id="98e8d-225">These activities enable traditionally structured programming language constructs and, when appropriate, provide language parity with common procedural languages such as C#/VB.</span></span>  
  
### <a name="getting-started"></a><span data-ttu-id="98e8d-226">快速入門</span><span class="sxs-lookup"><span data-stu-id="98e8d-226">Getting Started</span></span>  
  
-   <span data-ttu-id="98e8d-227">在 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 中，建立工作流程主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="98e8d-227">In [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], create a workflow console application.</span></span> <span data-ttu-id="98e8d-228">在工作流程設計工具中加入程序性活動。</span><span class="sxs-lookup"><span data-stu-id="98e8d-228">Add procedural activities in the workflow designer.</span></span>  
  
-   <span data-ttu-id="98e8d-229">範例：</span><span class="sxs-lookup"><span data-stu-id="98e8d-229">Samples:</span></span>  
  
    -   [<span data-ttu-id="98e8d-230">招聘程序</span><span class="sxs-lookup"><span data-stu-id="98e8d-230">Hiring Process</span></span>](../../../docs/framework/windows-workflow-foundation/samples/hiring-process.md)  
  
    -   [<span data-ttu-id="98e8d-231">公司購買程序</span><span class="sxs-lookup"><span data-stu-id="98e8d-231">Corporate Purchase Process</span></span>](../../../docs/framework/windows-workflow-foundation/samples/corporate-purchase-process.md)  
  
-   <span data-ttu-id="98e8d-232">設計工具文件：</span><span class="sxs-lookup"><span data-stu-id="98e8d-232">Designer Documentation:</span></span>  
  
    -   [<span data-ttu-id="98e8d-233">Parallel 活動設計工具</span><span class="sxs-lookup"><span data-stu-id="98e8d-233">Parallel Activity Designer</span></span>](/visualstudio/workflow-designer/parallel-activity-designer)  
  
    -   [<span data-ttu-id="98e8d-234">ParallelForEach\<T > 活動設計工具</span><span class="sxs-lookup"><span data-stu-id="98e8d-234">ParallelForEach\<T> Activity Designer</span></span>](/visualstudio/workflow-designer/parallelforeach-t-activity-designer)  
  
### <a name="procedural-activity-scenarios"></a><span data-ttu-id="98e8d-235">程序性活動案例</span><span class="sxs-lookup"><span data-stu-id="98e8d-235">Procedural Activity Scenarios</span></span>  
  
-   <span data-ttu-id="98e8d-236"><xref:System.Activities.Statements.Parallel>： 這是內部網路文件管理系統具有文件核准工作流程。</span><span class="sxs-lookup"><span data-stu-id="98e8d-236"><xref:System.Activities.Statements.Parallel>: An intranet document management system has a document approval workflow.</span></span> <span data-ttu-id="98e8d-237">文件必須先由數個部門的人員核准，然後才能發行至內部網路。</span><span class="sxs-lookup"><span data-stu-id="98e8d-237">Documents need to be approved by people in several departments before they can be published to the intranet.</span></span> <span data-ttu-id="98e8d-238">沒有建立的訂單的核准。文件處於 「 待核准 」 階段時前, 可能發生在任何時間。</span><span class="sxs-lookup"><span data-stu-id="98e8d-238">There isn’t an established order for the approvals; they can occur at any time while the document is in the "approval pending" phase.</span></span> <span data-ttu-id="98e8d-239">當使用者送出文件以供檢閱時，其直屬經理、內部網路管理員和內部通訊經理就必須核准該份文件。</span><span class="sxs-lookup"><span data-stu-id="98e8d-239">When a user submits a document for review it must be approved by her direct manager, the intranet administrator, and the internal communications manager.</span></span>  
  
-   <span data-ttu-id="98e8d-240"><xref:System.Activities.Statements.ParallelForEach%601>：WF 應用程式可管理大型公司內部的企業採購。</span><span class="sxs-lookup"><span data-stu-id="98e8d-240"><xref:System.Activities.Statements.ParallelForEach%601>: A WF application manages corporate buys within a large company.</span></span> <span data-ttu-id="98e8d-241">企業規則表示，規劃任何採購作業之前，需要三家不同廠商的估價。</span><span class="sxs-lookup"><span data-stu-id="98e8d-241">The corporate rules dictate that before planning any purchase operation, the valuations of three different vendors is required.</span></span> <span data-ttu-id="98e8d-242">採購部門的員工會從公司的廠商清單中選取三家廠商。</span><span class="sxs-lookup"><span data-stu-id="98e8d-242">An employee from the buying department selects three vendors from the company’s vendor list.</span></span> <span data-ttu-id="98e8d-243">選取並通知這些廠商之後，公司將等候其經濟提案。</span><span class="sxs-lookup"><span data-stu-id="98e8d-243">After these vendors have been selected and notified, the company will wait for their economic proposals.</span></span> <span data-ttu-id="98e8d-244">這些提案可以按照任何順序提出。</span><span class="sxs-lookup"><span data-stu-id="98e8d-244">The proposals can come in any order.</span></span> <span data-ttu-id="98e8d-245">為了在 WF 中實作此案例，我們使用了 <xref:System.Activities.Statements.ParallelForEach%601>，以便逐一查看廠商的集合並且要求其經濟提案。</span><span class="sxs-lookup"><span data-stu-id="98e8d-245">To implement this scenario in WF, we use a <xref:System.Activities.Statements.ParallelForEach%601> that will iterate through our collection of vendors and ask for their economic proposals.</span></span> <span data-ttu-id="98e8d-246">蒐集所有提案之後，系統會選取並顯示最佳提案。</span><span class="sxs-lookup"><span data-stu-id="98e8d-246">After all offers are gathered, the best one is selected and displayed.</span></span>  
  
## <a name="invokemethod"></a><span data-ttu-id="98e8d-247">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="98e8d-247">InvokeMethod</span></span>  
 <span data-ttu-id="98e8d-248"><xref:System.Activities.Statements.InvokeMethod> 活動允許叫用範圍內物件或型別的公用方法。</span><span class="sxs-lookup"><span data-stu-id="98e8d-248">The <xref:System.Activities.Statements.InvokeMethod> activity allows invoking public methods in objects or types in scope.</span></span> <span data-ttu-id="98e8d-249">它支援叫用包含或不包含參數 (包括參數陣列) 的執行個體和靜態方法，以及泛型方法。</span><span class="sxs-lookup"><span data-stu-id="98e8d-249">It supports invoking instance and static methods with or without parameters (including parameter arrays), and generic methods.</span></span> <span data-ttu-id="98e8d-250">此外，它也允許以同步和非同步方式執行方法。</span><span class="sxs-lookup"><span data-stu-id="98e8d-250">It also allows executing method synchronously and asynchronously.</span></span>  
  
### <a name="getting-started"></a><span data-ttu-id="98e8d-251">快速入門</span><span class="sxs-lookup"><span data-stu-id="98e8d-251">Getting Started</span></span>  
  
-   <span data-ttu-id="98e8d-252">在 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 中，建立工作流程主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="98e8d-252">In [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], create a workflow console application.</span></span> <span data-ttu-id="98e8d-253">在工作流程設計工具中加入 <xref:System.Activities.Statements.InvokeMethod> 活動，並且針對此活動設定靜態和執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="98e8d-253">Add an <xref:System.Activities.Statements.InvokeMethod> activity in the workflow designer, and configure static and instance methods on it.</span></span>  
  
-   <span data-ttu-id="98e8d-254">範例：</span><span class="sxs-lookup"><span data-stu-id="98e8d-254">Samples:</span></span>  
  
    -   [<span data-ttu-id="98e8d-255">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="98e8d-255">InvokeMethod</span></span>](../../../docs/framework/windows-workflow-foundation/samples/invokemethod.md)  
  
-   <span data-ttu-id="98e8d-256">設計工具的文件： [InvokeMethod 活動設計工具](/visualstudio/workflow-designer/invokemethod-activity-designer)</span><span class="sxs-lookup"><span data-stu-id="98e8d-256">Designer Documentation: [InvokeMethod Activity Designer](/visualstudio/workflow-designer/invokemethod-activity-designer)</span></span>  
  
### <a name="invokemethod-scenarios"></a><span data-ttu-id="98e8d-257">InvokeMethod 案例</span><span class="sxs-lookup"><span data-stu-id="98e8d-257">InvokeMethod Scenarios</span></span>  
  
-   <span data-ttu-id="98e8d-258">需要叫用範圍內物件的方法。</span><span class="sxs-lookup"><span data-stu-id="98e8d-258">A method in an object in scope needs to be invoked.</span></span> <span data-ttu-id="98e8d-259">例如，需要將某個值加入至字典。</span><span class="sxs-lookup"><span data-stu-id="98e8d-259">For example, a value needs to be added to a dictionary.</span></span> <span data-ttu-id="98e8d-260">此時，系統會叫用字典執行個體的 Add 方法，並且提供索引鍵和值。</span><span class="sxs-lookup"><span data-stu-id="98e8d-260">The Add method of the instance of the dictionary is invoked, and the key and value are provided.</span></span>  
  
-   <span data-ttu-id="98e8d-261">需要針對舊版 CLR 物件叫用方法。</span><span class="sxs-lookup"><span data-stu-id="98e8d-261">A method needs to be invoked on a legacy CLR object.</span></span> <span data-ttu-id="98e8d-262">您可以使用 <xref:System.Activities.Statements.InvokeMethod>，而非建立自訂活動來包裝該舊版類別的呼叫 (如果它在工作流程執行期間位於範圍內的話)。</span><span class="sxs-lookup"><span data-stu-id="98e8d-262">Instead of creating a custom activity to wrap the call to that legacy class, if it is in scope during the workflow execution, <xref:System.Activities.Statements.InvokeMethod> can be used.</span></span>  
  
## <a name="error-handling-activities"></a><span data-ttu-id="98e8d-263">錯誤處理活動</span><span class="sxs-lookup"><span data-stu-id="98e8d-263">Error handling activities</span></span>  
 <span data-ttu-id="98e8d-264"><xref:System.Activities.Statements.TryCatch> 活動會提供一項機制來攔截一組包含活動執行時發生的例外狀況 (與在 C#/VB 中建構的 Try/Catch 很相似)。</span><span class="sxs-lookup"><span data-stu-id="98e8d-264">The <xref:System.Activities.Statements.TryCatch> activity provides a mechanism for catching exceptions that occur during the execution of a set of contained activities (similar to the Try/Catch construct in C#/VB).</span></span> <span data-ttu-id="98e8d-265"><xref:System.Activities.Statements.TryCatch> 提供工作流程層級的例外狀況處理。</span><span class="sxs-lookup"><span data-stu-id="98e8d-265"><xref:System.Activities.Statements.TryCatch> provides exception handling at the workflow level.</span></span> <span data-ttu-id="98e8d-266">當系統擲回未處理的例外狀況時，就會中止工作流程，而且不會執行 Finally 區塊。</span><span class="sxs-lookup"><span data-stu-id="98e8d-266">When an unhandled exception is thrown, the workflow is aborted and the Finally block won’t be executed.</span></span> <span data-ttu-id="98e8d-267">這種行為與 C# 一致。</span><span class="sxs-lookup"><span data-stu-id="98e8d-267">This behavior is consistent with C#.</span></span>  
  
### <a name="getting-started"></a><span data-ttu-id="98e8d-268">快速入門</span><span class="sxs-lookup"><span data-stu-id="98e8d-268">Getting Started</span></span>  
  
-   <span data-ttu-id="98e8d-269">在 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 中，建立工作流程主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="98e8d-269">In [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], create a workflow console application.</span></span> <span data-ttu-id="98e8d-270">在工作流程設計工具中加入 <xref:System.Activities.Statements.TryCatch> 活動。</span><span class="sxs-lookup"><span data-stu-id="98e8d-270">Add a <xref:System.Activities.Statements.TryCatch> activity in the workflow designer.</span></span>  
  
-   <span data-ttu-id="98e8d-271">範例：</span><span class="sxs-lookup"><span data-stu-id="98e8d-271">Samples:</span></span>  
  
    1.  [<span data-ttu-id="98e8d-272">使用 TryCatch 錯誤處理流程圖活動</span><span class="sxs-lookup"><span data-stu-id="98e8d-272">Fault Handling in a Flowchart Activity Using TryCatch</span></span>](../../../docs/framework/windows-workflow-foundation/samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)  
  
    2.  [<span data-ttu-id="98e8d-273">使用程序性活動</span><span class="sxs-lookup"><span data-stu-id="98e8d-273">Using Procedural Activities</span></span>](../../../docs/framework/windows-workflow-foundation/samples/using-procedural-activities.md)  
  
-   <span data-ttu-id="98e8d-274">設計工具的文件：[錯誤處理活動設計工具](/visualstudio/workflow-designer/error-handling-activity-designers)</span><span class="sxs-lookup"><span data-stu-id="98e8d-274">Designer Documentation: [Error Handling Activity Designers](/visualstudio/workflow-designer/error-handling-activity-designers)</span></span>  
  
### <a name="error-handling-scenarios"></a><span data-ttu-id="98e8d-275">錯誤處理案例</span><span class="sxs-lookup"><span data-stu-id="98e8d-275">Error handling scenarios</span></span>  
 <span data-ttu-id="98e8d-276">需要執行一組活動，而且需要在發生錯誤時執行特定邏輯。</span><span class="sxs-lookup"><span data-stu-id="98e8d-276">A set of activities needs to be executed, and specific logic needs to be executed when an error occurs.</span></span> <span data-ttu-id="98e8d-277">如果在錯誤處理邏輯期間發現錯誤無法復原，就會重新擲回例外狀況，而且父活動 (或主機) 將會處理此問題。</span><span class="sxs-lookup"><span data-stu-id="98e8d-277">If during that error handling logic it is found that the error is not recoverable, the exception will be rethrown, and the parent activity (or the host) will deal with the problem.</span></span>  
  
## <a name="pick-activity"></a><span data-ttu-id="98e8d-278">Pick 活動</span><span class="sxs-lookup"><span data-stu-id="98e8d-278">Pick activity</span></span>  
 <span data-ttu-id="98e8d-279"><xref:System.Activities.Statements.Pick> 活動會提供 WF 中以事件為主的控制流程模型。</span><span class="sxs-lookup"><span data-stu-id="98e8d-279">The <xref:System.Activities.Statements.Pick> Activity provides event-based control flow modeling in WF.</span></span> <span data-ttu-id="98e8d-280"><xref:System.Activities.Statements.Pick> 包含許多分支，每個分支會先等待特定事件發生後，再開始執行。</span><span class="sxs-lookup"><span data-stu-id="98e8d-280"><xref:System.Activities.Statements.Pick> contains many branches where each branch waits for a particular event to occur before running.</span></span> <span data-ttu-id="98e8d-281">在此設定中，<xref:System.Activities.Statements.Pick> 的行為與 <xref:System.Activities.Statements.Switch%601> 很相似，因為此活動只會執行它所接聽的其中一個事件集。</span><span class="sxs-lookup"><span data-stu-id="98e8d-281">In this setup, a <xref:System.Activities.Statements.Pick> behaves similar to a <xref:System.Activities.Statements.Switch%601> to which the Activity will execute only one of the set of events it is listening.</span></span> <span data-ttu-id="98e8d-282">每個分支都是由事件驅動，而發生的事件會先執行對應的分支。</span><span class="sxs-lookup"><span data-stu-id="98e8d-282">Each branch is event driven and the event that occurs runs the corresponding branch first.</span></span> <span data-ttu-id="98e8d-283">所有其他的分支都會取消並停止接聽事件。</span><span class="sxs-lookup"><span data-stu-id="98e8d-283">All other branches cancel and stop listening for events.</span></span>  
  
### <a name="getting-started"></a><span data-ttu-id="98e8d-284">快速入門</span><span class="sxs-lookup"><span data-stu-id="98e8d-284">Getting Started</span></span>  
  
-   <span data-ttu-id="98e8d-285">在 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 中，建立工作流程主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="98e8d-285">In [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], create a workflow console application.</span></span> <span data-ttu-id="98e8d-286">在工作流程設計工具中加入 <xref:System.Activities.Statements.Pick> 活動。</span><span class="sxs-lookup"><span data-stu-id="98e8d-286">Add a <xref:System.Activities.Statements.Pick> activity in the workflow designer.</span></span>  
  
-   <span data-ttu-id="98e8d-287">範例：[使用 Pick 活動](../../../docs/framework/windows-workflow-foundation/samples/using-the-pick-activity.md)</span><span class="sxs-lookup"><span data-stu-id="98e8d-287">Sample: [Using the Pick Activity](../../../docs/framework/windows-workflow-foundation/samples/using-the-pick-activity.md)</span></span>  
  
-   <span data-ttu-id="98e8d-288">設計工具文件： [Pick 活動設計工具](/visualstudio/workflow-designer/pick-activity-designer)</span><span class="sxs-lookup"><span data-stu-id="98e8d-288">Designer documentation: [Pick Activity Designer](/visualstudio/workflow-designer/pick-activity-designer)</span></span>  
  
### <a name="pick-scenario"></a><span data-ttu-id="98e8d-289">Pick 案例</span><span class="sxs-lookup"><span data-stu-id="98e8d-289">Pick Scenario</span></span>  
 <span data-ttu-id="98e8d-290">系統需要提示使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="98e8d-290">A user needs to be prompted for input.</span></span> <span data-ttu-id="98e8d-291">在一般情況下，開發人員會使用 <xref:System.Console.ReadLine%2A> 之類的方法呼叫來提示使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="98e8d-291">Under normal circumstances, the developer would use a method call like <xref:System.Console.ReadLine%2A> to prompt for a user’s input.</span></span> <span data-ttu-id="98e8d-292">這種設定的問題在於，直到使用者輸入某些內容為止，程式都會處於等候狀態。</span><span class="sxs-lookup"><span data-stu-id="98e8d-292">The problem with this setup is that the program waits until the user enters something.</span></span> <span data-ttu-id="98e8d-293">在此案例中，您需要使用逾時將封鎖的活動解除封鎖。</span><span class="sxs-lookup"><span data-stu-id="98e8d-293">In this scenario, a time-out is needed to unblock a blocking activity.</span></span> <span data-ttu-id="98e8d-294">常見的案例就是要求在指定的一段時間內完成工作。</span><span class="sxs-lookup"><span data-stu-id="98e8d-294">A common scenario is one that requires a task to be completed within a given time duration.</span></span> <span data-ttu-id="98e8d-295">讓封鎖的活動逾時則為 Pick 發揮功能的案例。</span><span class="sxs-lookup"><span data-stu-id="98e8d-295">Timing out a blocking activity is a scenario where Pick adds a lot of value.</span></span>  
  
## <a name="wcf-routing-service"></a><span data-ttu-id="98e8d-296">WCF 路由服務</span><span class="sxs-lookup"><span data-stu-id="98e8d-296">WCF Routing Service</span></span>  
 <span data-ttu-id="98e8d-297">路由服務設計為一般的軟體路由器，可讓您控制如何[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]訊息用戶端和服務之間的流量。</span><span class="sxs-lookup"><span data-stu-id="98e8d-297">The Routing Service is designed to be a generic software Router that allows you to control how [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]messages flow in between your clients and services.</span></span>  <span data-ttu-id="98e8d-298">路由服務可讓您分離您的用戶端，從您的服務，它將提供更多的自由，組態設定方面，您可以在支援彈性時，您必須考慮如何裝載您的服務。</span><span class="sxs-lookup"><span data-stu-id="98e8d-298">The Routing Service allows you to decouple your clients from your services, which gives you much more freedom in terms of the configurations that you can support and the flexibility you have when considering how to host your services.</span></span>  <span data-ttu-id="98e8d-299">在.NET 3.5 用戶端和服務所緊密結合。用戶端必須知道所有的服務，需要向他們不到。</span><span class="sxs-lookup"><span data-stu-id="98e8d-299">In .NET 3.5, clients and services were tightly coupled; a client had to know about all of the services it needed to talk to and where they were located.</span></span> <span data-ttu-id="98e8d-300">此外，.Net Framework 3.5 中的 WCF 具有下列限制：</span><span class="sxs-lookup"><span data-stu-id="98e8d-300">In addition, WCF in .Net Framework 3.5 had the following limitations:</span></span>  
  
-   <span data-ttu-id="98e8d-301">錯誤處理很複雜，因為此邏輯必須透過硬式編碼寫入用戶端。</span><span class="sxs-lookup"><span data-stu-id="98e8d-301">Error handling was complex, as this logic had to be hard-coded into the client.</span></span>  
  
-   <span data-ttu-id="98e8d-302">用戶端與服務一定要使用相同的繫結。</span><span class="sxs-lookup"><span data-stu-id="98e8d-302">Clients and services had to always use the same bindings.</span></span>  
  
-   <span data-ttu-id="98e8d-303">很少妥善分解服務：讓用戶端與實作所有功能的單一服務通訊會比在多個服務之間選擇更簡單。</span><span class="sxs-lookup"><span data-stu-id="98e8d-303">Services were rarely well factored: it is easier to have the client talk to one service which implements everything, rather than needing to choose between multiple services.</span></span>  
  
 <span data-ttu-id="98e8d-304">.Net 4 中路由服務的設計目的是要讓上述問題更容易解決。</span><span class="sxs-lookup"><span data-stu-id="98e8d-304">The routing service in .Net 4 is designed to make these problems easier to solve.</span></span> <span data-ttu-id="98e8d-305">新的路由服務具有下列功能：</span><span class="sxs-lookup"><span data-stu-id="98e8d-305">The new routing service has the following features:</span></span>  
  
1.  <span data-ttu-id="98e8d-306">以內容為基礎的路由 (<xref:System.ServiceModel.Dispatcher.MessageFilter> 物件會檢查訊息來判斷應該傳送的目的地)。</span><span class="sxs-lookup"><span data-stu-id="98e8d-306">Content based routing (<xref:System.ServiceModel.Dispatcher.MessageFilter> objects examine a message to determine where it should be sent.)</span></span>  
  
2.  <span data-ttu-id="98e8d-307">通訊協定橋接 (傳輸與訊息)。</span><span class="sxs-lookup"><span data-stu-id="98e8d-307">Protocol bridging (transport & message)</span></span>  
  
3.  <span data-ttu-id="98e8d-308">錯誤處理 (路由器會攔截通訊例外狀況並容錯移轉至備份端點)。</span><span class="sxs-lookup"><span data-stu-id="98e8d-308">Error handling (the router catches communication exceptions and fails over to backup endpoints)</span></span>  
  
4.  <span data-ttu-id="98e8d-309"><xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> 和路由組態的動態 (記憶體中) 更新。</span><span class="sxs-lookup"><span data-stu-id="98e8d-309">Dynamic (in memory) update of <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> and Routing Configuration.</span></span>  
  
### <a name="getting-started"></a><span data-ttu-id="98e8d-310">快速入門</span><span class="sxs-lookup"><span data-stu-id="98e8d-310">Getting Started</span></span>  
  
1.  <span data-ttu-id="98e8d-311">文件集：[路由](../../../docs/framework/wcf/feature-details/routing.md)</span><span class="sxs-lookup"><span data-stu-id="98e8d-311">Documentation: [Routing](../../../docs/framework/wcf/feature-details/routing.md)</span></span>  
  
2.  <span data-ttu-id="98e8d-312">範例：[路由服務 &#91;WCF 範例 &#93;](../../../docs/framework/wcf/samples/routing-services.md)</span><span class="sxs-lookup"><span data-stu-id="98e8d-312">Samples: [Routing Services &#91;WCF Samples&#93;](../../../docs/framework/wcf/samples/routing-services.md)</span></span>  
  
3.  <span data-ttu-id="98e8d-313">部落格：[路由規則 ！](http://go.microsoft.com/fwlink/?LinkId=204956)</span><span class="sxs-lookup"><span data-stu-id="98e8d-313">Blog: [Routing Rules!](http://go.microsoft.com/fwlink/?LinkId=204956)</span></span>  
  
### <a name="routing-scenarios"></a><span data-ttu-id="98e8d-314">路由案例</span><span class="sxs-lookup"><span data-stu-id="98e8d-314">Routing Scenarios</span></span>  
 <span data-ttu-id="98e8d-315">在下列案例中，路由服務很有用：</span><span class="sxs-lookup"><span data-stu-id="98e8d-315">The routing service is useful in the following scenarios:</span></span>  
  
-   <span data-ttu-id="98e8d-316">用戶端可以與多個服務通訊，而不需要直接處理所有服務。</span><span class="sxs-lookup"><span data-stu-id="98e8d-316">Clients can talk to multiple services without having to address them all directly.</span></span>  
  
-   <span data-ttu-id="98e8d-317">用戶端可以針對用戶端要求執行其他邏輯，以便判斷要路由傳送的目的地。</span><span class="sxs-lookup"><span data-stu-id="98e8d-317">Clients can perform additional logic on a client request to determine where to route it</span></span>  
  
-   <span data-ttu-id="98e8d-318">將用戶端所執行的作業分解成多個服務實作，而不需要重構用戶端。</span><span class="sxs-lookup"><span data-stu-id="98e8d-318">Decompose the operations a client performs into multiple service implementations without refactoring the client.</span></span>  
  
-   <span data-ttu-id="98e8d-319">用戶端與服務可以宣告具有不同安全性設定的不同繫結。</span><span class="sxs-lookup"><span data-stu-id="98e8d-319">Clients and services can speak different bindings with different security settings.</span></span>  
  
-   <span data-ttu-id="98e8d-320">用戶端可以具備更健全的功能，以防範失敗或無法使用服務的情況。</span><span class="sxs-lookup"><span data-stu-id="98e8d-320">Clients can be enabled to be more robust against failure or the unavailability of services.</span></span>  
  
## <a name="wcf-discovery"></a><span data-ttu-id="98e8d-321">WCF 探索</span><span class="sxs-lookup"><span data-stu-id="98e8d-321">WCF Discovery</span></span>  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="98e8d-322"> 探索是一項架構技術，可讓您將探索機制併入應用程式基礎結構中。</span><span class="sxs-lookup"><span data-stu-id="98e8d-322"> Discovery is a framework technology that allows you to incorporate a discovery mechanism to your application infrastructure.</span></span> <span data-ttu-id="98e8d-323">您可以使用這項技術，讓服務成為可探索的服務，並且設定用戶端來搜尋服務。</span><span class="sxs-lookup"><span data-stu-id="98e8d-323">You can use this to make your service discoverable, and configure your clients to search for services.</span></span> <span data-ttu-id="98e8d-324">用戶端不再需要對端點進行硬式編碼，讓應用程式更健全並提高容錯能力。</span><span class="sxs-lookup"><span data-stu-id="98e8d-324">Clients no longer need to be hard coded with endpoint, making your application more robust and fault tolerant.</span></span> <span data-ttu-id="98e8d-325">探索是在應用程式中建置自動組態功能的完美平台。</span><span class="sxs-lookup"><span data-stu-id="98e8d-325">Discovery is the perfect platform to build auto-configuration capabilities into your application.</span></span>  
  
 <span data-ttu-id="98e8d-326">此產品是以 WS-Discovery 標準為建置基礎。</span><span class="sxs-lookup"><span data-stu-id="98e8d-326">The product is built on top of the WS-Discovery standard.</span></span> <span data-ttu-id="98e8d-327">其設計目的是要成為可互通、可擴充且泛型的產品。</span><span class="sxs-lookup"><span data-stu-id="98e8d-327">It’s designed to be interoperable, extensible, and generic.</span></span> <span data-ttu-id="98e8d-328">此產品支援兩種作業模式：</span><span class="sxs-lookup"><span data-stu-id="98e8d-328">The product supports two modes of operation:</span></span>  
  
1.  <span data-ttu-id="98e8d-329">受管理：網路上有一個了解現有服務的實體，因此用戶端會直接查詢此實體以取得資訊。</span><span class="sxs-lookup"><span data-stu-id="98e8d-329">Managed: where there is an entity on the network knowledgeable about existing services, clients query it directly for information.</span></span> <span data-ttu-id="98e8d-330">這種模式類似於 Active Directory。</span><span class="sxs-lookup"><span data-stu-id="98e8d-330">This is analogous to Active Directory.</span></span>  
  
2.  <span data-ttu-id="98e8d-331">臨機操作：用戶端會使用多點傳送訊息來找出服務。</span><span class="sxs-lookup"><span data-stu-id="98e8d-331">Ad-hoc: where clients use multicast messages to locate services.</span></span>  
  
 <span data-ttu-id="98e8d-332">此外，探索訊息無從驗證網路通訊協定。您可以在支援模式需求的任何通訊協定上使用這些訊息。</span><span class="sxs-lookup"><span data-stu-id="98e8d-332">Furthermore, discovery messages are network protocol agnostic; you can use them on top any protocol that supports the mode requirements.</span></span> <span data-ttu-id="98e8d-333">例如，探索可以透過 UDP 通道或支援多點傳送訊息的其他任何網路傳送多點傳送的訊息。</span><span class="sxs-lookup"><span data-stu-id="98e8d-333">For example, discovery multicast messages can be sent over the UDP channel or any other network that supports multicast messaging.</span></span>  <span data-ttu-id="98e8d-334">這些設計點，結合功能的彈性，可讓您調整探索，特別是以您的方案。</span><span class="sxs-lookup"><span data-stu-id="98e8d-334">These design points, combined with feature flexibility, allow you to adapt the discovery specifically to your solution.</span></span>  
  
### <a name="getting-started"></a><span data-ttu-id="98e8d-335">快速入門</span><span class="sxs-lookup"><span data-stu-id="98e8d-335">Getting Started</span></span>  
  
-   <span data-ttu-id="98e8d-336">文件集： [WCF 探索](../../../docs/framework/wcf/feature-details/wcf-discovery.md)</span><span class="sxs-lookup"><span data-stu-id="98e8d-336">Documentation: [WCF Discovery](../../../docs/framework/wcf/feature-details/wcf-discovery.md)</span></span>  
  
-   <span data-ttu-id="98e8d-337">範例：[探索 （範例）](../../../docs/framework/wcf/samples/discovery-samples.md)</span><span class="sxs-lookup"><span data-stu-id="98e8d-337">Samples: [Discovery (Samples)](../../../docs/framework/wcf/samples/discovery-samples.md)</span></span>  
  
### <a name="discovery-scenarios"></a><span data-ttu-id="98e8d-338">探索案例</span><span class="sxs-lookup"><span data-stu-id="98e8d-338">Discovery Scenarios</span></span>  
 <span data-ttu-id="98e8d-339">開發人員不想要對端點進行硬式編碼，因為它在服務可用時處於未知狀態。</span><span class="sxs-lookup"><span data-stu-id="98e8d-339">A developer doesn't want to hard code endpoints, since it is unknown when my service will be available.</span></span> <span data-ttu-id="98e8d-340">不過，開發人員想要在執行階段選擇服務。</span><span class="sxs-lookup"><span data-stu-id="98e8d-340">Instead, the developer wants to choose a service at runtime.</span></span> <span data-ttu-id="98e8d-341">因此，應用程式的元件之間需要降低耦合、提高健全度，以及自動組態功能。</span><span class="sxs-lookup"><span data-stu-id="98e8d-341">More decoupling, robustness, and auto-configuration is needed between the components in the application.</span></span>  
  
## <a name="tracking"></a><span data-ttu-id="98e8d-342">追蹤</span><span class="sxs-lookup"><span data-stu-id="98e8d-342">Tracking</span></span>  
 <span data-ttu-id="98e8d-343">工作流程追蹤提供深入了解在執行工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="98e8d-343">Workflow tracking provides insight into the execution of a workflow instance.</span></span>  <span data-ttu-id="98e8d-344">從工作流程執行個體層級和活動工作流程中的執行工作流程不會發出追蹤事件。</span><span class="sxs-lookup"><span data-stu-id="98e8d-344">The tracking events are emitted from a workflow at the workflow instance level and when activities within the workflow execute.</span></span> <span data-ttu-id="98e8d-345">您必須將工作流程追蹤參與者加入至工作流程主機，才能訂閱追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="98e8d-345">A workflow tracking participant needs to be added to the workflow host to subscribe to tracking records.</span></span> <span data-ttu-id="98e8d-346">系統會使用追蹤設定檔來篩選追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="98e8d-346">The tracking records are filtered using a tracking profile.</span></span> <span data-ttu-id="98e8d-347">.Net Framework 提供了 ETW (Windows 事件追蹤) 追蹤參與者，而且基本設定檔安裝在 machine.config 檔案中。</span><span class="sxs-lookup"><span data-stu-id="98e8d-347">The .Net Framework provides an ETW (Event Tracing for Windows) tracking participant, and a basic profile is installed in the machine.config file.</span></span>  
  
### <a name="getting-started"></a><span data-ttu-id="98e8d-348">快速入門</span><span class="sxs-lookup"><span data-stu-id="98e8d-348">Getting Started</span></span>  
  
1.  <span data-ttu-id="98e8d-349">在 [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] 中，建立 WCF 工作流程服務應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="98e8d-349">In [!INCLUDE[vs2010](../../../includes/vs2010-md.md)], create a WCF Workflow Service Application project.</span></span> <span data-ttu-id="98e8d-350">一組 <xref:System.ServiceModel.Activities.Receive> 和 <xref:System.ServiceModel.Activities.SendReply> 將置於畫布上，以便開始。</span><span class="sxs-lookup"><span data-stu-id="98e8d-350">A <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply> pair will be placed on your canvas to start.</span></span>  
  
2.  <span data-ttu-id="98e8d-351">開啟 web.config 並加入不含設定檔的 ETW 追蹤行為。</span><span class="sxs-lookup"><span data-stu-id="98e8d-351">Open the web.config and add an ETW tracking behavior with no profile.</span></span>  
  
    1.  <span data-ttu-id="98e8d-352">系統會使用預設設定檔。</span><span class="sxs-lookup"><span data-stu-id="98e8d-352">The default profile is used.</span></span>  
  
    2.  <span data-ttu-id="98e8d-353">開啟 事件檢視器並啟用下列節點中的分析通道：**事件檢視器**， **Applications and Services Logs**， **Microsoft**， **Windows**，**應用程式伺服器-應用程式**。</span><span class="sxs-lookup"><span data-stu-id="98e8d-353">Open event viewer and enable the analytic channel in the following node: **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="98e8d-354">以滑鼠右鍵按一下**分析**選取**啟用記錄**。</span><span class="sxs-lookup"><span data-stu-id="98e8d-354">Right-click **Analytic** and select **Enable Log**.</span></span>  
  
    3.  <span data-ttu-id="98e8d-355">執行工作流程服務。</span><span class="sxs-lookup"><span data-stu-id="98e8d-355">Run the workflow service.</span></span>  
  
    4.  <span data-ttu-id="98e8d-356">在事件檢視器中查看工作流程追蹤事件。</span><span class="sxs-lookup"><span data-stu-id="98e8d-356">Observe the workflow tracking events in event viewer.</span></span>  
  
3.  <span data-ttu-id="98e8d-357">範例：[追蹤](../../../docs/framework/windows-workflow-foundation/samples/tracking.md)</span><span class="sxs-lookup"><span data-stu-id="98e8d-357">Samples: [Tracking](../../../docs/framework/windows-workflow-foundation/samples/tracking.md)</span></span>  
  
4.  <span data-ttu-id="98e8d-358">概念文件：[工作流程追蹤](../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)</span><span class="sxs-lookup"><span data-stu-id="98e8d-358">Conceptual documentation: [Workflow Tracking and Tracing](../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)</span></span>  
  
## <a name="sql-workflow-instance-store"></a><span data-ttu-id="98e8d-359">SQL 工作流程執行個體存放區</span><span class="sxs-lookup"><span data-stu-id="98e8d-359">SQL Workflow Instance Store</span></span>  
 <span data-ttu-id="98e8d-360"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 是以 SQL Server 為基礎的執行個體存放區實作。</span><span class="sxs-lookup"><span data-stu-id="98e8d-360">The <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> is a SQL Server-based implementation of an instance store.</span></span> <span data-ttu-id="98e8d-361">執行個體存放區會儲存執行中執行個體的狀態以及載入和繼續該執行個體所需的所有資料。</span><span class="sxs-lookup"><span data-stu-id="98e8d-361">An instance store stores the state of a running instance together with all data necessary to load and resume that instance.</span></span> <span data-ttu-id="98e8d-362">如果工作流程會保存，服務主機就會指示執行個體存放區儲存執行個體狀態，而且當該執行個體的訊息送達或延遲活動過期時，它就會指示執行個體存放區載入執行個體狀態。</span><span class="sxs-lookup"><span data-stu-id="98e8d-362">The service host instructs the instance store to save the instance state if the workflow persists, and it instructs the instance store to load the instance state when a message arrives for that instance or a delay activity expires.</span></span>  
  
### <a name="getting-started"></a><span data-ttu-id="98e8d-363">快速入門</span><span class="sxs-lookup"><span data-stu-id="98e8d-363">Getting Started</span></span>  
  
1.  <span data-ttu-id="98e8d-364">在 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 中，建立包含隱含或明確 <xref:System.Activities.Statements.Persist> 活動的工作流程。</span><span class="sxs-lookup"><span data-stu-id="98e8d-364">In [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], create a Workflow that contains an implicit or explicit <xref:System.Activities.Statements.Persist> activity.</span></span> <span data-ttu-id="98e8d-365">將 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 行為加入至工作流程服務主機。</span><span class="sxs-lookup"><span data-stu-id="98e8d-365">Add the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> behavior to your workflow service host.</span></span> <span data-ttu-id="98e8d-366">您可以在程式碼或應用程式組態檔中進行這項作業。</span><span class="sxs-lookup"><span data-stu-id="98e8d-366">This can be done in code or in the application configuration file.</span></span>  
  
2.  <span data-ttu-id="98e8d-367">範例：[持續性](../../../docs/framework/windows-workflow-foundation/samples/persistence.md)</span><span class="sxs-lookup"><span data-stu-id="98e8d-367">Samples: [Persistence](../../../docs/framework/windows-workflow-foundation/samples/persistence.md)</span></span>  
  
3.  <span data-ttu-id="98e8d-368">概念文件： [SQL 工作流程執行個體存放區](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md)。</span><span class="sxs-lookup"><span data-stu-id="98e8d-368">Conceptual documentation: [SQL Workflow Instance Store](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span></span>
