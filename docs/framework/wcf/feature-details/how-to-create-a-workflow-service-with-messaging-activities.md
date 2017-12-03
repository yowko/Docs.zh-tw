---
title: "HOW TO：說明如何使用訊息活動建立工作流程服務。"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53d094e2-6901-4aa1-88b8-024b27ccf78b
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b57139fdf2a07f2d37bc337a041704eee174328e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-workflow-service-with-messaging-activities"></a><span data-ttu-id="3010f-102">HOW TO：說明如何使用訊息活動建立工作流程服務。</span><span class="sxs-lookup"><span data-stu-id="3010f-102">How to: Create a Workflow Service with Messaging Activities</span></span>
<span data-ttu-id="3010f-103">本主題描述如何使用訊息活動建立簡單的工作流程服務。</span><span class="sxs-lookup"><span data-stu-id="3010f-103">This topic describes how to create a simple workflow service using messaging activities.</span></span> <span data-ttu-id="3010f-104">本主題的重點在於建立工作流程服務的機制，而該服務主要包含的便是訊息活動。</span><span class="sxs-lookup"><span data-stu-id="3010f-104">This topic focuses on the mechanics of creating a workflow service where the service consists solely of messaging activities.</span></span> <span data-ttu-id="3010f-105">在真實世界的服務中，工作流程包含許多其他活動。</span><span class="sxs-lookup"><span data-stu-id="3010f-105">In a real-world service, the workflow contains many other activities.</span></span> <span data-ttu-id="3010f-106">服務會實作一項稱為 Echo 的作業，該作業會使用字串並將字串傳回呼叫端。</span><span class="sxs-lookup"><span data-stu-id="3010f-106">The service implements one operation called Echo, which takes a string and returns the string to the caller.</span></span> <span data-ttu-id="3010f-107">本主題即為兩個主題的第一個。</span><span class="sxs-lookup"><span data-stu-id="3010f-107">This topic is the first in a series of two topics.</span></span> <span data-ttu-id="3010f-108">下一個主題[How To: 服務從工作流程應用程式存取](../../../../docs/framework/wcf/feature-details/how-to-access-a-service-from-a-workflow-application.md)討論如何建立可呼叫服務，本主題中建立工作流程應用程式。</span><span class="sxs-lookup"><span data-stu-id="3010f-108">The next topic [How To: Access a Service From a Workflow Application](../../../../docs/framework/wcf/feature-details/how-to-access-a-service-from-a-workflow-application.md) discusses how to create a workflow application that can call the service created in this topic.</span></span>  
  
### <a name="to-create-a-workflow-service-project"></a><span data-ttu-id="3010f-109">若要建立工作流程服務專案</span><span class="sxs-lookup"><span data-stu-id="3010f-109">To create a workflow service project</span></span>  
  
1.  <span data-ttu-id="3010f-110">啟動 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3010f-110">Start [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="3010f-111">按一下**檔案**功能表上，選取**新增**，然後**專案**顯示**新增專案 對話方塊**。</span><span class="sxs-lookup"><span data-stu-id="3010f-111">Click the **File** menu, select **New**, and then **Project** to display the **New Project Dialog**.</span></span> <span data-ttu-id="3010f-112">選取**工作流程**從已安裝的範本清單和**WCF 工作流程服務應用程式**從專案類型清單。</span><span class="sxs-lookup"><span data-stu-id="3010f-112">Select **Workflow** from the list of installed templates and **WCF Workflow Service Application** from the list of project types.</span></span> <span data-ttu-id="3010f-113">將專案命名`MyWFService`並使用預設位置，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="3010f-113">Name the project `MyWFService` and use the default location as shown in the following illustration.</span></span>  
  
     <span data-ttu-id="3010f-114">按一下**確定**按鈕以關閉**新增專案 對話方塊**。</span><span class="sxs-lookup"><span data-stu-id="3010f-114">Click the **OK** button to dismiss the **New Project Dialog**.</span></span>  
  
3.  <span data-ttu-id="3010f-115">建立專案後，會在設計工具中開啟 Service1.xamlx 檔案，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="3010f-115">When the project is created, the Service1.xamlx file is opened in the designer as shown in the following illustration.</span></span>  
  
     <span data-ttu-id="3010f-116">![預設的工作流程設計工具中顯示](../../../../docs/framework/wcf/feature-details/media/defaultworkflowservice.JPG "DefaultWorkflowService")</span><span class="sxs-lookup"><span data-stu-id="3010f-116">![The default workflow displayed in the designer](../../../../docs/framework/wcf/feature-details/media/defaultworkflowservice.JPG "DefaultWorkflowService")</span></span>  
  
     <span data-ttu-id="3010f-117">以滑鼠右鍵按一下活動標示為**循序服務**選取**刪除**。</span><span class="sxs-lookup"><span data-stu-id="3010f-117">Right-click the activity labeled **Sequential Service** and select **Delete**.</span></span>  
  
