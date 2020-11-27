---
title: 如何：存取來自工作流程應用程式的服務
ms.date: 03/30/2017
ms.assetid: 925ef8ea-5550-4c9d-bb7b-209e20c280ad
ms.openlocfilehash: 13fae7dec3026e96e3c196467da29fe768a3655f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96257928"
---
# <a name="how-to-access-a-service-from-a-workflow-application"></a><span data-ttu-id="a53ba-102">如何：存取來自工作流程應用程式的服務</span><span class="sxs-lookup"><span data-stu-id="a53ba-102">How To: Access a Service From a Workflow Application</span></span>

<span data-ttu-id="a53ba-103">本主題描述如何從工作流程主控台應用程式呼叫工作流程服務。</span><span class="sxs-lookup"><span data-stu-id="a53ba-103">This topic describes how to call a workflow service from a workflow console application.</span></span> <span data-ttu-id="a53ba-104">這取決於完成 how [to：使用訊息活動建立工作流程服務](how-to-create-a-workflow-service-with-messaging-activities.md) 主題。</span><span class="sxs-lookup"><span data-stu-id="a53ba-104">It depends on completion of the [How to: Create a Workflow Service with Messaging Activities](how-to-create-a-workflow-service-with-messaging-activities.md) topic.</span></span> <span data-ttu-id="a53ba-105">雖然本主題描述如何從工作流應用程式呼叫工作流程服務，但是您可以使用相同的方法，從工作流應用程式呼叫任何 Windows Communication Foundation (WCF) 服務。</span><span class="sxs-lookup"><span data-stu-id="a53ba-105">Although this topic describes how to call a workflow service from a workflow application, the same methods can be used to call any Windows Communication Foundation (WCF) service from a workflow application.</span></span>

### <a name="create-a-workflow-console-application-project"></a><span data-ttu-id="a53ba-106">建立工作流程主控台應用程式專案</span><span class="sxs-lookup"><span data-stu-id="a53ba-106">Create a Workflow Console Application Project</span></span>

1. <span data-ttu-id="a53ba-107">啟動 Visual Studio 2012。</span><span class="sxs-lookup"><span data-stu-id="a53ba-107">Start Visual Studio 2012.</span></span>

2. <span data-ttu-id="a53ba-108">載入您在 how [to：使用訊息活動建立工作流程服務](how-to-create-a-workflow-service-with-messaging-activities.md) 主題中建立的 MyWFService 專案。</span><span class="sxs-lookup"><span data-stu-id="a53ba-108">Load the MyWFService project you created in the [How to: Create a Workflow Service with Messaging Activities](how-to-create-a-workflow-service-with-messaging-activities.md) topic.</span></span>

3. <span data-ttu-id="a53ba-109">以滑鼠右鍵按一下 **方案總管** 中的 [ **MyWFService** ] 方案，然後選取 [**加入**]、[**新增專案**]。</span><span class="sxs-lookup"><span data-stu-id="a53ba-109">Right click the **MyWFService** solution in the **Solution Explorer** and select **Add**, **New Project**.</span></span> <span data-ttu-id="a53ba-110">從專案類型清單中，選取 [**已安裝的範本**] 和 [**工作流程主控台應用程式**] 中的 **工作流程**。</span><span class="sxs-lookup"><span data-stu-id="a53ba-110">Select **Workflow** in the **Installed Templates** and **Workflow Console Application** from the list of project types.</span></span> <span data-ttu-id="a53ba-111">將專案命名為 MyWFClient，並且使用預設位置，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="a53ba-111">Name the project MyWFClient and use the default location as shown in the following illustration.</span></span>

     ![加入新的專案對話方塊](./media/how-to-access-a-service-from-a-workflow-application/add-new-project-dialog.jpg)

     <span data-ttu-id="a53ba-113">按一下 [ **確定]** 按鈕以關閉 [ **加入新的專案] 對話方塊**。</span><span class="sxs-lookup"><span data-stu-id="a53ba-113">Click the **OK** button to dismiss the **Add New Project Dialog**.</span></span>

4. <span data-ttu-id="a53ba-114">建立專案之後，Workflow1.xaml 檔會在設計工具中開啟。</span><span class="sxs-lookup"><span data-stu-id="a53ba-114">After the project is created, the Workflow1.xaml file is opened in the designer.</span></span> <span data-ttu-id="a53ba-115">按一下 [ **工具箱** ] 索引標籤以開啟 [工具箱] （如果尚未開啟），然後按一下圖釘將 [工具箱] 視窗保持開啟。</span><span class="sxs-lookup"><span data-stu-id="a53ba-115">Click the **Toolbox** tab to open the toolbox if it is not already open and click the pushpin to keep the toolbox window open.</span></span>

