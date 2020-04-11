---
title: HOW TO：開發在 IIS 上執行的 WCF Data Service
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- WCF Data Services, hosting
ms.assetid: f6f768c5-4989-49e3-a36f-896ab4ded86e
ms.openlocfilehash: 8a1a0c2c55267940463e2c9ab82bb52345269260
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121605"
---
# <a name="how-to-develop-a-wcf-data-service-running-on-iis"></a><span data-ttu-id="5ad9a-102">如何:開發在 IIS 上執行的 WCF 資料服務</span><span class="sxs-lookup"><span data-stu-id="5ad9a-102">How to: Develop a WCF data service running on IIS</span></span>

<span data-ttu-id="5ad9a-103">本文演示如何使用 WCF 資料服務創建基於在 Internet 資訊服務 (IIS) 上運行的 ASP.NET Web 應用託管的北風範例資料庫的數據服務。</span><span class="sxs-lookup"><span data-stu-id="5ad9a-103">This article shows how to use WCF Data Services to create a data service that's based on the Northwind sample database that's hosted by an ASP.NET Web app running on Internet Information Services (IIS).</span></span> <span data-ttu-id="5ad9a-104">有關如何建立與在ASP.NET開發伺服器上執行的ASP.NET Web 應用相同的北風資料服務的範例,請參閱[WCF 資料服務快速入門](quickstart-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="5ad9a-104">For an example of how to create the same Northwind data service as an ASP.NET Web app that runs on the ASP.NET Development Server, see the [WCF Data Services quickstart](quickstart-wcf-data-services.md).</span></span>

> [!NOTE]
> <span data-ttu-id="5ad9a-105">要創建北風數據服務,請先在本地電腦上安裝北風樣本資料庫。</span><span class="sxs-lookup"><span data-stu-id="5ad9a-105">To create the Northwind data service, first install the Northwind sample database on the local computer.</span></span> <span data-ttu-id="5ad9a-106">要安裝資料庫,請從北風執行 Transact-SQL 文稿[,並為 Microsoft SQL Server 執行 pubs 範例資料庫](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)。</span><span class="sxs-lookup"><span data-stu-id="5ad9a-106">To install the database, run the Transact-SQL script from [Northwind and pubs sample databases for Microsoft SQL Server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs).</span></span>

<span data-ttu-id="5ad9a-107">本文演示如何使用實體框架提供程式創建數據服務。</span><span class="sxs-lookup"><span data-stu-id="5ad9a-107">This article shows how to create a data service by using the Entity Framework provider.</span></span> <span data-ttu-id="5ad9a-108">有其他資料服務提供者可以使用。</span><span class="sxs-lookup"><span data-stu-id="5ad9a-108">Other data services providers are available.</span></span> <span data-ttu-id="5ad9a-109">有關詳細資訊,請參閱[資料服務提供者](data-services-providers-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="5ad9a-109">For more information, see [Data Services Providers](data-services-providers-wcf-data-services.md).</span></span>

<span data-ttu-id="5ad9a-110">當您建立服務之後，您必須明確提供資料服務資源的存取權。</span><span class="sxs-lookup"><span data-stu-id="5ad9a-110">After you create the service, you must explicitly provide access to data service resources.</span></span> <span data-ttu-id="5ad9a-111">關於詳細資訊,請參考[如何:啟用對資料服務的權限](how-to-enable-access-to-the-data-service-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="5ad9a-111">For more information, see [How to: Enable Access to the Data Service](how-to-enable-access-to-the-data-service-wcf-data-services.md).</span></span>

## <a name="create-the-aspnet-web-application-that-runs-on-iis"></a><span data-ttu-id="5ad9a-112">建立在 IIS 上執行的 ASP.NET Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="5ad9a-112">Create the ASP.NET web application that runs on IIS</span></span>

1. <span data-ttu-id="5ad9a-113">在 Visual Studio 中，於 [檔案]  功能表上選取 [新增]   > [專案]  。</span><span class="sxs-lookup"><span data-stu-id="5ad9a-113">In Visual Studio, on the **File** menu, select **New** > **Project**.</span></span>

2. <span data-ttu-id="5ad9a-114">在 **"新項目**"對話框中,選擇"**已安裝**> [**視覺 C#** 或**可視化基本**] > **Web**類別。</span><span class="sxs-lookup"><span data-stu-id="5ad9a-114">In the **New Project** dialog box, select the **Installed** > [**Visual C#** or **Visual Basic**] > **Web** category.</span></span>

3. <span data-ttu-id="5ad9a-115">選取 [ **ASP.NET Web 應用程式** ] 範本。</span><span class="sxs-lookup"><span data-stu-id="5ad9a-115">Select the **ASP.NET Web Application** template.</span></span>

4. <span data-ttu-id="5ad9a-116">輸入`NorthwindService`為專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="5ad9a-116">Enter `NorthwindService` as the name of the project.</span></span>

5. <span data-ttu-id="5ad9a-117">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="5ad9a-117">Click **OK**.</span></span>

6. <span data-ttu-id="5ad9a-118">在 **「專案」** 選單上,選擇 **「北風服務屬性**」。</span><span class="sxs-lookup"><span data-stu-id="5ad9a-118">On the **Project** menu, select **NorthwindService Properties**.</span></span>

7. <span data-ttu-id="5ad9a-119">選擇**Web**選項卡,然後選擇 **「使用本地 IIS Web 伺服器**」。。</span><span class="sxs-lookup"><span data-stu-id="5ad9a-119">Select the **Web** tab, and then select **Use Local IIS Web Server**.</span></span>

8. <span data-ttu-id="5ad9a-120">按下 **「創建虛擬目錄**」,然後按一下 **「 確定**」。</span><span class="sxs-lookup"><span data-stu-id="5ad9a-120">Click **Create Virtual Directory** and then click **OK**.</span></span>

9. <span data-ttu-id="5ad9a-121">在具有系統管理員權限的命令提示字元中，執行下列其中一個命令 (視作業系統而定)：</span><span class="sxs-lookup"><span data-stu-id="5ad9a-121">From the command prompt with administrator privileges, execute one of the following commands (depending on the operating system):</span></span>

    - <span data-ttu-id="5ad9a-122">32 位元系統：</span><span class="sxs-lookup"><span data-stu-id="5ad9a-122">32-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

    - <span data-ttu-id="5ad9a-123">64 位元系統：</span><span class="sxs-lookup"><span data-stu-id="5ad9a-123">64-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework64\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

     <span data-ttu-id="5ad9a-124">這樣會確定 Windows Communication Foundation (WCF) 已在電腦上登錄。</span><span class="sxs-lookup"><span data-stu-id="5ad9a-124">This makes sure that Windows Communication Foundation (WCF) is registered on the computer.</span></span>

10. <span data-ttu-id="5ad9a-125">在具有系統管理員權限的命令提示字元中，執行下列其中一個命令 (視作業系統而定)：</span><span class="sxs-lookup"><span data-stu-id="5ad9a-125">From the command prompt with administrator privileges, execute one of the following commands (depending on the operating system):</span></span>

    - <span data-ttu-id="5ad9a-126">32 位元系統：</span><span class="sxs-lookup"><span data-stu-id="5ad9a-126">32-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

    - <span data-ttu-id="5ad9a-127">64 位元系統：</span><span class="sxs-lookup"><span data-stu-id="5ad9a-127">64-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

     <span data-ttu-id="5ad9a-128">這樣可確保 IIS 會在電腦上安裝 WCF 之後正確執行。</span><span class="sxs-lookup"><span data-stu-id="5ad9a-128">This makes sure that IIS runs correctly after WCF has been installed on the computer.</span></span> <span data-ttu-id="5ad9a-129">此外，您可能也必須重新啟動 IIS。</span><span class="sxs-lookup"><span data-stu-id="5ad9a-129">You might have to also restart IIS.</span></span>

11. <span data-ttu-id="5ad9a-130">當 ASP.NET 應用程式在 IIS7 上執行時，您也必須執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="5ad9a-130">When the ASP.NET application runs on IIS7, you must also perform the following steps:</span></span>

    1. <span data-ttu-id="5ad9a-131">打開 IIS 管理員並導航到**預設網站**下的 Photo 服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="5ad9a-131">Open IIS Manager and navigate to the PhotoService application under **Default Web Site**.</span></span>

    2. <span data-ttu-id="5ad9a-132">在 [功能檢視]\*\*\*\* 中，連按兩下 [驗證]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5ad9a-132">In **Features View**, double-click **Authentication**.</span></span>

    3. <span data-ttu-id="5ad9a-133">在 [驗證]\*\*\*\* 頁面上，選取 [匿名驗證]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5ad9a-133">On the **Authentication** page, select **Anonymous Authentication**.</span></span>

    4. <span data-ttu-id="5ad9a-134">在「**操作」** 窗格中,按下 **「編輯」** 以設定匿名使用者將連接到網站的安全主體。</span><span class="sxs-lookup"><span data-stu-id="5ad9a-134">In the **Actions** pane, click **Edit** to set the security principal under which anonymous users will connect to the site.</span></span>

    5. <span data-ttu-id="5ad9a-135">在 **「編輯匿名身份驗證認證認證」** 對話框中,選擇 **「應用程式池標識**」。</span><span class="sxs-lookup"><span data-stu-id="5ad9a-135">In the **Edit Anonymous Authentication Credentials** dialog box, select **Application pool identity**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="5ad9a-136">當您使用 Network Service 帳戶時，就會將與該帳戶相關聯的所有內部網路存取權授與匿名使用者。</span><span class="sxs-lookup"><span data-stu-id="5ad9a-136">When you use the Network Service account, you grant anonymous users all the internal network access associated with that account.</span></span>

12. <span data-ttu-id="5ad9a-137">使用 SQL Server Management Studio、sqlcmd.exe 公用程式或 Visual Studio 中的 Transact-SQL 編輯器，針對已附加 Northwind 資料庫的 SQL Server 執行個體執行下列 Transact-SQL 命令：</span><span class="sxs-lookup"><span data-stu-id="5ad9a-137">By using SQL Server Management Studio, the sqlcmd.exe utility, or the Transact-SQL Editor in Visual Studio, execute the following Transact-SQL command against the instance of SQL Server that has the Northwind database attached:</span></span>

    ```sql
    CREATE LOGIN [NT AUTHORITY\NETWORK SERVICE] FROM WINDOWS;
    GO
    ```

    <span data-ttu-id="5ad9a-138">這樣會在用來執行 IIS 之 Windows 帳戶的 SQL Server 執行個體中建立登入。</span><span class="sxs-lookup"><span data-stu-id="5ad9a-138">This creates a login in the SQL Server instance for the Windows account used to run IIS.</span></span> <span data-ttu-id="5ad9a-139">如此可讓 IIS 連接至 SQL Server 執行個體。</span><span class="sxs-lookup"><span data-stu-id="5ad9a-139">This enables IIS to connect to the SQL Server instance.</span></span>

13. <span data-ttu-id="5ad9a-140">當附加 Northwind 資料庫之後，執行下列 Transact-SQL 命令：</span><span class="sxs-lookup"><span data-stu-id="5ad9a-140">With the Northwind database attached, execute the following Transact-SQL commands:</span></span>

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

    <span data-ttu-id="5ad9a-141">這樣會授與新登入的權限，此權限可讓 IIS 讀取 Northwind 資料庫中的資料並將資料寫入其中。</span><span class="sxs-lookup"><span data-stu-id="5ad9a-141">This grants rights to the new login, which enables IIS to read data from and write data to the Northwind database.</span></span>

## <a name="define-the-data-model"></a><span data-ttu-id="5ad9a-142">定義資料模型</span><span class="sxs-lookup"><span data-stu-id="5ad9a-142">Define the data model</span></span>

1. <span data-ttu-id="5ad9a-143">在**解決方案資源管理器**中,右鍵單擊ASP.NET專案的名稱,然後單擊「**添加新** > **項**」。</span><span class="sxs-lookup"><span data-stu-id="5ad9a-143">In **Solution Explorer**, right-click the name of the ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="5ad9a-144">在「**新增新項目」** 對話框中, 選擇**ADO.NET 實體資料模型**。</span><span class="sxs-lookup"><span data-stu-id="5ad9a-144">In the **Add New Item** dialog box, select **ADO.NET Entity Data Model**.</span></span>

3. <span data-ttu-id="5ad9a-145">對於資料模型的名稱,鍵入`Northwind.edmx`。</span><span class="sxs-lookup"><span data-stu-id="5ad9a-145">For the name of the data model, type `Northwind.edmx`.</span></span>

4. <span data-ttu-id="5ad9a-146">在「實體資料模型精靈」中,選擇 **「從資料庫生成**」,然後單擊「**下一步**」。</span><span class="sxs-lookup"><span data-stu-id="5ad9a-146">In the Entity Data Model Wizard, select **Generate from Database**, and then click **Next**.</span></span>

5. <span data-ttu-id="5ad9a-147">執行以下步驟之一會連接到資料庫,然後按**下 「下一步**」 :</span><span class="sxs-lookup"><span data-stu-id="5ad9a-147">Connect the data model to the database by doing one of the following steps, and then click **Next**:</span></span>

    - <span data-ttu-id="5ad9a-148">如果尚未設定資料庫連接,請按下 **「新建連線**」並創建新連接。</span><span class="sxs-lookup"><span data-stu-id="5ad9a-148">If you do not have a database connection already configured, click **New Connection** and create a new connection.</span></span> <span data-ttu-id="5ad9a-149">如需詳細資訊，請參閱 [How to: Create Connections to SQL Server Databases](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="5ad9a-149">For more information, see [How to: Create Connections to SQL Server Databases](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)).</span></span> <span data-ttu-id="5ad9a-150">此 SQL Server 執行個體必須已附加 Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="5ad9a-150">This SQL Server instance must have the Northwind sample database attached.</span></span>

         <span data-ttu-id="5ad9a-151">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="5ad9a-151">\- or -</span></span>

    - <span data-ttu-id="5ad9a-152">如果您擁有已經設定為連接至 Northwind 資料庫的資料庫連接，請從連接清單中選取該連接。</span><span class="sxs-lookup"><span data-stu-id="5ad9a-152">If you have a database connection already configured to connect to the Northwind database, select that connection from the list of connections.</span></span>

6. <span data-ttu-id="5ad9a-153">在精靈的最後一頁上，選取資料庫中所有資料表的核取方塊，並且清除檢視表和預存程序 (Stored Procedure) 的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="5ad9a-153">On the final page of the wizard, select the check boxes for all tables in the database, and clear the check boxes for views and stored procedures.</span></span>

7. <span data-ttu-id="5ad9a-154">按一下 **[完成]** 關閉精靈。</span><span class="sxs-lookup"><span data-stu-id="5ad9a-154">Click **Finish** to close the wizard.</span></span>

## <a name="create-the-data-service"></a><span data-ttu-id="5ad9a-155">建立資料服務</span><span class="sxs-lookup"><span data-stu-id="5ad9a-155">Create the data service</span></span>

1. <span data-ttu-id="5ad9a-156">在**解決方案資源管理器中**,右鍵單擊ASP.NET專案的名稱,然後單擊「**添加新** > **專案**」。</span><span class="sxs-lookup"><span data-stu-id="5ad9a-156">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="5ad9a-157">在「**新增新項目」** 對話框中,選擇**WCF 資料服務**。</span><span class="sxs-lookup"><span data-stu-id="5ad9a-157">In the **Add New Item** dialog box, select **WCF Data Service**.</span></span>

   ![2015 年可視化工作室中的 WCF 資料服務項目範本](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="5ad9a-159">**WCF 資料服務**範本在 Visual Studio 2015 中提供,但在 Visual Studio 2017 或更高版本中不可用。</span><span class="sxs-lookup"><span data-stu-id="5ad9a-159">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017 or later.</span></span>

3. <span data-ttu-id="5ad9a-160">對服務的名稱,請輸入`Northwind`。</span><span class="sxs-lookup"><span data-stu-id="5ad9a-160">For the name of the service, enter `Northwind`.</span></span>

     <span data-ttu-id="5ad9a-161">Visual Studio 會針對新的服務建立 XML 標記和程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="5ad9a-161">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="5ad9a-162">根據預設，程式碼編輯器視窗隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="5ad9a-162">By default, the code-editor window opens.</span></span> <span data-ttu-id="5ad9a-163">在**解決方案資源管理員**中,該服務的名稱、北風和擴展 .svc.cs或 .svc.vb。</span><span class="sxs-lookup"><span data-stu-id="5ad9a-163">In **Solution Explorer**, the service has the name, Northwind, and the extension .svc.cs or .svc.vb.</span></span>

4. <span data-ttu-id="5ad9a-164">在資料服務的程式碼裡，於定義資料服務和型別的類別定義中，取代註解 `/* TODO: put your data source class name here */`，該型別是資料模型的實體容器，在這個案例中是 `NorthwindEntities`。</span><span class="sxs-lookup"><span data-stu-id="5ad9a-164">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindEntities`.</span></span> <span data-ttu-id="5ad9a-165">類別定義看起來應如下列：</span><span class="sxs-lookup"><span data-stu-id="5ad9a-165">The class definition should look this the following:</span></span>

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="see-also"></a><span data-ttu-id="5ad9a-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5ad9a-166">See also</span></span>

- [<span data-ttu-id="5ad9a-167">將資料公開為服務</span><span class="sxs-lookup"><span data-stu-id="5ad9a-167">Exposing Your Data as a Service</span></span>](exposing-your-data-as-a-service-wcf-data-services.md)