### <a name="to-implement-the-workflow-service"></a><span data-ttu-id="3010f-118">若要實作工作流程服務</span><span class="sxs-lookup"><span data-stu-id="3010f-118">To implement the workflow service</span></span>  
  
1.  <span data-ttu-id="3010f-119">選取**工具箱** 索引標籤上顯示 工具箱，然後按一下圖釘，讓視窗保持開啟畫面的左半部。</span><span class="sxs-lookup"><span data-stu-id="3010f-119">Select the **Toolbox** tab on the left side of the screen to display the toolbox and click the pushpin to keep the window open.</span></span> <span data-ttu-id="3010f-120">展開**傳訊**顯示訊息活動和訊息活動範本，如下圖所示的 [工具箱] 的區段。</span><span class="sxs-lookup"><span data-stu-id="3010f-120">Expand the **Messaging** section of the toolbox to display the messaging activities and the messaging activity templates as shown in the following illustration.</span></span>  
  
     <span data-ttu-id="3010f-121">![展開傳訊 索引標籤的工具箱](../../../../docs/framework/wcf/feature-details/media/wfdesignertoolbox.JPG "WFDesignerToolbox")</span><span class="sxs-lookup"><span data-stu-id="3010f-121">![The toolbox with messaging tab expanded](../../../../docs/framework/wcf/feature-details/media/wfdesignertoolbox.JPG "WFDesignerToolbox")</span></span>  
  
2.  <span data-ttu-id="3010f-122">將拖放**ReceiveAndSendReply**工作流程設計工具的範本。</span><span class="sxs-lookup"><span data-stu-id="3010f-122">Drag and drop a **ReceiveAndSendReply** template to the workflow designer.</span></span> <span data-ttu-id="3010f-123">這會建立<!--zz <xref:System.ServiceModel.Activities.Sequence>-->`System.ServiceModel.Activities.Sequence`活動，具有**接收**活動，後面<xref:System.ServiceModel.Activities.SendReply>活動，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="3010f-123">This creates a <!--zz <xref:System.ServiceModel.Activities.Sequence>--> `System.ServiceModel.Activities.Sequence` activity with a **Receive** activity followed by a <xref:System.ServiceModel.Activities.SendReply> activity as shown in the following illustration.</span></span>  
  
     <span data-ttu-id="3010f-124">![在設計工具中的 ReceiveAndSendReply 範本](../../../../docs/framework/wcf/feature-details/media/receiveandsendreply.JPG "ReceiveAndSendReply")</span><span class="sxs-lookup"><span data-stu-id="3010f-124">![ReceiveAndSendReply template in designer](../../../../docs/framework/wcf/feature-details/media/receiveandsendreply.JPG "ReceiveAndSendReply")</span></span>  
  
     <span data-ttu-id="3010f-125">注意，<xref:System.ServiceModel.Activities.SendReply> 活動的 <xref:System.ServiceModel.Activities.SendReply.Request%2A> 屬性會設為 `Receive`，也就是 <xref:System.ServiceModel.Activities.Receive> 活動所回覆之 <xref:System.ServiceModel.Activities.SendReply> 活動的名稱。</span><span class="sxs-lookup"><span data-stu-id="3010f-125">Notice that the <xref:System.ServiceModel.Activities.SendReply> activity’s <xref:System.ServiceModel.Activities.SendReply.Request%2A> property is set to `Receive`, the name of the <xref:System.ServiceModel.Activities.Receive> activity to which the <xref:System.ServiceModel.Activities.SendReply> activity is replying.</span></span>  
  
3.  <span data-ttu-id="3010f-126">在<xref:System.ServiceModel.Activities.Receive>活動型別`Echo`標示為文字方塊**OperationName**。</span><span class="sxs-lookup"><span data-stu-id="3010f-126">In the <xref:System.ServiceModel.Activities.Receive> activity type `Echo` into the textbox labeled **OperationName**.</span></span> <span data-ttu-id="3010f-127">這樣做會定義服務所實作之作業的名稱。</span><span class="sxs-lookup"><span data-stu-id="3010f-127">This defines the name of the operation the service implements.</span></span>  
  
     <span data-ttu-id="3010f-128">![指定作業名稱](../../../../docs/framework/wcf/feature-details/media/defineoperation.JPG "DefineOperation")</span><span class="sxs-lookup"><span data-stu-id="3010f-128">![Specify the operation name](../../../../docs/framework/wcf/feature-details/media/defineoperation.JPG "DefineOperation")</span></span>  
  
