---
title: 作法：開發在 IIS 上執行的 WCF 資料服務
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- WCF Data Services, hosting
ms.assetid: f6f768c5-4989-49e3-a36f-896ab4ded86e
ms.openlocfilehash: 89be7aa8339a4edf6d6ab9c0c243e4320d2fdfa8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052979"
---
# <a name="how-to-develop-a-wcf-data-service-running-on-iis"></a><span data-ttu-id="25bc3-102">作法：開發在 IIS 上執行的 WCF 資料服務</span><span class="sxs-lookup"><span data-stu-id="25bc3-102">How to: Develop a WCF data service running on IIS</span></span>

<span data-ttu-id="25bc3-103">本主題將示範如何使用 WCF Data Services 來建立以 Northwind 範例資料庫為基礎的資料服務，該資料庫是由在 Internet Information Services （IIS）上執行的 ASP.NET Web 應用程式所裝載。</span><span class="sxs-lookup"><span data-stu-id="25bc3-103">This topic shows how to use WCF Data Services to create a data service that is based on the Northwind sample database that is hosted by an ASP.NET Web application that is running on Internet Information Services (IIS).</span></span> <span data-ttu-id="25bc3-104">如需如何建立與 ASP.NET 程式開發伺服器上執行的 ASP.NET Web 應用程式相同的 Northwind 資料服務的範例，請參閱[WCF Data Services 快速入門](quickstart-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="25bc3-104">For an example of how to create the same Northwind data service as an ASP.NET Web application that runs on the ASP.NET Development Server, see the [WCF Data Services quickstart](quickstart-wcf-data-services.md).</span></span>

> [!NOTE]
> <span data-ttu-id="25bc3-105">若要建立 Northwind 資料服務，您必須在本機電腦上安裝 Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="25bc3-105">To create the Northwind data service, you must have installed the Northwind sample database on the local computer.</span></span> <span data-ttu-id="25bc3-106">若要下載此範例資料庫，請參閱下載頁面： [SQL Server 的範例資料庫](https://go.microsoft.com/fwlink/?linkid=24758)。</span><span class="sxs-lookup"><span data-stu-id="25bc3-106">To download this sample database, see the download page, [Sample Databases for SQL Server](https://go.microsoft.com/fwlink/?linkid=24758).</span></span>

<span data-ttu-id="25bc3-107">本主題示範如何使用 Entity Framework 提供者建立資料服務。</span><span class="sxs-lookup"><span data-stu-id="25bc3-107">This topic shows how to create a data service by using the Entity Framework provider.</span></span> <span data-ttu-id="25bc3-108">有其他資料服務提供者可以使用。</span><span class="sxs-lookup"><span data-stu-id="25bc3-108">Other data services providers are available.</span></span> <span data-ttu-id="25bc3-109">如需詳細資訊，請參閱[資料服務提供者](data-services-providers-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="25bc3-109">For more information, see [Data Services Providers](data-services-providers-wcf-data-services.md).</span></span>

<span data-ttu-id="25bc3-110">當您建立服務之後，您必須明確提供資料服務資源的存取權。</span><span class="sxs-lookup"><span data-stu-id="25bc3-110">After you create the service, you must explicitly provide access to data service resources.</span></span> <span data-ttu-id="25bc3-111">如需詳細資訊，請參閱[如何：啟用資料服務](how-to-enable-access-to-the-data-service-wcf-data-services.md)的存取權。</span><span class="sxs-lookup"><span data-stu-id="25bc3-111">For more information, see [How to: Enable Access to the Data Service](how-to-enable-access-to-the-data-service-wcf-data-services.md).</span></span>

## <a name="create-the-aspnet-web-application-that-runs-on-iis"></a><span data-ttu-id="25bc3-112">建立在 IIS 上執行的 ASP.NET web 應用程式</span><span class="sxs-lookup"><span data-stu-id="25bc3-112">Create the ASP.NET web application that runs on IIS</span></span>

1. <span data-ttu-id="25bc3-113">**在 Visual Studio 的 [檔案**] 功能表上，選取 [**新增** > **專案**]。</span><span class="sxs-lookup"><span data-stu-id="25bc3-113">In Visual Studio, on the **File** menu, select **New** > **Project**.</span></span>

2. <span data-ttu-id="25bc3-114">在 [**新增專案**] 對話方塊中，選取 [**已安裝**的 > [**視覺效果C#** 或**Visual Basic**] > **Web**類別]。</span><span class="sxs-lookup"><span data-stu-id="25bc3-114">In the **New Project** dialog box, select the **Installed** > [**Visual C#** or **Visual Basic**] > **Web** category.</span></span>

3. <span data-ttu-id="25bc3-115">選取 [ **ASP.NET Web 應用程式**] 範本。</span><span class="sxs-lookup"><span data-stu-id="25bc3-115">Select the **ASP.NET Web Application** template.</span></span>

4. <span data-ttu-id="25bc3-116">輸入`NorthwindService`作為專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="25bc3-116">Enter `NorthwindService` as the name of the project.</span></span>

5. <span data-ttu-id="25bc3-117">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="25bc3-117">Click **OK**.</span></span>

6. <span data-ttu-id="25bc3-118">在 [**專案**] 功能表上，選取 [ **NorthwindService 屬性**]。</span><span class="sxs-lookup"><span data-stu-id="25bc3-118">On the **Project** menu, select **NorthwindService Properties**.</span></span>

7. <span data-ttu-id="25bc3-119">選取 [ **Web** ] 索引標籤，然後選取 [**使用本機 IIS Web 服務器**]。</span><span class="sxs-lookup"><span data-stu-id="25bc3-119">Select the **Web** tab, and then select **Use Local IIS Web Server**.</span></span>

8. <span data-ttu-id="25bc3-120">按一下 [**建立虛擬目錄**]，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="25bc3-120">Click **Create Virtual Directory** and then click **OK**.</span></span>

9. <span data-ttu-id="25bc3-121">在具有系統管理員權限的命令提示字元中，執行下列其中一個命令 (視作業系統而定)：</span><span class="sxs-lookup"><span data-stu-id="25bc3-121">From the command prompt with administrator privileges, execute one of the following commands (depending on the operating system):</span></span>

    - <span data-ttu-id="25bc3-122">32 位元系統：</span><span class="sxs-lookup"><span data-stu-id="25bc3-122">32-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

    - <span data-ttu-id="25bc3-123">64 位元系統：</span><span class="sxs-lookup"><span data-stu-id="25bc3-123">64-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework64\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

     <span data-ttu-id="25bc3-124">這樣會確定 Windows Communication Foundation (WCF) 已在電腦上登錄。</span><span class="sxs-lookup"><span data-stu-id="25bc3-124">This makes sure that Windows Communication Foundation (WCF) is registered on the computer.</span></span>

10. <span data-ttu-id="25bc3-125">在具有系統管理員權限的命令提示字元中，執行下列其中一個命令 (視作業系統而定)：</span><span class="sxs-lookup"><span data-stu-id="25bc3-125">From the command prompt with administrator privileges, execute one of the following commands (depending on the operating system):</span></span>

    - <span data-ttu-id="25bc3-126">32 位元系統：</span><span class="sxs-lookup"><span data-stu-id="25bc3-126">32-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

    - <span data-ttu-id="25bc3-127">64 位元系統：</span><span class="sxs-lookup"><span data-stu-id="25bc3-127">64-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

     <span data-ttu-id="25bc3-128">這樣可確保 IIS 會在電腦上安裝 WCF 之後正確執行。</span><span class="sxs-lookup"><span data-stu-id="25bc3-128">This makes sure that IIS runs correctly after WCF has been installed on the computer.</span></span> <span data-ttu-id="25bc3-129">此外，您可能也必須重新啟動 IIS。</span><span class="sxs-lookup"><span data-stu-id="25bc3-129">You might have to also restart IIS.</span></span>

11. <span data-ttu-id="25bc3-130">當 ASP.NET 應用程式在 IIS7 上執行時，您也必須執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="25bc3-130">When the ASP.NET application runs on IIS7, you must also perform the following steps:</span></span>

    1. <span data-ttu-id="25bc3-131">開啟 [IIS 管理員] 並流覽至 [**預設網站**] 底下的 [PhotoService] 應用程式。</span><span class="sxs-lookup"><span data-stu-id="25bc3-131">Open IIS Manager and navigate to the PhotoService application under **Default Web Site**.</span></span>

    2. <span data-ttu-id="25bc3-132">在 [**功能視圖**] 中，按兩下 [**驗證**]。</span><span class="sxs-lookup"><span data-stu-id="25bc3-132">In **Features View**, double-click **Authentication**.</span></span>

    3. <span data-ttu-id="25bc3-133">在 [**驗證**] 頁面上，選取 [**匿名驗證**]。</span><span class="sxs-lookup"><span data-stu-id="25bc3-133">On the **Authentication** page, select **Anonymous Authentication**.</span></span>

    4. <span data-ttu-id="25bc3-134">在 [**動作**] 窗格中，按一下 [**編輯**]，設定匿名使用者用來連線到網站的安全性主體。</span><span class="sxs-lookup"><span data-stu-id="25bc3-134">In the **Actions** pane, click **Edit** to set the security principal under which anonymous users will connect to the site.</span></span>

    5. <span data-ttu-id="25bc3-135">在 [**編輯匿名驗證認證**] 對話方塊中，選取 [**應用程式集**區身分識別]。</span><span class="sxs-lookup"><span data-stu-id="25bc3-135">In the **Edit Anonymous Authentication Credentials** dialog box, select **Application pool identity**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="25bc3-136">當您使用 Network Service 帳戶時，就會將與該帳戶相關聯的所有內部網路存取權授與匿名使用者。</span><span class="sxs-lookup"><span data-stu-id="25bc3-136">When you use the Network Service account, you grant anonymous users all the internal network access associated with that account.</span></span>

12. <span data-ttu-id="25bc3-137">使用 SQL Server Management Studio、sqlcmd.exe 公用程式或 Visual Studio 中的 Transact-SQL 編輯器，針對已附加 Northwind 資料庫的 SQL Server 執行個體執行下列 Transact-SQL 命令：</span><span class="sxs-lookup"><span data-stu-id="25bc3-137">By using SQL Server Management Studio, the sqlcmd.exe utility, or the Transact-SQL Editor in Visual Studio, execute the following Transact-SQL command against the instance of SQL Server that has the Northwind database attached:</span></span>

    ```sql
    CREATE LOGIN [NT AUTHORITY\NETWORK SERVICE] FROM WINDOWS;
    GO
    ```

    <span data-ttu-id="25bc3-138">這樣會在用來執行 IIS 之 Windows 帳戶的 SQL Server 執行個體中建立登入。</span><span class="sxs-lookup"><span data-stu-id="25bc3-138">This creates a login in the SQL Server instance for the Windows account used to run IIS.</span></span> <span data-ttu-id="25bc3-139">如此可讓 IIS 連接至 SQL Server 執行個體。</span><span class="sxs-lookup"><span data-stu-id="25bc3-139">This enables IIS to connect to the SQL Server instance.</span></span>

13. <span data-ttu-id="25bc3-140">當附加 Northwind 資料庫之後，執行下列 Transact-SQL 命令：</span><span class="sxs-lookup"><span data-stu-id="25bc3-140">With the Northwind database attached, execute the following Transact-SQL commands:</span></span>

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

    <span data-ttu-id="25bc3-141">這樣會授與新登入的權限，此權限可讓 IIS 讀取 Northwind 資料庫中的資料並將資料寫入其中。</span><span class="sxs-lookup"><span data-stu-id="25bc3-141">This grants rights to the new login, which enables IIS to read data from and write data to the Northwind database.</span></span>

## <a name="define-the-data-model"></a><span data-ttu-id="25bc3-142">定義資料模型</span><span class="sxs-lookup"><span data-stu-id="25bc3-142">Define the data model</span></span>

1. <span data-ttu-id="25bc3-143">在**方案總管**中，以滑鼠右鍵按一下 ASP.NET 專案的名稱，然後按一下 [**加入** > **新專案**]。</span><span class="sxs-lookup"><span data-stu-id="25bc3-143">In **Solution Explorer**, right-click the name of the ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="25bc3-144">在 [**加入新專案**] 對話方塊中，選取 [ **ADO.NET 實體資料模型**]。</span><span class="sxs-lookup"><span data-stu-id="25bc3-144">In the **Add New Item** dialog box, select **ADO.NET Entity Data Model**.</span></span>

3. <span data-ttu-id="25bc3-145">針對資料模型的名稱，輸入`Northwind.edmx`。</span><span class="sxs-lookup"><span data-stu-id="25bc3-145">For the name of the data model, type `Northwind.edmx`.</span></span>

4. <span data-ttu-id="25bc3-146">在 [實體資料模型 Wizard] 中，選取 [**從資料庫產生**]，然後按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="25bc3-146">In the Entity Data Model Wizard, select **Generate from Database**, and then click **Next**.</span></span>

5. <span data-ttu-id="25bc3-147">執行下列其中一個步驟，將資料模型連接至資料庫，然後按 **[下一步]** ：</span><span class="sxs-lookup"><span data-stu-id="25bc3-147">Connect the data model to the database by doing one of the following steps, and then click **Next**:</span></span>

    - <span data-ttu-id="25bc3-148">如果您尚未設定資料庫連接，請按一下 [**新增連接**]，然後建立新的連接。</span><span class="sxs-lookup"><span data-stu-id="25bc3-148">If you do not have a database connection already configured, click **New Connection** and create a new connection.</span></span> <span data-ttu-id="25bc3-149">如需詳細資訊，請參閱[如何：建立 SQL Server 資料庫](https://go.microsoft.com/fwlink/?LinkId=123631)的連接。</span><span class="sxs-lookup"><span data-stu-id="25bc3-149">For more information, see [How to: Create Connections to SQL Server Databases](https://go.microsoft.com/fwlink/?LinkId=123631).</span></span> <span data-ttu-id="25bc3-150">此 SQL Server 執行個體必須已附加 Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="25bc3-150">This SQL Server instance must have the Northwind sample database attached.</span></span>

         <span data-ttu-id="25bc3-151">\-或-</span><span class="sxs-lookup"><span data-stu-id="25bc3-151">\- or -</span></span>

    - <span data-ttu-id="25bc3-152">如果您擁有已經設定為連接至 Northwind 資料庫的資料庫連接，請從連接清單中選取該連接。</span><span class="sxs-lookup"><span data-stu-id="25bc3-152">If you have a database connection already configured to connect to the Northwind database, select that connection from the list of connections.</span></span>

6. <span data-ttu-id="25bc3-153">在精靈的最後一頁上，選取資料庫中所有資料表的核取方塊，並且清除檢視表和預存程序 (Stored Procedure) 的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="25bc3-153">On the final page of the wizard, select the check boxes for all tables in the database, and clear the check boxes for views and stored procedures.</span></span>

7. <span data-ttu-id="25bc3-154">按一下 [完成] 以關閉精靈。</span><span class="sxs-lookup"><span data-stu-id="25bc3-154">Click **Finish** to close the wizard.</span></span>

## <a name="create-the-data-service"></a><span data-ttu-id="25bc3-155">建立資料服務</span><span class="sxs-lookup"><span data-stu-id="25bc3-155">Create the data service</span></span>

1. <span data-ttu-id="25bc3-156">在**方案總管**中，以滑鼠右鍵按一下 ASP.NET 專案的名稱，然後按一下 [**加入** > **新專案**]。</span><span class="sxs-lookup"><span data-stu-id="25bc3-156">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="25bc3-157">在 [**加入新專案**] 對話方塊中，選取 [ **WCF 資料服務**]。</span><span class="sxs-lookup"><span data-stu-id="25bc3-157">In the **Add New Item** dialog box, select **WCF Data Service**.</span></span>

   ![Visual Studio 2015 中的 WCF 資料服務專案範本](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="25bc3-159">**WCF 資料服務**範本可在 Visual Studio 2015 中取得，但 Visual Studio 2017 則不提供。</span><span class="sxs-lookup"><span data-stu-id="25bc3-159">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017.</span></span>

3. <span data-ttu-id="25bc3-160">針對服務的名稱，輸入`Northwind`。</span><span class="sxs-lookup"><span data-stu-id="25bc3-160">For the name of the service, enter `Northwind`.</span></span>

     <span data-ttu-id="25bc3-161">Visual Studio 會針對新的服務建立 XML 標記和程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="25bc3-161">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="25bc3-162">根據預設，程式碼編輯器視窗隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="25bc3-162">By default, the code-editor window opens.</span></span> <span data-ttu-id="25bc3-163">在**方案總管**中，服務的名稱為、Northwind 和 svc.cs 或 .svc。</span><span class="sxs-lookup"><span data-stu-id="25bc3-163">In **Solution Explorer**, the service has the name, Northwind, and the extension .svc.cs or .svc.vb.</span></span>

4. <span data-ttu-id="25bc3-164">在資料服務的程式碼裡，於定義資料服務和型別的類別定義中，取代註解 `/* TODO: put your data source class name here */`，該型別是資料模型的實體容器，在這個案例中是 `NorthwindEntities`。</span><span class="sxs-lookup"><span data-stu-id="25bc3-164">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindEntities`.</span></span> <span data-ttu-id="25bc3-165">類別定義看起來應如下列：</span><span class="sxs-lookup"><span data-stu-id="25bc3-165">The class definition should look this the following:</span></span>

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="see-also"></a><span data-ttu-id="25bc3-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25bc3-166">See also</span></span>

- [<span data-ttu-id="25bc3-167">將資料當作服務公開</span><span class="sxs-lookup"><span data-stu-id="25bc3-167">Exposing Your Data as a Service</span></span>](exposing-your-data-as-a-service-wcf-data-services.md)
