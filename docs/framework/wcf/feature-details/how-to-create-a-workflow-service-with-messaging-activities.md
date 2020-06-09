---
title: HOW TO：說明如何使用訊息活動建立工作流程服務。
ms.date: 03/30/2017
ms.assetid: 53d094e2-6901-4aa1-88b8-024b27ccf78b
ms.openlocfilehash: b4991fc9f8a6c45cae3943f1506247c42ed2b30b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597120"
---
# <a name="how-to-create-a-workflow-service-with-messaging-activities"></a><span data-ttu-id="c3de1-102">HOW TO：說明如何使用訊息活動建立工作流程服務。</span><span class="sxs-lookup"><span data-stu-id="c3de1-102">How to: Create a Workflow Service with Messaging Activities</span></span>
<span data-ttu-id="c3de1-103">本主題描述如何使用訊息活動建立簡單的工作流程服務。</span><span class="sxs-lookup"><span data-stu-id="c3de1-103">This topic describes how to create a simple workflow service using messaging activities.</span></span> <span data-ttu-id="c3de1-104">本主題的重點在於建立工作流程服務的機制，而該服務主要包含的便是訊息活動。</span><span class="sxs-lookup"><span data-stu-id="c3de1-104">This topic focuses on the mechanics of creating a workflow service where the service consists solely of messaging activities.</span></span> <span data-ttu-id="c3de1-105">在真實世界的服務中，工作流程包含許多其他活動。</span><span class="sxs-lookup"><span data-stu-id="c3de1-105">In a real-world service, the workflow contains many other activities.</span></span> <span data-ttu-id="c3de1-106">服務會實作一項稱為 Echo 的作業，該作業會使用字串並將字串傳回呼叫端。</span><span class="sxs-lookup"><span data-stu-id="c3de1-106">The service implements one operation called Echo, which takes a string and returns the string to the caller.</span></span> <span data-ttu-id="c3de1-107">本主題即為兩個主題的第一個。</span><span class="sxs-lookup"><span data-stu-id="c3de1-107">This topic is the first in a series of two topics.</span></span> <span data-ttu-id="c3de1-108">下一個主題[如何：從工作流應用程式存取服務](how-to-access-a-service-from-a-workflow-application.md)討論如何建立可以呼叫本主題中所建立之服務的工作流程應用程式。</span><span class="sxs-lookup"><span data-stu-id="c3de1-108">The next topic [How To: Access a Service From a Workflow Application](how-to-access-a-service-from-a-workflow-application.md) discusses how to create a workflow application that can call the service created in this topic.</span></span>  
  
### <a name="to-create-a-workflow-service-project"></a><span data-ttu-id="c3de1-109">若要建立工作流程服務專案</span><span class="sxs-lookup"><span data-stu-id="c3de1-109">To create a workflow service project</span></span>  
  
1. <span data-ttu-id="c3de1-110">啟動 Visual Studio 2012。</span><span class="sxs-lookup"><span data-stu-id="c3de1-110">Start Visual Studio 2012.</span></span>  
  
2. <span data-ttu-id="c3de1-111">依序**按一下 [檔案**] 功能表、[**新增**] 和 [**專案**]，以顯示 [**新增專案] 對話方塊**。</span><span class="sxs-lookup"><span data-stu-id="c3de1-111">Click the **File** menu, select **New**, and then **Project** to display the **New Project Dialog**.</span></span> <span data-ttu-id="c3de1-112">從專案類型清單中選取 [已安裝的範本] 和 [ **WCF 工作流程服務應用程式**] 清單中的 [**工作流程**]。</span><span class="sxs-lookup"><span data-stu-id="c3de1-112">Select **Workflow** from the list of installed templates and **WCF Workflow Service Application** from the list of project types.</span></span> <span data-ttu-id="c3de1-113">將專案命名 `MyWFService` 為，並使用預設位置，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="c3de1-113">Name the project `MyWFService` and use the default location as shown in the following illustration.</span></span>  
  
     <span data-ttu-id="c3de1-114">按一下 [**確定]** 按鈕以關閉 [**新增專案] 對話方塊**。</span><span class="sxs-lookup"><span data-stu-id="c3de1-114">Click the **OK** button to dismiss the **New Project Dialog**.</span></span>  
  