4.  <span data-ttu-id="3010f-129">與<xref:System.ServiceModel.Activities.Receive>活動選取，開啟 屬性 視窗如果未開啟，即可**檢視**功能表，然後選取**屬性 視窗**。</span><span class="sxs-lookup"><span data-stu-id="3010f-129">With the <xref:System.ServiceModel.Activities.Receive> activity selected, open the properties window if not already open by clicking the **View** menu and selecting **Properties Window**.</span></span> <span data-ttu-id="3010f-130">在**屬性 視窗**向下捲動直到您看到**CanCreateInstance**按一下核取方塊，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="3010f-130">In the **Properties Window** scroll down until you see **CanCreateInstance** and click the checkbox as shown in the following illustration.</span></span> <span data-ttu-id="3010f-131">這項設定可讓工作流程服務主機在接收訊息時建立新的服務執行個體 (如果需要的話)。</span><span class="sxs-lookup"><span data-stu-id="3010f-131">This setting enables the workflow service host to create a new instance of the service (if needed) when a message is received.</span></span>  
  
     <span data-ttu-id="3010f-132">![CanCreateInstance 屬性](../../../../docs/framework/wcf/feature-details/media/cancreateinstance.JPG "CanCreateInstance")</span><span class="sxs-lookup"><span data-stu-id="3010f-132">![CanCreateInstance property](../../../../docs/framework/wcf/feature-details/media/cancreateinstance.JPG "CanCreateInstance")</span></span>  
  
5.  <span data-ttu-id="3010f-133">選取<!--zz <xref:System.ServiceModel.Activities.Sequence>-->`System.ServiceModel.Activities.Sequence`活動，然後按一下**變數**在設計工具左下角的按鈕。</span><span class="sxs-lookup"><span data-stu-id="3010f-133">Select the <!--zz <xref:System.ServiceModel.Activities.Sequence>--> `System.ServiceModel.Activities.Sequence` activity and click the **Variables** button in the lower left corner of the designer.</span></span> <span data-ttu-id="3010f-134">如此將會顯示變數編輯器。</span><span class="sxs-lookup"><span data-stu-id="3010f-134">This displays the variables editor.</span></span> <span data-ttu-id="3010f-135">按一下**建立變數**連結加入變數，以儲存傳送作業的字串。</span><span class="sxs-lookup"><span data-stu-id="3010f-135">Click the **Create Variable** link to add a variable to store the string sent to the operation.</span></span> <span data-ttu-id="3010f-136">將變數命名`msg`並設定其**變數**輸入為字串，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="3010f-136">Name the variable `msg` and set its **Variable** type to String as shown in the following illustration.</span></span>  
  
     <span data-ttu-id="3010f-137">![將變數加入](../../../../docs/framework/wcf/feature-details/media/addvariable.JPG "AddVariable")</span><span class="sxs-lookup"><span data-stu-id="3010f-137">![Add a variable](../../../../docs/framework/wcf/feature-details/media/addvariable.JPG "AddVariable")</span></span>  
  
     <span data-ttu-id="3010f-138">按一下**變數**按鈕以關閉變數編輯器。</span><span class="sxs-lookup"><span data-stu-id="3010f-138">Click the **Variables** button again to close the variables editor.</span></span>  
  
