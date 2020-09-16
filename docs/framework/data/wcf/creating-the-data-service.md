---
title: 在 Visual Studio 中建立 WCF 資料服務
description: 瞭解如何建立範例資料服務，此服務會使用 WCF Data Services 來公開以範例資料庫為基礎的 OData 摘要。
ms.date: 08/24/2018
dev_langs:
- csharp
- vb
ms.assetid: 34d1d971-5e18-4c22-9bf6-d3612e27ea59
ms.openlocfilehash: f6e95ce58e055f0c745b781c664309e4ef91ffc6
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554009"
---
# <a name="create-the-data-service"></a><span data-ttu-id="f7f75-103">建立資料服務</span><span class="sxs-lookup"><span data-stu-id="f7f75-103">Create the data service</span></span>

<span data-ttu-id="f7f75-104">在本主題中，您會建立範例資料服務，此服務會使用 WCF Data Services 來公開以 Northwind 範例資料庫為基礎的開放式資料通訊協定 (OData) 摘要。</span><span class="sxs-lookup"><span data-stu-id="f7f75-104">In this topic, you create a sample data service that uses WCF Data Services to expose an Open Data Protocol (OData) feed that's based on the Northwind sample database.</span></span> <span data-ttu-id="f7f75-105">這個工作包含下列基本步驟：</span><span class="sxs-lookup"><span data-stu-id="f7f75-105">The task involves the following basic steps:</span></span>

1. <span data-ttu-id="f7f75-106">建立 ASP.NET Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="f7f75-106">Create an ASP.NET Web application.</span></span>

2. <span data-ttu-id="f7f75-107">使用實體資料模型工具定義資料模型。</span><span class="sxs-lookup"><span data-stu-id="f7f75-107">Define the data model by using the Entity Data Model tools.</span></span>

3. <span data-ttu-id="f7f75-108">將資料服務加入至 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="f7f75-108">Add the data service to the Web application.</span></span>

4. <span data-ttu-id="f7f75-109">啟用資料服務的存取。</span><span class="sxs-lookup"><span data-stu-id="f7f75-109">Enable access to the data service.</span></span>

## <a name="create-the-aspnet-web-app"></a><span data-ttu-id="f7f75-110">建立 ASP.NET web 應用程式</span><span class="sxs-lookup"><span data-stu-id="f7f75-110">Create the ASP.NET web app</span></span>

1. <span data-ttu-id="f7f75-111">在 Visual Studio 中，於 [檔案]  功能表上選取 [新增]   > [專案]  。</span><span class="sxs-lookup"><span data-stu-id="f7f75-111">In Visual Studio, on the **File** menu, select **New** > **Project**.</span></span>