3. <span data-ttu-id="c3de1-115">建立專案後，會在設計工具中開啟 Service1.xamlx 檔案，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="c3de1-115">When the project is created, the Service1.xamlx file is opened in the designer as shown in the following illustration.</span></span>  
  
     ![螢幕擷取畫面：在設計工具中顯示開啟的 Service1 service1.xamlx 檔案。](./media/how-to-create-a-workflow-service-with-messaging-activities/default-workflow-service.jpg)  
  
     <span data-ttu-id="c3de1-117">以滑鼠右鍵按一下標示為 [**連續服務**] 的活動，然後選取 [**刪除**]。</span><span class="sxs-lookup"><span data-stu-id="c3de1-117">Right-click the activity labeled **Sequential Service** and select **Delete**.</span></span>  
  
### <a name="to-implement-the-workflow-service"></a><span data-ttu-id="c3de1-118">若要實作工作流程服務</span><span class="sxs-lookup"><span data-stu-id="c3de1-118">To implement the workflow service</span></span>  
  
1. <span data-ttu-id="c3de1-119">選取畫面左側的 [**工具箱**] 索引標籤，以顯示 [工具箱]，然後按一下圖釘讓視窗保持開啟。</span><span class="sxs-lookup"><span data-stu-id="c3de1-119">Select the **Toolbox** tab on the left side of the screen to display the toolbox and click the pushpin to keep the window open.</span></span> <span data-ttu-id="c3de1-120">展開 [工具箱] 的 [**訊息**] 區段，顯示訊息活動和訊息活動範本，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="c3de1-120">Expand the **Messaging** section of the toolbox to display the messaging activities and the messaging activity templates as shown in the following illustration.</span></span>  
  
     ![顯示已展開 [訊息] 區段的 [工具箱] 的螢幕擷取畫面。](./media/how-to-create-a-workflow-service-with-messaging-activities/toolbox-messaging-section.jpg)  
  
2. <span data-ttu-id="c3de1-122">將**receiveandsendreply]** 範本拖放到工作流程設計工具。</span><span class="sxs-lookup"><span data-stu-id="c3de1-122">Drag and drop a **ReceiveAndSendReply** template to the workflow designer.</span></span> <span data-ttu-id="c3de1-123">這會建立一個 <xref:System.Activities.Statements.Sequence> 活動， **Receive**其後面接著一個活動，如下 <xref:System.ServiceModel.Activities.SendReply> 圖所示。</span><span class="sxs-lookup"><span data-stu-id="c3de1-123">This creates a <xref:System.Activities.Statements.Sequence> activity with a **Receive** activity followed by a <xref:System.ServiceModel.Activities.SendReply> activity as shown in the following illustration.</span></span>  
  
     ![顯示 Receiveandsendreply] 範本的螢幕擷取畫面。](./media/how-to-create-a-workflow-service-with-messaging-activities/receiveandsendreply-template.jpg)  
  
     <span data-ttu-id="c3de1-125">注意，<xref:System.ServiceModel.Activities.SendReply> 活動的 <xref:System.ServiceModel.Activities.SendReply.Request%2A> 屬性會設為 `Receive`，也就是 <xref:System.ServiceModel.Activities.Receive> 活動所回覆之 <xref:System.ServiceModel.Activities.SendReply> 活動的名稱。</span><span class="sxs-lookup"><span data-stu-id="c3de1-125">Notice that the <xref:System.ServiceModel.Activities.SendReply> activity’s <xref:System.ServiceModel.Activities.SendReply.Request%2A> property is set to `Receive`, the name of the <xref:System.ServiceModel.Activities.Receive> activity to which the <xref:System.ServiceModel.Activities.SendReply> activity is replying.</span></span>  
  
