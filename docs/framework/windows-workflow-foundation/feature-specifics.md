---
title: Windows Workflow Foundation 功能內容
ms.date: 03/30/2017
ms.assetid: e84d12da-a055-45f6-b4d1-878d127b46b6
ms.openlocfilehash: 063d2472443431423cea9b164831cd1e7a669408
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64753728"
---
# <a name="windows-workflow-foundation-feature-specifics"></a><span data-ttu-id="908e6-102">Windows Workflow Foundation 功能內容</span><span class="sxs-lookup"><span data-stu-id="908e6-102">Windows Workflow Foundation Feature Specifics</span></span>

[!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)] <span data-ttu-id="908e6-103">在 Windows Workflow Foundation 中加入一些功能。</span><span class="sxs-lookup"><span data-stu-id="908e6-103">adds a number of features to Windows Workflow Foundation.</span></span> <span data-ttu-id="908e6-104">本文件將描述一些新功能，並且詳細說明適合使用這些功能的案例。</span><span class="sxs-lookup"><span data-stu-id="908e6-104">This document describes a number of the new features, and gives details about scenarios in which they may be useful.</span></span>

## <a name="messaging-activities"></a><span data-ttu-id="908e6-105">傳訊活動</span><span class="sxs-lookup"><span data-stu-id="908e6-105">Messaging Activities</span></span>

<span data-ttu-id="908e6-106">傳訊活動 (<xref:System.ServiceModel.Activities.Receive>， <xref:System.ServiceModel.Activities.SendReply>， <xref:System.ServiceModel.Activities.Send>， <xref:System.ServiceModel.Activities.ReceiveReply>) 用來傳送和接收 WCF 訊息，從您的工作流程。</span><span class="sxs-lookup"><span data-stu-id="908e6-106">The messaging activities (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.ReceiveReply>) are used to send and receive WCF messages from your workflow.</span></span> <span data-ttu-id="908e6-107"><xref:System.ServiceModel.Activities.Receive> 和<xref:System.ServiceModel.Activities.SendReply>活動用來形成可透過 WSDL 公開，就像標準的 WCF web 服務的 Windows Communication Foundation (WCF) 服務作業。</span><span class="sxs-lookup"><span data-stu-id="908e6-107"><xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply> activities are used to form a Windows Communication Foundation (WCF) service operation that is exposed via WSDL just like standard WCF web services.</span></span> <span data-ttu-id="908e6-108"><xref:System.ServiceModel.Activities.Send> 並<xref:System.ServiceModel.Activities.ReceiveReply>用來取用 web 服務，類似於 WCF <xref:System.ServiceModel.ChannelFactory>;**加入服務參考**體驗也存在會產生預先設定的活動的 Workflow Foundation。</span><span class="sxs-lookup"><span data-stu-id="908e6-108"><xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.ReceiveReply> are used to consume a web service similar to a WCF <xref:System.ServiceModel.ChannelFactory>; an **Add Service Reference** experience also exists for Workflow Foundation that generates pre-configured activities.</span></span>

### <a name="getting-started-with-messaging-activities"></a><span data-ttu-id="908e6-109">傳訊活動使用者入門</span><span class="sxs-lookup"><span data-stu-id="908e6-109">Getting Started with Messaging Activities</span></span>

- <span data-ttu-id="908e6-110">在 Visual Studio 2012 中，建立 WCF 工作流程服務應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="908e6-110">In Visual Studio 2012, create a WCF Workflow Service Application project.</span></span> <span data-ttu-id="908e6-111">一組 <xref:System.ServiceModel.Activities.Receive> 和 <xref:System.ServiceModel.Activities.SendReply> 將置於畫布上。</span><span class="sxs-lookup"><span data-stu-id="908e6-111">A <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply> pair will be placed on your canvas.</span></span>

- <span data-ttu-id="908e6-112">以滑鼠右鍵按一下專案，然後選取**加入服務參考**。</span><span class="sxs-lookup"><span data-stu-id="908e6-112">Right-click on the project and select **Add Service Reference**.</span></span> <span data-ttu-id="908e6-113">指向現有的 web 服務 WSDL，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="908e6-113">Point to an existing web service WSDL and click **OK**.</span></span> <span data-ttu-id="908e6-114">建置您的專案，以顯示產生的活動 (使用實作<xref:System.ServiceModel.Activities.Send>和<xref:System.ServiceModel.Activities.ReceiveReply>) 在工具箱中。</span><span class="sxs-lookup"><span data-stu-id="908e6-114">Build your project to show the generated activities (implemented using <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.ReceiveReply>) in your toolbox.</span></span>

- [<span data-ttu-id="908e6-115">工作流程服務 」 文件</span><span class="sxs-lookup"><span data-stu-id="908e6-115">Workflow services documentation</span></span>](../wcf/feature-details/workflow-services.md)

### <a name="messaging-activities-example-scenario"></a><span data-ttu-id="908e6-116">傳訊活動範例案例</span><span class="sxs-lookup"><span data-stu-id="908e6-116">Messaging Activities Example Scenario</span></span>

<span data-ttu-id="908e6-117">A`BestPriceFinder`服務會呼叫多個航空公司服務，以便尋找最佳票證的特定路由。</span><span class="sxs-lookup"><span data-stu-id="908e6-117">A `BestPriceFinder` service calls out to multiple airline services to find the best ticket price for a particular route.</span></span> <span data-ttu-id="908e6-118">實作此案例會要求您使用訊息活動來接收價格要求、 從後端服務擷取價格回覆價格要求，以最佳價格。</span><span class="sxs-lookup"><span data-stu-id="908e6-118">Implementing this scenario would require you to use the message activities to receive the price request, retrieve the prices from the back-end services, and reply to the price request with the best price.</span></span> <span data-ttu-id="908e6-119">它也需要您使用其他的全新活動來建立計算最佳價格的商務邏輯。</span><span class="sxs-lookup"><span data-stu-id="908e6-119">It would also require you to use other out-of-box activities to create the business logic for calculating the best price.</span></span>

## <a name="workflowservicehost"></a><span data-ttu-id="908e6-120">WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="908e6-120">WorkflowServiceHost</span></span>

<span data-ttu-id="908e6-121"><xref:System.ServiceModel.WorkflowServiceHost>是立即可用的工作流程主應用程式支援多個執行個體、 組態和 WCF 傳訊 （雖然這些工作流程不需要使用訊息，就能夠裝載）。</span><span class="sxs-lookup"><span data-stu-id="908e6-121">The <xref:System.ServiceModel.WorkflowServiceHost> is the out-of-box workflow host that supports multiple instances, configuration, and WCF messaging (although the workflows aren’t required to use messaging in order to be hosted).</span></span> <span data-ttu-id="908e6-122">此外，它也會透過一組服務行為，與持續性、追蹤和執行個體控制項整合。</span><span class="sxs-lookup"><span data-stu-id="908e6-122">It also integrates with persistence, tracking, and instance control through a set of service behaviors.</span></span> <span data-ttu-id="908e6-123">就像 WCF 的<xref:System.ServiceModel.ServiceHost>，則<xref:System.ServiceModel.WorkflowServiceHost>可以自我裝載於主控台/WinForms/WPF 應用程式或 Windows 服務或 web 裝載 （成為.xamlx 檔案） 在 IIS 或 WAS 中。</span><span class="sxs-lookup"><span data-stu-id="908e6-123">Just like WCF’s <xref:System.ServiceModel.ServiceHost>, the <xref:System.ServiceModel.WorkflowServiceHost> can be self-hosted in a console/WinForms/WPF application or Windows service, or web-hosted (as a .xamlx file) in IIS or WAS.</span></span>

### <a name="getting-started-with-workflow-service-host"></a><span data-ttu-id="908e6-124">工作流程服務主機使用者入門</span><span class="sxs-lookup"><span data-stu-id="908e6-124">Getting Started with Workflow Service Host</span></span>

- <span data-ttu-id="908e6-125">在 Visual Studio 2010 中，建立 WCF 工作流程服務應用程式專案： 此專案將會設定為使用<xref:System.ServiceModel.WorkflowServiceHost>web 主機環境中。</span><span class="sxs-lookup"><span data-stu-id="908e6-125">In Visual Studio 2010, create a WCF Workflow Service Application project: this project will be set up to use <xref:System.ServiceModel.WorkflowServiceHost> in a web-host environment.</span></span>

- <span data-ttu-id="908e6-126">若要裝載非傳訊工作流程，請加入會根據訊息建立執行個體的自訂 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>。</span><span class="sxs-lookup"><span data-stu-id="908e6-126">In order to host a non-messaging workflow, add a custom <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> that will create the instance based on a message.</span></span>

