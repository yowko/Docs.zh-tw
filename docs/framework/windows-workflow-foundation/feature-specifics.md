---
title: Windows Workflow Foundation 功能內容
description: 本文說明 .NET Framework 4 新增至 Windows Workflow Foundation 的新功能，以及這些功能可能會很有用的案例。
ms.date: 03/30/2017
ms.assetid: e84d12da-a055-45f6-b4d1-878d127b46b6
ms.openlocfilehash: ae15f3ed536967cb15d1a5913f9ca1eab8a510d9
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554602"
---
# <a name="windows-workflow-foundation-feature-specifics"></a><span data-ttu-id="ec160-103">Windows Workflow Foundation 功能內容</span><span class="sxs-lookup"><span data-stu-id="ec160-103">Windows Workflow Foundation Feature Specifics</span></span>

<span data-ttu-id="ec160-104">.NET Framework 4 會將一些功能新增至 Windows Workflow Foundation。</span><span class="sxs-lookup"><span data-stu-id="ec160-104">.NET Framework 4 adds a number of features to Windows Workflow Foundation.</span></span> <span data-ttu-id="ec160-105">本文件將描述一些新功能，並且詳細說明適合使用這些功能的案例。</span><span class="sxs-lookup"><span data-stu-id="ec160-105">This document describes a number of the new features, and gives details about scenarios in which they may be useful.</span></span>

## <a name="messaging-activities"></a><span data-ttu-id="ec160-106">傳訊活動</span><span class="sxs-lookup"><span data-stu-id="ec160-106">Messaging Activities</span></span>

<span data-ttu-id="ec160-107">訊息活動 (<xref:System.ServiceModel.Activities.Receive> 、 <xref:System.ServiceModel.Activities.SendReply> 、 <xref:System.ServiceModel.Activities.Send> 、 <xref:System.ServiceModel.Activities.ReceiveReply>) 用來從您的工作流程傳送和接收 WCF 訊息。</span><span class="sxs-lookup"><span data-stu-id="ec160-107">The messaging activities (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.ReceiveReply>) are used to send and receive WCF messages from your workflow.</span></span> <span data-ttu-id="ec160-108"><xref:System.ServiceModel.Activities.Receive> 和 <xref:System.ServiceModel.Activities.SendReply> 活動可用來形成 Windows Communication Foundation (WCF) 服務作業，此作業會透過 WSDL 公開，就像標準 WCF web 服務一樣。</span><span class="sxs-lookup"><span data-stu-id="ec160-108"><xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply> activities are used to form a Windows Communication Foundation (WCF) service operation that is exposed via WSDL just like standard WCF web services.</span></span> <span data-ttu-id="ec160-109"><xref:System.ServiceModel.Activities.Send> 和 <xref:System.ServiceModel.Activities.ReceiveReply> 可用來取用類似于 WCF 的 web 服務 <xref:System.ServiceModel.ChannelFactory> ; 針對產生預先設定活動的 Workflow Foundation 也有 **加入服務參考** 體驗。</span><span class="sxs-lookup"><span data-stu-id="ec160-109"><xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.ReceiveReply> are used to consume a web service similar to a WCF <xref:System.ServiceModel.ChannelFactory>; an **Add Service Reference** experience also exists for Workflow Foundation that generates pre-configured activities.</span></span>

### <a name="getting-started-with-messaging-activities"></a><span data-ttu-id="ec160-110">傳訊活動使用者入門</span><span class="sxs-lookup"><span data-stu-id="ec160-110">Getting Started with Messaging Activities</span></span>

- <span data-ttu-id="ec160-111">在 Visual Studio 2012 中，建立 WCF 工作流程服務應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="ec160-111">In Visual Studio 2012, create a WCF Workflow Service Application project.</span></span> <span data-ttu-id="ec160-112">一組 <xref:System.ServiceModel.Activities.Receive> 和 <xref:System.ServiceModel.Activities.SendReply> 將置於畫布上。</span><span class="sxs-lookup"><span data-stu-id="ec160-112">A <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply> pair will be placed on your canvas.</span></span>

- <span data-ttu-id="ec160-113">以滑鼠右鍵按一下專案，然後選取 [ **加入服務參考**]。</span><span class="sxs-lookup"><span data-stu-id="ec160-113">Right-click on the project and select **Add Service Reference**.</span></span> <span data-ttu-id="ec160-114">指向現有的 web 服務 WSDL，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="ec160-114">Point to an existing web service WSDL and click **OK**.</span></span> <span data-ttu-id="ec160-115">建立您的專案，以顯示 (<xref:System.ServiceModel.Activities.Send> 在工具箱中使用和) 所產生的活動 <xref:System.ServiceModel.Activities.ReceiveReply> 。</span><span class="sxs-lookup"><span data-stu-id="ec160-115">Build your project to show the generated activities (implemented using <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.ReceiveReply>) in your toolbox.</span></span>

- [<span data-ttu-id="ec160-116">工作流程服務檔</span><span class="sxs-lookup"><span data-stu-id="ec160-116">Workflow services documentation</span></span>](../wcf/feature-details/workflow-services.md)

### <a name="messaging-activities-example-scenario"></a><span data-ttu-id="ec160-117">傳訊活動範例案例</span><span class="sxs-lookup"><span data-stu-id="ec160-117">Messaging Activities Example Scenario</span></span>

<span data-ttu-id="ec160-118">`BestPriceFinder`服務會呼叫多個航空公司服務，以找出特定路線的最佳票證價格。</span><span class="sxs-lookup"><span data-stu-id="ec160-118">A `BestPriceFinder` service calls out to multiple airline services to find the best ticket price for a particular route.</span></span> <span data-ttu-id="ec160-119">若要執行此案例，您必須使用訊息活動來接收價格要求、從後端服務取得價格，並以最佳價格回復價格要求。</span><span class="sxs-lookup"><span data-stu-id="ec160-119">Implementing this scenario would require you to use the message activities to receive the price request, retrieve the prices from the back-end services, and reply to the price request with the best price.</span></span> <span data-ttu-id="ec160-120">您也需要使用其他的現成活動來建立商務邏輯，以計算最佳價格。</span><span class="sxs-lookup"><span data-stu-id="ec160-120">It would also require you to use other out-of-box activities to create the business logic for calculating the best price.</span></span>

## <a name="workflowservicehost"></a><span data-ttu-id="ec160-121">WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="ec160-121">WorkflowServiceHost</span></span>