3. <span data-ttu-id="c3de1-126">在活動類型中，加上 <xref:System.ServiceModel.Activities.Receive> `Echo` 標示為**OperationName**的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="c3de1-126">In the <xref:System.ServiceModel.Activities.Receive> activity type `Echo` into the textbox labeled **OperationName**.</span></span> <span data-ttu-id="c3de1-127">這樣做會定義服務所實作之作業的名稱。</span><span class="sxs-lookup"><span data-stu-id="c3de1-127">This defines the name of the operation the service implements.</span></span>  
  
     ![顯示要在何處指定作業名稱的螢幕擷取畫面。](./media/how-to-create-a-workflow-service-with-messaging-activities/define-operation-name.jpg)  
  
4. <span data-ttu-id="c3de1-129"><xref:System.ServiceModel.Activities.Receive>選取活動後，按一下 [**流覽**] 功能表並選取 [**屬性視窗]**，開啟 [屬性] 視窗（如果尚未開啟）。</span><span class="sxs-lookup"><span data-stu-id="c3de1-129">With the <xref:System.ServiceModel.Activities.Receive> activity selected, open the properties window if not already open by clicking the **View** menu and selecting **Properties Window**.</span></span> <span data-ttu-id="c3de1-130">在 [**屬性] 視窗**中，向下**CanCreateInstance** ，直到您看到 []，然後按一下核取方塊，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="c3de1-130">In the **Properties Window** scroll down until you see **CanCreateInstance** and click the checkbox as shown in the following illustration.</span></span> <span data-ttu-id="c3de1-131">這項設定可讓工作流程服務主機在接收訊息時建立新的服務執行個體 (如果需要的話)。</span><span class="sxs-lookup"><span data-stu-id="c3de1-131">This setting enables the workflow service host to create a new instance of the service (if needed) when a message is received.</span></span>  
  
     ![顯示 CanCreateInstance 屬性的螢幕擷取畫面。](./media/how-to-create-a-workflow-service-with-messaging-activities/cancreateinstance-property.jpg)  
  