- <span data-ttu-id="908e6-127">您可以將 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> 加入至 <xref:System.ServiceModel.WorkflowServiceHost>，然後使用 <xref:System.ServiceModel.Activities.WorkflowControlClient>，藉以控制工作流程執行個體 (例如暫停或終止)。</span><span class="sxs-lookup"><span data-stu-id="908e6-127">Workflow instances can be controlled (e.g. suspended or terminated) by adding a <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> to the <xref:System.ServiceModel.WorkflowServiceHost> and then using a <xref:System.ServiceModel.Activities.WorkflowControlClient>.</span></span>

- <span data-ttu-id="908e6-128">您可以在下列章節中找到 <xref:System.ServiceModel.WorkflowServiceHost> 的範例：</span><span class="sxs-lookup"><span data-stu-id="908e6-128">Samples for the <xref:System.ServiceModel.WorkflowServiceHost> can be found in the following sections:</span></span>

  - [<span data-ttu-id="908e6-129">執行</span><span class="sxs-lookup"><span data-stu-id="908e6-129">Execution</span></span>](./samples/execution.md)

  - <span data-ttu-id="908e6-130">應用程式：[暫停的執行個體管理](./samples/suspended-instance-management.md)</span><span class="sxs-lookup"><span data-stu-id="908e6-130">Application: [Suspended Instance Management](./samples/suspended-instance-management.md)</span></span>

- [<span data-ttu-id="908e6-131">裝載工作流程服務概觀</span><span class="sxs-lookup"><span data-stu-id="908e6-131">Hosting Workflow services overview</span></span>](../wcf/feature-details/hosting-workflow-services-overview.md)

### <a name="workflowservicehost-scenario"></a><span data-ttu-id="908e6-132">WorkflowServiceHost 案例</span><span class="sxs-lookup"><span data-stu-id="908e6-132">WorkflowServiceHost Scenario</span></span>

<span data-ttu-id="908e6-133">BestPriceFinder 服務會呼叫多個航空公司服務，以便尋找最佳票證的特定路由。</span><span class="sxs-lookup"><span data-stu-id="908e6-133">A BestPriceFinder service calls out to multiple airline services to find the best ticket price for a particular route.</span></span> <span data-ttu-id="908e6-134">實作此案例需要您裝載中的工作流程<xref:System.ServiceModel.WorkflowServiceHost>。</span><span class="sxs-lookup"><span data-stu-id="908e6-134">Implementing this scenario would require you to host the workflow in <xref:System.ServiceModel.WorkflowServiceHost>.</span></span> <span data-ttu-id="908e6-135">它也會使用訊息活動來接收價格要求、 從後端服務擷取價格回覆價格要求，以最佳價格。</span><span class="sxs-lookup"><span data-stu-id="908e6-135">It would also use the message activities to receive the price request, retrieve the prices from the back-end services, and reply to the price request with the best price.</span></span>

## <a name="correlation"></a><span data-ttu-id="908e6-136">相互關聯</span><span class="sxs-lookup"><span data-stu-id="908e6-136">Correlation</span></span>

<span data-ttu-id="908e6-137">相互關聯是指下列其中一種情況：</span><span class="sxs-lookup"><span data-stu-id="908e6-137">A correlation is one of two things:</span></span>

- <span data-ttu-id="908e6-138">群組訊息的方式。亦即，要求訊息與其回覆之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="908e6-138">A way of grouping messages together; that is, the relationship between a request message and its reply.</span></span>

- <span data-ttu-id="908e6-139">將資料片段對應至服務執行個體的方式。</span><span class="sxs-lookup"><span data-stu-id="908e6-139">A way of mapping a piece of data to a service instance</span></span>

### <a name="getting-started"></a><span data-ttu-id="908e6-140">快速入門</span><span class="sxs-lookup"><span data-stu-id="908e6-140">Getting Started</span></span>

- <span data-ttu-id="908e6-141">若要開始使用相互關聯，請在 Visual Studio 中建立新的專案。</span><span class="sxs-lookup"><span data-stu-id="908e6-141">To get started with correlation, create a new project in Visual Studio.</span></span> <span data-ttu-id="908e6-142">建立型別為 <xref:System.ServiceModel.Activities.CorrelationHandle> 的變數。</span><span class="sxs-lookup"><span data-stu-id="908e6-142">Create a variable of type <xref:System.ServiceModel.Activities.CorrelationHandle>.</span></span>

- <span data-ttu-id="908e6-143">用來將訊息群組在一起之相互關聯的範例就是，將訊息群組在一起的要求-回覆相互關聯。</span><span class="sxs-lookup"><span data-stu-id="908e6-143">An example of correlation used to group messages together is a Request-Reply correlation that groups messages together.</span></span>

  - <span data-ttu-id="908e6-144">在 <xref:System.ServiceModel.Activities.Receive>活動上，按一下<xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A>屬性，並新增<xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>使用 CorrelationHandle 上述的第一個步驟中建立。</span><span class="sxs-lookup"><span data-stu-id="908e6-144">On a <xref:System.ServiceModel.Activities.Receive> activity, click on the <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> property and add a <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> using the CorrelationHandle created in the first step above.</span></span>

  - <span data-ttu-id="908e6-145">建立<xref:System.ServiceModel.Activities.SendReply>活動上按一下滑鼠右鍵<xref:System.ServiceModel.Activities.Receive>，然後按一下 「 建立 SendReply。</span><span class="sxs-lookup"><span data-stu-id="908e6-145">Create a <xref:System.ServiceModel.Activities.SendReply> activity by right-clicking on the <xref:System.ServiceModel.Activities.Receive> and clicking "Create SendReply".</span></span> <span data-ttu-id="908e6-146">接著，將它貼入工作流程中 <xref:System.ServiceModel.Activities.Receive> 活動的後面。</span><span class="sxs-lookup"><span data-stu-id="908e6-146">Paste it into your workflow after the <xref:System.ServiceModel.Activities.Receive> activity.</span></span>

- <span data-ttu-id="908e6-147">將資料片段對應至服務執行個體的範例就是內容架構的相互關聯，它會將資料片段 (例如訂單 ID) 對應至特定工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="908e6-147">An example of mapping a piece of data to a service instance is content-based correlation which maps a piece of data (for example, an order ID) to a particular workflow instance.</span></span>

  - <span data-ttu-id="908e6-148">在任何傳訊活動上，按一下 `CorrelationInitializers` 屬性，然後使用您在上述步驟中建立的 <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> 變數來加入 <xref:System.ServiceModel.Activities.CorrelationHandle>。</span><span class="sxs-lookup"><span data-stu-id="908e6-148">On any messaging activity, click on the `CorrelationInitializers` property and add a <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> using the <xref:System.ServiceModel.Activities.CorrelationHandle> variable created above.</span></span> <span data-ttu-id="908e6-149">在下拉式功能表中，按兩下所需的訊息屬性 (例如 OrderID)。</span><span class="sxs-lookup"><span data-stu-id="908e6-149">Double-click on the desired property on the message (e.g. OrderID) from the drop-down menu.</span></span> <span data-ttu-id="908e6-150">接著，將 `CorrelatesWith` 屬性設定為上述使用的 <xref:System.ServiceModel.Activities.CorrelationHandle> 變數。</span><span class="sxs-lookup"><span data-stu-id="908e6-150">Set the `CorrelatesWith` property to the <xref:System.ServiceModel.Activities.CorrelationHandle> variable used above.</span></span>

- [<span data-ttu-id="908e6-151">相互關聯概念文件</span><span class="sxs-lookup"><span data-stu-id="908e6-151">Correlation Conceptual Documentation</span></span>](../wcf/feature-details/correlation.md)

### <a name="correlation-scenario"></a><span data-ttu-id="908e6-152">相互關聯案例</span><span class="sxs-lookup"><span data-stu-id="908e6-152">Correlation Scenario</span></span>

<span data-ttu-id="908e6-153">訂單處理工作流程用來處理新訂單建立和更新程序中的現有訂單。</span><span class="sxs-lookup"><span data-stu-id="908e6-153">An order-processing workflow is used to handle new order creation and updating existing orders that are in process.</span></span> <span data-ttu-id="908e6-154">實作此案例需要您裝載中的工作流程<xref:System.ServiceModel.WorkflowServiceHost>和使用傳訊活動。</span><span class="sxs-lookup"><span data-stu-id="908e6-154">Implementing this scenario would require you to host the workflow in <xref:System.ServiceModel.WorkflowServiceHost> and use the messaging activities.</span></span> <span data-ttu-id="908e6-155">它也需要為基礎的相互關聯`orderId`以確保系統會對更新正確的工作流程。</span><span class="sxs-lookup"><span data-stu-id="908e6-155">It would also require correlation based on the `orderId` to ensure that updates are made to the correct workflow.</span></span>

