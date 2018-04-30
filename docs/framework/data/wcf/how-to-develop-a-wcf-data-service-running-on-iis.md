---
title: HOW TO：開發在 IIS 上執行的 WCF Data Service
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- WCF Data Services, hosting
ms.assetid: f6f768c5-4989-49e3-a36f-896ab4ded86e
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f9df38d200be864ab24efdb0d002fe7b75cfc3e4
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-develop-a-wcf-data-service-running-on-iis"></a><span data-ttu-id="208eb-102">HOW TO：開發在 IIS 上執行的 WCF Data Service</span><span class="sxs-lookup"><span data-stu-id="208eb-102">How to: Develop a WCF Data Service Running on IIS</span></span>
<span data-ttu-id="208eb-103">本主題示範如何使用[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]來建立 ASP.NET Web 應用程式執行網際網路資訊服務 (IIS) 所裝載的 Northwind 範例資料庫為基礎的資料服務。</span><span class="sxs-lookup"><span data-stu-id="208eb-103">This topic shows how to use [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] to create a data service that is based on the Northwind sample database that is hosted by an ASP.NET Web application that is running on Internet Information Services (IIS).</span></span> <span data-ttu-id="208eb-104">如需如何建立相同的 Northwind 資料服務，以在 ASP.NET 程式開發伺服器執行的 ASP.NET Web 應用程式的範例，請參閱[WCF Data Services 快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="208eb-104">For an example of how to create the same Northwind data service as an ASP.NET Web application that runs on the ASP.NET Development Server, see the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="208eb-105">若要建立 Northwind 資料服務，您必須在本機電腦上安裝 Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="208eb-105">To create the Northwind data service, you must have installed the Northwind sample database on the local computer.</span></span> <span data-ttu-id="208eb-106">若要下載此範例資料庫，請參閱下載頁面： [SQL Server 的範例資料庫](http://go.microsoft.com/fwlink/?linkid=24758)。</span><span class="sxs-lookup"><span data-stu-id="208eb-106">To download this sample database, see the download page, [Sample Databases for SQL Server](http://go.microsoft.com/fwlink/?linkid=24758).</span></span>  
  
 <span data-ttu-id="208eb-107">本主題示範如何使用 Entity Framework 提供者建立資料服務。</span><span class="sxs-lookup"><span data-stu-id="208eb-107">This topic shows how to create a data service by using the Entity Framework provider.</span></span> <span data-ttu-id="208eb-108">有其他資料服務提供者可以使用。</span><span class="sxs-lookup"><span data-stu-id="208eb-108">Other data services providers are available.</span></span> <span data-ttu-id="208eb-109">如需詳細資訊，請參閱[資料服務提供者](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="208eb-109">For more information, see [Data Services Providers](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="208eb-110">當您建立服務之後，您必須明確提供資料服務資源的存取權。</span><span class="sxs-lookup"><span data-stu-id="208eb-110">After you create the service, you must explicitly provide access to data service resources.</span></span> <span data-ttu-id="208eb-111">如需詳細資訊，請參閱[How to： 啟用資料服務的存取](../../../../docs/framework/data/wcf/how-to-enable-access-to-the-data-service-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="208eb-111">For more information, see [How to: Enable Access to the Data Service](../../../../docs/framework/data/wcf/how-to-enable-access-to-the-data-service-wcf-data-services.md).</span></span>  
  
### <a name="to-create-the-aspnet-web-application-that-runs-on-iis"></a><span data-ttu-id="208eb-112">若要建立在 IIS 上執行的 ASP.NET Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="208eb-112">To create the ASP.NET Web application that runs on IIS</span></span>  
  
1.  <span data-ttu-id="208eb-113">在 Visual Studio 中，在**檔案**功能表上，選取**新增**，然後選取**專案**。</span><span class="sxs-lookup"><span data-stu-id="208eb-113">In Visual Studio, on the **File** menu, select **New**, and then select **Project**.</span></span>  
  
2.  <span data-ttu-id="208eb-114">在**新專案**對話方塊方塊中，選取 Visual Basic 或 Visual C# 當做程式語言。</span><span class="sxs-lookup"><span data-stu-id="208eb-114">In the **New Project** dialog box, select either Visual Basic or Visual C# as the programming language.</span></span>  
  
3.  <span data-ttu-id="208eb-115">在**範本**窗格中，選取**ASP.NET Web 應用程式**。</span><span class="sxs-lookup"><span data-stu-id="208eb-115">In the **Templates** pane, select **ASP.NET Web Application**.</span></span> <span data-ttu-id="208eb-116">注意：如果您使用 Visual Studio Web Developer，您必須建立新網站，而非建立新的 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="208eb-116">Note: If you use Visual Studio Web Developer, you must create a new Web site instead of a new Web application.</span></span>  
  
4.  <span data-ttu-id="208eb-117">型別`NorthwindService`做為專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="208eb-117">Type `NorthwindService` as the name of the project.</span></span>  
  
5.  <span data-ttu-id="208eb-118">按一下 [確定 **Deploying Office Solutions**]。</span><span class="sxs-lookup"><span data-stu-id="208eb-118">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="208eb-119">在**專案**功能表上，選取**NorthwindService 屬性**。</span><span class="sxs-lookup"><span data-stu-id="208eb-119">On the **Project** menu, select **NorthwindService Properties**.</span></span>  
  
7.  <span data-ttu-id="208eb-120">選取**Web**索引標籤，然後選取**使用本機 IIS Web 伺服器**。</span><span class="sxs-lookup"><span data-stu-id="208eb-120">Select the **Web** tab, and then select **Use Local IIS Web Server**.</span></span>  
  
8.  <span data-ttu-id="208eb-121">按一下**建立虛擬目錄**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="208eb-121">Click **Create Virtual Directory** and then click **OK**.</span></span>  
  
9. <span data-ttu-id="208eb-122">在具有系統管理員權限的命令提示字元中，執行下列其中一個命令 (視作業系統而定)：</span><span class="sxs-lookup"><span data-stu-id="208eb-122">From the command prompt with administrator privileges, execute one of the following commands (depending on the operating system):</span></span>  
  
    -   <span data-ttu-id="208eb-123">32 位元系統：</span><span class="sxs-lookup"><span data-stu-id="208eb-123">32-bit systems:</span></span>  
  
        ```console
        "%windir%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i  
        ```  
  
    -   <span data-ttu-id="208eb-124">64 位元系統：</span><span class="sxs-lookup"><span data-stu-id="208eb-124">64-bit systems:</span></span>  
  
        ```console
        "%windir%\Microsoft.NET\Framework64\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i  
        ```  
  
     <span data-ttu-id="208eb-125">這樣會確定 Windows Communication Foundation (WCF) 已在電腦上登錄。</span><span class="sxs-lookup"><span data-stu-id="208eb-125">This makes sure that Windows Communication Foundation (WCF) is registered on the computer.</span></span>  
  
10. <span data-ttu-id="208eb-126">在具有系統管理員權限的命令提示字元中，執行下列其中一個命令 (視作業系統而定)：</span><span class="sxs-lookup"><span data-stu-id="208eb-126">From the command prompt with administrator privileges, execute one of the following commands (depending on the operating system):</span></span>  
  
    -   <span data-ttu-id="208eb-127">32 位元系統：</span><span class="sxs-lookup"><span data-stu-id="208eb-127">32-bit systems:</span></span>  
  
        ```console
        "%windir%\Microsoft.NET\Framework\v4.0.30319\aspnet_regiis.exe" -i -enable  
        ```  
  
    -   <span data-ttu-id="208eb-128">64 位元系統：</span><span class="sxs-lookup"><span data-stu-id="208eb-128">64-bit systems:</span></span>  
  
        ```console
        "%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe" -i -enable  
        ```  
  
     <span data-ttu-id="208eb-129">這樣可確保 IIS 會在電腦上安裝 WCF 之後正確執行。</span><span class="sxs-lookup"><span data-stu-id="208eb-129">This makes sure that IIS runs correctly after WCF has been installed on the computer.</span></span> <span data-ttu-id="208eb-130">此外，您可能也必須重新啟動 IIS。</span><span class="sxs-lookup"><span data-stu-id="208eb-130">You might have to also restart IIS.</span></span>  
  
11. <span data-ttu-id="208eb-131">當 ASP.NET 應用程式在 IIS7 上執行時，您也必須執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="208eb-131">When the ASP.NET application runs on IIS7, you must also perform the following steps:</span></span>  
  
    1.  <span data-ttu-id="208eb-132">開啟 IIS 管理員，並瀏覽至底下的 PhotoService 應用程式**Default Web Site**。</span><span class="sxs-lookup"><span data-stu-id="208eb-132">Open IIS Manager and navigate to the PhotoService application under **Default Web Site**.</span></span>  
  
    2.  <span data-ttu-id="208eb-133">在**功能檢視**，連按兩下**驗證**。</span><span class="sxs-lookup"><span data-stu-id="208eb-133">In **Features View**, double-click **Authentication**.</span></span>  
  
    3.  <span data-ttu-id="208eb-134">在**驗證**頁面上，選取**匿名驗證**。</span><span class="sxs-lookup"><span data-stu-id="208eb-134">On the **Authentication** page, select **Anonymous Authentication**.</span></span>  
  
    4.  <span data-ttu-id="208eb-135">在**動作**] 窗格中，按一下 [**編輯**設定安全性主體匿名使用者會連線至站台。</span><span class="sxs-lookup"><span data-stu-id="208eb-135">In the **Actions** pane, click **Edit** to set the security principal under which anonymous users will connect to the site.</span></span>  
  
    5.  <span data-ttu-id="208eb-136">在**編輯匿名驗證認證**對話方塊中，選取**應用程式集區識別**。</span><span class="sxs-lookup"><span data-stu-id="208eb-136">In the **Edit Anonymous Authentication Credentials** dialog box, select **Application pool identity**.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="208eb-137">當您使用 Network Service 帳戶時，就會將與該帳戶相關聯的所有內部網路存取權授與匿名使用者。</span><span class="sxs-lookup"><span data-stu-id="208eb-137">When you use the Network Service account, you grant anonymous users all the internal network access associated with that account.</span></span>  
  
12. <span data-ttu-id="208eb-138">使用 SQL Server Management Studio、sqlcmd.exe 公用程式或 Visual Studio 中的 Transact-SQL 編輯器，針對已附加 Northwind 資料庫的 SQL Server 執行個體執行下列 Transact-SQL 命令：</span><span class="sxs-lookup"><span data-stu-id="208eb-138">By using SQL Server Management Studio, the sqlcmd.exe utility, or the Transact-SQL Editor in Visual Studio, execute the following Transact-SQL command against the instance of SQL Server that has the Northwind database attached:</span></span>  
  
    ```sql  
    CREATE LOGIN [NT AUTHORITY\NETWORK SERVICE] FROM WINDOWS;  
    GO   
    ```  
  
     <span data-ttu-id="208eb-139">這樣會在用來執行 IIS 之 Windows 帳戶的 SQL Server 執行個體中建立登入。</span><span class="sxs-lookup"><span data-stu-id="208eb-139">This creates a login in the SQL Server instance for the Windows account used to run IIS.</span></span> <span data-ttu-id="208eb-140">如此可讓 IIS 連接至 SQL Server 執行個體。</span><span class="sxs-lookup"><span data-stu-id="208eb-140">This enables IIS to connect to the SQL Server instance.</span></span>  
  
13. <span data-ttu-id="208eb-141">當附加 Northwind 資料庫之後，執行下列 Transact-SQL 命令：</span><span class="sxs-lookup"><span data-stu-id="208eb-141">With the Northwind database attached, execute the following Transact-SQL commands:</span></span>  
  
    ```sql  
    USE Northwind  
    GO  
    CREATE USER [NT AUTHORITY\NETWORK SERVICE]   
    FOR LOGIN [NT AUTHORITY\NETWORK SERVICE] WITH DEFAULT_SCHEMA=[dbo];  
    GO  
    ALTER LOGIN [NT AUTHORITY\NETWORK SERVICE]   
    WITH DEFAULT_DATABASE=[Northwind];   
    GO  
    EXEC sp_addrolemember 'db_datareader', 'NT AUTHORITY\NETWORK SERVICE'  
    GO  
    EXEC sp_addrolemember 'db_datawriter', 'NT AUTHORITY\NETWORK SERVICE'  
    GO   
    ```  
  
     <span data-ttu-id="208eb-142">這樣會授與新登入的權限，此權限可讓 IIS 讀取 Northwind 資料庫中的資料並將資料寫入其中。</span><span class="sxs-lookup"><span data-stu-id="208eb-142">This grants rights to the new login, which enables IIS to read data from and write data to the Northwind database.</span></span>  
  
### <a name="to-define-the-data-model"></a><span data-ttu-id="208eb-143">若要定義資料模型</span><span class="sxs-lookup"><span data-stu-id="208eb-143">To define the data model</span></span>  
  
1.  <span data-ttu-id="208eb-144">在**方案總管 中**，以滑鼠右鍵按一下 ASP.NET 專案的名稱，然後按一下**加入新項目。**</span><span class="sxs-lookup"><span data-stu-id="208eb-144">In **Solution Explorer**, right-click the name of the ASP.NET project, and then click **Add New Item.**</span></span>  
  
2.  <span data-ttu-id="208eb-145">在**加入新項目**對話方塊中，選取**ADO.NET 實體資料模型**。</span><span class="sxs-lookup"><span data-stu-id="208eb-145">In the **Add New Item** dialog box, select **ADO.NET Entity Data Model**.</span></span>  
  
3.  <span data-ttu-id="208eb-146">資料模型的名稱，輸入`Northwind.edmx`。</span><span class="sxs-lookup"><span data-stu-id="208eb-146">For the name of the data model, type `Northwind.edmx`.</span></span>  
  
4.  <span data-ttu-id="208eb-147">在 實體資料模型精靈中，選取 **從資料庫產生**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="208eb-147">In the Entity Data Model Wizard, select **Generate from Database**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="208eb-148">執行下列步驟中，連接到資料庫的資料模型，然後按一下**下一步**:</span><span class="sxs-lookup"><span data-stu-id="208eb-148">Connect the data model to the database by doing one of the following steps, and then click **Next**:</span></span>  
  
    -   <span data-ttu-id="208eb-149">如果您沒有已設定的資料庫連接，按一下**新連線**並建立新的連接。</span><span class="sxs-lookup"><span data-stu-id="208eb-149">If you do not have a database connection already configured, click **New Connection** and create a new connection.</span></span> <span data-ttu-id="208eb-150">如需詳細資訊，請參閱[How to： 建立連接至 SQL Server 資料庫](http://go.microsoft.com/fwlink/?LinkId=123631)。</span><span class="sxs-lookup"><span data-stu-id="208eb-150">For more information, see [How to: Create Connections to SQL Server Databases](http://go.microsoft.com/fwlink/?LinkId=123631).</span></span> <span data-ttu-id="208eb-151">此 SQL Server 執行個體必須已附加 Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="208eb-151">This SQL Server instance must have the Northwind sample database attached.</span></span>  
  
         <span data-ttu-id="208eb-152">\-或-</span><span class="sxs-lookup"><span data-stu-id="208eb-152">\- or -</span></span>  
  
    -   <span data-ttu-id="208eb-153">如果您擁有已經設定為連接至 Northwind 資料庫的資料庫連接，請從連接清單中選取該連接。</span><span class="sxs-lookup"><span data-stu-id="208eb-153">If you have a database connection already configured to connect to the Northwind database, select that connection from the list of connections.</span></span>  
  
6.  <span data-ttu-id="208eb-154">在精靈的最後一頁上，選取資料庫中所有資料表的核取方塊，並且清除檢視表和預存程序 (Stored Procedure) 的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="208eb-154">On the final page of the wizard, select the check boxes for all tables in the database, and clear the check boxes for views and stored procedures.</span></span>  
  
7.  <span data-ttu-id="208eb-155">按一下**完成**關閉精靈。</span><span class="sxs-lookup"><span data-stu-id="208eb-155">Click **Finish** to close the wizard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="208eb-156">這樣產生的資料模型會在實體類型上公開外部索引鍵屬性。</span><span class="sxs-lookup"><span data-stu-id="208eb-156">This generated data model exposes foreign key properties on entity types.</span></span> <span data-ttu-id="208eb-157">使用 Visual Studio 2008 建立的資料模型不包含這些外部索引鍵屬性。</span><span class="sxs-lookup"><span data-stu-id="208eb-157">Data models created using Visual Studio 2008 do not include these foreign key properties.</span></span> <span data-ttu-id="208eb-158">因此，您必須更新之前為了存取 Northwind 資料服務所建立之任何用戶端應用程式的用戶端資料服務類別，此資料服務是在嘗試存取這一版的 Northwind 資料服務之前使用 Visual Studio 2008 所建立。</span><span class="sxs-lookup"><span data-stu-id="208eb-158">Because of this, you must update the client data service classes of any client applications that were created to access the Northwind data service that was created using Visual Studio 2008 before attempting to access this version of the Northwind data service.</span></span>  
  
### <a name="to-create-the-data-service"></a><span data-ttu-id="208eb-159">若要建立資料服務</span><span class="sxs-lookup"><span data-stu-id="208eb-159">To create the data service</span></span>  
  
1.  <span data-ttu-id="208eb-160">在**方案總管 中**，以滑鼠右鍵按一下您的 ASP.NET 專案的名稱，然後按一下**加入新項目**。</span><span class="sxs-lookup"><span data-stu-id="208eb-160">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add New Item**.</span></span>  
  
2.  <span data-ttu-id="208eb-161">在**加入新項目**對話方塊中，選取**ADO.NET Data Services**。</span><span class="sxs-lookup"><span data-stu-id="208eb-161">In the **Add New Item** dialog box, select **ADO.NET Data Service**.</span></span>  
  
3.  <span data-ttu-id="208eb-162">服務的名稱，輸入`Northwind`。</span><span class="sxs-lookup"><span data-stu-id="208eb-162">For the name of the service, type `Northwind`.</span></span>  
  
     <span data-ttu-id="208eb-163">Visual Studio 會針對新的服務建立 XML 標記和程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="208eb-163">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="208eb-164">根據預設，程式碼編輯器視窗隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="208eb-164">By default, the code-editor window opens.</span></span> <span data-ttu-id="208eb-165">在**方案總管 中**，服務將會具有名稱 Northwind，副檔名。 為.svc.cs 或.svc.vb。</span><span class="sxs-lookup"><span data-stu-id="208eb-165">In **Solution Explorer**, the service will have the name, Northwind, with the extension .svc.cs or .svc.vb.</span></span>  
  
4.  <span data-ttu-id="208eb-166">在資料服務的程式碼裡，於定義資料服務和型別的類別定義中，取代註解 `/* TODO: put your data source class name here */`，該型別是資料模型的實體容器，在這個案例中是 `NorthwindEntities`。</span><span class="sxs-lookup"><span data-stu-id="208eb-166">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindEntities`.</span></span> <span data-ttu-id="208eb-167">類別定義看起來應如下列：</span><span class="sxs-lookup"><span data-stu-id="208eb-167">The class definition should look this the following:</span></span>  
  
     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]  
  
## <a name="see-also"></a><span data-ttu-id="208eb-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="208eb-168">See Also</span></span>  
 [<span data-ttu-id="208eb-169">將資料當作服務公開</span><span class="sxs-lookup"><span data-stu-id="208eb-169">Exposing Your Data as a Service</span></span>](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md)