<span data-ttu-id="ec160-122"><xref:System.ServiceModel.WorkflowServiceHost>是現成的工作流程主機，可支援多個實例、設定和 WCF 訊息 (雖然工作流程不需要使用訊息來裝載) 。</span><span class="sxs-lookup"><span data-stu-id="ec160-122">The <xref:System.ServiceModel.WorkflowServiceHost> is the out-of-box workflow host that supports multiple instances, configuration, and WCF messaging (although the workflows aren't required to use messaging in order to be hosted).</span></span> <span data-ttu-id="ec160-123">此外，它也會透過一組服務行為，與持續性、追蹤和執行個體控制項整合。</span><span class="sxs-lookup"><span data-stu-id="ec160-123">It also integrates with persistence, tracking, and instance control through a set of service behaviors.</span></span> <span data-ttu-id="ec160-124">就像 WCF 的一樣 <xref:System.ServiceModel.ServiceHost> ， <xref:System.ServiceModel.WorkflowServiceHost> 可以在主控台/WINFORMS/WPF 應用程式或 Windows 服務中自我裝載，或是在 IIS 或 WAS 中) service1.xamlx 檔案的 web 裝載 (。</span><span class="sxs-lookup"><span data-stu-id="ec160-124">Just like WCF's <xref:System.ServiceModel.ServiceHost>, the <xref:System.ServiceModel.WorkflowServiceHost> can be self-hosted in a console/WinForms/WPF application or Windows service, or web-hosted (as a .xamlx file) in IIS or WAS.</span></span>

### <a name="getting-started-with-workflow-service-host"></a><span data-ttu-id="ec160-125">工作流程服務主機使用者入門</span><span class="sxs-lookup"><span data-stu-id="ec160-125">Getting Started with Workflow Service Host</span></span>

- <span data-ttu-id="ec160-126">在 Visual Studio 2010 中，建立 WCF 工作流程服務應用程式專案：此專案將設定為 <xref:System.ServiceModel.WorkflowServiceHost> 在 web 主機環境中使用。</span><span class="sxs-lookup"><span data-stu-id="ec160-126">In Visual Studio 2010, create a WCF Workflow Service Application project: this project will be set up to use <xref:System.ServiceModel.WorkflowServiceHost> in a web-host environment.</span></span>

- <span data-ttu-id="ec160-127">若要裝載非傳訊工作流程，請加入會根據訊息建立執行個體的自訂 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>。</span><span class="sxs-lookup"><span data-stu-id="ec160-127">In order to host a non-messaging workflow, add a custom <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> that will create the instance based on a message.</span></span>

- <span data-ttu-id="ec160-128">您可以將 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> 加入至 <xref:System.ServiceModel.WorkflowServiceHost>，然後使用 <xref:System.ServiceModel.Activities.WorkflowControlClient>，藉以控制工作流程執行個體 (例如暫停或終止)。</span><span class="sxs-lookup"><span data-stu-id="ec160-128">Workflow instances can be controlled (e.g. suspended or terminated) by adding a <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> to the <xref:System.ServiceModel.WorkflowServiceHost> and then using a <xref:System.ServiceModel.Activities.WorkflowControlClient>.</span></span>

- <span data-ttu-id="ec160-129">您可以在下列章節中找到 <xref:System.ServiceModel.WorkflowServiceHost> 的範例：</span><span class="sxs-lookup"><span data-stu-id="ec160-129">Samples for the <xref:System.ServiceModel.WorkflowServiceHost> can be found in the following sections:</span></span>

  - [<span data-ttu-id="ec160-130">執行</span><span class="sxs-lookup"><span data-stu-id="ec160-130">Execution</span></span>](./samples/execution.md)

  - <span data-ttu-id="ec160-131">應用程式： [暫停的實例管理](./samples/suspended-instance-management.md)</span><span class="sxs-lookup"><span data-stu-id="ec160-131">Application: [Suspended Instance Management](./samples/suspended-instance-management.md)</span></span>

- [<span data-ttu-id="ec160-132">裝載工作流程服務總覽</span><span class="sxs-lookup"><span data-stu-id="ec160-132">Hosting Workflow services overview</span></span>](../wcf/feature-details/hosting-workflow-services-overview.md)

### <a name="workflowservicehost-scenario"></a><span data-ttu-id="ec160-133">WorkflowServiceHost 案例</span><span class="sxs-lookup"><span data-stu-id="ec160-133">WorkflowServiceHost Scenario</span></span>

<span data-ttu-id="ec160-134">BestPriceFinder 服務會呼叫多個航空公司服務，以找出特定路線的最佳票證價格。</span><span class="sxs-lookup"><span data-stu-id="ec160-134">A BestPriceFinder service calls out to multiple airline services to find the best ticket price for a particular route.</span></span> <span data-ttu-id="ec160-135">若要執行此案例，您必須在中裝載工作流程 <xref:System.ServiceModel.WorkflowServiceHost> 。</span><span class="sxs-lookup"><span data-stu-id="ec160-135">Implementing this scenario would require you to host the workflow in <xref:System.ServiceModel.WorkflowServiceHost>.</span></span> <span data-ttu-id="ec160-136">它也會使用訊息活動來接收價格要求、從後端服務中取出價格，並以最佳價格回復價格要求。</span><span class="sxs-lookup"><span data-stu-id="ec160-136">It would also use the message activities to receive the price request, retrieve the prices from the back-end services, and reply to the price request with the best price.</span></span>

## <a name="correlation"></a><span data-ttu-id="ec160-137">相互關聯</span><span class="sxs-lookup"><span data-stu-id="ec160-137">Correlation</span></span>

<span data-ttu-id="ec160-138">相互關聯是指下列其中一種情況：</span><span class="sxs-lookup"><span data-stu-id="ec160-138">A correlation is one of two things:</span></span>

- <span data-ttu-id="ec160-139">群組訊息的方式。亦即，要求訊息與其回覆之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="ec160-139">A way of grouping messages together; that is, the relationship between a request message and its reply.</span></span>

- <span data-ttu-id="ec160-140">將資料片段對應至服務執行個體的方式。</span><span class="sxs-lookup"><span data-stu-id="ec160-140">A way of mapping a piece of data to a service instance</span></span>

### <a name="getting-started"></a><span data-ttu-id="ec160-141">開始使用</span><span class="sxs-lookup"><span data-stu-id="ec160-141">Getting Started</span></span>

- <span data-ttu-id="ec160-142">若要開始使用相互關聯，請在 Visual Studio 中建立新的專案。</span><span class="sxs-lookup"><span data-stu-id="ec160-142">To get started with correlation, create a new project in Visual Studio.</span></span> <span data-ttu-id="ec160-143">建立型別為 <xref:System.ServiceModel.Activities.CorrelationHandle> 的變數。</span><span class="sxs-lookup"><span data-stu-id="ec160-143">Create a variable of type <xref:System.ServiceModel.Activities.CorrelationHandle>.</span></span>

- <span data-ttu-id="ec160-144">用來將訊息群組在一起之相互關聯的範例就是，將訊息群組在一起的要求-回覆相互關聯。</span><span class="sxs-lookup"><span data-stu-id="ec160-144">An example of correlation used to group messages together is a Request-Reply correlation that groups messages together.</span></span>

  - <span data-ttu-id="ec160-145">在 <xref:System.ServiceModel.Activities.Receive> 活動上，按一下 <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> 屬性，並 <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> 使用在上述第一個步驟中建立的 CorrelationHandle 來新增。</span><span class="sxs-lookup"><span data-stu-id="ec160-145">On a <xref:System.ServiceModel.Activities.Receive> activity, click on the <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> property and add a <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> using the CorrelationHandle created in the first step above.</span></span>

  - <span data-ttu-id="ec160-146"><xref:System.ServiceModel.Activities.SendReply>以滑鼠右鍵按一下 <xref:System.ServiceModel.Activities.Receive> ，然後按一下 [建立 SendReply] 來建立活動。</span><span class="sxs-lookup"><span data-stu-id="ec160-146">Create a <xref:System.ServiceModel.Activities.SendReply> activity by right-clicking on the <xref:System.ServiceModel.Activities.Receive> and clicking "Create SendReply".</span></span> <span data-ttu-id="ec160-147">接著，將它貼入工作流程中 <xref:System.ServiceModel.Activities.Receive> 活動的後面。</span><span class="sxs-lookup"><span data-stu-id="ec160-147">Paste it into your workflow after the <xref:System.ServiceModel.Activities.Receive> activity.</span></span>

- <span data-ttu-id="ec160-148">將資料片段對應至服務執行個體的範例就是內容架構的相互關聯，它會將資料片段 (例如訂單 ID) 對應至特定工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="ec160-148">An example of mapping a piece of data to a service instance is content-based correlation which maps a piece of data (for example, an order ID) to a particular workflow instance.</span></span>

  - <span data-ttu-id="ec160-149">在任何傳訊活動上，按一下 `CorrelationInitializers` 屬性，然後使用您在上述步驟中建立的 <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> 變數來加入 <xref:System.ServiceModel.Activities.CorrelationHandle>。</span><span class="sxs-lookup"><span data-stu-id="ec160-149">On any messaging activity, click on the `CorrelationInitializers` property and add a <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> using the <xref:System.ServiceModel.Activities.CorrelationHandle> variable created above.</span></span> <span data-ttu-id="ec160-150">在下拉式功能表中，按兩下所需的訊息屬性 (例如 OrderID)。</span><span class="sxs-lookup"><span data-stu-id="ec160-150">Double-click on the desired property on the message (e.g. OrderID) from the drop-down menu.</span></span> <span data-ttu-id="ec160-151">接著，將 `CorrelatesWith` 屬性設定為上述使用的 <xref:System.ServiceModel.Activities.CorrelationHandle> 變數。</span><span class="sxs-lookup"><span data-stu-id="ec160-151">Set the `CorrelatesWith` property to the <xref:System.ServiceModel.Activities.CorrelationHandle> variable used above.</span></span>

- [<span data-ttu-id="ec160-152">相互關聯概念文件</span><span class="sxs-lookup"><span data-stu-id="ec160-152">Correlation Conceptual Documentation</span></span>](../wcf/feature-details/correlation.md)

### <a name="correlation-scenario"></a><span data-ttu-id="ec160-153">相互關聯案例</span><span class="sxs-lookup"><span data-stu-id="ec160-153">Correlation Scenario</span></span>

<span data-ttu-id="ec160-154">訂單處理工作流程是用來處理新訂單的建立，並更新正在處理的現有訂單。</span><span class="sxs-lookup"><span data-stu-id="ec160-154">An order-processing workflow is used to handle new order creation and updating existing orders that are in process.</span></span> <span data-ttu-id="ec160-155">若要執行此案例，您必須在中裝載工作流程 <xref:System.ServiceModel.WorkflowServiceHost> ，並使用訊息活動。</span><span class="sxs-lookup"><span data-stu-id="ec160-155">Implementing this scenario would require you to host the workflow in <xref:System.ServiceModel.WorkflowServiceHost> and use the messaging activities.</span></span> <span data-ttu-id="ec160-156">它也需要根據的相互關聯 `orderId` ，以確保會對正確的工作流程進行更新。</span><span class="sxs-lookup"><span data-stu-id="ec160-156">It would also require correlation based on the `orderId` to ensure that updates are made to the correct workflow.</span></span>

## <a name="simplified-configuration"></a><span data-ttu-id="ec160-157">簡化的組態</span><span class="sxs-lookup"><span data-stu-id="ec160-157">Simplified Configuration</span></span>

<span data-ttu-id="ec160-158">WCF 設定架構很複雜，可為使用者提供許多難以找到的功能。</span><span class="sxs-lookup"><span data-stu-id="ec160-158">The WCF configuration schema is complex and provides users with many hard to find features.</span></span> <span data-ttu-id="ec160-159">在中 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] ，我們著重于協助 WCF 使用者使用下列功能來設定其服務：</span><span class="sxs-lookup"><span data-stu-id="ec160-159">In [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], we have focused on helping WCF users configure their services with the following features:</span></span>