6.  <span data-ttu-id="3010f-139">按一下**定義...**</span><span class="sxs-lookup"><span data-stu-id="3010f-139">Click the **Define..**</span></span> <span data-ttu-id="3010f-140">連結中**內容**文字方塊中<xref:System.ServiceModel.Activities.Receive>活動顯示**內容定義**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="3010f-140">link in the **Content** text box in the <xref:System.ServiceModel.Activities.Receive> activity to display the **Content Definition** dialog.</span></span> <span data-ttu-id="3010f-141">選取**參數**選項按鈕，按一下**加入新的參數**連結，輸入`inMsg`中**名稱**文字方塊中，選取**字串**中**類型**下拉式清單方塊，然後輸入`msg`中**指派給**文字方塊中，在下圖所示。</span><span class="sxs-lookup"><span data-stu-id="3010f-141">Select the **Parameters** radio button, click the **Add new Parameter** link, type `inMsg` in the **name** text box, select **String** in the **Type** drop down list box, and type `msg` in the **Assign To** text box as shown in the following illustration.</span></span>  
  
     <span data-ttu-id="3010f-142">![加入參數內容](../../../../docs/framework/wcf/feature-details/media/parameterscontent.jpg "ParametersContent")</span><span class="sxs-lookup"><span data-stu-id="3010f-142">![Adding Parameters Content](../../../../docs/framework/wcf/feature-details/media/parameterscontent.jpg "ParametersContent")</span></span>  
  
     <span data-ttu-id="3010f-143">這樣會指定 [接收] 活動接收字串參數，且該資料繫結至 `msg` 變數。</span><span class="sxs-lookup"><span data-stu-id="3010f-143">This specifies that the Receive activity receives string parameter and that data is bound to the `msg` variable.</span></span> <span data-ttu-id="3010f-144">按一下**確定**關閉**內容定義**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="3010f-144">Click **OK** to close the **Content Definition** dialog.</span></span>  
  
7.  <span data-ttu-id="3010f-145">按一下**定義...**中連結**內容**方塊中<xref:System.ServiceModel.Activities.SendReply>活動顯示**內容定義**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="3010f-145">Click the **Define...** link in the **Content** box in the <xref:System.ServiceModel.Activities.SendReply> activity to display the **Content Definition** dialog.</span></span> <span data-ttu-id="3010f-146">選取**參數**選項按鈕，按一下**加入新的參數**連結，輸入`outMsg`中**名稱**文字方塊中，選取**字串**中**類型**下拉式清單方塊中，和`msg`中**值**文字方塊中，在下圖所示。</span><span class="sxs-lookup"><span data-stu-id="3010f-146">Select the **Parameters** radio button, click the **Add new Parameter** link, type `outMsg` in the **name** textbox, select **String** in the **Type** dropdown list box, and `msg` in the **Value** text box as shown in the following illustration.</span></span>  
  
     <span data-ttu-id="3010f-147">![加入參數內容](../../../../docs/framework/wcf/feature-details/media/parameterscontent2.jpg "ParametersContent2")</span><span class="sxs-lookup"><span data-stu-id="3010f-147">![Adding Parameters Content](../../../../docs/framework/wcf/feature-details/media/parameterscontent2.jpg "ParametersContent2")</span></span>  
  
     <span data-ttu-id="3010f-148">這樣會指定 <xref:System.ServiceModel.Activities.SendReply> 活動傳送訊息或訊息合約型別，且該資料繫結至 `msg` 變數。</span><span class="sxs-lookup"><span data-stu-id="3010f-148">This specifies that the <xref:System.ServiceModel.Activities.SendReply> activity sends a message or message contract type and that data is bound to the `msg` variable.</span></span> <span data-ttu-id="3010f-149">由於此為 <xref:System.ServiceModel.Activities.SendReply> 活動，代表 `msg` 中的資料是用來填入由活動傳回用戶端的訊息。</span><span class="sxs-lookup"><span data-stu-id="3010f-149">Because this is a <xref:System.ServiceModel.Activities.SendReply> activity, this means the data in `msg` is used to populate the message the activity sends back to the client.</span></span> <span data-ttu-id="3010f-150">按一下**確定**關閉**內容定義**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="3010f-150">Click **OK** to close the **Content Definition** dialog.</span></span>  
  
8.  <span data-ttu-id="3010f-151">儲存並建置此方案，依序按一下**建置**功能表，然後選取**建置方案**。</span><span class="sxs-lookup"><span data-stu-id="3010f-151">Save and build the solution by clicking the **Build** menu and selecting **Build Solution**.</span></span>  
  
## <a name="configure-the-workflow-service-project"></a><span data-ttu-id="3010f-152">設定工作流程服務專案。</span><span class="sxs-lookup"><span data-stu-id="3010f-152">Configure the Workflow Service Project</span></span>  
 <span data-ttu-id="3010f-153">工作流程執行服務已完成。</span><span class="sxs-lookup"><span data-stu-id="3010f-153">The workflow service is complete.</span></span> <span data-ttu-id="3010f-154">本節說明如何設定工作流程服務方案，讓裝載和執行更順利。</span><span class="sxs-lookup"><span data-stu-id="3010f-154">This section explains how to configure the workflow service solution to make it easy to host and run.</span></span> <span data-ttu-id="3010f-155">此方案是使用 ASP.NET 程式開發伺服器來裝載服務。</span><span class="sxs-lookup"><span data-stu-id="3010f-155">This solution uses the ASP.NET Development Server to host the service.</span></span>  
  