5. <span data-ttu-id="c3de1-133">選取 <xref:System.Activities.Statements.Sequence> 活動，然後按一下設計工具左下角的 [**變數**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="c3de1-133">Select the <xref:System.Activities.Statements.Sequence> activity and click the **Variables** button in the lower left corner of the designer.</span></span> <span data-ttu-id="c3de1-134">如此將會顯示變數編輯器。</span><span class="sxs-lookup"><span data-stu-id="c3de1-134">This displays the variables editor.</span></span> <span data-ttu-id="c3de1-135">按一下 [**建立變數**] 連結以新增變數，以儲存傳送至作業的字串。</span><span class="sxs-lookup"><span data-stu-id="c3de1-135">Click the **Create Variable** link to add a variable to store the string sent to the operation.</span></span> <span data-ttu-id="c3de1-136">將變數命名為 `msg` ，並將其**變數**類型設定為 [字串]，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="c3de1-136">Name the variable `msg` and set its **Variable** type to String as shown in the following illustration.</span></span>  
  
     ![顯示如何新增變數的螢幕擷取畫面。](./media/how-to-create-a-workflow-service-with-messaging-activities/add-variable-msg-string.jpg)  
  
     <span data-ttu-id="c3de1-138">再次按一下 [**變數**] 按鈕，以關閉 [變數編輯器]。</span><span class="sxs-lookup"><span data-stu-id="c3de1-138">Click the **Variables** button again to close the variables editor.</span></span>  
  
6. <span data-ttu-id="c3de1-139">按一下 [**定義]。**</span><span class="sxs-lookup"><span data-stu-id="c3de1-139">Click the **Define..**</span></span> <span data-ttu-id="c3de1-140">在活動的 [**內容**] 文字方塊中連結 <xref:System.ServiceModel.Activities.Receive> ，以顯示 [**內容定義**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c3de1-140">link in the **Content** text box in the <xref:System.ServiceModel.Activities.Receive> activity to display the **Content Definition** dialog.</span></span> <span data-ttu-id="c3de1-141">選取 [**參數**] 選項按鈕，按一下 [**加入新的參數**] 連結， `inMsg` 在 [**名稱**] 文字方塊中輸入，在 [**類型**] 下拉式清單方塊中選取 [**字串**]，然後在 [指派給] 文字方塊中輸入，如下 `msg` 圖所示。 **Assign To**</span><span class="sxs-lookup"><span data-stu-id="c3de1-141">Select the **Parameters** radio button, click the **Add new Parameter** link, type `inMsg` in the **name** text box, select **String** in the **Type** drop down list box, and type `msg` in the **Assign To** text box as shown in the following illustration.</span></span>  
  
     ![顯示新增參數內容的螢幕擷取畫面。](./media/how-to-create-a-workflow-service-with-messaging-activities/adding-parameters-content.jpg)  
  
     <span data-ttu-id="c3de1-143">這樣會指定 [接收] 活動接收字串參數，且該資料繫結至 `msg` 變數。</span><span class="sxs-lookup"><span data-stu-id="c3de1-143">This specifies that the Receive activity receives string parameter and that data is bound to the `msg` variable.</span></span> <span data-ttu-id="c3de1-144">按一下 **[確定**] 以關閉 [**內容定義**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c3de1-144">Click **OK** to close the **Content Definition** dialog.</span></span>  
  
7. <span data-ttu-id="c3de1-145">在活動的 [**內容**] 方塊中按一下 [**定義**] 連結 <xref:System.ServiceModel.Activities.SendReply> ，以顯示 [**內容定義**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c3de1-145">Click the **Define...** link in the **Content** box in the <xref:System.ServiceModel.Activities.SendReply> activity to display the **Content Definition** dialog.</span></span> <span data-ttu-id="c3de1-146">選取 [**參數**] 選項按鈕，按一下 [**加入新的參數**] 連結， `outMsg` 在 [**名稱**] 文字方塊中輸入，在 [**類型**] 下拉式清單方塊中選取 [**字串**]，然後 `msg` 在 [**值**] 文字方塊中顯示，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="c3de1-146">Select the **Parameters** radio button, click the **Add new Parameter** link, type `outMsg` in the **name** textbox, select **String** in the **Type** dropdown list box, and `msg` in the **Value** text box as shown in the following illustration.</span></span>  
  
     ![顯示如何新增 outMsg 參數的螢幕擷取畫面。](./media/how-to-create-a-workflow-service-with-messaging-activities/outmsg-parameters-content.jpg)  
  
     <span data-ttu-id="c3de1-148">這樣會指定 <xref:System.ServiceModel.Activities.SendReply> 活動傳送訊息或訊息合約型別，且該資料繫結至 `msg` 變數。</span><span class="sxs-lookup"><span data-stu-id="c3de1-148">This specifies that the <xref:System.ServiceModel.Activities.SendReply> activity sends a message or message contract type and that data is bound to the `msg` variable.</span></span> <span data-ttu-id="c3de1-149">由於此為 <xref:System.ServiceModel.Activities.SendReply> 活動，代表 `msg` 中的資料是用來填入由活動傳回用戶端的訊息。</span><span class="sxs-lookup"><span data-stu-id="c3de1-149">Because this is a <xref:System.ServiceModel.Activities.SendReply> activity, this means the data in `msg` is used to populate the message the activity sends back to the client.</span></span> <span data-ttu-id="c3de1-150">按一下 **[確定**] 以關閉 [**內容定義**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c3de1-150">Click **OK** to close the **Content Definition** dialog.</span></span>  
  
8. <span data-ttu-id="c3de1-151">按一下 [**建立**] 功能表，然後選取 [**建立方案**]，以儲存並建立解決方案。</span><span class="sxs-lookup"><span data-stu-id="c3de1-151">Save and build the solution by clicking the **Build** menu and selecting **Build Solution**.</span></span>  
  
## <a name="configure-the-workflow-service-project"></a><span data-ttu-id="c3de1-152">設定工作流程服務專案。</span><span class="sxs-lookup"><span data-stu-id="c3de1-152">Configure the Workflow Service Project</span></span>  
 <span data-ttu-id="c3de1-153">工作流程執行服務已完成。</span><span class="sxs-lookup"><span data-stu-id="c3de1-153">The workflow service is complete.</span></span> <span data-ttu-id="c3de1-154">本節說明如何設定工作流程服務方案，讓裝載和執行更順利。</span><span class="sxs-lookup"><span data-stu-id="c3de1-154">This section explains how to configure the workflow service solution to make it easy to host and run.</span></span> <span data-ttu-id="c3de1-155">此方案是使用 ASP.NET 程式開發伺服器來裝載服務。</span><span class="sxs-lookup"><span data-stu-id="c3de1-155">This solution uses the ASP.NET Development Server to host the service.</span></span>  
  
#### <a name="to-set-project-start-up-options"></a><span data-ttu-id="c3de1-156">若要設定專案啟動選項</span><span class="sxs-lookup"><span data-stu-id="c3de1-156">To set project start up options</span></span>  
  
1. <span data-ttu-id="c3de1-157">在 [**方案總管**中，以滑鼠右鍵按一下 [ **MyWFService** ]，然後選取 [**屬性**] 以顯示 [**專案屬性**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c3de1-157">In the **Solution Explorer**, right-click **MyWFService** and select **Properties** to display the **Project Properties** dialog.</span></span>  
  
2. <span data-ttu-id="c3de1-158">選取 [ **Web** ] 索引標籤，並選取 [**起始動作**] 底下的 [**特定頁面**]，然後 `Service1.xamlx` 在文字方塊中輸入，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="c3de1-158">Select the **Web** tab and select **Specific Page** under **Start Action** and type `Service1.xamlx` in the text box as shown in the following illustration.</span></span>  
  
     ![顯示 [專案屬性] 對話方塊的螢幕擷取畫面。](./media/how-to-create-a-workflow-service-with-messaging-activities/project-properties-dialog.jpg)  
  
     <span data-ttu-id="c3de1-160">這樣做會裝載在 ASP.NET 程式開發伺服器的 Service1.xamlx 中所定義的服務。</span><span class="sxs-lookup"><span data-stu-id="c3de1-160">This hosts the service defined in Service1.xamlx in the ASP.NET Development Server.</span></span>  
  
3. <span data-ttu-id="c3de1-161">按 Ctrl+F5 啟動服務。</span><span class="sxs-lookup"><span data-stu-id="c3de1-161">Press Ctrl + F5 to launch the service.</span></span> <span data-ttu-id="c3de1-162">[ASP.NET 程式開發伺服器] 圖示會顯示在桌面的右下角，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="c3de1-162">The ASP.NET Development Server icon is displayed in the lower right side of the desktop as shown in the following image.</span></span>  
  
     ![顯示 ASP.NET 開發人員伺服器圖示的螢幕擷取畫面。](./media/how-to-create-a-workflow-service-with-messaging-activities/asp-net-dev-server-icon.jpg)  
  
     <span data-ttu-id="c3de1-164">此外，Internet Explorer 還會顯示該服務的 WCF 服務說明網頁。</span><span class="sxs-lookup"><span data-stu-id="c3de1-164">In addition, Internet Explorer displays the WCF Service Help Page for the service.</span></span>  
  
     ![顯示 [WCF 服務說明] 頁面的螢幕擷取畫面。](./media/how-to-create-a-workflow-service-with-messaging-activities/wcf-service-help-page.jpg)  
  
4. <span data-ttu-id="c3de1-166">繼續前往[如何：從工作流應用程式存取服務](how-to-access-a-service-from-a-workflow-application.md)主題，以建立呼叫此服務的工作流程用戶端。</span><span class="sxs-lookup"><span data-stu-id="c3de1-166">Continue on to the [How To: Access a Service From a Workflow Application](how-to-access-a-service-from-a-workflow-application.md) topic to create a workflow client that calls this service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3de1-167">請參閱</span><span class="sxs-lookup"><span data-stu-id="c3de1-167">See also</span></span>

- [<span data-ttu-id="c3de1-168">工作流程服務</span><span class="sxs-lookup"><span data-stu-id="c3de1-168">Workflow Services</span></span>](workflow-services.md)
- [<span data-ttu-id="c3de1-169">裝載工作流程服務概觀</span><span class="sxs-lookup"><span data-stu-id="c3de1-169">Hosting Workflow Services Overview</span></span>](hosting-workflow-services-overview.md)
- [<span data-ttu-id="c3de1-170">傳訊活動</span><span class="sxs-lookup"><span data-stu-id="c3de1-170">Messaging Activities</span></span>](messaging-activities.md)