1. <span data-ttu-id="f7f75-112">在 [ **新增專案** ] 對話方塊的 [Visual Basic] 或 [Visual c #] 底下，選取 [ **web** ] 類別，然後選取 [ **ASP.NET web 應用程式**]。</span><span class="sxs-lookup"><span data-stu-id="f7f75-112">In the **New Project** dialog box, under either Visual Basic or Visual C# select the **Web** category, and then select **ASP.NET Web Application**.</span></span>

1. <span data-ttu-id="f7f75-113">輸入 `NorthwindService` 做為專案的名稱，然後選取 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="f7f75-113">Enter `NorthwindService` as the name of the project and then select **OK**.</span></span>

1. <span data-ttu-id="f7f75-114">在 [ **新增 ASP.NET Web 應用程式** ] 對話方塊中，選取 [ **空白** ]，然後選取 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="f7f75-114">In the **New ASP.NET Web Application** dialog, select **Empty** and then select **OK**.</span></span>

1. <span data-ttu-id="f7f75-115">(選擇性) 指定 Web 應用程式的連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="f7f75-115">(Optional) Specify a specific port number for your Web application.</span></span> <span data-ttu-id="f7f75-116">注意：此通訊埠編號 `12345` 會在這一系列的快速入門主題中使用。</span><span class="sxs-lookup"><span data-stu-id="f7f75-116">Note: the port number `12345` is used in this series of quickstart topics.</span></span>

    1. <span data-ttu-id="f7f75-117">在 **方案總管**中，以滑鼠右鍵按一下您剛才建立的 ASP.NET 專案，然後選擇 [ **屬性**]。</span><span class="sxs-lookup"><span data-stu-id="f7f75-117">In **Solution Explorer**, right-click on the ASP.NET project that you just created, and then choose **Properties**.</span></span>

    2. <span data-ttu-id="f7f75-118">選取 [ **Web** ] 索引標籤，並將 [ **特定通訊埠** ] 文字方塊的值設定為 `12345` 。</span><span class="sxs-lookup"><span data-stu-id="f7f75-118">Select the **Web** tab, and set the value of the **Specific port** text box to `12345`.</span></span>

## <a name="define-the-data-model"></a><span data-ttu-id="f7f75-119">定義資料模型</span><span class="sxs-lookup"><span data-stu-id="f7f75-119">Define the data model</span></span>

1. <span data-ttu-id="f7f75-120">在**方案總管**中，以滑鼠右鍵按一下 ASP.NET 專案的名稱，然後按一下 [**加入**  >  **新專案**]。</span><span class="sxs-lookup"><span data-stu-id="f7f75-120">In **Solution Explorer**, right-click the name of the ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="f7f75-121">在 [ **加入新專案** ] 對話方塊中，選取 [ **資料** ] 分類，然後選取 [ **ADO.NET 實體資料模型**]。</span><span class="sxs-lookup"><span data-stu-id="f7f75-121">In the **Add New Item** dialog box, select the **Data** category, and then select **ADO.NET Entity Data Model**.</span></span>

3. <span data-ttu-id="f7f75-122">若為資料模型的名稱，請輸入 `Northwind.edmx` 。</span><span class="sxs-lookup"><span data-stu-id="f7f75-122">For the name of the data model, enter `Northwind.edmx`.</span></span>

4. <span data-ttu-id="f7f75-123">在 **實體資料模型 Wizard**中，從 [資料庫] 選取 [ **EF Designer**]，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="f7f75-123">In the **Entity Data Model Wizard**, select **EF Designer from Database**, and then click **Next**.</span></span>

5. <span data-ttu-id="f7f75-124">執行下列其中一個步驟，將資料模型連接至資料庫，然後按 **[下一步]**：</span><span class="sxs-lookup"><span data-stu-id="f7f75-124">Connect the data model to the database by doing one of the following steps, and then click **Next**:</span></span>

    - <span data-ttu-id="f7f75-125">如果您尚未設定資料庫連接，請按一下 [ **新增連接** ] 並建立新的連接。</span><span class="sxs-lookup"><span data-stu-id="f7f75-125">If you don't have a database connection already configured, click **New Connection** and create a new connection.</span></span> <span data-ttu-id="f7f75-126">如需詳細資訊，請參閱 [How to: Create Connections to SQL Server Databases](/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="f7f75-126">For more information, see [How to: Create Connections to SQL Server Databases](/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)).</span></span> <span data-ttu-id="f7f75-127">此 SQL Server 執行個體必須已附加 Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="f7f75-127">This SQL Server instance must have the Northwind sample database attached.</span></span>

         <span data-ttu-id="f7f75-128">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="f7f75-128">\- or -</span></span>

    - <span data-ttu-id="f7f75-129">如果您擁有已經設定為連接至 Northwind 資料庫的資料庫連接，請從連接清單中選取該連接。</span><span class="sxs-lookup"><span data-stu-id="f7f75-129">If you have a database connection already configured to connect to the Northwind database, select that connection from the list of connections.</span></span>

6. <span data-ttu-id="f7f75-130">在精靈的最後一頁上，選取資料庫中所有資料表的核取方塊，並且清除檢視表和預存程序 (Stored Procedure) 的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="f7f75-130">On the final page of the wizard, select the check boxes for all tables in the database, and clear the check boxes for views and stored procedures.</span></span>

7. <span data-ttu-id="f7f75-131">按一下 **[完成** ] 以關閉嚮導。</span><span class="sxs-lookup"><span data-stu-id="f7f75-131">Click **Finish** to close the wizard.</span></span>

## <a name="create-the-wcf-data-service"></a><span data-ttu-id="f7f75-132">建立 WCF 資料服務</span><span class="sxs-lookup"><span data-stu-id="f7f75-132">Create the WCF data service</span></span>

1. <span data-ttu-id="f7f75-133">在**方案總管**中，以滑鼠右鍵按一下 ASP.NET 專案，然後選擇 [**加入**  >  **新專案**]。</span><span class="sxs-lookup"><span data-stu-id="f7f75-133">In **Solution Explorer**, right-click on the ASP.NET project, and then choose **Add** > **New Item**.</span></span>

2. <span data-ttu-id="f7f75-134">在 [**加入新專案**] 對話方塊中，從 [ **Web** ] 類別選取 [ **WCF 資料服務**專案] 範本。</span><span class="sxs-lookup"><span data-stu-id="f7f75-134">In the **Add New Item** dialog box, select the **WCF Data Service** item template from the **Web** category.</span></span>

   ![Visual Studio 2015 中的 WCF 資料服務專案範本](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="f7f75-136">**WCF 資料服務**範本可在 Visual Studio 2015 中使用，但不能在 Visual Studio 2017 或更新版本中使用。</span><span class="sxs-lookup"><span data-stu-id="f7f75-136">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017 or later.</span></span>

3. <span data-ttu-id="f7f75-137">在 [服務名稱] 中，輸入 `Northwind` 。</span><span class="sxs-lookup"><span data-stu-id="f7f75-137">For the name of the service, type `Northwind`.</span></span>

     <span data-ttu-id="f7f75-138">Visual Studio 會針對新的服務建立 XML 標記和程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="f7f75-138">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="f7f75-139">根據預設，程式碼編輯器視窗隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="f7f75-139">By default, the code-editor window opens.</span></span> <span data-ttu-id="f7f75-140">在 **方案總管**中，服務的名稱是 Northwind，副檔名為 *svc.cs* 或 *.svc*。</span><span class="sxs-lookup"><span data-stu-id="f7f75-140">In **Solution Explorer**, the service has the name Northwind with the extension *.svc.cs* or *.svc.vb*.</span></span>

4. <span data-ttu-id="f7f75-141">在資料服務的程式碼裡，於定義資料服務和型別的類別定義中，取代註解 `/* TODO: put your data source class name here */`，該型別是資料模型的實體容器，在這個案例中是 `NorthwindEntities`。</span><span class="sxs-lookup"><span data-stu-id="f7f75-141">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindEntities`.</span></span> <span data-ttu-id="f7f75-142">類別定義看起來應如下列：</span><span class="sxs-lookup"><span data-stu-id="f7f75-142">The class definition should look this the following:</span></span>

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="enable-access-to-data-service-resources"></a><span data-ttu-id="f7f75-143">啟用資料服務資源的存取</span><span class="sxs-lookup"><span data-stu-id="f7f75-143">Enable access to data service resources</span></span>

1. <span data-ttu-id="f7f75-144">在資料服務的程式碼中，以下列程式碼取代 `InitializeService` 函數中的預留位置程式碼：</span><span class="sxs-lookup"><span data-stu-id="f7f75-144">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>

     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#allreadconfig)]

     <span data-ttu-id="f7f75-145">如此可讓授權的用戶端具有指定之實體集資源的讀取和寫入存取權。</span><span class="sxs-lookup"><span data-stu-id="f7f75-145">This enables authorized clients to have read and write access to resources for the specified entity sets.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f7f75-146">任何可以存取 ASP.NET 應用程式的用戶端也可以存取資料服務公開的資源。</span><span class="sxs-lookup"><span data-stu-id="f7f75-146">Any client that can access the ASP.NET application can also access the resources exposed by the data service.</span></span> <span data-ttu-id="f7f75-147">在產生資料服務的過程中，若要避免未經授權存取資源，您也應該要保護應用程式本身。</span><span class="sxs-lookup"><span data-stu-id="f7f75-147">In a production data service, to prevent unauthorized access to resources you should also secure the application itself.</span></span> <span data-ttu-id="f7f75-148">如需詳細資訊，請參閱 [Securing WCF Data Services](securing-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="f7f75-148">For more information, see [Securing WCF Data Services](securing-wcf-data-services.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="f7f75-149">後續步驟</span><span class="sxs-lookup"><span data-stu-id="f7f75-149">Next steps</span></span>

<span data-ttu-id="f7f75-150">您已成功建立新的資料服務，此服務會公開以 Northwind 範例資料庫為基礎的 OData 摘要，而且您已針對在 ASP.NET Web 應用程式上具有許可權的用戶端啟用存取饋送。</span><span class="sxs-lookup"><span data-stu-id="f7f75-150">You have successfully created a new data service that exposes an OData feed that is based on the Northwind sample database, and you have enabled access to the feed for clients that have permissions on the ASP.NET Web application.</span></span> <span data-ttu-id="f7f75-151">接下來，您會從 Visual Studio 啟動資料服務，並透過網頁瀏覽器提交 HTTP GET 要求來存取 OData 摘要：</span><span class="sxs-lookup"><span data-stu-id="f7f75-151">Next, you'll start the data service from Visual Studio and access the OData feed by submitting HTTP GET requests through a Web browser:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f7f75-152">從網頁瀏覽器存取服務</span><span class="sxs-lookup"><span data-stu-id="f7f75-152">Access the service from a web browser</span></span>](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

## <a name="see-also"></a><span data-ttu-id="f7f75-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7f75-153">See also</span></span>

- <span data-ttu-id="f7f75-154">[ADO.NET 實體資料模型工具](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f7f75-154">[ADO.NET Entity Data Model Tools](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