#### <a name="to-set-project-start-up-options"></a><span data-ttu-id="3010f-156">若要設定專案啟動選項</span><span class="sxs-lookup"><span data-stu-id="3010f-156">To set project start up options</span></span>  
  
1.  <span data-ttu-id="3010f-157">在**方案總管 中**，以滑鼠右鍵按一下**MyWFService**選取**屬性**顯示**專案屬性**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="3010f-157">In the **Solution Explorer**, right-click **MyWFService** and select **Properties** to display the **Project Properties** dialog.</span></span>  
  
2.  <span data-ttu-id="3010f-158">選取**Web**索引標籤並選取**特定頁面**下**起始動作**和型別`Service1.xamlx`在文字方塊中，在下圖所示。</span><span class="sxs-lookup"><span data-stu-id="3010f-158">Select the **Web** tab and select **Specific Page** under **Start Action** and type `Service1.xamlx` in the text box as shown in the following illustration.</span></span>  
  
     <span data-ttu-id="3010f-159">![專案屬性對話方塊](../../../../docs/framework/wcf/feature-details/media/projectpropertiesdlg.JPG "ProjectPropertiesDlg")</span><span class="sxs-lookup"><span data-stu-id="3010f-159">![The project properties dialog](../../../../docs/framework/wcf/feature-details/media/projectpropertiesdlg.JPG "ProjectPropertiesDlg")</span></span>  
  
     <span data-ttu-id="3010f-160">這樣做會裝載在 ASP.NET 程式開發伺服器的 Service1.xamlx 中所定義的服務。</span><span class="sxs-lookup"><span data-stu-id="3010f-160">This hosts the service defined in Service1.xamlx in the ASP.NET Development Server.</span></span>  
  
3.  <span data-ttu-id="3010f-161">按 Ctrl+F5 啟動服務。</span><span class="sxs-lookup"><span data-stu-id="3010f-161">Press Ctrl + F5 to launch the service.</span></span> <span data-ttu-id="3010f-162">[ASP.NET 程式開發伺服器] 圖示會顯示在桌面的右下角，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="3010f-162">The ASP.NET Development Server icon is displayed in the lower right side of the desktop as shown in the following image.</span></span>  
  
     <span data-ttu-id="3010f-163">![ASP.NET Developer Server 圖示](../../../../docs/framework/wcf/feature-details/media/aspnetdevservericon.JPG "ASPNETDEVServerIcon")</span><span class="sxs-lookup"><span data-stu-id="3010f-163">![The ASP.NET Developer Server Icon](../../../../docs/framework/wcf/feature-details/media/aspnetdevservericon.JPG "ASPNETDEVServerIcon")</span></span>  
  
     <span data-ttu-id="3010f-164">此外，Internet Explorer 還會顯示該服務的 WCF 服務說明網頁。</span><span class="sxs-lookup"><span data-stu-id="3010f-164">In addition, Internet Explorer displays the WCF Service Help Page for the service.</span></span>  
  
     <span data-ttu-id="3010f-165">![WCF 說明頁面](../../../../docs/framework/wcf/feature-details/media/wcfhelppate.JPG "WCFHelpPate")</span><span class="sxs-lookup"><span data-stu-id="3010f-165">![WCF Help Page](../../../../docs/framework/wcf/feature-details/media/wcfhelppate.JPG "WCFHelpPate")</span></span>  
  
4.  <span data-ttu-id="3010f-166">繼續前往[How To: 服務從工作流程應用程式存取](../../../../docs/framework/wcf/feature-details/how-to-access-a-service-from-a-workflow-application.md)主題以建立工作流程用戶端會呼叫此服務。</span><span class="sxs-lookup"><span data-stu-id="3010f-166">Continue on to the [How To: Access a Service From a Workflow Application](../../../../docs/framework/wcf/feature-details/how-to-access-a-service-from-a-workflow-application.md) topic to create a workflow client that calls this service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3010f-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3010f-167">See Also</span></span>  
 [<span data-ttu-id="3010f-168">工作流程服務</span><span class="sxs-lookup"><span data-stu-id="3010f-168">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="3010f-169">裝載工作流程服務概觀</span><span class="sxs-lookup"><span data-stu-id="3010f-169">Hosting Workflow Services Overview</span></span>](../../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md)  
 [<span data-ttu-id="3010f-170">傳訊活動</span><span class="sxs-lookup"><span data-stu-id="3010f-170">Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/messaging-activities.md)
