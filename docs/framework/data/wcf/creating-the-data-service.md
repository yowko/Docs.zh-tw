---
title: 建立資料服務
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 34d1d971-5e18-4c22-9bf6-d3612e27ea59
ms.openlocfilehash: bb6e2f7c1160fa51cd897cc953ad0ed721559294
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33362832"
---
# <a name="creating-the-data-service"></a><span data-ttu-id="659a6-102">建立資料服務</span><span class="sxs-lookup"><span data-stu-id="659a6-102">Creating the Data Service</span></span>
<span data-ttu-id="659a6-103">在這個工作中，您將建立使用的範例資料服務[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]公開 [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Northwind 範例資料庫為基礎的摘要。</span><span class="sxs-lookup"><span data-stu-id="659a6-103">In this task, you will create a sample data service that uses [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] to expose an [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed that is based on the Northwind sample database.</span></span> <span data-ttu-id="659a6-104">這個工作包含下列基本步驟：</span><span class="sxs-lookup"><span data-stu-id="659a6-104">The task involves the following basic steps:</span></span>  
  
1.  <span data-ttu-id="659a6-105">建立 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="659a6-105">Create an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web application.</span></span>  
  
2.  <span data-ttu-id="659a6-106">使用 [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] 工具來定義資料模型。</span><span class="sxs-lookup"><span data-stu-id="659a6-106">Define the data model by using the [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] tools.</span></span>  
  
3.  <span data-ttu-id="659a6-107">將資料服務加入至 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="659a6-107">Add the data service to the Web application.</span></span>  
  
4.  <span data-ttu-id="659a6-108">啟用資料服務的存取。</span><span class="sxs-lookup"><span data-stu-id="659a6-108">Enable access to the data service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="659a6-109">[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]完成這項工作時，您建立的 Web 應用程式上執行[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Visual Studio 所提供的程式開發伺服器。</span><span class="sxs-lookup"><span data-stu-id="659a6-109">The [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web application that you create when you complete this task runs on the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Development Server provided by Visual Studio.</span></span> [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]<span data-ttu-id="659a6-110"> 程式開發伺服器只支援從本機電腦存取。</span><span class="sxs-lookup"><span data-stu-id="659a6-110"> Development Server only supports access from the local computer.</span></span> <span data-ttu-id="659a6-111">若要一併在開發期間更輕鬆地測試資料服務並進行疑難排解，請考慮使用 Internet Information Services (IIS) 執行可裝載資料服務的應用程式。</span><span class="sxs-lookup"><span data-stu-id="659a6-111">To also make it easier to test and troubleshoot the data service during development, consider running the application that hosts the data service by using Internet Information Services (IIS).</span></span> <span data-ttu-id="659a6-112">如需詳細資訊，請參閱 [如何：開發在 IIS 上執行的 WCF 資料服務](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md)。</span><span class="sxs-lookup"><span data-stu-id="659a6-112">For more information, see [How to: Develop a WCF Data Service Running on IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md).</span></span>  
  
### <a name="to-create-the-aspnet-web-application"></a><span data-ttu-id="659a6-113">若要建立 ASP.NET Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="659a6-113">To create the ASP.NET Web application</span></span>  
  
1.  <span data-ttu-id="659a6-114">在 Visual Studio 中，在**檔案**功能表上，選取**新增**，然後選取**專案**。</span><span class="sxs-lookup"><span data-stu-id="659a6-114">In Visual Studio, on the **File** menu, select **New**, and then select **Project**.</span></span>  
  
2.  <span data-ttu-id="659a6-115">在**新專案**對話方塊中的，在 Visual Basic 或 Visual C# 選取**Web**範本，，然後選取**ASP.NET Web 應用程式**。</span><span class="sxs-lookup"><span data-stu-id="659a6-115">In the **New Project** dialog box, under either Visual Basic or Visual C# select the **Web** template, and then select **ASP.NET Web Application**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="659a6-116">如果您使用 Visual Studio Web Developer，您必須建立新網站，而非建立新的 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="659a6-116">If you use Visual Studio Web Developer, you must create a new Web site instead of a new Web application.</span></span>  
  
3.  <span data-ttu-id="659a6-117">型別`NorthwindService`做為專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="659a6-117">Type `NorthwindService` as the name of the project.</span></span>  
  
4.  <span data-ttu-id="659a6-118">按一下 [確定 **Deploying Office Solutions**]。</span><span class="sxs-lookup"><span data-stu-id="659a6-118">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="659a6-119">(選擇性) 指定 Web 應用程式的連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="659a6-119">(Optional) Specify a specific port number for your Web application.</span></span> <span data-ttu-id="659a6-120">注意：快速入門的其餘部分會使用通訊埠編號 `12345`。</span><span class="sxs-lookup"><span data-stu-id="659a6-120">Note: the port number `12345` is used in the rest of the quickstart.</span></span>  
  
    1.  <span data-ttu-id="659a6-121">在**方案總管 中**，以滑鼠右鍵按一下名稱[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]專案您剛才建立的，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="659a6-121">In **Solution Explorer**, right-click the name of the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] project that you just created, and then click **Properties**.</span></span>  
  
    2.  <span data-ttu-id="659a6-122">選取**Web**索引標籤，然後設定的值**特定通訊埠**文字方塊`12345`。</span><span class="sxs-lookup"><span data-stu-id="659a6-122">Select the **Web** tab, and set the value of the **Specific port** text box to `12345`.</span></span>  
  
### <a name="to-define-the-data-model"></a><span data-ttu-id="659a6-123">若要定義資料模型</span><span class="sxs-lookup"><span data-stu-id="659a6-123">To define the data model</span></span>  
  
1.  <span data-ttu-id="659a6-124">在**方案總管 中**，以滑鼠右鍵按一下名稱[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]專案，然後再按一下**加入新項目。**</span><span class="sxs-lookup"><span data-stu-id="659a6-124">In **Solution Explorer**, right-click the name of the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] project, and then click **Add New Item.**</span></span>  
  
2.  <span data-ttu-id="659a6-125">在**加入新項目**對話方塊中，按一下 **資料**範本，然後選取**ADO.NET 實體資料模型**。</span><span class="sxs-lookup"><span data-stu-id="659a6-125">In the **Add New Item** dialog box, click the **Data** template and then select **ADO.NET Entity Data Model**.</span></span>  
  
3.  <span data-ttu-id="659a6-126">資料模型的名稱，輸入`Northwind.edmx`。</span><span class="sxs-lookup"><span data-stu-id="659a6-126">For the name of the data model, type `Northwind.edmx`.</span></span>  
  
4.  <span data-ttu-id="659a6-127">在[!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)]精靈中，選取**從資料庫產生**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="659a6-127">In the [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] Wizard, select **Generate from Database**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="659a6-128">執行下列步驟中，連接到資料庫的資料模型，然後按一下**下一步**:</span><span class="sxs-lookup"><span data-stu-id="659a6-128">Connect the data model to the database by doing one of the following steps, and then click **Next**:</span></span>  
  
    -   <span data-ttu-id="659a6-129">如果您沒有已設定的資料庫連接，按一下**新連線**並建立新的連接。</span><span class="sxs-lookup"><span data-stu-id="659a6-129">If you do not have a database connection already configured, click **New Connection** and create a new connection.</span></span> <span data-ttu-id="659a6-130">如需詳細資訊，請參閱[How to： 建立連接至 SQL Server 資料庫](http://go.microsoft.com/fwlink/?LinkId=123631)。</span><span class="sxs-lookup"><span data-stu-id="659a6-130">For more information, see [How to: Create Connections to SQL Server Databases](http://go.microsoft.com/fwlink/?LinkId=123631).</span></span> <span data-ttu-id="659a6-131">此 SQL Server 執行個體必須已附加 Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="659a6-131">This SQL Server instance must have the Northwind sample database attached.</span></span>  
  
         <span data-ttu-id="659a6-132">\-或-</span><span class="sxs-lookup"><span data-stu-id="659a6-132">\- or -</span></span>  
  
    -   <span data-ttu-id="659a6-133">如果您擁有已經設定為連接至 Northwind 資料庫的資料庫連接，請從連接清單中選取該連接。</span><span class="sxs-lookup"><span data-stu-id="659a6-133">If you have a database connection already configured to connect to the Northwind database, select that connection from the list of connections.</span></span>  
  
6.  <span data-ttu-id="659a6-134">在精靈的最後一頁上，選取資料庫中所有資料表的核取方塊，並且清除檢視表和預存程序 (Stored Procedure) 的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="659a6-134">On the final page of the wizard, select the check boxes for all tables in the database, and clear the check boxes for views and stored procedures.</span></span>  
  
7.  <span data-ttu-id="659a6-135">按一下**完成**關閉精靈。</span><span class="sxs-lookup"><span data-stu-id="659a6-135">Click **Finish** to close the wizard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="659a6-136">這樣產生的資料模型會在實體類型上公開外部索引鍵屬性。</span><span class="sxs-lookup"><span data-stu-id="659a6-136">This generated data model exposes foreign key properties on entity types.</span></span> <span data-ttu-id="659a6-137">使用 Visual Studio 2008 建立的資料模型不包含這些外部索引鍵屬性。</span><span class="sxs-lookup"><span data-stu-id="659a6-137">Data models created using Visual Studio 2008 do not include these foreign key properties.</span></span> <span data-ttu-id="659a6-138">因此，您必須更新之前為了存取 Northwind 資料服務所建立之任何用戶端應用程式的用戶端資料服務類別，此資料服務是在嘗試存取這一版的 Northwind 資料服務之前使用 Visual Studio 2008 所建立。</span><span class="sxs-lookup"><span data-stu-id="659a6-138">Because of this, you must update the client data service classes of any client applications that were created to access the Northwind data service that was created using Visual Studio 2008 before attempting to access this version of the Northwind data service.</span></span>  
  
### <a name="to-create-the-data-service"></a><span data-ttu-id="659a6-139">若要建立資料服務</span><span class="sxs-lookup"><span data-stu-id="659a6-139">To create the data service</span></span>  
  
1.  <span data-ttu-id="659a6-140">在**方案總管 中**，以滑鼠右鍵按一下名稱您[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]專案，然後再按一下**加入新項目**。</span><span class="sxs-lookup"><span data-stu-id="659a6-140">In **Solution Explorer**, right-click the name of your [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] project, and then click **Add New Item**.</span></span>  
  
2.  <span data-ttu-id="659a6-141">在**加入新項目**對話方塊中，選取**WCF 資料服務**。</span><span class="sxs-lookup"><span data-stu-id="659a6-141">In the **Add New Item** dialog box, select **WCF Data Service**.</span></span>  
  
3.  <span data-ttu-id="659a6-142">服務的名稱，輸入`Northwind`。</span><span class="sxs-lookup"><span data-stu-id="659a6-142">For the name of the service, type `Northwind`.</span></span>  
  
     <span data-ttu-id="659a6-143">Visual StudioVisual Studio 會建立新服務的 XML 標記和程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="659a6-143">Visual StudioVisual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="659a6-144">根據預設，程式碼編輯器視窗隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="659a6-144">By default, the code-editor window opens.</span></span> <span data-ttu-id="659a6-145">在**方案總管 中**，服務將會具有名稱 Northwind，副檔名。 為.svc.cs 或.svc.vb。</span><span class="sxs-lookup"><span data-stu-id="659a6-145">In **Solution Explorer**, the service will have the name, Northwind, with the extension .svc.cs or .svc.vb.</span></span>  
  
4.  <span data-ttu-id="659a6-146">在資料服務的程式碼裡，於定義資料服務和型別的類別定義中，取代註解 `/* TODO: put your data source class name here */`，該型別是資料模型的實體容器，在這個案例中是 `NorthwindEntities`。</span><span class="sxs-lookup"><span data-stu-id="659a6-146">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindEntities`.</span></span> <span data-ttu-id="659a6-147">類別定義看起來應如下列：</span><span class="sxs-lookup"><span data-stu-id="659a6-147">The class definition should look this the following:</span></span>  
  
     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]  
  
### <a name="to-enable-access-to-data-service-resources"></a><span data-ttu-id="659a6-148">若要啟用資料服務資源的存取</span><span class="sxs-lookup"><span data-stu-id="659a6-148">To enable access to data service resources</span></span>  
  
1.  <span data-ttu-id="659a6-149">在資料服務的程式碼中，以下列程式碼取代 `InitializeService` 函數中的預留位置程式碼：</span><span class="sxs-lookup"><span data-stu-id="659a6-149">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#allreadconfig)]  
  
     <span data-ttu-id="659a6-150">如此可讓授權的用戶端具有指定之實體集資源的讀取和寫入存取權。</span><span class="sxs-lookup"><span data-stu-id="659a6-150">This enables authorized clients to have read and write access to resources for the specified entity sets.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="659a6-151">任何可存取 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 應用程式的用戶端也可以存取資料服務公開的資源。</span><span class="sxs-lookup"><span data-stu-id="659a6-151">Any client that can access the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application can also access the resources exposed by the data service.</span></span> <span data-ttu-id="659a6-152">在產生資料服務的過程中，若要避免未經授權存取資源，您也應該要保護應用程式本身。</span><span class="sxs-lookup"><span data-stu-id="659a6-152">In a production data service, to prevent unauthorized access to resources you should also secure the application itself.</span></span> <span data-ttu-id="659a6-153">如需詳細資訊，請參閱 [Securing WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="659a6-153">For more information, see [Securing WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="659a6-154">後續步驟</span><span class="sxs-lookup"><span data-stu-id="659a6-154">Next Steps</span></span>  
 <span data-ttu-id="659a6-155">您已成功建立新的資料服務公開[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]摘要，根據 Northwind 範例資料庫，而且您已啟用的存取權之用戶端上的權限摘要[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="659a6-155">You have successfully created a new data service that exposes an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed that is based on the Northwind sample database, and you have enabled access to the feed for clients that have permissions on the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web application.</span></span> <span data-ttu-id="659a6-156">接著，您會從 Visual Studio 啟動資料服務，然後透過 Web 瀏覽器送出 HTTP GET 要求，以存取 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要：</span><span class="sxs-lookup"><span data-stu-id="659a6-156">Next, you will start the data service from Visual Studio and you will access the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed by submitting HTTP GET requests through a Web browser:</span></span>  
  
 [<span data-ttu-id="659a6-157">從網頁瀏覽器存取服務</span><span class="sxs-lookup"><span data-stu-id="659a6-157">Accessing the Service from a Web Browser</span></span>](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)  
  
## <a name="see-also"></a><span data-ttu-id="659a6-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="659a6-158">See Also</span></span>  
 [<span data-ttu-id="659a6-159">ADO.NET 實體資料模型工具</span><span class="sxs-lookup"><span data-stu-id="659a6-159">ADO.NET Entity Data Model  Tools</span></span>](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)