- <span data-ttu-id="ec160-160">移除每項服務明確組態的需求。</span><span class="sxs-lookup"><span data-stu-id="ec160-160">Removing the need for explicit per-service configuration.</span></span> <span data-ttu-id="ec160-161">如果您沒有為服務設定任何專案 \<service> ，而且您的服務並未以程式設計方式定義任何端點，則會自動將一組端點新增至您的服務，每個服務基底位址和服務所執行的每個合約各一個端點。</span><span class="sxs-lookup"><span data-stu-id="ec160-161">If you do not configure any \<service> elements for your service, and your service does not define programmatically any endpoint, then a set of endpoints will be automatically added to your service, one per service base address and per contract implemented by your service.</span></span>

- <span data-ttu-id="ec160-162">讓使用者定義 WCF 繫結和行為的預設值，以便套用至沒有明確組態的服務。</span><span class="sxs-lookup"><span data-stu-id="ec160-162">Enables the user to define default values for WCF bindings and behaviors, which will be applied to services with no explicit configuration.</span></span>

- <span data-ttu-id="ec160-163">標準端點會定義可重複使用的預先設定端點，其中一個或多個端點屬性 (位址、繫結和合約) 具有固定的值，而且允許定義自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="ec160-163">Standard endpoints define reusable preconfigured endpoints, which have fixed values for one or more of the endpoint properties (address, binding and contract), and allow defining custom properties.</span></span>

- <span data-ttu-id="ec160-164">最後，可 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> 讓您進行 WCF 用戶端設定的集中管理，這在應用程式域載入時間之後選取或變更設定的情況下很有用。</span><span class="sxs-lookup"><span data-stu-id="ec160-164">Finally, the <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> allows you to do central management of WCF client configuration, useful in scenarios in which configuration is selected or changed after the application domain load time.</span></span>

### <a name="getting-started"></a><span data-ttu-id="ec160-165">開始使用</span><span class="sxs-lookup"><span data-stu-id="ec160-165">Getting Started</span></span>

