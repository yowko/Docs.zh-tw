---
title: 在 Visual Studio 中建立 WCF 資料服務
ms.date: 08/24/2018
dev_langs:
- csharp
- vb
ms.assetid: 34d1d971-5e18-4c22-9bf6-d3612e27ea59
ms.openlocfilehash: d23df38d479cb8f29f3e49225e96552ccdb84645
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64641142"
---
# <a name="create-the-data-service"></a><span data-ttu-id="bd372-102">建立資料服務</span><span class="sxs-lookup"><span data-stu-id="bd372-102">Create the data service</span></span>

<span data-ttu-id="bd372-103">本主題中，您可以建立會使用 WCF 資料服務公開的範例資料服務[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]Northwind 範例資料庫為基礎的摘要。</span><span class="sxs-lookup"><span data-stu-id="bd372-103">In this topic, you create a sample data service that uses WCF Data Services to expose an [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed that's based on the Northwind sample database.</span></span> <span data-ttu-id="bd372-104">這個工作包含下列基本步驟：</span><span class="sxs-lookup"><span data-stu-id="bd372-104">The task involves the following basic steps:</span></span>

1. <span data-ttu-id="bd372-105">建立 ASP.NET Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="bd372-105">Create an ASP.NET Web application.</span></span>

2. <span data-ttu-id="bd372-106">使用實體資料模型工具定義資料模型。</span><span class="sxs-lookup"><span data-stu-id="bd372-106">Define the data model by using the Entity Data Model tools.</span></span>

3. <span data-ttu-id="bd372-107">將資料服務加入至 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="bd372-107">Add the data service to the Web application.</span></span>

4. <span data-ttu-id="bd372-108">啟用資料服務的存取。</span><span class="sxs-lookup"><span data-stu-id="bd372-108">Enable access to the data service.</span></span>

## <a name="create-the-aspnet-web-app"></a><span data-ttu-id="bd372-109">建立 ASP.NET web 應用程式</span><span class="sxs-lookup"><span data-stu-id="bd372-109">Create the ASP.NET web app</span></span>

1. <span data-ttu-id="bd372-110">在 Visual Studio 中，在**檔案**功能表上，選取**新增** > **專案**。</span><span class="sxs-lookup"><span data-stu-id="bd372-110">In Visual Studio, on the **File** menu, select **New** > **Project**.</span></span>

1. <span data-ttu-id="bd372-111">在 **新的專案**對話方塊的 Visual Basic 或 Visual C# 中選取下**Web**類別目錄，然後選取**ASP.NET Web 應用程式**。</span><span class="sxs-lookup"><span data-stu-id="bd372-111">In the **New Project** dialog box, under either Visual Basic or Visual C# select the **Web** category, and then select **ASP.NET Web Application**.</span></span>

1. <span data-ttu-id="bd372-112">請輸入`NorthwindService`做為名稱的專案，然後選取 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="bd372-112">Enter `NorthwindService` as the name of the project and then select **OK**.</span></span>

1. <span data-ttu-id="bd372-113">在 **新的 ASP.NET Web 應用程式**對話方塊中，選取**空白**，然後選取**確定**。</span><span class="sxs-lookup"><span data-stu-id="bd372-113">In the **New ASP.NET Web Application** dialog, select **Empty** and then select **OK**.</span></span>

1. <span data-ttu-id="bd372-114">(選擇性) 指定 Web 應用程式的連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="bd372-114">(Optional) Specify a specific port number for your Web application.</span></span> <span data-ttu-id="bd372-115">注意： 連接埠號碼`12345`會在這一系列的快速入門主題。</span><span class="sxs-lookup"><span data-stu-id="bd372-115">Note: the port number `12345` is used in this series of quickstart topics.</span></span>

    1. <span data-ttu-id="bd372-116">在 **方案總管**，以滑鼠右鍵按一下您剛才建立的 ASP.NET 專案，然後選擇**屬性**。</span><span class="sxs-lookup"><span data-stu-id="bd372-116">In **Solution Explorer**, right-click on the ASP.NET project that you just created, and then choose **Properties**.</span></span>

    2. <span data-ttu-id="bd372-117">選取  **Web**索引標籤，並將值**特定連接埠**文字方塊中，以`12345`。</span><span class="sxs-lookup"><span data-stu-id="bd372-117">Select the **Web** tab, and set the value of the **Specific port** text box to `12345`.</span></span>

## <a name="define-the-data-model"></a><span data-ttu-id="bd372-118">定義資料模型</span><span class="sxs-lookup"><span data-stu-id="bd372-118">Define the data model</span></span>

1. <span data-ttu-id="bd372-119">在 [**方案總管] 中**，以滑鼠右鍵按一下 ASP.NET 專案中，名稱，然後按一下**新增** > **新項目**。</span><span class="sxs-lookup"><span data-stu-id="bd372-119">In **Solution Explorer**, right-click the name of the ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="bd372-120">在 **加入新項目**對話方塊中，選取**資料**類別，然後再選取**ADO.NET 實體資料模型**。</span><span class="sxs-lookup"><span data-stu-id="bd372-120">In the **Add New Item** dialog box, select the **Data** category, and then select **ADO.NET Entity Data Model**.</span></span>

3. <span data-ttu-id="bd372-121">針對資料模型的名稱，輸入`Northwind.edmx`。</span><span class="sxs-lookup"><span data-stu-id="bd372-121">For the name of the data model, enter `Northwind.edmx`.</span></span>

4. <span data-ttu-id="bd372-122">在**Entity Data Model 精靈**，選取**資料庫的 EF Designer**，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="bd372-122">In the **Entity Data Model Wizard**, select **EF Designer from Database**, and then click **Next**.</span></span>

5. <span data-ttu-id="bd372-123">連接到資料庫的資料模型，執行下列步驟中，其中，然後按一下**下一步**:</span><span class="sxs-lookup"><span data-stu-id="bd372-123">Connect the data model to the database by doing one of the following steps, and then click **Next**:</span></span>

    - <span data-ttu-id="bd372-124">如果您沒有已設定的資料庫連線，請按一下**新的連接**並建立新的連接。</span><span class="sxs-lookup"><span data-stu-id="bd372-124">If you don't have a database connection already configured, click **New Connection** and create a new connection.</span></span> <span data-ttu-id="bd372-125">如需詳細資訊，請參閱[如何：建立連接至 SQL Server 資料庫](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="bd372-125">For more information, see [How to: Create Connections to SQL Server Databases](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)).</span></span> <span data-ttu-id="bd372-126">此 SQL Server 執行個體必須已附加 Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="bd372-126">This SQL Server instance must have the Northwind sample database attached.</span></span>

         <span data-ttu-id="bd372-127">\-或-</span><span class="sxs-lookup"><span data-stu-id="bd372-127">\- or -</span></span>

    - <span data-ttu-id="bd372-128">如果您擁有已經設定為連接至 Northwind 資料庫的資料庫連接，請從連接清單中選取該連接。</span><span class="sxs-lookup"><span data-stu-id="bd372-128">If you have a database connection already configured to connect to the Northwind database, select that connection from the list of connections.</span></span>

6. <span data-ttu-id="bd372-129">在精靈的最後一頁上，選取資料庫中所有資料表的核取方塊，並且清除檢視表和預存程序 (Stored Procedure) 的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="bd372-129">On the final page of the wizard, select the check boxes for all tables in the database, and clear the check boxes for views and stored procedures.</span></span>

7. <span data-ttu-id="bd372-130">按一下 **完成**即可關閉精靈。</span><span class="sxs-lookup"><span data-stu-id="bd372-130">Click **Finish** to close the wizard.</span></span>

## <a name="create-the-wcf-data-service"></a><span data-ttu-id="bd372-131">建立 WCF 資料服務</span><span class="sxs-lookup"><span data-stu-id="bd372-131">Create the WCF data service</span></span>

1. <span data-ttu-id="bd372-132">在 [**方案總管] 中**，以滑鼠右鍵按一下 ASP.NET 專案，然後選擇**新增** > **新項目**。</span><span class="sxs-lookup"><span data-stu-id="bd372-132">In **Solution Explorer**, right-click on the ASP.NET project, and then choose **Add** > **New Item**.</span></span>

2. <span data-ttu-id="bd372-133">在 **加入新項目**對話方塊中，選取**WCF 資料服務**項目範本，從**Web**類別目錄。</span><span class="sxs-lookup"><span data-stu-id="bd372-133">In the **Add New Item** dialog box, select the **WCF Data Service** item template from the **Web** category.</span></span>

   ![Visual Studio 2015 中的 WCF 資料服務項目範本](media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="bd372-135">**WCF 資料服務**範本位於 Visual Studio 2015，但不是能在 Visual Studio 2017。</span><span class="sxs-lookup"><span data-stu-id="bd372-135">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017.</span></span>

3. <span data-ttu-id="bd372-136">如需服務的名稱，輸入`Northwind`。</span><span class="sxs-lookup"><span data-stu-id="bd372-136">For the name of the service, type `Northwind`.</span></span>

     <span data-ttu-id="bd372-137">Visual Studio 會針對新的服務建立 XML 標記和程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="bd372-137">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="bd372-138">根據預設，程式碼編輯器視窗隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="bd372-138">By default, the code-editor window opens.</span></span> <span data-ttu-id="bd372-139">在 [**方案總管] 中**，此服務具有名稱 Northwind，副檔名 *.svc.cs*或 *.svc.vb*。</span><span class="sxs-lookup"><span data-stu-id="bd372-139">In **Solution Explorer**, the service has the name Northwind with the extension *.svc.cs* or *.svc.vb*.</span></span>

4. <span data-ttu-id="bd372-140">在資料服務的程式碼裡，於定義資料服務和型別的類別定義中，取代註解 `/* TODO: put your data source class name here */`，該型別是資料模型的實體容器，在這個案例中是 `NorthwindEntities`。</span><span class="sxs-lookup"><span data-stu-id="bd372-140">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindEntities`.</span></span> <span data-ttu-id="bd372-141">類別定義看起來應如下列：</span><span class="sxs-lookup"><span data-stu-id="bd372-141">The class definition should look this the following:</span></span>

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="enable-access-to-data-service-resources"></a><span data-ttu-id="bd372-142">啟用資料服務資源的存取權</span><span class="sxs-lookup"><span data-stu-id="bd372-142">Enable access to data service resources</span></span>

1. <span data-ttu-id="bd372-143">在資料服務的程式碼中，以下列程式碼取代 `InitializeService` 函數中的預留位置程式碼：</span><span class="sxs-lookup"><span data-stu-id="bd372-143">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>

     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#allreadconfig)]

     <span data-ttu-id="bd372-144">如此可讓授權的用戶端具有指定之實體集資源的讀取和寫入存取權。</span><span class="sxs-lookup"><span data-stu-id="bd372-144">This enables authorized clients to have read and write access to resources for the specified entity sets.</span></span>

    > [!NOTE]
    > <span data-ttu-id="bd372-145">任何可以存取 ASP.NET 應用程式的用戶端也可以存取資料服務公開的資源。</span><span class="sxs-lookup"><span data-stu-id="bd372-145">Any client that can access the ASP.NET application can also access the resources exposed by the data service.</span></span> <span data-ttu-id="bd372-146">在產生資料服務的過程中，若要避免未經授權存取資源，您也應該要保護應用程式本身。</span><span class="sxs-lookup"><span data-stu-id="bd372-146">In a production data service, to prevent unauthorized access to resources you should also secure the application itself.</span></span> <span data-ttu-id="bd372-147">如需詳細資訊，請參閱 [Securing WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="bd372-147">For more information, see [Securing WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="bd372-148">後續步驟</span><span class="sxs-lookup"><span data-stu-id="bd372-148">Next steps</span></span>

<span data-ttu-id="bd372-149">您已成功建立新的資料服務公開以 Northwind 範例資料庫為基礎的 OData 摘要，且您已啟用存取該用戶端擁有 ASP.NET Web 應用程式的權限摘要。</span><span class="sxs-lookup"><span data-stu-id="bd372-149">You have successfully created a new data service that exposes an OData feed that is based on the Northwind sample database, and you have enabled access to the feed for clients that have permissions on the ASP.NET Web application.</span></span> <span data-ttu-id="bd372-150">接下來，您將從 Visual Studio 啟動資料服務，並存取 OData 摘要送出 HTTP GET 要求，透過網頁瀏覽器：</span><span class="sxs-lookup"><span data-stu-id="bd372-150">Next, you'll start the data service from Visual Studio and access the OData feed by submitting HTTP GET requests through a Web browser:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bd372-151">從網頁瀏覽器存取服務</span><span class="sxs-lookup"><span data-stu-id="bd372-151">Access the service from a web browser</span></span>](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

## <a name="see-also"></a><span data-ttu-id="bd372-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd372-152">See also</span></span>

- <span data-ttu-id="bd372-153">[ADO.NET 實體資料模型工具](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="bd372-153">[ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>