5. <span data-ttu-id="a53ba-116">按下 **Ctrl** + **F5** 來建立和啟動服務。</span><span class="sxs-lookup"><span data-stu-id="a53ba-116">Press **Ctrl**+**F5** to build and launch the service.</span></span> <span data-ttu-id="a53ba-117">ASP.NET 程式開發伺服器會如往常一般隨即啟動，而且 Internet Explorer 會顯示 WCF 說明網頁。</span><span class="sxs-lookup"><span data-stu-id="a53ba-117">As before, the ASP.NET Development Server is launched and Internet Explorer displays the WCF Help Page.</span></span> <span data-ttu-id="a53ba-118">請記下這個網頁的 URI，因為您必須在下一個步驟中使用。</span><span class="sxs-lookup"><span data-stu-id="a53ba-118">Notice the URI for this page as you must use it in the next step.</span></span>

     ![顯示 WCF 說明頁面和 URI 的 IE](./media/how-to-access-a-service-from-a-workflow-application/ie-wcf-help-page-uri.jpg)

6. <span data-ttu-id="a53ba-120">以滑鼠右鍵按一下 **方案總管** 中的 [ **MyWFClient** ] 專案，然後選取 [**加入**  >  **服務參考**]。</span><span class="sxs-lookup"><span data-stu-id="a53ba-120">Right click the **MyWFClient** project in the **Solution Explorer** and select **Add** > **Service Reference**.</span></span> <span data-ttu-id="a53ba-121">按一下 [ **探索** ] 按鈕，在目前的解決方案中搜尋任何服務。</span><span class="sxs-lookup"><span data-stu-id="a53ba-121">Click the **Discover** button to search the current solution for any services.</span></span> <span data-ttu-id="a53ba-122">按一下 [服務] 清單中 Service1.xamlx 旁邊的三角形。</span><span class="sxs-lookup"><span data-stu-id="a53ba-122">Click the triangle next to Service1.xamlx in the Services list.</span></span> <span data-ttu-id="a53ba-123">按一下 Service1 旁邊的三角形，即可列出 Service1 服務實作的合約。</span><span class="sxs-lookup"><span data-stu-id="a53ba-123">Click the triangle next to Service1 to list the contracts implemented by the Service1 service.</span></span> <span data-ttu-id="a53ba-124">展開 [**服務**] 清單中的 [ **Service1** ] 節點。</span><span class="sxs-lookup"><span data-stu-id="a53ba-124">Expand the **Service1** node in the **Services** list.</span></span> <span data-ttu-id="a53ba-125">Echo 作業會顯示在 **作業** 清單中，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="a53ba-125">The Echo operation is displayed in the **Operations** list as shown in the following illustration.</span></span>

     ![加入服務參考對話方塊](./media/how-to-access-a-service-from-a-workflow-application/add-service-reference.jpg)

     <span data-ttu-id="a53ba-127">保留預設的命名空間，然後按一下 **[確定** ] 關閉 **加入服務參考** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a53ba-127">Keep the default namespace and click **OK** to dismiss the **Add Service Reference** dialog.</span></span> <span data-ttu-id="a53ba-128">此時會顯示下列對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a53ba-128">The following dialog is displayed.</span></span>

     ![加入服務參考通知對話方塊](./media/how-to-access-a-service-from-a-workflow-application/add-service-reference-dialog.jpg)

     <span data-ttu-id="a53ba-130">按一下 **[確定** ] 關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a53ba-130">Click **OK** to dismiss the dialog.</span></span> <span data-ttu-id="a53ba-131">接著，請按下 CTRL+SHIFT+B 建置方案。</span><span class="sxs-lookup"><span data-stu-id="a53ba-131">Next, press CTRL+SHIFT+B to build the solution.</span></span> <span data-ttu-id="a53ba-132">請注意，在 [工具箱] 中已新增新的區段，稱為 **MyWFClient ServiceReference1。活動**。</span><span class="sxs-lookup"><span data-stu-id="a53ba-132">Notice in the toolbox a new section has been added called **MyWFClient.ServiceReference1.Activities**.</span></span> <span data-ttu-id="a53ba-133">展開此區段並注意已加入的 Echo 活動，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="a53ba-133">Expand this section and notice the Echo activity that has been added as shown in the following illustration.</span></span>

     ![工具箱中的 Echo 活動](./media/how-to-access-a-service-from-a-workflow-application/echo-activity-toolbox.jpg)

7. <span data-ttu-id="a53ba-135">將 <xref:System.Activities.Statements.Sequence> 活動拖放至設計工具介面上。</span><span class="sxs-lookup"><span data-stu-id="a53ba-135">Drag and drop a <xref:System.Activities.Statements.Sequence> activity onto the designer surface.</span></span> <span data-ttu-id="a53ba-136">它位於 [工具箱] 的 [ **控制流程** ] 區段下。</span><span class="sxs-lookup"><span data-stu-id="a53ba-136">It is under the **Control Flow** section of the toolbox.</span></span>

8. <span data-ttu-id="a53ba-137"><xref:System.Activities.Statements.Sequence>在焦點的活動中，按一下 [**變數**] 連結，然後新增名為的字串變數 `inString` 。</span><span class="sxs-lookup"><span data-stu-id="a53ba-137">With the <xref:System.Activities.Statements.Sequence> activity in focus, click the **Variables** link and add a string variable named `inString`.</span></span> <span data-ttu-id="a53ba-138">提供變數的預設值 `"Hello, world"` ，以及名為的字串變數，如下 `outString` 圖所示。</span><span class="sxs-lookup"><span data-stu-id="a53ba-138">Give the variable a default value of `"Hello, world"` as well as a string variable named `outString` as shown in the following diagram.</span></span>

     ![新增 inString 變數](./media/how-to-access-a-service-from-a-workflow-application/add-instring-variable.jpg)