- <span data-ttu-id="ec160-166">[WCF 4.0 開發人員指南](/previous-versions/dotnet/articles/ee354381(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="ec160-166">[A Developer's Guide to WCF 4.0](/previous-versions/dotnet/articles/ee354381(v=msdn.10))</span></span>

- [<span data-ttu-id="ec160-167">組態通道處理站</span><span class="sxs-lookup"><span data-stu-id="ec160-167">Configuration Channel Factory</span></span>](xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601)

- [<span data-ttu-id="ec160-168">標準端點項目</span><span class="sxs-lookup"><span data-stu-id="ec160-168">Standard Endpoint Element</span></span>](xref:System.ServiceModel.Configuration.StandardEndpointElement)

- [<span data-ttu-id="ec160-169">.NET Framework 4 中的服務設定改善</span><span class="sxs-lookup"><span data-stu-id="ec160-169">Service configuration improvements in .NET Framework 4</span></span>](/archive/blogs/endpoint/service-configuration-improvements-in-net-4)

- [<span data-ttu-id="ec160-170">.NET 4 的常見使用者錯誤：WF/WCF 服務組態名稱拼錯</span><span class="sxs-lookup"><span data-stu-id="ec160-170">Common User Mistake in .NET 4: Mistyping the WF/WCF Service Configuration Name</span></span>](/archive/blogs/endpoint/common-user-mistake-in-net-4-mistyping-the-wfwcf-service-configuration-name)

### <a name="simplified-configuration-scenarios"></a><span data-ttu-id="ec160-171">簡化的組態案例</span><span class="sxs-lookup"><span data-stu-id="ec160-171">Simplified Configuration Scenarios</span></span>

- <span data-ttu-id="ec160-172">有經驗的 .ASMX 開發人員想要開始使用 WCF。</span><span class="sxs-lookup"><span data-stu-id="ec160-172">An experienced ASMX developer wants to start using WCF.</span></span> <span data-ttu-id="ec160-173">不過，WCF 的方式似乎太複雜！</span><span class="sxs-lookup"><span data-stu-id="ec160-173">However, WCF seems way too complicated!</span></span> <span data-ttu-id="ec160-174">我需要在組態檔中寫入哪些資訊？</span><span class="sxs-lookup"><span data-stu-id="ec160-174">What is all that information that I need to write in a configuration file?</span></span> <span data-ttu-id="ec160-175">在 .NET 4 中，您甚至可以決定完全不使用組態檔。</span><span class="sxs-lookup"><span data-stu-id="ec160-175">In .NET 4, you can even decide to not have a configuration file at all.</span></span>

- <span data-ttu-id="ec160-176">現有的 WCF 服務集非常難以設定和維護。</span><span class="sxs-lookup"><span data-stu-id="ec160-176">An existing set of WCF services are very difficult to configure and maintain.</span></span> <span data-ttu-id="ec160-177">組態檔具有數千行 XML 程式碼，任意修改可能會非常危險。</span><span class="sxs-lookup"><span data-stu-id="ec160-177">The configuration file has thousands of lines of XML code that are extremely dangerous to touch.</span></span> <span data-ttu-id="ec160-178">因此需要相關協助，以便將程式碼數量減少至較容易管理的數量。</span><span class="sxs-lookup"><span data-stu-id="ec160-178">Help is needed to reduce that amount of code to something more manageable.</span></span>

## <a name="data-contract-resolver"></a><span data-ttu-id="ec160-179">資料合約解析程式</span><span class="sxs-lookup"><span data-stu-id="ec160-179">Data Contract Resolver</span></span>

<span data-ttu-id="ec160-180">在 .NET 3.5 中，已知型別的設計具有一些限制：</span><span class="sxs-lookup"><span data-stu-id="ec160-180">In .NET 3.5, there were a few limitations in the design of known types:</span></span>

- <span data-ttu-id="ec160-181">您無法在序列化或還原序列化期間，以動態方式加入已知型別。</span><span class="sxs-lookup"><span data-stu-id="ec160-181">Adding known types dynamically, during serialization or deserialization, was not possible.</span></span>

- <span data-ttu-id="ec160-182">序列化程式無法處理不明的 xsi:type 資訊。</span><span class="sxs-lookup"><span data-stu-id="ec160-182">Serializers could not deal with unknown xsi:type information.</span></span>

- <span data-ttu-id="ec160-183">使用者無法指定想要顯示在 Wire 上的 xsi:type，以便降低 Wire 上序列化執行個體的大小。</span><span class="sxs-lookup"><span data-stu-id="ec160-183">It was not possible for users to specify what xsi:type they would like to have appear on the wire to, for instance, make the size of a serialization instance on the wire smaller.</span></span>

<span data-ttu-id="ec160-184">[DataContractResolver](../wcf/samples/datacontractresolver.md)在 .net 4.5 中解決了這些問題。</span><span class="sxs-lookup"><span data-stu-id="ec160-184">The [DataContractResolver](../wcf/samples/datacontractresolver.md) solves these issues in .NET 4.5.</span></span>

### <a name="getting-started"></a><span data-ttu-id="ec160-185">開始使用</span><span class="sxs-lookup"><span data-stu-id="ec160-185">Getting Started</span></span>

- [<span data-ttu-id="ec160-186">資料合約解析程式 API 文件</span><span class="sxs-lookup"><span data-stu-id="ec160-186">Data Contract Resolver API documentation</span></span>](xref:System.Runtime.Serialization.DataContractResolver)

- [<span data-ttu-id="ec160-187">資料合約解析程式簡介</span><span class="sxs-lookup"><span data-stu-id="ec160-187">Introducing the Data Contract Resolver</span></span>](/archive/blogs/youssefm/configuring-known-types-dynamically-introducing-the-datacontractresolver)

- <span data-ttu-id="ec160-188">範例：</span><span class="sxs-lookup"><span data-stu-id="ec160-188">Samples:</span></span>

  - [<span data-ttu-id="ec160-189">DataContractResolver</span><span class="sxs-lookup"><span data-stu-id="ec160-189">DataContractResolver</span></span>](../wcf/samples/datacontractresolver.md)

  - [<span data-ttu-id="ec160-190">KnownAssemblyAttribute</span><span class="sxs-lookup"><span data-stu-id="ec160-190">KnownAssemblyAttribute</span></span>](../wcf/samples/knownassemblyattribute.md)

### <a name="data-contract-resolver-scenarios"></a><span data-ttu-id="ec160-191">資料合約解析程式案例</span><span class="sxs-lookup"><span data-stu-id="ec160-191">Data Contract Resolver Scenarios</span></span>

- <span data-ttu-id="ec160-192">避免在服務中宣告數十個 <xref:System.Runtime.Serialization.KnownTypeAttribute> 物件。</span><span class="sxs-lookup"><span data-stu-id="ec160-192">Avoiding having to declare tens of <xref:System.Runtime.Serialization.KnownTypeAttribute> objects in a service.</span></span>

- <span data-ttu-id="ec160-193">減少 XML BLOB 的大小。</span><span class="sxs-lookup"><span data-stu-id="ec160-193">Reducing the size of the XML blob.</span></span>

## <a name="flowchart"></a><span data-ttu-id="ec160-194">流程圖</span><span class="sxs-lookup"><span data-stu-id="ec160-194">Flowchart</span></span>

<span data-ttu-id="ec160-195">流程圖是已知的開發架構，可以視覺化方式表示網域問題。</span><span class="sxs-lookup"><span data-stu-id="ec160-195">Flowchart is a well-known paradigm to visually represent domain problems.</span></span> <span data-ttu-id="ec160-196">這是我們在 .NET 4 中引進的新控制流程樣式。</span><span class="sxs-lookup"><span data-stu-id="ec160-196">It is a new control flow style we're introducing in .NET 4.</span></span> <span data-ttu-id="ec160-197">流程圖的核心特性在於，一次只能執行一項活動。</span><span class="sxs-lookup"><span data-stu-id="ec160-197">A core characteristic of Flowchart is that only one activity is executed at any given time.</span></span> <span data-ttu-id="ec160-198">流程圖可以表達迴圈和替代的結果，但本身無法表示同時執行的多個節點。</span><span class="sxs-lookup"><span data-stu-id="ec160-198">Flowcharts can express loops and alternative outcomes, but cannot natively express concurrent execution of multiple nodes.</span></span>

### <a name="getting-started"></a><span data-ttu-id="ec160-199">開始使用</span><span class="sxs-lookup"><span data-stu-id="ec160-199">Getting Started</span></span>

- <span data-ttu-id="ec160-200">在 Visual Studio 2012 中，建立工作流程主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="ec160-200">In Visual Studio 2012, create a workflow console application.</span></span> <span data-ttu-id="ec160-201">在工作流程設計工具中加入流程圖。</span><span class="sxs-lookup"><span data-stu-id="ec160-201">Add a Flowchart in the workflow designer.</span></span>

- <span data-ttu-id="ec160-202">流程圖功能會使用下列類別：</span><span class="sxs-lookup"><span data-stu-id="ec160-202">The flowchart feature uses the following classes:</span></span>

  - <xref:System.Activities.Statements.Flowchart>

  - <xref:System.Activities.Statements.FlowNode>

  - <xref:System.Activities.Statements.FlowDecision>

  - <xref:System.Activities.Statements.FlowStep>

  - <xref:System.Activities.Statements.FlowSwitch%601>

- <span data-ttu-id="ec160-203">範例：</span><span class="sxs-lookup"><span data-stu-id="ec160-203">Samples:</span></span>

  - [<span data-ttu-id="ec160-204">使用 TryCatch 錯誤處理流程圖活動</span><span class="sxs-lookup"><span data-stu-id="ec160-204">Fault Handling in a Flowchart Activity Using TryCatch</span></span>](./samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)

  - [<span data-ttu-id="ec160-205">招聘程序</span><span class="sxs-lookup"><span data-stu-id="ec160-205">Hiring Process</span></span>](./samples/hiring-process.md)

- <span data-ttu-id="ec160-206">設計工具文件：</span><span class="sxs-lookup"><span data-stu-id="ec160-206">Designer Documentation:</span></span>

  - [<span data-ttu-id="ec160-207">Flowchart 活動設計工具</span><span class="sxs-lookup"><span data-stu-id="ec160-207">Flowchart Activity Designers</span></span>](/visualstudio/workflow-designer/flowchart-activity-designers)

### <a name="flowchart-scenarios"></a><span data-ttu-id="ec160-208">流程圖案例</span><span class="sxs-lookup"><span data-stu-id="ec160-208">Flowchart Scenarios</span></span>

<span data-ttu-id="ec160-209">流程圖活動可用來實作猜測遊戲。</span><span class="sxs-lookup"><span data-stu-id="ec160-209">A flowchart activity can be used to implement a guessing game.</span></span> <span data-ttu-id="ec160-210">猜測遊戲非常簡單：電腦會選取一個隨機數字，而玩家必須猜測該數字。</span><span class="sxs-lookup"><span data-stu-id="ec160-210">The guessing game is very simple: the computer selects a random number and the player has to guess that number.</span></span> <span data-ttu-id="ec160-211">當播放程式提交每個猜測時，電腦會顯示提示 (例如「試用較低的數位」 ) 。</span><span class="sxs-lookup"><span data-stu-id="ec160-211">When the player submits each guess, the computer shows them a hint (i.e. "try a lower number").</span></span> <span data-ttu-id="ec160-212">如果玩家在7次的嘗試中找到數位，則會從電腦收到特殊的 congratulation。</span><span class="sxs-lookup"><span data-stu-id="ec160-212">If the player finds the number in less than 7 attempts, they receive a special congratulation from the computer.</span></span> <span data-ttu-id="ec160-213">您可以透過組合下列程序性活動來實作此遊戲：</span><span class="sxs-lookup"><span data-stu-id="ec160-213">This game can be implemented with a combination of the following procedural activities:</span></span>

- <xref:System.Activities.Statements.Sequence>

- <xref:System.Activities.Statements.While>

- <xref:System.Activities.Statements.Switch%601>

- <xref:System.Activities.Statements.TryCatch>

- <xref:System.Activities.Statements.Assign%601>

- <xref:System.Activities.Statements.If>

## <a name="procedural-activities-sequence-if-foreach-switch-assign-dowhile-while"></a><span data-ttu-id="ec160-214">程序性活動 (Sequence、If、ForEach、Switch、Assign、DoWhile 和 While)</span><span class="sxs-lookup"><span data-stu-id="ec160-214">Procedural activities (Sequence, If, ForEach, Switch, Assign, DoWhile, While)</span></span>

<span data-ttu-id="ec160-215">程序性活動會使用程式設計人員所熟悉的概念來提供模型循序控制流程的機制。</span><span class="sxs-lookup"><span data-stu-id="ec160-215">Procedural activities provide a mechanism to model sequential control flow using concepts that are familiar to programmers.</span></span> <span data-ttu-id="ec160-216">這些活動會啟用傳統結構化的程式設計語言結構，並在適當時，提供與常見程式語言（如 c # 和 Visual Basic）的語言同位。</span><span class="sxs-lookup"><span data-stu-id="ec160-216">These activities enable traditionally structured programming language constructs and, when appropriate, provide language parity with common procedural languages such as C# and Visual Basic.</span></span>

### <a name="getting-started"></a><span data-ttu-id="ec160-217">開始使用</span><span class="sxs-lookup"><span data-stu-id="ec160-217">Getting Started</span></span>

- <span data-ttu-id="ec160-218">在 Visual Studio 2012 中，建立工作流程主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="ec160-218">In Visual Studio 2012, create a workflow console application.</span></span> <span data-ttu-id="ec160-219">在工作流程設計工具中加入程序性活動。</span><span class="sxs-lookup"><span data-stu-id="ec160-219">Add procedural activities in the workflow designer.</span></span>

- <span data-ttu-id="ec160-220">範例：</span><span class="sxs-lookup"><span data-stu-id="ec160-220">Samples:</span></span>

  - [<span data-ttu-id="ec160-221">招聘程序</span><span class="sxs-lookup"><span data-stu-id="ec160-221">Hiring Process</span></span>](./samples/hiring-process.md)

  - [<span data-ttu-id="ec160-222">公司購買程序</span><span class="sxs-lookup"><span data-stu-id="ec160-222">Corporate Purchase Process</span></span>](./samples/corporate-purchase-process.md)

- <span data-ttu-id="ec160-223">設計工具文件：</span><span class="sxs-lookup"><span data-stu-id="ec160-223">Designer Documentation:</span></span>

  - [<span data-ttu-id="ec160-224">Parallel 活動設計工具</span><span class="sxs-lookup"><span data-stu-id="ec160-224">Parallel Activity Designer</span></span>](/visualstudio/workflow-designer/parallel-activity-designer)

  - [<span data-ttu-id="ec160-225">ParallelForEach \<T> 活動設計工具</span><span class="sxs-lookup"><span data-stu-id="ec160-225">ParallelForEach\<T> Activity Designer</span></span>](/visualstudio/workflow-designer/parallelforeach-t-activity-designer)

### <a name="procedural-activity-scenarios"></a><span data-ttu-id="ec160-226">程序性活動案例</span><span class="sxs-lookup"><span data-stu-id="ec160-226">Procedural Activity Scenarios</span></span>

- <span data-ttu-id="ec160-227"><xref:System.Activities.Statements.Parallel>：內部網路檔管理系統有檔核准工作流程。</span><span class="sxs-lookup"><span data-stu-id="ec160-227"><xref:System.Activities.Statements.Parallel>: An intranet document management system has a document approval workflow.</span></span> <span data-ttu-id="ec160-228">文件必須先由數個部門的人員核准，然後才能發行至內部網路。</span><span class="sxs-lookup"><span data-stu-id="ec160-228">Documents need to be approved by people in several departments before they can be published to the intranet.</span></span> <span data-ttu-id="ec160-229">未建立核准的訂單;當檔處於「核准暫止」階段時，就可能會發生這些問題。</span><span class="sxs-lookup"><span data-stu-id="ec160-229">There isn't an established order for the approvals; they can occur at any time while the document is in the "approval pending" phase.</span></span> <span data-ttu-id="ec160-230">當使用者提交要審核的檔時，必須由其直接管理員、內部網路系統管理員和內部通訊管理員核准。</span><span class="sxs-lookup"><span data-stu-id="ec160-230">When a user submits a document for review, it must be approved by their direct manager, the intranet administrator, and the internal communications manager.</span></span>

- <span data-ttu-id="ec160-231"><xref:System.Activities.Statements.ParallelForEach%601>：WF 應用程式可管理大型公司內部的企業採購。</span><span class="sxs-lookup"><span data-stu-id="ec160-231"><xref:System.Activities.Statements.ParallelForEach%601>: A WF application manages corporate buys within a large company.</span></span> <span data-ttu-id="ec160-232">企業規則表示，規劃任何採購作業之前，需要三家不同廠商的估價。</span><span class="sxs-lookup"><span data-stu-id="ec160-232">The corporate rules dictate that before planning any purchase operation, the valuations of three different vendors is required.</span></span> <span data-ttu-id="ec160-233">購買部門的員工從公司的廠商清單中選取三個廠商。</span><span class="sxs-lookup"><span data-stu-id="ec160-233">An employee from the buying department selects three vendors from the company's vendor list.</span></span> <span data-ttu-id="ec160-234">選取並通知這些廠商之後，公司將等候其經濟提案。</span><span class="sxs-lookup"><span data-stu-id="ec160-234">After these vendors have been selected and notified, the company will wait for their economic proposals.</span></span> <span data-ttu-id="ec160-235">這些提案可以按照任何順序提出。</span><span class="sxs-lookup"><span data-stu-id="ec160-235">The proposals can come in any order.</span></span> <span data-ttu-id="ec160-236">為了在 WF 中實作此案例，我們使用了 <xref:System.Activities.Statements.ParallelForEach%601>，以便逐一查看廠商的集合並且要求其經濟提案。</span><span class="sxs-lookup"><span data-stu-id="ec160-236">To implement this scenario in WF, we use a <xref:System.Activities.Statements.ParallelForEach%601> that will iterate through our collection of vendors and ask for their economic proposals.</span></span> <span data-ttu-id="ec160-237">蒐集所有供應項目之後，系統會選取並顯示最佳提案。</span><span class="sxs-lookup"><span data-stu-id="ec160-237">After all offers are gathered, the best one is selected and displayed.</span></span>

## <a name="invokemethod"></a><span data-ttu-id="ec160-238">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="ec160-238">InvokeMethod</span></span>

<span data-ttu-id="ec160-239"><xref:System.Activities.Statements.InvokeMethod> 活動允許叫用範圍內物件或型別的公用方法。</span><span class="sxs-lookup"><span data-stu-id="ec160-239">The <xref:System.Activities.Statements.InvokeMethod> activity allows invoking public methods in objects or types in scope.</span></span> <span data-ttu-id="ec160-240">它支援叫用包含或不包含參數 (包括參數陣列) 的執行個體和靜態方法，以及泛型方法。</span><span class="sxs-lookup"><span data-stu-id="ec160-240">It supports invoking instance and static methods with or without parameters (including parameter arrays), and generic methods.</span></span> <span data-ttu-id="ec160-241">此外，它也允許以同步和非同步方式執行方法。</span><span class="sxs-lookup"><span data-stu-id="ec160-241">It also allows executing method synchronously and asynchronously.</span></span>

### <a name="getting-started"></a><span data-ttu-id="ec160-242">開始使用</span><span class="sxs-lookup"><span data-stu-id="ec160-242">Getting Started</span></span>

- <span data-ttu-id="ec160-243">在 Visual Studio 2012 中，建立工作流程主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="ec160-243">In Visual Studio 2012, create a workflow console application.</span></span> <span data-ttu-id="ec160-244">在工作流程設計工具中加入 <xref:System.Activities.Statements.InvokeMethod> 活動，並且針對此活動設定靜態和執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="ec160-244">Add an <xref:System.Activities.Statements.InvokeMethod> activity in the workflow designer, and configure static and instance methods on it.</span></span>

- <span data-ttu-id="ec160-245">設計工具檔： [InvokeMethod 活動設計](/visualstudio/workflow-designer/invokemethod-activity-designer)工具</span><span class="sxs-lookup"><span data-stu-id="ec160-245">Designer Documentation: [InvokeMethod Activity Designer](/visualstudio/workflow-designer/invokemethod-activity-designer)</span></span>

### <a name="invokemethod-scenarios"></a><span data-ttu-id="ec160-246">InvokeMethod 案例</span><span class="sxs-lookup"><span data-stu-id="ec160-246">InvokeMethod Scenarios</span></span>

- <span data-ttu-id="ec160-247">需要叫用範圍內物件的方法。</span><span class="sxs-lookup"><span data-stu-id="ec160-247">A method in an object in scope needs to be invoked.</span></span> <span data-ttu-id="ec160-248">例如，需要將某個值加入至字典。</span><span class="sxs-lookup"><span data-stu-id="ec160-248">For example, a value needs to be added to a dictionary.</span></span> <span data-ttu-id="ec160-249">此時，系統會叫用字典執行個體的 Add 方法，並且提供索引鍵和值。</span><span class="sxs-lookup"><span data-stu-id="ec160-249">The Add method of the instance of the dictionary is invoked, and the key and value are provided.</span></span>

- <span data-ttu-id="ec160-250">需要針對舊版 CLR 物件叫用方法。</span><span class="sxs-lookup"><span data-stu-id="ec160-250">A method needs to be invoked on a legacy CLR object.</span></span> <span data-ttu-id="ec160-251">您可以使用 <xref:System.Activities.Statements.InvokeMethod>，而非建立自訂活動來包裝該舊版類別的呼叫 (如果它在工作流程執行期間位於範圍內的話)。</span><span class="sxs-lookup"><span data-stu-id="ec160-251">Instead of creating a custom activity to wrap the call to that legacy class, if it is in scope during the workflow execution, <xref:System.Activities.Statements.InvokeMethod> can be used.</span></span>

## <a name="error-handling-activities"></a><span data-ttu-id="ec160-252">錯誤處理活動</span><span class="sxs-lookup"><span data-stu-id="ec160-252">Error handling activities</span></span>

<span data-ttu-id="ec160-253"><xref:System.Activities.Statements.TryCatch>活動會提供一種機制來攔截執行一組包含的活動時所發生的例外狀況， (類似于 c # 中的 Try/Catch 結構和 Visual Basic) 。</span><span class="sxs-lookup"><span data-stu-id="ec160-253">The <xref:System.Activities.Statements.TryCatch> activity provides a mechanism for catching exceptions that occur during the execution of a set of contained activities (similar to the Try/Catch construct in C# and Visual Basic).</span></span> <span data-ttu-id="ec160-254"><xref:System.Activities.Statements.TryCatch> 提供工作流程層級的例外狀況處理。</span><span class="sxs-lookup"><span data-stu-id="ec160-254"><xref:System.Activities.Statements.TryCatch> provides exception handling at the workflow level.</span></span> <span data-ttu-id="ec160-255">當擲回未處理的例外狀況時，工作流程會中止，且不會執行 Finally 區塊。</span><span class="sxs-lookup"><span data-stu-id="ec160-255">When an unhandled exception is thrown, the workflow is aborted and the Finally block won't be executed.</span></span> <span data-ttu-id="ec160-256">這種行為與 C# 一致。</span><span class="sxs-lookup"><span data-stu-id="ec160-256">This behavior is consistent with C#.</span></span>

### <a name="getting-started"></a><span data-ttu-id="ec160-257">開始使用</span><span class="sxs-lookup"><span data-stu-id="ec160-257">Getting Started</span></span>

- <span data-ttu-id="ec160-258">在 Visual Studio 2012 中，建立工作流程主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="ec160-258">In Visual Studio 2012, create a workflow console application.</span></span> <span data-ttu-id="ec160-259">在工作流程設計工具中加入 <xref:System.Activities.Statements.TryCatch> 活動。</span><span class="sxs-lookup"><span data-stu-id="ec160-259">Add a <xref:System.Activities.Statements.TryCatch> activity in the workflow designer.</span></span>

- <span data-ttu-id="ec160-260">範例： [使用 TryCatch 的流程圖活動中的錯誤處理](./samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)</span><span class="sxs-lookup"><span data-stu-id="ec160-260">Sample: [Fault Handling in a Flowchart Activity Using TryCatch](./samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)</span></span>

- <span data-ttu-id="ec160-261">設計工具檔：[錯誤處理活動設計](/visualstudio/workflow-designer/error-handling-activity-designers)工具</span><span class="sxs-lookup"><span data-stu-id="ec160-261">Designer Documentation: [Error Handling Activity Designers](/visualstudio/workflow-designer/error-handling-activity-designers)</span></span>

### <a name="error-handling-scenarios"></a><span data-ttu-id="ec160-262">錯誤處理案例</span><span class="sxs-lookup"><span data-stu-id="ec160-262">Error handling scenarios</span></span>

<span data-ttu-id="ec160-263">需要執行一組活動，而且需要在發生錯誤時執行特定邏輯。</span><span class="sxs-lookup"><span data-stu-id="ec160-263">A set of activities needs to be executed, and specific logic needs to be executed when an error occurs.</span></span> <span data-ttu-id="ec160-264">如果在錯誤處理邏輯期間發現錯誤無法復原，就會重新擲回例外狀況，而且父活動 (或主機) 將會處理此問題。</span><span class="sxs-lookup"><span data-stu-id="ec160-264">If during that error handling logic it is found that the error is not recoverable, the exception will be rethrown, and the parent activity (or the host) will deal with the problem.</span></span>

## <a name="pick-activity"></a><span data-ttu-id="ec160-265">Pick 活動</span><span class="sxs-lookup"><span data-stu-id="ec160-265">Pick activity</span></span>

<span data-ttu-id="ec160-266"><xref:System.Activities.Statements.Pick> 活動會提供 WF 中以事件為主的控制流程模型。</span><span class="sxs-lookup"><span data-stu-id="ec160-266">The <xref:System.Activities.Statements.Pick> Activity provides event-based control flow modeling in WF.</span></span> <span data-ttu-id="ec160-267"><xref:System.Activities.Statements.Pick> 包含許多分支，每個分支會先等待特定事件發生後，再開始執行。</span><span class="sxs-lookup"><span data-stu-id="ec160-267"><xref:System.Activities.Statements.Pick> contains many branches where each branch waits for a particular event to occur before running.</span></span> <span data-ttu-id="ec160-268">在此設定中，<xref:System.Activities.Statements.Pick> 的行為與 <xref:System.Activities.Statements.Switch%601> 很相似，因為此活動只會執行它所接聽的其中一個事件集。</span><span class="sxs-lookup"><span data-stu-id="ec160-268">In this setup, a <xref:System.Activities.Statements.Pick> behaves similar to a <xref:System.Activities.Statements.Switch%601> to which the Activity will execute only one of the set of events it is listening.</span></span> <span data-ttu-id="ec160-269">每個分支都是由事件驅動，而發生的事件會先執行對應的分支。</span><span class="sxs-lookup"><span data-stu-id="ec160-269">Each branch is event driven and the event that occurs runs the corresponding branch first.</span></span> <span data-ttu-id="ec160-270">所有其他的分支都會取消並停止接聽事件。</span><span class="sxs-lookup"><span data-stu-id="ec160-270">All other branches cancel and stop listening for events.</span></span>

### <a name="getting-started"></a><span data-ttu-id="ec160-271">開始使用</span><span class="sxs-lookup"><span data-stu-id="ec160-271">Getting Started</span></span>

- <span data-ttu-id="ec160-272">在 Visual Studio 2012 中，建立工作流程主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="ec160-272">In Visual Studio 2012, create a workflow console application.</span></span> <span data-ttu-id="ec160-273">在工作流程設計工具中加入 <xref:System.Activities.Statements.Pick> 活動。</span><span class="sxs-lookup"><span data-stu-id="ec160-273">Add a <xref:System.Activities.Statements.Pick> activity in the workflow designer.</span></span>

- <span data-ttu-id="ec160-274">範例： [使用 Pick 活動](./samples/using-the-pick-activity.md)</span><span class="sxs-lookup"><span data-stu-id="ec160-274">Sample: [Using the Pick Activity](./samples/using-the-pick-activity.md)</span></span>

- <span data-ttu-id="ec160-275">設計工具檔： [Pick 活動設計](/visualstudio/workflow-designer/pick-activity-designer)工具</span><span class="sxs-lookup"><span data-stu-id="ec160-275">Designer documentation: [Pick Activity Designer](/visualstudio/workflow-designer/pick-activity-designer)</span></span>

### <a name="pick-scenario"></a><span data-ttu-id="ec160-276">Pick 案例</span><span class="sxs-lookup"><span data-stu-id="ec160-276">Pick Scenario</span></span>

<span data-ttu-id="ec160-277">系統需要提示使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="ec160-277">A user needs to be prompted for input.</span></span> <span data-ttu-id="ec160-278">在一般情況下，開發人員會使用類似 <xref:System.Console.ReadLine%2A> 于提示使用者輸入的方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="ec160-278">Under normal circumstances, the developer would use a method call like <xref:System.Console.ReadLine%2A> to prompt for a user's input.</span></span> <span data-ttu-id="ec160-279">這種設定的問題在於，直到使用者輸入某些內容為止，程式都會處於等候狀態。</span><span class="sxs-lookup"><span data-stu-id="ec160-279">The problem with this setup is that the program waits until the user enters something.</span></span> <span data-ttu-id="ec160-280">在此案例中，您需要使用逾時將封鎖的活動解除封鎖。</span><span class="sxs-lookup"><span data-stu-id="ec160-280">In this scenario, a time-out is needed to unblock a blocking activity.</span></span> <span data-ttu-id="ec160-281">常見的案例就是要求在指定的一段時間內完成工作。</span><span class="sxs-lookup"><span data-stu-id="ec160-281">A common scenario is one that requires a task to be completed within a given time duration.</span></span> <span data-ttu-id="ec160-282">讓封鎖的活動逾時則為 Pick 發揮功能的案例。</span><span class="sxs-lookup"><span data-stu-id="ec160-282">Timing out a blocking activity is a scenario where Pick adds a lot of value.</span></span>

## <a name="wcf-routing-service"></a><span data-ttu-id="ec160-283">WCF 路由服務</span><span class="sxs-lookup"><span data-stu-id="ec160-283">WCF Routing Service</span></span>

<span data-ttu-id="ec160-284">路由服務設計為一般軟體路由器，可讓您控制 WCF 訊息在用戶端與服務之間流動的方式。</span><span class="sxs-lookup"><span data-stu-id="ec160-284">The Routing Service is designed to be a generic software Router that allows you to control how WCF messages flow in between your clients and services.</span></span> <span data-ttu-id="ec160-285">路由服務可讓您將用戶端與服務分離，如此可讓您更自由地使用可支援的設定，以及考慮如何裝載服務的彈性。</span><span class="sxs-lookup"><span data-stu-id="ec160-285">The Routing Service allows you to decouple your clients from your services, which gives you much more freedom in terms of the configurations that you can support and the flexibility you have when considering how to host your services.</span></span> <span data-ttu-id="ec160-286">在 .NET 3.5 中，用戶端與服務緊密結合;用戶端必須知道它需要與其交談的所有服務，以及它們所在的位置。</span><span class="sxs-lookup"><span data-stu-id="ec160-286">In .NET 3.5, clients and services were tightly coupled; a client had to know about all of the services it needed to talk to and where they were located.</span></span> <span data-ttu-id="ec160-287">此外，.NET Framework 3.5 中的 WCF 有下列限制：</span><span class="sxs-lookup"><span data-stu-id="ec160-287">In addition, WCF in .NET Framework 3.5 had the following limitations:</span></span>

- <span data-ttu-id="ec160-288">錯誤處理很複雜，因為此邏輯必須透過硬式編碼寫入用戶端。</span><span class="sxs-lookup"><span data-stu-id="ec160-288">Error handling was complex, as this logic had to be hard-coded into the client.</span></span>

- <span data-ttu-id="ec160-289">用戶端與服務一定要使用相同的繫結。</span><span class="sxs-lookup"><span data-stu-id="ec160-289">Clients and services had to always use the same bindings.</span></span>

- <span data-ttu-id="ec160-290">很少妥善分解服務：讓用戶端與實作所有功能的單一服務通訊會比在多個服務之間選擇更簡單。</span><span class="sxs-lookup"><span data-stu-id="ec160-290">Services were rarely well factored: it is easier to have the client talk to one service which implements everything, rather than needing to choose between multiple services.</span></span>

<span data-ttu-id="ec160-291">.NET 4 中的路由服務是設計來讓這些問題更容易解決。</span><span class="sxs-lookup"><span data-stu-id="ec160-291">The routing service in .NET 4 is designed to make these problems easier to solve.</span></span> <span data-ttu-id="ec160-292">新的路由服務具有下列功能：</span><span class="sxs-lookup"><span data-stu-id="ec160-292">The new routing service has the following features:</span></span>

1. <span data-ttu-id="ec160-293">以內容為基礎的路由 (<xref:System.ServiceModel.Dispatcher.MessageFilter> 物件會檢查訊息來判斷應該傳送的目的地)。</span><span class="sxs-lookup"><span data-stu-id="ec160-293">Content based routing (<xref:System.ServiceModel.Dispatcher.MessageFilter> objects examine a message to determine where it should be sent.)</span></span>

2. <span data-ttu-id="ec160-294">通訊協定橋接 (傳輸 & 訊息) </span><span class="sxs-lookup"><span data-stu-id="ec160-294">Protocol bridging (transport & message)</span></span>

3. <span data-ttu-id="ec160-295">錯誤處理 (路由器會攔截通訊例外狀況並容錯移轉至備份端點)。</span><span class="sxs-lookup"><span data-stu-id="ec160-295">Error handling (the router catches communication exceptions and fails over to backup endpoints)</span></span>

4. <span data-ttu-id="ec160-296"><xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> 和路由組態的動態 (記憶體中) 更新。</span><span class="sxs-lookup"><span data-stu-id="ec160-296">Dynamic (in memory) update of <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> and Routing Configuration.</span></span>

### <a name="getting-started"></a><span data-ttu-id="ec160-297">開始使用</span><span class="sxs-lookup"><span data-stu-id="ec160-297">Getting Started</span></span>

1. <span data-ttu-id="ec160-298">檔： [路由](../wcf/feature-details/routing.md)</span><span class="sxs-lookup"><span data-stu-id="ec160-298">Documentation: [Routing](../wcf/feature-details/routing.md)</span></span>

2. <span data-ttu-id="ec160-299">範例： [路由服務 &#91;WCF 範例&#93;](../wcf/samples/routing-services.md)</span><span class="sxs-lookup"><span data-stu-id="ec160-299">Samples: [Routing Services &#91;WCF Samples&#93;](../wcf/samples/routing-services.md)</span></span>

3. <span data-ttu-id="ec160-300">Blog： [路由規則！](/archive/blogs/RoutingRules/)</span><span class="sxs-lookup"><span data-stu-id="ec160-300">Blog: [Routing Rules!](/archive/blogs/RoutingRules/)</span></span>

### <a name="routing-scenarios"></a><span data-ttu-id="ec160-301">路由案例</span><span class="sxs-lookup"><span data-stu-id="ec160-301">Routing Scenarios</span></span>

<span data-ttu-id="ec160-302">在下列案例中，路由服務很有用：</span><span class="sxs-lookup"><span data-stu-id="ec160-302">The routing service is useful in the following scenarios:</span></span>

- <span data-ttu-id="ec160-303">用戶端可以與多個服務通訊，而不需要直接處理所有服務。</span><span class="sxs-lookup"><span data-stu-id="ec160-303">Clients can talk to multiple services without having to address them all directly.</span></span>

- <span data-ttu-id="ec160-304">用戶端可以針對用戶端要求執行其他邏輯，以便判斷要路由傳送的目的地。</span><span class="sxs-lookup"><span data-stu-id="ec160-304">Clients can perform additional logic on a client request to determine where to route it</span></span>

- <span data-ttu-id="ec160-305">將用戶端所執行的作業分解成多個服務實作，而不需要重構用戶端。</span><span class="sxs-lookup"><span data-stu-id="ec160-305">Decompose the operations a client performs into multiple service implementations without refactoring the client.</span></span>

- <span data-ttu-id="ec160-306">用戶端與服務可以宣告具有不同安全性設定的不同繫結。</span><span class="sxs-lookup"><span data-stu-id="ec160-306">Clients and services can speak different bindings with different security settings.</span></span>

- <span data-ttu-id="ec160-307">用戶端可以具備更健全的功能，以防範失敗或無法使用服務的情況。</span><span class="sxs-lookup"><span data-stu-id="ec160-307">Clients can be enabled to be more robust against failure or the unavailability of services.</span></span>

## <a name="wcf-discovery"></a><span data-ttu-id="ec160-308">WCF 探索</span><span class="sxs-lookup"><span data-stu-id="ec160-308">WCF Discovery</span></span>

<span data-ttu-id="ec160-309">WCF 探索是一種架構技術，可讓您將探索機制併入您的應用程式基礎結構。</span><span class="sxs-lookup"><span data-stu-id="ec160-309">WCF Discovery is a framework technology that allows you to incorporate a discovery mechanism to your application infrastructure.</span></span> <span data-ttu-id="ec160-310">您可以使用這項技術，讓服務成為可探索的服務，並且設定用戶端來搜尋服務。</span><span class="sxs-lookup"><span data-stu-id="ec160-310">You can use this to make your service discoverable, and configure your clients to search for services.</span></span> <span data-ttu-id="ec160-311">用戶端不再需要對端點進行硬式編碼，讓應用程式更健全並提高容錯能力。</span><span class="sxs-lookup"><span data-stu-id="ec160-311">Clients no longer need to be hard coded with endpoint, making your application more robust and fault tolerant.</span></span> <span data-ttu-id="ec160-312">探索是在應用程式中建置自動組態功能的完美平台。</span><span class="sxs-lookup"><span data-stu-id="ec160-312">Discovery is the perfect platform to build auto-configuration capabilities into your application.</span></span>

<span data-ttu-id="ec160-313">此產品是以 WS-Discovery 標準為建置基礎。</span><span class="sxs-lookup"><span data-stu-id="ec160-313">The product is built on top of the WS-Discovery standard.</span></span> <span data-ttu-id="ec160-314">它是設計成可互通、可擴充和一般。</span><span class="sxs-lookup"><span data-stu-id="ec160-314">It's designed to be interoperable, extensible, and generic.</span></span> <span data-ttu-id="ec160-315">此產品支援兩種作業模式：</span><span class="sxs-lookup"><span data-stu-id="ec160-315">The product supports two modes of operation:</span></span>

1. <span data-ttu-id="ec160-316">受管理：網路上有一個了解現有服務的實體，因此用戶端會直接查詢此實體以取得資訊。</span><span class="sxs-lookup"><span data-stu-id="ec160-316">Managed: where there is an entity on the network knowledgeable about existing services, clients query it directly for information.</span></span> <span data-ttu-id="ec160-317">這種模式類似於 Active Directory。</span><span class="sxs-lookup"><span data-stu-id="ec160-317">This is analogous to Active Directory.</span></span>

2. <span data-ttu-id="ec160-318">臨機操作：用戶端會使用多點傳送訊息來找出服務。</span><span class="sxs-lookup"><span data-stu-id="ec160-318">Ad-hoc: where clients use multicast messages to locate services.</span></span>

<span data-ttu-id="ec160-319">此外，探索訊息無從驗證網路通訊協定。您可以在支援模式需求的任何通訊協定上使用這些訊息。</span><span class="sxs-lookup"><span data-stu-id="ec160-319">Furthermore, discovery messages are network protocol agnostic; you can use them on top any protocol that supports the mode requirements.</span></span> <span data-ttu-id="ec160-320">例如，您可以透過 UDP 通道或任何其他支援多播訊息的網路來傳送探索多播訊息。</span><span class="sxs-lookup"><span data-stu-id="ec160-320">For example, discovery multicast messages can be sent over the UDP channel or any other network that supports multicast messaging.</span></span> <span data-ttu-id="ec160-321">這些設計點結合了功能彈性，可讓您特別針對您的解決方案調整探索。</span><span class="sxs-lookup"><span data-stu-id="ec160-321">These design points, combined with feature flexibility, allow you to adapt the discovery specifically to your solution.</span></span>

### <a name="getting-started"></a><span data-ttu-id="ec160-322">開始使用</span><span class="sxs-lookup"><span data-stu-id="ec160-322">Getting Started</span></span>

- <span data-ttu-id="ec160-323">檔： [WCF 探索](../wcf/feature-details/wcf-discovery.md)</span><span class="sxs-lookup"><span data-stu-id="ec160-323">Documentation: [WCF Discovery](../wcf/feature-details/wcf-discovery.md)</span></span>

- <span data-ttu-id="ec160-324">範例： [探索 (範例) ](../wcf/samples/discovery-samples.md)</span><span class="sxs-lookup"><span data-stu-id="ec160-324">Samples: [Discovery (Samples)](../wcf/samples/discovery-samples.md)</span></span>

### <a name="discovery-scenarios"></a><span data-ttu-id="ec160-325">探索案例</span><span class="sxs-lookup"><span data-stu-id="ec160-325">Discovery Scenarios</span></span>

<span data-ttu-id="ec160-326">開發人員不想要對端點進行硬式編碼，因為它在服務可用時處於未知狀態。</span><span class="sxs-lookup"><span data-stu-id="ec160-326">A developer doesn't want to hard code endpoints, since it is unknown when my service will be available.</span></span> <span data-ttu-id="ec160-327">不過，開發人員想要在執行階段選擇服務。</span><span class="sxs-lookup"><span data-stu-id="ec160-327">Instead, the developer wants to choose a service at runtime.</span></span> <span data-ttu-id="ec160-328">因此，應用程式的元件之間需要降低耦合、提高健全度，以及自動組態功能。</span><span class="sxs-lookup"><span data-stu-id="ec160-328">More decoupling, robustness, and auto-configuration is needed between the components in the application.</span></span>

## <a name="tracking"></a><span data-ttu-id="ec160-329">追蹤</span><span class="sxs-lookup"><span data-stu-id="ec160-329">Tracking</span></span>

<span data-ttu-id="ec160-330">工作流程追蹤可讓您深入瞭解工作流程實例的執行。</span><span class="sxs-lookup"><span data-stu-id="ec160-330">Workflow tracking provides insight into the execution of a workflow instance.</span></span> <span data-ttu-id="ec160-331">追蹤事件是從工作流程實例層級的工作流程發出，以及在工作流程中的活動執行時發出。</span><span class="sxs-lookup"><span data-stu-id="ec160-331">The tracking events are emitted from a workflow at the workflow instance level and when activities within the workflow execute.</span></span> <span data-ttu-id="ec160-332">您必須將工作流程追蹤參與者加入至工作流程主機，才能訂閱追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="ec160-332">A workflow tracking participant needs to be added to the workflow host to subscribe to tracking records.</span></span> <span data-ttu-id="ec160-333">系統會使用追蹤設定檔來篩選追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="ec160-333">The tracking records are filtered using a tracking profile.</span></span> <span data-ttu-id="ec160-334">.NET Framework 為 Windows) 追蹤參與者提供 ETW (事件追蹤，而且基本設定檔會安裝在 machine.config 檔案中。</span><span class="sxs-lookup"><span data-stu-id="ec160-334">The .NET Framework provides an ETW (Event Tracing for Windows) tracking participant, and a basic profile is installed in the machine.config file.</span></span>

### <a name="getting-started"></a><span data-ttu-id="ec160-335">開始使用</span><span class="sxs-lookup"><span data-stu-id="ec160-335">Getting Started</span></span>

1. <span data-ttu-id="ec160-336">在 Visual Studio 2010 中，建立 WCF 工作流程服務應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="ec160-336">In Visual Studio 2010, create a WCF Workflow Service Application project.</span></span> <span data-ttu-id="ec160-337">一組 <xref:System.ServiceModel.Activities.Receive> 和 <xref:System.ServiceModel.Activities.SendReply> 將置於畫布上，以便開始。</span><span class="sxs-lookup"><span data-stu-id="ec160-337">A <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply> pair will be placed on your canvas to start.</span></span>

2. <span data-ttu-id="ec160-338">開啟 web.config 並加入不含設定檔的 ETW 追蹤行為。</span><span class="sxs-lookup"><span data-stu-id="ec160-338">Open the web.config and add an ETW tracking behavior with no profile.</span></span>

    1. <span data-ttu-id="ec160-339">系統會使用預設設定檔。</span><span class="sxs-lookup"><span data-stu-id="ec160-339">The default profile is used.</span></span>

    2. <span data-ttu-id="ec160-340">開啟 [事件檢視器]，並在下列節點中啟用分析通道： **事件檢視器**、 **應用程式和服務記錄**檔、 **Microsoft**、 **Windows**、 **應用程式伺服器-應用程式**。</span><span class="sxs-lookup"><span data-stu-id="ec160-340">Open event viewer and enable the analytic channel in the following node: **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="ec160-341">以滑鼠右鍵按一下 [ **分析** ]，然後選取 [ **啟用記錄**]。</span><span class="sxs-lookup"><span data-stu-id="ec160-341">Right-click **Analytic** and select **Enable Log**.</span></span>

    3. <span data-ttu-id="ec160-342">執行工作流程服務。</span><span class="sxs-lookup"><span data-stu-id="ec160-342">Run the workflow service.</span></span>

    4. <span data-ttu-id="ec160-343">在事件檢視器中查看工作流程追蹤事件。</span><span class="sxs-lookup"><span data-stu-id="ec160-343">Observe the workflow tracking events in event viewer.</span></span>

3. <span data-ttu-id="ec160-344">範例： [追蹤](./samples/tracking.md)</span><span class="sxs-lookup"><span data-stu-id="ec160-344">Samples: [Tracking](./samples/tracking.md)</span></span>

4. <span data-ttu-id="ec160-345">概念檔： [工作流程追蹤和追蹤](workflow-tracking-and-tracing.md)</span><span class="sxs-lookup"><span data-stu-id="ec160-345">Conceptual documentation: [Workflow Tracking and Tracing](workflow-tracking-and-tracing.md)</span></span>

## <a name="sql-workflow-instance-store"></a><span data-ttu-id="ec160-346">SQL 工作流程執行個體存放區</span><span class="sxs-lookup"><span data-stu-id="ec160-346">SQL Workflow Instance Store</span></span>

<span data-ttu-id="ec160-347"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 是以 SQL Server 為基礎的執行個體存放區實作。</span><span class="sxs-lookup"><span data-stu-id="ec160-347">The <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> is a SQL Server-based implementation of an instance store.</span></span> <span data-ttu-id="ec160-348">執行個體存放區會儲存執行中執行個體的狀態以及載入和繼續該執行個體所需的所有資料。</span><span class="sxs-lookup"><span data-stu-id="ec160-348">An instance store stores the state of a running instance together with all data necessary to load and resume that instance.</span></span> <span data-ttu-id="ec160-349">如果工作流程會保存，服務主機就會指示執行個體存放區儲存執行個體狀態，而且當該執行個體的訊息送達或延遲活動過期時，它就會指示執行個體存放區載入執行個體狀態。</span><span class="sxs-lookup"><span data-stu-id="ec160-349">The service host instructs the instance store to save the instance state if the workflow persists, and it instructs the instance store to load the instance state when a message arrives for that instance or a delay activity expires.</span></span>

### <a name="getting-started"></a><span data-ttu-id="ec160-350">開始使用</span><span class="sxs-lookup"><span data-stu-id="ec160-350">Getting Started</span></span>

1. <span data-ttu-id="ec160-351">在 Visual Studio 2012 中，建立包含隱含或明確活動的工作流程 <xref:System.Activities.Statements.Persist> 。</span><span class="sxs-lookup"><span data-stu-id="ec160-351">In Visual Studio 2012, create a Workflow that contains an implicit or explicit <xref:System.Activities.Statements.Persist> activity.</span></span> <span data-ttu-id="ec160-352">將 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 行為加入至工作流程服務主機。</span><span class="sxs-lookup"><span data-stu-id="ec160-352">Add the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> behavior to your workflow service host.</span></span> <span data-ttu-id="ec160-353">您可以在程式碼或應用程式組態檔中進行這項作業。</span><span class="sxs-lookup"><span data-stu-id="ec160-353">This can be done in code or in the application configuration file.</span></span>

2. <span data-ttu-id="ec160-354">範例：[持續](/previous-versions/dotnet/netframework-4.0/dd699769(v%3dvs.100))性</span><span class="sxs-lookup"><span data-stu-id="ec160-354">Samples: [Persistence](/previous-versions/dotnet/netframework-4.0/dd699769(v%3dvs.100))</span></span>

3. <span data-ttu-id="ec160-355">概念檔： [SQL 工作流程實例存放區](sql-workflow-instance-store.md)。</span><span class="sxs-lookup"><span data-stu-id="ec160-355">Conceptual documentation: [SQL Workflow Instance Store](sql-workflow-instance-store.md).</span></span>