## <a name="simplified-configuration"></a><span data-ttu-id="908e6-156">簡化的組態</span><span class="sxs-lookup"><span data-stu-id="908e6-156">Simplified Configuration</span></span>

<span data-ttu-id="908e6-157">WCF 組態結構描述很複雜，而且使用者提供許多不易發現的功能。</span><span class="sxs-lookup"><span data-stu-id="908e6-157">The WCF configuration schema is complex and provides users with many hard to find features.</span></span> <span data-ttu-id="908e6-158">在  [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]，我們已經著重於協助 WCF 使用者設定其服務的下列功能：</span><span class="sxs-lookup"><span data-stu-id="908e6-158">In [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], we have focused on helping WCF users configure their services with the following features:</span></span>

- <span data-ttu-id="908e6-159">移除每項服務明確組態的需求。</span><span class="sxs-lookup"><span data-stu-id="908e6-159">Removing the need for explicit per-service configuration.</span></span> <span data-ttu-id="908e6-160">如果您未設定任何\<服務 > 您的服務，而您服務的項目並未定義任何端點以程式設計的方式，則一組端點將會自動新增至您的服務，其中每個服務基底位址和每個合約實作您的服務。</span><span class="sxs-lookup"><span data-stu-id="908e6-160">If you do not configure any \<service> elements for your service, and your service does not define programmatically any endpoint, then a set of endpoints will be automatically added to your service, one per service base address and per contract implemented by your service.</span></span>

- <span data-ttu-id="908e6-161">讓使用者定義 WCF 繫結和行為的預設值，以便套用至沒有明確組態的服務。</span><span class="sxs-lookup"><span data-stu-id="908e6-161">Enables the user to define default values for WCF bindings and behaviors, which will be applied to services with no explicit configuration.</span></span>

- <span data-ttu-id="908e6-162">標準端點會定義可重複使用的預先設定端點，其中一個或多個端點屬性 (位址、繫結和合約) 具有固定的值，而且允許定義自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="908e6-162">Standard endpoints define reusable preconfigured endpoints, which have fixed values for one or more of the endpoint properties (address, binding and contract), and allow defining custom properties.</span></span>

- <span data-ttu-id="908e6-163">最後，<xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>可讓您集中管理 WCF 用戶端組態，組態是選取或變更應用程式定義域載入時間之後的案例中很有用。</span><span class="sxs-lookup"><span data-stu-id="908e6-163">Finally, the <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> allows you to do central management of WCF client configuration, useful in scenarios in which configuration is selected or changed after the application domain load time.</span></span>

### <a name="getting-started"></a><span data-ttu-id="908e6-164">快速入門</span><span class="sxs-lookup"><span data-stu-id="908e6-164">Getting Started</span></span>