9. <span data-ttu-id="a53ba-140">將 [ **Echo** ] 活動拖放到中 <xref:System.Activities.Statements.Sequence> 。</span><span class="sxs-lookup"><span data-stu-id="a53ba-140">Drag and drop an **Echo** activity into the <xref:System.Activities.Statements.Sequence>.</span></span> <span data-ttu-id="a53ba-141">在 [屬性] 視窗中，將變數和引數的引數系結至 `inMsg` `inString` 變數，如下 `outMsg` `outString` 圖所示。</span><span class="sxs-lookup"><span data-stu-id="a53ba-141">In the properties window bind the `inMsg` argument to the `inString` variable and the `outMsg` argument to the `outString` variable as shown in the following illustration.</span></span> <span data-ttu-id="a53ba-142">這樣做會將 `inString` 變數的值傳遞至作業中，然後取得傳回值並放入 `outString` 變數。</span><span class="sxs-lookup"><span data-stu-id="a53ba-142">This passes in the value of the `inString` variable to the operation and then takes the return value and places it in the `outString` variable.</span></span>

     ![將引數繫結至變數](./media/how-to-access-a-service-from-a-workflow-application/bind-arguments-variables.jpg)

10. <span data-ttu-id="a53ba-144">將 [ **WriteLine** ] 活動拖放到 [ **Echo** ] 活動下方，以顯示服務呼叫所傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="a53ba-144">Drag and drop a **WriteLine** activity below the **Echo** activity to display the string returned by the service call.</span></span> <span data-ttu-id="a53ba-145">[ **WriteLine** ] 活動位於 [工具箱] 的 [ **基本** ] 節點中。</span><span class="sxs-lookup"><span data-stu-id="a53ba-145">The **WriteLine** activity is located in the **Primitives** node in the toolbox.</span></span> <span data-ttu-id="a53ba-146">藉由 **Text** 在 **WriteLine** `outString` `outString` [ **writeline** ] 活動的文字方塊中輸入，將 WriteLine 活動的文字引數系結至變數。</span><span class="sxs-lookup"><span data-stu-id="a53ba-146">Bind the **Text** argument of the **WriteLine** activity to the `outString` variable by typing `outString` into the text box on the **WriteLine** activity.</span></span> <span data-ttu-id="a53ba-147">現在，工作流程的外觀應該如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="a53ba-147">The workflow should now look like the following illustration.</span></span>

     ![完整的用戶端工作流程](./media/how-to-access-a-service-from-a-workflow-application/complete-client-workflow.jpg)

11. <span data-ttu-id="a53ba-149">以滑鼠右鍵按一下 MyWFService 方案，然後選取 [**設定啟始專案 ...**]。選取 [**多個啟始專案**] 選項按鈕，然後針對 [**動作**] 欄中的每個專案選取 [**開始**]，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="a53ba-149">Right-click the MyWFService solution and select **Set Startup Projects ...**. Select the **Multiple startup projects** radio button and select **Start** for each project in the **Action** column as shown in the following illustration.</span></span>

     ![啟始專案選項](./media/how-to-access-a-service-from-a-workflow-application/startup-project-options.jpg)

12. <span data-ttu-id="a53ba-151">按下 Ctrl+F5，同時啟動服務與用戶端。</span><span class="sxs-lookup"><span data-stu-id="a53ba-151">Press Ctrl + F5 to launch both the service and the client.</span></span> <span data-ttu-id="a53ba-152">ASP.NET 程式開發伺服器裝載服務，Internet Explorer 會顯示 WCF 說明頁面，而用戶端工作流程應用程式會在主控台視窗中啟動，並顯示從服務傳回的字串 ( "Hello，world" ) 。</span><span class="sxs-lookup"><span data-stu-id="a53ba-152">The ASP.NET Development Server hosts the service, Internet Explorer displays the WCF help page, and the client workflow application is launched in a console window and displays the string returned from the service ("Hello, world").</span></span>

## <a name="see-also"></a><span data-ttu-id="a53ba-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a53ba-153">See also</span></span>

- [<span data-ttu-id="a53ba-154">工作流程服務</span><span class="sxs-lookup"><span data-stu-id="a53ba-154">Workflow Services</span></span>](workflow-services.md)
- [<span data-ttu-id="a53ba-155">作法：使用傳訊活動建立工作流程服務</span><span class="sxs-lookup"><span data-stu-id="a53ba-155">How to: Create a Workflow Service with Messaging Activities</span></span>](how-to-create-a-workflow-service-with-messaging-activities.md)
- [<span data-ttu-id="a53ba-156">從 Web 專案的工作流程中取用 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="a53ba-156">Consuming a WCF Service from a Workflow in a Web Project</span></span>](/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow)