- [<span data-ttu-id="908e6-165">WCF 4.0 開發人員指南</span><span class="sxs-lookup"><span data-stu-id="908e6-165">A Developer's Guide to WCF 4.0</span></span>](https://go.microsoft.com/fwlink/?LinkId=204940)

- [<span data-ttu-id="908e6-166">組態通道處理站</span><span class="sxs-lookup"><span data-stu-id="908e6-166">Configuration Channel Factory</span></span>](https://go.microsoft.com/fwlink/?LinkId=204941)

- [<span data-ttu-id="908e6-167">標準端點項目</span><span class="sxs-lookup"><span data-stu-id="908e6-167">Standard Endpoint Element</span></span>](https://go.microsoft.com/fwlink/?LinkId=204942)

- [<span data-ttu-id="908e6-168">.NET Framework 4 中的服務組態改良</span><span class="sxs-lookup"><span data-stu-id="908e6-168">Service configuration improvements in .NET Framework 4</span></span>](https://go.microsoft.com/fwlink/?LinkId=204943)

- [<span data-ttu-id="908e6-169">.NET 4 中的常見使用者錯誤：拼錯 WF/WCF 服務組態名稱</span><span class="sxs-lookup"><span data-stu-id="908e6-169">Common User Mistake in .NET 4: Mistyping the WF/WCF Service Configuration Name</span></span>](https://go.microsoft.com/fwlink/?LinkId=204944)

### <a name="simplified-configuration-scenarios"></a><span data-ttu-id="908e6-170">簡化的組態案例</span><span class="sxs-lookup"><span data-stu-id="908e6-170">Simplified Configuration Scenarios</span></span>

- <span data-ttu-id="908e6-171">有經驗的 ASMX 開發人員想要開始使用 WCF。</span><span class="sxs-lookup"><span data-stu-id="908e6-171">An experienced ASMX developer wants to start using WCF.</span></span> <span data-ttu-id="908e6-172">不過，WCF 看起來太複雜 ！</span><span class="sxs-lookup"><span data-stu-id="908e6-172">However, WCF seems way too complicated!</span></span> <span data-ttu-id="908e6-173">我需要在組態檔中寫入哪些資訊？</span><span class="sxs-lookup"><span data-stu-id="908e6-173">What is all that information that I need to write in a configuration file?</span></span> <span data-ttu-id="908e6-174">在 .NET 4 中，您甚至可以決定完全不使用組態檔。</span><span class="sxs-lookup"><span data-stu-id="908e6-174">In .NET 4, you can even decide to not have a configuration file at all.</span></span>

- <span data-ttu-id="908e6-175">現有的 WCF 服務集非常難以設定和維護。</span><span class="sxs-lookup"><span data-stu-id="908e6-175">An existing set of WCF services are very difficult to configure and maintain.</span></span> <span data-ttu-id="908e6-176">組態檔具有數千行 XML 程式碼，任意修改可能會非常危險。</span><span class="sxs-lookup"><span data-stu-id="908e6-176">The configuration file has thousands of lines of XML code that are extremely dangerous to touch.</span></span> <span data-ttu-id="908e6-177">因此需要相關協助，以便將程式碼數量減少至較容易管理的數量。</span><span class="sxs-lookup"><span data-stu-id="908e6-177">Help is needed to reduce that amount of code to something more manageable.</span></span>

## <a name="data-contract-resolver"></a><span data-ttu-id="908e6-178">資料合約解析程式</span><span class="sxs-lookup"><span data-stu-id="908e6-178">Data Contract Resolver</span></span>

<span data-ttu-id="908e6-179">在 .NET 3.5 中，已知型別的設計具有一些限制：</span><span class="sxs-lookup"><span data-stu-id="908e6-179">In .NET 3.5, there were a few limitations in the design of known types:</span></span>

- <span data-ttu-id="908e6-180">您無法在序列化或還原序列化期間，以動態方式加入已知型別。</span><span class="sxs-lookup"><span data-stu-id="908e6-180">Adding known types dynamically, during serialization or deserialization, was not possible.</span></span>

- <span data-ttu-id="908e6-181">序列化程式無法處理不明的 xsi:type 資訊。</span><span class="sxs-lookup"><span data-stu-id="908e6-181">Serializers could not deal with unknown xsi:type information.</span></span>

- <span data-ttu-id="908e6-182">使用者無法指定想要顯示在 Wire 上的 xsi:type，以便降低 Wire 上序列化執行個體的大小。</span><span class="sxs-lookup"><span data-stu-id="908e6-182">It was not possible for users to specify what xsi:type they would like to have appear on the wire to, for instance, make the size of a serialization instance on the wire smaller.</span></span>

<span data-ttu-id="908e6-183">[DataContractResolver](../wcf/samples/datacontractresolver.md)可以解決這些問題在.NET 4.5 中的。</span><span class="sxs-lookup"><span data-stu-id="908e6-183">The [DataContractResolver](../wcf/samples/datacontractresolver.md) solves these issues in .NET 4.5.</span></span>

### <a name="getting-started"></a><span data-ttu-id="908e6-184">快速入門</span><span class="sxs-lookup"><span data-stu-id="908e6-184">Getting Started</span></span>

- [<span data-ttu-id="908e6-185">資料合約解析程式 API 文件</span><span class="sxs-lookup"><span data-stu-id="908e6-185">Data Contract Resolver API documentation</span></span>](https://go.microsoft.com/fwlink/?LinkId=204946)

- [<span data-ttu-id="908e6-186">資料合約解析程式簡介</span><span class="sxs-lookup"><span data-stu-id="908e6-186">Introducing the Data Contract Resolver</span></span>](https://go.microsoft.com/fwlink/?LinkId=204947)

- <span data-ttu-id="908e6-187">範例：</span><span class="sxs-lookup"><span data-stu-id="908e6-187">Samples:</span></span>

  - [<span data-ttu-id="908e6-188">DataContractResolver</span><span class="sxs-lookup"><span data-stu-id="908e6-188">DataContractResolver</span></span>](../wcf/samples/datacontractresolver.md)

  - [<span data-ttu-id="908e6-189">KnownAssemblyAttribute</span><span class="sxs-lookup"><span data-stu-id="908e6-189">KnownAssemblyAttribute</span></span>](../wcf/samples/knownassemblyattribute.md)

### <a name="data-contract-resolver-scenarios"></a><span data-ttu-id="908e6-190">資料合約解析程式案例</span><span class="sxs-lookup"><span data-stu-id="908e6-190">Data Contract Resolver Scenarios</span></span>

- <span data-ttu-id="908e6-191">避免在服務中宣告數十個 <xref:System.Runtime.Serialization.KnownTypeAttribute> 物件。</span><span class="sxs-lookup"><span data-stu-id="908e6-191">Avoiding having to declare tens of <xref:System.Runtime.Serialization.KnownTypeAttribute> objects in a service.</span></span>

- <span data-ttu-id="908e6-192">減少 XML BLOB 的大小。</span><span class="sxs-lookup"><span data-stu-id="908e6-192">Reducing the size of the XML blob.</span></span>

## <a name="flowchart"></a><span data-ttu-id="908e6-193">流程圖</span><span class="sxs-lookup"><span data-stu-id="908e6-193">Flowchart</span></span>

<span data-ttu-id="908e6-194">流程圖是已知的開發架構，可以視覺化方式表示網域問題。</span><span class="sxs-lookup"><span data-stu-id="908e6-194">Flowchart is a well-known paradigm to visually represent domain problems.</span></span> <span data-ttu-id="908e6-195">它是我們在 .NET 4 中導入的新控制流程樣式。</span><span class="sxs-lookup"><span data-stu-id="908e6-195">It is a new control flow style we’re introducing in .NET 4.</span></span> <span data-ttu-id="908e6-196">流程圖的核心特性在於，一次只能執行一項活動。</span><span class="sxs-lookup"><span data-stu-id="908e6-196">A core characteristic of Flowchart is that only one activity is executed at any given time.</span></span> <span data-ttu-id="908e6-197">流程圖可以表達迴圈和替代的結果，但本身無法表示同時執行的多個節點。</span><span class="sxs-lookup"><span data-stu-id="908e6-197">Flowcharts can express loops and alternative outcomes, but cannot natively express concurrent execution of multiple nodes.</span></span>

### <a name="getting-started"></a><span data-ttu-id="908e6-198">快速入門</span><span class="sxs-lookup"><span data-stu-id="908e6-198">Getting Started</span></span>

- <span data-ttu-id="908e6-199">在 Visual Studio 2012 中，建立工作流程主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="908e6-199">In Visual Studio 2012, create a workflow console application.</span></span> <span data-ttu-id="908e6-200">在工作流程設計工具中加入流程圖。</span><span class="sxs-lookup"><span data-stu-id="908e6-200">Add a Flowchart in the workflow designer.</span></span>

- <span data-ttu-id="908e6-201">流程圖功能會使用下列類別：</span><span class="sxs-lookup"><span data-stu-id="908e6-201">The flowchart feature uses the following classes:</span></span>

  - <xref:System.Activities.Statements.Flowchart>

  - <xref:System.Activities.Statements.FlowNode>

  - <xref:System.Activities.Statements.FlowDecision>

  - <xref:System.Activities.Statements.FlowStep>

  - <xref:System.Activities.Statements.FlowSwitch%601>

- <span data-ttu-id="908e6-202">範例：</span><span class="sxs-lookup"><span data-stu-id="908e6-202">Samples:</span></span>

  - [<span data-ttu-id="908e6-203">使用 TryCatch 錯誤處理流程圖活動</span><span class="sxs-lookup"><span data-stu-id="908e6-203">Fault Handling in a Flowchart Activity Using TryCatch</span></span>](./samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)

  - [<span data-ttu-id="908e6-204">招聘程序</span><span class="sxs-lookup"><span data-stu-id="908e6-204">Hiring Process</span></span>](./samples/hiring-process.md)

- <span data-ttu-id="908e6-205">設計工具文件：</span><span class="sxs-lookup"><span data-stu-id="908e6-205">Designer Documentation:</span></span>

  - [<span data-ttu-id="908e6-206">Flowchart 活動設計工具</span><span class="sxs-lookup"><span data-stu-id="908e6-206">Flowchart Activity Designers</span></span>](/visualstudio/workflow-designer/flowchart-activity-designers)

### <a name="flowchart-scenarios"></a><span data-ttu-id="908e6-207">流程圖案例</span><span class="sxs-lookup"><span data-stu-id="908e6-207">Flowchart Scenarios</span></span>

<span data-ttu-id="908e6-208">流程圖活動可用來實作猜測遊戲。</span><span class="sxs-lookup"><span data-stu-id="908e6-208">A flowchart activity can be used to implement a guessing game.</span></span> <span data-ttu-id="908e6-209">猜測遊戲非常簡單：電腦會選取一個隨機數字，而玩家必須猜測該數字。</span><span class="sxs-lookup"><span data-stu-id="908e6-209">The guessing game is very simple: the computer selects a random number and the player has to guess that number.</span></span> <span data-ttu-id="908e6-210">當玩家送出每項猜測時，電腦會顯示一個提示 （亦即 「 試試看較低數字 」）。</span><span class="sxs-lookup"><span data-stu-id="908e6-210">When the player submits each guess, the computer shows him a hint (i.e. "try a lower number").</span></span> <span data-ttu-id="908e6-211">如果玩家在 7 次內猜到數字，電腦會對使用者顯示特別的恭賀畫面。</span><span class="sxs-lookup"><span data-stu-id="908e6-211">If the player finds the number in less than 7 attempts, he receives a special congratulation from the computer.</span></span> <span data-ttu-id="908e6-212">您可以透過組合下列程序性活動來實作此遊戲：</span><span class="sxs-lookup"><span data-stu-id="908e6-212">This game can be implemented with a combination of the following procedural activities:</span></span>

- <xref:System.Activities.Statements.Sequence>

- <xref:System.Activities.Statements.While>

- <xref:System.Activities.Statements.Switch%601>

- <xref:System.Activities.Statements.TryCatch>

- <xref:System.Activities.Statements.Assign%601>

- <xref:System.Activities.Statements.If>

## <a name="procedural-activities-sequence-if-foreach-switch-assign-dowhile-while"></a><span data-ttu-id="908e6-213">程序性活動 (Sequence、If、ForEach、Switch、Assign、DoWhile 和 While)</span><span class="sxs-lookup"><span data-stu-id="908e6-213">Procedural activities (Sequence, If, ForEach, Switch, Assign, DoWhile, While)</span></span>

<span data-ttu-id="908e6-214">程序性活動會使用程式設計人員所熟悉的概念來提供模型循序控制流程的機制。</span><span class="sxs-lookup"><span data-stu-id="908e6-214">Procedural activities provide a mechanism to model sequential control flow using concepts that are familiar to programmers.</span></span> <span data-ttu-id="908e6-215">這些活動會啟用傳統結構的程式語言建構，並且在適當的情況下，提供一般程序性語言 (例如 C#/VB) 的語言同位項目。</span><span class="sxs-lookup"><span data-stu-id="908e6-215">These activities enable traditionally structured programming language constructs and, when appropriate, provide language parity with common procedural languages such as C#/VB.</span></span>

### <a name="getting-started"></a><span data-ttu-id="908e6-216">快速入門</span><span class="sxs-lookup"><span data-stu-id="908e6-216">Getting Started</span></span>

- <span data-ttu-id="908e6-217">在 Visual Studio 2012 中，建立工作流程主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="908e6-217">In Visual Studio 2012, create a workflow console application.</span></span> <span data-ttu-id="908e6-218">在工作流程設計工具中加入程序性活動。</span><span class="sxs-lookup"><span data-stu-id="908e6-218">Add procedural activities in the workflow designer.</span></span>

- <span data-ttu-id="908e6-219">範例：</span><span class="sxs-lookup"><span data-stu-id="908e6-219">Samples:</span></span>

  - [<span data-ttu-id="908e6-220">招聘程序</span><span class="sxs-lookup"><span data-stu-id="908e6-220">Hiring Process</span></span>](./samples/hiring-process.md)

  - [<span data-ttu-id="908e6-221">公司購買程序</span><span class="sxs-lookup"><span data-stu-id="908e6-221">Corporate Purchase Process</span></span>](./samples/corporate-purchase-process.md)

- <span data-ttu-id="908e6-222">設計工具文件：</span><span class="sxs-lookup"><span data-stu-id="908e6-222">Designer Documentation:</span></span>

  - [<span data-ttu-id="908e6-223">Parallel 活動設計工具</span><span class="sxs-lookup"><span data-stu-id="908e6-223">Parallel Activity Designer</span></span>](/visualstudio/workflow-designer/parallel-activity-designer)

  - [<span data-ttu-id="908e6-224">ParallelForEach\<T > 活動設計工具</span><span class="sxs-lookup"><span data-stu-id="908e6-224">ParallelForEach\<T> Activity Designer</span></span>](/visualstudio/workflow-designer/parallelforeach-t-activity-designer)

### <a name="procedural-activity-scenarios"></a><span data-ttu-id="908e6-225">程序性活動案例</span><span class="sxs-lookup"><span data-stu-id="908e6-225">Procedural Activity Scenarios</span></span>

- <span data-ttu-id="908e6-226"><xref:System.Activities.Statements.Parallel>：內部網路文件管理系統具有文件核准工作流程。</span><span class="sxs-lookup"><span data-stu-id="908e6-226"><xref:System.Activities.Statements.Parallel>: An intranet document management system has a document approval workflow.</span></span> <span data-ttu-id="908e6-227">文件必須先由數個部門的人員核准，然後才能發行至內部網路。</span><span class="sxs-lookup"><span data-stu-id="908e6-227">Documents need to be approved by people in several departments before they can be published to the intranet.</span></span> <span data-ttu-id="908e6-228">沒有已建立的訂單核准;文件處於 「 待核准 」 階段時可能發生在任何時間。</span><span class="sxs-lookup"><span data-stu-id="908e6-228">There isn’t an established order for the approvals; they can occur at any time while the document is in the "approval pending" phase.</span></span> <span data-ttu-id="908e6-229">當使用者送出文件以供檢閱時，其直屬經理、內部網路管理員和內部通訊經理就必須核准該份文件。</span><span class="sxs-lookup"><span data-stu-id="908e6-229">When a user submits a document for review it must be approved by her direct manager, the intranet administrator, and the internal communications manager.</span></span>

- <span data-ttu-id="908e6-230"><xref:System.Activities.Statements.ParallelForEach%601>：WF 應用程式管理的大型公司內部的企業採購。</span><span class="sxs-lookup"><span data-stu-id="908e6-230"><xref:System.Activities.Statements.ParallelForEach%601>: A WF application manages corporate buys within a large company.</span></span> <span data-ttu-id="908e6-231">企業規則表示，規劃任何採購作業之前，需要三家不同廠商的估價。</span><span class="sxs-lookup"><span data-stu-id="908e6-231">The corporate rules dictate that before planning any purchase operation, the valuations of three different vendors is required.</span></span> <span data-ttu-id="908e6-232">採購部門的員工會從公司的廠商清單中選取三家廠商。</span><span class="sxs-lookup"><span data-stu-id="908e6-232">An employee from the buying department selects three vendors from the company’s vendor list.</span></span> <span data-ttu-id="908e6-233">選取並通知這些廠商之後，公司將等候其經濟提案。</span><span class="sxs-lookup"><span data-stu-id="908e6-233">After these vendors have been selected and notified, the company will wait for their economic proposals.</span></span> <span data-ttu-id="908e6-234">這些提案可以按照任何順序提出。</span><span class="sxs-lookup"><span data-stu-id="908e6-234">The proposals can come in any order.</span></span> <span data-ttu-id="908e6-235">為了在 WF 中實作此案例，我們使用了 <xref:System.Activities.Statements.ParallelForEach%601>，以便逐一查看廠商的集合並且要求其經濟提案。</span><span class="sxs-lookup"><span data-stu-id="908e6-235">To implement this scenario in WF, we use a <xref:System.Activities.Statements.ParallelForEach%601> that will iterate through our collection of vendors and ask for their economic proposals.</span></span> <span data-ttu-id="908e6-236">蒐集所有供應項目之後，系統會選取並顯示最佳提案。</span><span class="sxs-lookup"><span data-stu-id="908e6-236">After all offers are gathered, the best one is selected and displayed.</span></span>

## <a name="invokemethod"></a><span data-ttu-id="908e6-237">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="908e6-237">InvokeMethod</span></span>

<span data-ttu-id="908e6-238"><xref:System.Activities.Statements.InvokeMethod> 活動允許叫用範圍內物件或型別的公用方法。</span><span class="sxs-lookup"><span data-stu-id="908e6-238">The <xref:System.Activities.Statements.InvokeMethod> activity allows invoking public methods in objects or types in scope.</span></span> <span data-ttu-id="908e6-239">它支援叫用包含或不包含參數 (包括參數陣列) 的執行個體和靜態方法，以及泛型方法。</span><span class="sxs-lookup"><span data-stu-id="908e6-239">It supports invoking instance and static methods with or without parameters (including parameter arrays), and generic methods.</span></span> <span data-ttu-id="908e6-240">此外，它也允許以同步和非同步方式執行方法。</span><span class="sxs-lookup"><span data-stu-id="908e6-240">It also allows executing method synchronously and asynchronously.</span></span>

### <a name="getting-started"></a><span data-ttu-id="908e6-241">快速入門</span><span class="sxs-lookup"><span data-stu-id="908e6-241">Getting Started</span></span>

- <span data-ttu-id="908e6-242">在 Visual Studio 2012 中，建立工作流程主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="908e6-242">In Visual Studio 2012, create a workflow console application.</span></span> <span data-ttu-id="908e6-243">在工作流程設計工具中加入 <xref:System.Activities.Statements.InvokeMethod> 活動，並且針對此活動設定靜態和執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="908e6-243">Add an <xref:System.Activities.Statements.InvokeMethod> activity in the workflow designer, and configure static and instance methods on it.</span></span>

- <span data-ttu-id="908e6-244">設計工具文件：[InvokeMethod 活動設計工具](/visualstudio/workflow-designer/invokemethod-activity-designer)</span><span class="sxs-lookup"><span data-stu-id="908e6-244">Designer Documentation: [InvokeMethod Activity Designer](/visualstudio/workflow-designer/invokemethod-activity-designer)</span></span>

### <a name="invokemethod-scenarios"></a><span data-ttu-id="908e6-245">InvokeMethod 案例</span><span class="sxs-lookup"><span data-stu-id="908e6-245">InvokeMethod Scenarios</span></span>

- <span data-ttu-id="908e6-246">需要叫用範圍內物件的方法。</span><span class="sxs-lookup"><span data-stu-id="908e6-246">A method in an object in scope needs to be invoked.</span></span> <span data-ttu-id="908e6-247">例如，需要將某個值加入至字典。</span><span class="sxs-lookup"><span data-stu-id="908e6-247">For example, a value needs to be added to a dictionary.</span></span> <span data-ttu-id="908e6-248">此時，系統會叫用字典執行個體的 Add 方法，並且提供索引鍵和值。</span><span class="sxs-lookup"><span data-stu-id="908e6-248">The Add method of the instance of the dictionary is invoked, and the key and value are provided.</span></span>

- <span data-ttu-id="908e6-249">需要針對舊版 CLR 物件叫用方法。</span><span class="sxs-lookup"><span data-stu-id="908e6-249">A method needs to be invoked on a legacy CLR object.</span></span> <span data-ttu-id="908e6-250">您可以使用 <xref:System.Activities.Statements.InvokeMethod>，而非建立自訂活動來包裝該舊版類別的呼叫 (如果它在工作流程執行期間位於範圍內的話)。</span><span class="sxs-lookup"><span data-stu-id="908e6-250">Instead of creating a custom activity to wrap the call to that legacy class, if it is in scope during the workflow execution, <xref:System.Activities.Statements.InvokeMethod> can be used.</span></span>

## <a name="error-handling-activities"></a><span data-ttu-id="908e6-251">錯誤處理活動</span><span class="sxs-lookup"><span data-stu-id="908e6-251">Error handling activities</span></span>

<span data-ttu-id="908e6-252"><xref:System.Activities.Statements.TryCatch> 活動會提供一項機制來攔截一組包含活動執行時發生的例外狀況 (與在 C#/VB 中建構的 Try/Catch 很相似)。</span><span class="sxs-lookup"><span data-stu-id="908e6-252">The <xref:System.Activities.Statements.TryCatch> activity provides a mechanism for catching exceptions that occur during the execution of a set of contained activities (similar to the Try/Catch construct in C#/VB).</span></span> <span data-ttu-id="908e6-253"><xref:System.Activities.Statements.TryCatch> 提供工作流程層級的例外狀況處理。</span><span class="sxs-lookup"><span data-stu-id="908e6-253"><xref:System.Activities.Statements.TryCatch> provides exception handling at the workflow level.</span></span> <span data-ttu-id="908e6-254">當系統擲回未處理的例外狀況時，就會中止工作流程，而且不會執行 Finally 區塊。</span><span class="sxs-lookup"><span data-stu-id="908e6-254">When an unhandled exception is thrown, the workflow is aborted and the Finally block won’t be executed.</span></span> <span data-ttu-id="908e6-255">這種行為與 C# 一致。</span><span class="sxs-lookup"><span data-stu-id="908e6-255">This behavior is consistent with C#.</span></span>

### <a name="getting-started"></a><span data-ttu-id="908e6-256">快速入門</span><span class="sxs-lookup"><span data-stu-id="908e6-256">Getting Started</span></span>

- <span data-ttu-id="908e6-257">在 Visual Studio 2012 中，建立工作流程主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="908e6-257">In Visual Studio 2012, create a workflow console application.</span></span> <span data-ttu-id="908e6-258">在工作流程設計工具中加入 <xref:System.Activities.Statements.TryCatch> 活動。</span><span class="sxs-lookup"><span data-stu-id="908e6-258">Add a <xref:System.Activities.Statements.TryCatch> activity in the workflow designer.</span></span>

- <span data-ttu-id="908e6-259">範例：[使用 TryCatch 錯誤處理流程圖活動](./samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)</span><span class="sxs-lookup"><span data-stu-id="908e6-259">Sample: [Fault Handling in a Flowchart Activity Using TryCatch](./samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)</span></span>

- <span data-ttu-id="908e6-260">設計工具文件：[Error Handling 活動設計工具](/visualstudio/workflow-designer/error-handling-activity-designers)</span><span class="sxs-lookup"><span data-stu-id="908e6-260">Designer Documentation: [Error Handling Activity Designers](/visualstudio/workflow-designer/error-handling-activity-designers)</span></span>

### <a name="error-handling-scenarios"></a><span data-ttu-id="908e6-261">錯誤處理案例</span><span class="sxs-lookup"><span data-stu-id="908e6-261">Error handling scenarios</span></span>

<span data-ttu-id="908e6-262">需要執行一組活動，而且需要在發生錯誤時執行特定邏輯。</span><span class="sxs-lookup"><span data-stu-id="908e6-262">A set of activities needs to be executed, and specific logic needs to be executed when an error occurs.</span></span> <span data-ttu-id="908e6-263">如果在錯誤處理邏輯期間發現錯誤無法復原，就會重新擲回例外狀況，而且父活動 (或主機) 將會處理此問題。</span><span class="sxs-lookup"><span data-stu-id="908e6-263">If during that error handling logic it is found that the error is not recoverable, the exception will be rethrown, and the parent activity (or the host) will deal with the problem.</span></span>

## <a name="pick-activity"></a><span data-ttu-id="908e6-264">Pick 活動</span><span class="sxs-lookup"><span data-stu-id="908e6-264">Pick activity</span></span>

<span data-ttu-id="908e6-265"><xref:System.Activities.Statements.Pick> 活動會提供 WF 中以事件為主的控制流程模型。</span><span class="sxs-lookup"><span data-stu-id="908e6-265">The <xref:System.Activities.Statements.Pick> Activity provides event-based control flow modeling in WF.</span></span> <span data-ttu-id="908e6-266"><xref:System.Activities.Statements.Pick> 包含許多分支，每個分支會先等待特定事件發生後，再開始執行。</span><span class="sxs-lookup"><span data-stu-id="908e6-266"><xref:System.Activities.Statements.Pick> contains many branches where each branch waits for a particular event to occur before running.</span></span> <span data-ttu-id="908e6-267">在此設定中，<xref:System.Activities.Statements.Pick> 的行為與 <xref:System.Activities.Statements.Switch%601> 很相似，因為此活動只會執行它所接聽的其中一個事件集。</span><span class="sxs-lookup"><span data-stu-id="908e6-267">In this setup, a <xref:System.Activities.Statements.Pick> behaves similar to a <xref:System.Activities.Statements.Switch%601> to which the Activity will execute only one of the set of events it is listening.</span></span> <span data-ttu-id="908e6-268">每個分支都是由事件驅動，而發生的事件會先執行對應的分支。</span><span class="sxs-lookup"><span data-stu-id="908e6-268">Each branch is event driven and the event that occurs runs the corresponding branch first.</span></span> <span data-ttu-id="908e6-269">所有其他的分支都會取消並停止接聽事件。</span><span class="sxs-lookup"><span data-stu-id="908e6-269">All other branches cancel and stop listening for events.</span></span>

### <a name="getting-started"></a><span data-ttu-id="908e6-270">快速入門</span><span class="sxs-lookup"><span data-stu-id="908e6-270">Getting Started</span></span>

- <span data-ttu-id="908e6-271">在 Visual Studio 2012 中，建立工作流程主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="908e6-271">In Visual Studio 2012, create a workflow console application.</span></span> <span data-ttu-id="908e6-272">在工作流程設計工具中加入 <xref:System.Activities.Statements.Pick> 活動。</span><span class="sxs-lookup"><span data-stu-id="908e6-272">Add a <xref:System.Activities.Statements.Pick> activity in the workflow designer.</span></span>

- <span data-ttu-id="908e6-273">範例：[使用 Pick 活動](./samples/using-the-pick-activity.md)</span><span class="sxs-lookup"><span data-stu-id="908e6-273">Sample: [Using the Pick Activity](./samples/using-the-pick-activity.md)</span></span>

- <span data-ttu-id="908e6-274">設計工具的文件：[Pick 活動設計工具](/visualstudio/workflow-designer/pick-activity-designer)</span><span class="sxs-lookup"><span data-stu-id="908e6-274">Designer documentation: [Pick Activity Designer](/visualstudio/workflow-designer/pick-activity-designer)</span></span>

### <a name="pick-scenario"></a><span data-ttu-id="908e6-275">Pick 案例</span><span class="sxs-lookup"><span data-stu-id="908e6-275">Pick Scenario</span></span>

<span data-ttu-id="908e6-276">系統需要提示使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="908e6-276">A user needs to be prompted for input.</span></span> <span data-ttu-id="908e6-277">在一般情況下，開發人員會使用 <xref:System.Console.ReadLine%2A> 之類的方法呼叫來提示使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="908e6-277">Under normal circumstances, the developer would use a method call like <xref:System.Console.ReadLine%2A> to prompt for a user’s input.</span></span> <span data-ttu-id="908e6-278">這種設定的問題在於，直到使用者輸入某些內容為止，程式都會處於等候狀態。</span><span class="sxs-lookup"><span data-stu-id="908e6-278">The problem with this setup is that the program waits until the user enters something.</span></span> <span data-ttu-id="908e6-279">在此案例中，您需要使用逾時將封鎖的活動解除封鎖。</span><span class="sxs-lookup"><span data-stu-id="908e6-279">In this scenario, a time-out is needed to unblock a blocking activity.</span></span> <span data-ttu-id="908e6-280">常見的案例就是要求在指定的一段時間內完成工作。</span><span class="sxs-lookup"><span data-stu-id="908e6-280">A common scenario is one that requires a task to be completed within a given time duration.</span></span> <span data-ttu-id="908e6-281">讓封鎖的活動逾時則為 Pick 發揮功能的案例。</span><span class="sxs-lookup"><span data-stu-id="908e6-281">Timing out a blocking activity is a scenario where Pick adds a lot of value.</span></span>

## <a name="wcf-routing-service"></a><span data-ttu-id="908e6-282">WCF 路由服務</span><span class="sxs-lookup"><span data-stu-id="908e6-282">WCF Routing Service</span></span>

<span data-ttu-id="908e6-283">路由服務被設計為泛型軟體路由器，可讓您控制 WCF 訊息如何在您的用戶端和服務之間流動。</span><span class="sxs-lookup"><span data-stu-id="908e6-283">The Routing Service is designed to be a generic software Router that allows you to control how WCF messages flow in between your clients and services.</span></span> <span data-ttu-id="908e6-284">路由服務可讓您減少您的用戶端，從您的服務，讓您根據設定的更多自由可支援，和彈性，您必須考慮如何裝載您的服務時。</span><span class="sxs-lookup"><span data-stu-id="908e6-284">The Routing Service allows you to decouple your clients from your services, which gives you much more freedom in terms of the configurations that you can support and the flexibility you have when considering how to host your services.</span></span> <span data-ttu-id="908e6-285">在.NET 3.5 中，用戶端和服務必須緊密關聯;用戶端必須知道的所有服務與互動所需和它們所在位置。</span><span class="sxs-lookup"><span data-stu-id="908e6-285">In .NET 3.5, clients and services were tightly coupled; a client had to know about all of the services it needed to talk to and where they were located.</span></span> <span data-ttu-id="908e6-286">此外，.NET Framework 3.5 中的 WCF 具有下列限制：</span><span class="sxs-lookup"><span data-stu-id="908e6-286">In addition, WCF in .NET Framework 3.5 had the following limitations:</span></span>

- <span data-ttu-id="908e6-287">錯誤處理很複雜，因為此邏輯必須透過硬式編碼寫入用戶端。</span><span class="sxs-lookup"><span data-stu-id="908e6-287">Error handling was complex, as this logic had to be hard-coded into the client.</span></span>

- <span data-ttu-id="908e6-288">用戶端與服務一定要使用相同的繫結。</span><span class="sxs-lookup"><span data-stu-id="908e6-288">Clients and services had to always use the same bindings.</span></span>

- <span data-ttu-id="908e6-289">很少妥善分解服務：讓用戶端與實作所有功能的單一服務通訊會比在多個服務之間選擇更簡單。</span><span class="sxs-lookup"><span data-stu-id="908e6-289">Services were rarely well factored: it is easier to have the client talk to one service which implements everything, rather than needing to choose between multiple services.</span></span>

<span data-ttu-id="908e6-290">.NET 4 中的路由服務可讓您更輕鬆地解決這些問題。</span><span class="sxs-lookup"><span data-stu-id="908e6-290">The routing service in .NET 4 is designed to make these problems easier to solve.</span></span> <span data-ttu-id="908e6-291">新的路由服務具有下列功能：</span><span class="sxs-lookup"><span data-stu-id="908e6-291">The new routing service has the following features:</span></span>

1. <span data-ttu-id="908e6-292">以內容為基礎的路由 (<xref:System.ServiceModel.Dispatcher.MessageFilter> 物件會檢查訊息來判斷應該傳送的目的地)。</span><span class="sxs-lookup"><span data-stu-id="908e6-292">Content based routing (<xref:System.ServiceModel.Dispatcher.MessageFilter> objects examine a message to determine where it should be sent.)</span></span>

2. <span data-ttu-id="908e6-293">通訊協定橋接 （傳輸與訊息）</span><span class="sxs-lookup"><span data-stu-id="908e6-293">Protocol bridging (transport & message)</span></span>

3. <span data-ttu-id="908e6-294">錯誤處理 (路由器會攔截通訊例外狀況並容錯移轉至備份端點)。</span><span class="sxs-lookup"><span data-stu-id="908e6-294">Error handling (the router catches communication exceptions and fails over to backup endpoints)</span></span>

4. <span data-ttu-id="908e6-295"><xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> 和路由組態的動態 (記憶體中) 更新。</span><span class="sxs-lookup"><span data-stu-id="908e6-295">Dynamic (in memory) update of <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> and Routing Configuration.</span></span>

### <a name="getting-started"></a><span data-ttu-id="908e6-296">快速入門</span><span class="sxs-lookup"><span data-stu-id="908e6-296">Getting Started</span></span>

1. <span data-ttu-id="908e6-297">文件：[路由傳送](../wcf/feature-details/routing.md)</span><span class="sxs-lookup"><span data-stu-id="908e6-297">Documentation: [Routing](../wcf/feature-details/routing.md)</span></span>

2. <span data-ttu-id="908e6-298">範例：[路由服務&#91;WCF 範例&#93;](../wcf/samples/routing-services.md)</span><span class="sxs-lookup"><span data-stu-id="908e6-298">Samples: [Routing Services &#91;WCF Samples&#93;](../wcf/samples/routing-services.md)</span></span>

3. <span data-ttu-id="908e6-299">部落格：[路由規則 ！](https://go.microsoft.com/fwlink/?LinkId=204956)</span><span class="sxs-lookup"><span data-stu-id="908e6-299">Blog: [Routing Rules!](https://go.microsoft.com/fwlink/?LinkId=204956)</span></span>

### <a name="routing-scenarios"></a><span data-ttu-id="908e6-300">路由案例</span><span class="sxs-lookup"><span data-stu-id="908e6-300">Routing Scenarios</span></span>

<span data-ttu-id="908e6-301">在下列案例中，路由服務很有用：</span><span class="sxs-lookup"><span data-stu-id="908e6-301">The routing service is useful in the following scenarios:</span></span>

- <span data-ttu-id="908e6-302">用戶端可以與多個服務通訊，而不需要直接處理所有服務。</span><span class="sxs-lookup"><span data-stu-id="908e6-302">Clients can talk to multiple services without having to address them all directly.</span></span>

- <span data-ttu-id="908e6-303">用戶端可以針對用戶端要求執行其他邏輯，以便判斷要路由傳送的目的地。</span><span class="sxs-lookup"><span data-stu-id="908e6-303">Clients can perform additional logic on a client request to determine where to route it</span></span>

- <span data-ttu-id="908e6-304">將用戶端所執行的作業分解成多個服務實作，而不需要重構用戶端。</span><span class="sxs-lookup"><span data-stu-id="908e6-304">Decompose the operations a client performs into multiple service implementations without refactoring the client.</span></span>

- <span data-ttu-id="908e6-305">用戶端與服務可以宣告具有不同安全性設定的不同繫結。</span><span class="sxs-lookup"><span data-stu-id="908e6-305">Clients and services can speak different bindings with different security settings.</span></span>

- <span data-ttu-id="908e6-306">用戶端可以具備更健全的功能，以防範失敗或無法使用服務的情況。</span><span class="sxs-lookup"><span data-stu-id="908e6-306">Clients can be enabled to be more robust against failure or the unavailability of services.</span></span>

## <a name="wcf-discovery"></a><span data-ttu-id="908e6-307">WCF 探索</span><span class="sxs-lookup"><span data-stu-id="908e6-307">WCF Discovery</span></span>

<span data-ttu-id="908e6-308">WCF 探索是一種架構的技術，可讓您將應用程式基礎結構的探索機制。</span><span class="sxs-lookup"><span data-stu-id="908e6-308">WCF Discovery is a framework technology that allows you to incorporate a discovery mechanism to your application infrastructure.</span></span> <span data-ttu-id="908e6-309">您可以使用這項技術，讓服務成為可探索的服務，並且設定用戶端來搜尋服務。</span><span class="sxs-lookup"><span data-stu-id="908e6-309">You can use this to make your service discoverable, and configure your clients to search for services.</span></span> <span data-ttu-id="908e6-310">用戶端不再需要對端點進行硬式編碼，讓應用程式更健全並提高容錯能力。</span><span class="sxs-lookup"><span data-stu-id="908e6-310">Clients no longer need to be hard coded with endpoint, making your application more robust and fault tolerant.</span></span> <span data-ttu-id="908e6-311">探索是在應用程式中建置自動組態功能的完美平台。</span><span class="sxs-lookup"><span data-stu-id="908e6-311">Discovery is the perfect platform to build auto-configuration capabilities into your application.</span></span>

<span data-ttu-id="908e6-312">此產品是以 WS-Discovery 標準為建置基礎。</span><span class="sxs-lookup"><span data-stu-id="908e6-312">The product is built on top of the WS-Discovery standard.</span></span> <span data-ttu-id="908e6-313">其設計目的是要成為可互通、可擴充且泛型的產品。</span><span class="sxs-lookup"><span data-stu-id="908e6-313">It’s designed to be interoperable, extensible, and generic.</span></span> <span data-ttu-id="908e6-314">此產品支援兩種作業模式：</span><span class="sxs-lookup"><span data-stu-id="908e6-314">The product supports two modes of operation:</span></span>

1. <span data-ttu-id="908e6-315">受管理：網路上有一個了解現有服務的實體，因此用戶端會直接查詢此實體以取得資訊。</span><span class="sxs-lookup"><span data-stu-id="908e6-315">Managed: where there is an entity on the network knowledgeable about existing services, clients query it directly for information.</span></span> <span data-ttu-id="908e6-316">這種模式類似於 Active Directory。</span><span class="sxs-lookup"><span data-stu-id="908e6-316">This is analogous to Active Directory.</span></span>

2. <span data-ttu-id="908e6-317">臨機操作：用戶端會使用多點傳送訊息來找出服務。</span><span class="sxs-lookup"><span data-stu-id="908e6-317">Ad-hoc: where clients use multicast messages to locate services.</span></span>

<span data-ttu-id="908e6-318">此外，探索訊息無從驗證網路通訊協定。您可以在支援模式需求的任何通訊協定上使用這些訊息。</span><span class="sxs-lookup"><span data-stu-id="908e6-318">Furthermore, discovery messages are network protocol agnostic; you can use them on top any protocol that supports the mode requirements.</span></span> <span data-ttu-id="908e6-319">例如，透過 UDP 通道或支援多點傳送訊息的任何其他網路傳送多點傳送的訊息。</span><span class="sxs-lookup"><span data-stu-id="908e6-319">For example, discovery multicast messages can be sent over the UDP channel or any other network that supports multicast messaging.</span></span> <span data-ttu-id="908e6-320">這些設計與功能彈性結合可讓您調整方案明確地探索的點。</span><span class="sxs-lookup"><span data-stu-id="908e6-320">These design points, combined with feature flexibility, allow you to adapt the discovery specifically to your solution.</span></span>

### <a name="getting-started"></a><span data-ttu-id="908e6-321">快速入門</span><span class="sxs-lookup"><span data-stu-id="908e6-321">Getting Started</span></span>

- <span data-ttu-id="908e6-322">文件：[WCF 探索](../wcf/feature-details/wcf-discovery.md)</span><span class="sxs-lookup"><span data-stu-id="908e6-322">Documentation: [WCF Discovery](../wcf/feature-details/wcf-discovery.md)</span></span>

- <span data-ttu-id="908e6-323">範例：[探索 （範例）](../wcf/samples/discovery-samples.md)</span><span class="sxs-lookup"><span data-stu-id="908e6-323">Samples: [Discovery (Samples)](../wcf/samples/discovery-samples.md)</span></span>

### <a name="discovery-scenarios"></a><span data-ttu-id="908e6-324">探索案例</span><span class="sxs-lookup"><span data-stu-id="908e6-324">Discovery Scenarios</span></span>

<span data-ttu-id="908e6-325">開發人員不想要對端點進行硬式編碼，因為它在服務可用時處於未知狀態。</span><span class="sxs-lookup"><span data-stu-id="908e6-325">A developer doesn't want to hard code endpoints, since it is unknown when my service will be available.</span></span> <span data-ttu-id="908e6-326">不過，開發人員想要在執行階段選擇服務。</span><span class="sxs-lookup"><span data-stu-id="908e6-326">Instead, the developer wants to choose a service at runtime.</span></span> <span data-ttu-id="908e6-327">因此，應用程式的元件之間需要降低耦合、提高健全度，以及自動組態功能。</span><span class="sxs-lookup"><span data-stu-id="908e6-327">More decoupling, robustness, and auto-configuration is needed between the components in the application.</span></span>

## <a name="tracking"></a><span data-ttu-id="908e6-328">追蹤</span><span class="sxs-lookup"><span data-stu-id="908e6-328">Tracking</span></span>

<span data-ttu-id="908e6-329">工作流程追蹤可執行的工作流程執行個體的深入解析。</span><span class="sxs-lookup"><span data-stu-id="908e6-329">Workflow tracking provides insight into the execution of a workflow instance.</span></span> <span data-ttu-id="908e6-330">從工作流程工作流程執行個體層級，並在工作流程內的活動執行時，會發出追蹤事件。</span><span class="sxs-lookup"><span data-stu-id="908e6-330">The tracking events are emitted from a workflow at the workflow instance level and when activities within the workflow execute.</span></span> <span data-ttu-id="908e6-331">您必須將工作流程追蹤參與者加入至工作流程主機，才能訂閱追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="908e6-331">A workflow tracking participant needs to be added to the workflow host to subscribe to tracking records.</span></span> <span data-ttu-id="908e6-332">系統會使用追蹤設定檔來篩選追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="908e6-332">The tracking records are filtered using a tracking profile.</span></span> <span data-ttu-id="908e6-333">.NET Framework 提供了 ETW (事件追蹤的 Windows) 追蹤參與者，以及基本的設定檔安裝在 machine.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="908e6-333">The .NET Framework provides an ETW (Event Tracing for Windows) tracking participant, and a basic profile is installed in the machine.config file.</span></span>

### <a name="getting-started"></a><span data-ttu-id="908e6-334">快速入門</span><span class="sxs-lookup"><span data-stu-id="908e6-334">Getting Started</span></span>

1. <span data-ttu-id="908e6-335">在 Visual Studio 2010 中，建立 WCF 工作流程服務應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="908e6-335">In Visual Studio 2010, create a WCF Workflow Service Application project.</span></span> <span data-ttu-id="908e6-336">一組 <xref:System.ServiceModel.Activities.Receive> 和 <xref:System.ServiceModel.Activities.SendReply> 將置於畫布上，以便開始。</span><span class="sxs-lookup"><span data-stu-id="908e6-336">A <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply> pair will be placed on your canvas to start.</span></span>

2. <span data-ttu-id="908e6-337">開啟 web.config 並加入不含設定檔的 ETW 追蹤行為。</span><span class="sxs-lookup"><span data-stu-id="908e6-337">Open the web.config and add an ETW tracking behavior with no profile.</span></span>

    1. <span data-ttu-id="908e6-338">系統會使用預設設定檔。</span><span class="sxs-lookup"><span data-stu-id="908e6-338">The default profile is used.</span></span>

    2. <span data-ttu-id="908e6-339">開啟事件檢視器，並啟用下列節點中的分析通道：**事件檢視器**， **Applications and Services Logs**， **Microsoft**， **Windows**，**應用程式伺服器-應用程式**.</span><span class="sxs-lookup"><span data-stu-id="908e6-339">Open event viewer and enable the analytic channel in the following node: **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="908e6-340">以滑鼠右鍵按一下**分析**，然後選取**啟用記錄**。</span><span class="sxs-lookup"><span data-stu-id="908e6-340">Right-click **Analytic** and select **Enable Log**.</span></span>

    3. <span data-ttu-id="908e6-341">執行工作流程服務。</span><span class="sxs-lookup"><span data-stu-id="908e6-341">Run the workflow service.</span></span>

    4. <span data-ttu-id="908e6-342">在事件檢視器中查看工作流程追蹤事件。</span><span class="sxs-lookup"><span data-stu-id="908e6-342">Observe the workflow tracking events in event viewer.</span></span>

3. <span data-ttu-id="908e6-343">範例：[追蹤](./samples/tracking.md)</span><span class="sxs-lookup"><span data-stu-id="908e6-343">Samples: [Tracking](./samples/tracking.md)</span></span>

4. <span data-ttu-id="908e6-344">概念文件：[工作流程追蹤及追蹤](workflow-tracking-and-tracing.md)</span><span class="sxs-lookup"><span data-stu-id="908e6-344">Conceptual documentation: [Workflow Tracking and Tracing](workflow-tracking-and-tracing.md)</span></span>

## <a name="sql-workflow-instance-store"></a><span data-ttu-id="908e6-345">SQL 工作流程執行個體存放區</span><span class="sxs-lookup"><span data-stu-id="908e6-345">SQL Workflow Instance Store</span></span>

<span data-ttu-id="908e6-346"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 是以 SQL Server 為基礎的執行個體存放區實作。</span><span class="sxs-lookup"><span data-stu-id="908e6-346">The <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> is a SQL Server-based implementation of an instance store.</span></span> <span data-ttu-id="908e6-347">執行個體存放區會儲存執行中執行個體的狀態以及載入和繼續該執行個體所需的所有資料。</span><span class="sxs-lookup"><span data-stu-id="908e6-347">An instance store stores the state of a running instance together with all data necessary to load and resume that instance.</span></span> <span data-ttu-id="908e6-348">如果工作流程會保存，服務主機就會指示執行個體存放區儲存執行個體狀態，而且當該執行個體的訊息送達或延遲活動過期時，它就會指示執行個體存放區載入執行個體狀態。</span><span class="sxs-lookup"><span data-stu-id="908e6-348">The service host instructs the instance store to save the instance state if the workflow persists, and it instructs the instance store to load the instance state when a message arrives for that instance or a delay activity expires.</span></span>

### <a name="getting-started"></a><span data-ttu-id="908e6-349">快速入門</span><span class="sxs-lookup"><span data-stu-id="908e6-349">Getting Started</span></span>

1. <span data-ttu-id="908e6-350">在 Visual Studio 2012 中，建立包含隱含或明確的工作流程<xref:System.Activities.Statements.Persist>活動。</span><span class="sxs-lookup"><span data-stu-id="908e6-350">In Visual Studio 2012, create a Workflow that contains an implicit or explicit <xref:System.Activities.Statements.Persist> activity.</span></span> <span data-ttu-id="908e6-351">將 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 行為加入至工作流程服務主機。</span><span class="sxs-lookup"><span data-stu-id="908e6-351">Add the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> behavior to your workflow service host.</span></span> <span data-ttu-id="908e6-352">您可以在程式碼或應用程式組態檔中進行這項作業。</span><span class="sxs-lookup"><span data-stu-id="908e6-352">This can be done in code or in the application configuration file.</span></span>

2. <span data-ttu-id="908e6-353">範例：[持續性](./samples/persistence.md)</span><span class="sxs-lookup"><span data-stu-id="908e6-353">Samples: [Persistence](./samples/persistence.md)</span></span>

3. <span data-ttu-id="908e6-354">概念文件：[SQL 工作流程執行個體存放區](sql-workflow-instance-store.md)。</span><span class="sxs-lookup"><span data-stu-id="908e6-354">Conceptual documentation: [SQL Workflow Instance Store](sql-workflow-instance-store.md).</span></span>
