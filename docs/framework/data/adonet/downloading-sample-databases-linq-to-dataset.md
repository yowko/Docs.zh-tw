---
title: "下載範例資料庫 (LINQ to DataSet)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eb42a7af-d410-4b7f-b4a8-13c72ce6fd09
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c8c1c2dabb13393764ca8b1fd9c1a717b9e2527e
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="downloading-sample-databases-linq-to-dataset"></a><span data-ttu-id="91afe-102">下載範例資料庫 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="91afe-102">Downloading Sample Databases (LINQ to DataSet)</span></span>
<span data-ttu-id="91afe-103">範例和逐步解說中的[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]文件會使用 AdventureWorks 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="91afe-103">The samples and walkthroughs in the [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] documentation use the AdventureWorks sample database.</span></span> <span data-ttu-id="91afe-104">您可以從 Microsoft 下載網站免費下載這個產品。</span><span class="sxs-lookup"><span data-stu-id="91afe-104">You can download this product free of charge from the Microsoft download site.</span></span> <span data-ttu-id="91afe-105">[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 文件中的範例和逐步解說會使用 SQL Server 當做資料存放區。</span><span class="sxs-lookup"><span data-stu-id="91afe-105">The samples and walkthroughs in the [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] documentation use SQL Server as the data store.</span></span> <span data-ttu-id="91afe-106">除了 SQL Server 以外，可免費取得的 SQL Server Express Edition 也可以當做資料存放區使用。</span><span class="sxs-lookup"><span data-stu-id="91afe-106">SQL Server Express Edition, which is available without charge, can also be used as the data store instead of SQL Server.</span></span>  
  
## <a name="downloading-and-installing-the-adventureworks-database"></a><span data-ttu-id="91afe-107">下載和安裝 AdventureWorks 資料庫</span><span class="sxs-lookup"><span data-stu-id="91afe-107">Downloading and Installing the AdventureWorks Database</span></span>  
  
#### <a name="to-download-and-install-the-adventureworks-sample-database-for-sql-server"></a><span data-ttu-id="91afe-108">若要下載和安裝 SQL Server 的 AdventureWorks 範例資料庫</span><span class="sxs-lookup"><span data-stu-id="91afe-108">To download and install the AdventureWorks sample database for SQL Server</span></span>  
  
1.  <span data-ttu-id="91afe-109">開啟 Internet Explorer。</span><span class="sxs-lookup"><span data-stu-id="91afe-109">Open Internet Explorer.</span></span>  
  
2.  <span data-ttu-id="91afe-110">移至[SQL Server 2005 範例和範例資料庫](http://go.microsoft.com/fwlink/?linkid=31046)網站。</span><span class="sxs-lookup"><span data-stu-id="91afe-110">Go to the [SQL Server 2005 Samples and Sample Databases](http://go.microsoft.com/fwlink/?linkid=31046) Web site.</span></span>  
  
3.  <span data-ttu-id="91afe-111">請遵循指示進行，以便下載適用於您處理器類型的 AdventureWorks 範例資料庫 (例如 AdventureWorksDB.msi)，並將 .MSI 檔儲存至本機電腦。</span><span class="sxs-lookup"><span data-stu-id="91afe-111">Follow the instructions for downloading the AdventureWorks sample database for your processor type (such as AdventureWorksDB.msi), and save the .MSI file to your local computer.</span></span>  
  
4.  <span data-ttu-id="91afe-112">如果您先前已經透過下載或在 SQL Server 安裝期間安裝過舊版 AdventureWorks，就必須先移除它，然後再執行 AdventureWorks.msi。</span><span class="sxs-lookup"><span data-stu-id="91afe-112">If you have a previous version of AdventureWorks installed from the download or during the SQL Server setup, you must remove it before running AdventureWorks.msi.</span></span>  
  
#### <a name="to-remove-a-previous-download-of-an-adventureworks-sample-database"></a><span data-ttu-id="91afe-113">若要移除先前下載的 AdventureWorks 範例資料庫</span><span class="sxs-lookup"><span data-stu-id="91afe-113">To remove a previous download of an AdventureWorks sample database</span></span>  
  
1.  <span data-ttu-id="91afe-114">卸除 AdventureWorks 或 AdventureWorksDW 資料庫。</span><span class="sxs-lookup"><span data-stu-id="91afe-114">Drop the AdventureWorks or AdventureWorksDW database.</span></span>  
  
2.  <span data-ttu-id="91afe-115">從**新增或移除程式**，選取**AdventureWorksDB**或**AdventureWorksBI**按一下**移除**。</span><span class="sxs-lookup"><span data-stu-id="91afe-115">From **Add or Remove Programs**, select **AdventureWorksDB** or **AdventureWorksBI** and click **Remove**.</span></span>  
  
#### <a name="to-remove-an-adventureworks-sample-database-previously-installed-using-setup"></a><span data-ttu-id="91afe-116">若要移除先前使用安裝程式安裝的 AdventureWorks 範例資料庫</span><span class="sxs-lookup"><span data-stu-id="91afe-116">To remove an AdventureWorks sample database previously installed using Setup</span></span>  
  
1.  <span data-ttu-id="91afe-117">卸除 AdventureWorks 或 AdventureWorksDW 資料庫。</span><span class="sxs-lookup"><span data-stu-id="91afe-117">Drop the AdventureWorks or AdventureWorksDW database.</span></span>  
  
2.  <span data-ttu-id="91afe-118">從**新增或移除程式**，選取**Microsoft SQL Server 2005**按一下**變更**。</span><span class="sxs-lookup"><span data-stu-id="91afe-118">From **Add or Remove Programs**, select **Microsoft SQL Server 2005** and click **Change**.</span></span>  
  
3.  <span data-ttu-id="91afe-119">從**元件選擇**，選取**工作站元件**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="91afe-119">From **Component Selection**, select **Workstation Components** and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="91afe-120">從**歡迎使用 SQL Server 安裝精靈**，按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="91afe-120">From **Welcome to the SQL Server Installation Wizard**, click **Next**.</span></span>  
  
5.  <span data-ttu-id="91afe-121">從**系統組態檢查**，按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="91afe-121">From **System Configuration Check**, click **Next**.</span></span>  
  
6.  <span data-ttu-id="91afe-122">從**變更或移除執行個體**，按一下 **變更安裝的元件**。</span><span class="sxs-lookup"><span data-stu-id="91afe-122">From **Change or Remove Instance**, click **Change Installed Components**.</span></span>  
  
7.  <span data-ttu-id="91afe-123">從**特徵選取**，依序展開**文件、 範例和範例資料庫**節點。</span><span class="sxs-lookup"><span data-stu-id="91afe-123">From **Feature Selection**, expand the **Documentation, Samples, and Sample Databases** node.</span></span>  
  
8.  <span data-ttu-id="91afe-124">選取**範例程式碼和應用程式**。</span><span class="sxs-lookup"><span data-stu-id="91afe-124">Select **Sample Code and Applications**.</span></span> <span data-ttu-id="91afe-125">展開**範例資料庫**，選取要移除，然後選取的範例資料庫**整個功能將無法使用**。</span><span class="sxs-lookup"><span data-stu-id="91afe-125">Expand **Sample Databases**, select the sample database to be removed, and select **Entire feature will be unavailable**.</span></span> <span data-ttu-id="91afe-126">按 [ **下一步**]。</span><span class="sxs-lookup"><span data-stu-id="91afe-126">Click **Next**.</span></span>  
  
9. <span data-ttu-id="91afe-127">按一下**安裝**並完成安裝精靈。</span><span class="sxs-lookup"><span data-stu-id="91afe-127">Click **Install** and finish the installation wizard.</span></span>  
  
#### <a name="to-attach-the-adventureworks-sample-database-files-to-an-instance-of-sql-server"></a><span data-ttu-id="91afe-128">若要將 AdventureWorks 範例資料庫檔案附加至 SQL Server 的執行個體</span><span class="sxs-lookup"><span data-stu-id="91afe-128">To attach the AdventureWorks sample database files to an instance of SQL Server</span></span>  
  
1.  <span data-ttu-id="91afe-129">下載範例資料庫安裝程式檔案之後，按兩下**AdventureWorksDB.msi**檔案 （或您所下載的檔案） 來安裝資料庫。</span><span class="sxs-lookup"><span data-stu-id="91afe-129">After the file sample database installer file has downloaded, double-click the **AdventureWorksDB.msi** file (or the file you downloaded) to install the database.</span></span> <span data-ttu-id="91afe-130">根據預設，此資料庫會安裝在 c:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data。</span><span class="sxs-lookup"><span data-stu-id="91afe-130">By default, the database is installed at c:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data.</span></span>  
  
2.  <span data-ttu-id="91afe-131">執行下列指令碼 SQLCMD 或 SQL Server Management Studio，將 AdventureWorks 資料庫檔案附加至 SQL Server 的執行個體 (Instance)：</span><span class="sxs-lookup"><span data-stu-id="91afe-131">Attach the AdventureWorks database files to an instance of SQL Server by executing the following script SQLCMD or SQL Server Management Studio:</span></span>  
  
    ```  
    exec sp_attach_db @dbname=N'AdventureWorks', @filename1=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_Data.mdf', @filename2=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_log.ldf'  
    ```  
  
     <span data-ttu-id="91afe-132">如果您已將這些檔案安裝至不同的磁碟機或目錄，就必須先適當地修訂路徑，然後再執行 `sp_attach_db` 預存程序 (Stored Procedure)。</span><span class="sxs-lookup"><span data-stu-id="91afe-132">If you have installed these files to a different drive or directory, you must revise the paths appropriately before you execute the `sp_attach_db` stored procedure.</span></span>  
  
## <a name="downloading-sql-server-express-edition"></a><span data-ttu-id="91afe-133">下載 SQL Server Express Edition</span><span class="sxs-lookup"><span data-stu-id="91afe-133">Downloading SQL Server Express Edition</span></span>  
 <span data-ttu-id="91afe-134">範例和逐步解說中的[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]區段使用 SQL Server 2005 做為資料存放區，而改為使用 SQL Server Express Edition，則可修改。</span><span class="sxs-lookup"><span data-stu-id="91afe-134">The samples and walkthroughs in the [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] section use SQL Server 2005 as the data store but can be modified to use SQL Server Express Edition, instead.</span></span> <span data-ttu-id="91afe-135">SQL Server Express Edition 可免費取得，而且可以將它連同應用程式一起轉散發。</span><span class="sxs-lookup"><span data-stu-id="91afe-135">SQL Server Express Edition is available without charge, and you can redistribute it with applications.</span></span> <span data-ttu-id="91afe-136">如果您正使用 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]，SQL Server Express Edition 會隨附於專業版和更高階的版本中。</span><span class="sxs-lookup"><span data-stu-id="91afe-136">If you are using [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], SQL Server Express Edition is included in the Pro and higher editions.</span></span>  
  
#### <a name="to-download-and-install-sql-server-express-edition"></a><span data-ttu-id="91afe-137">若要下載並安裝 SQL Server Express Edition</span><span class="sxs-lookup"><span data-stu-id="91afe-137">To download and install SQL Server Express Edition</span></span>  
  
1.  <span data-ttu-id="91afe-138">啟動 Internet Explorer。</span><span class="sxs-lookup"><span data-stu-id="91afe-138">Start Internet Explorer.</span></span>  
  
2.  <span data-ttu-id="91afe-139">移至[Microsoft SQL Server 2005 Express 的 Edition](http://go.microsoft.com/fwlink/?LinkID=31070)下載頁面。</span><span class="sxs-lookup"><span data-stu-id="91afe-139">Go to the  [Microsoft SQL Server 2005 Express Edition](http://go.microsoft.com/fwlink/?LinkID=31070) download page.</span></span>  
  
3.  <span data-ttu-id="91afe-140">請遵循網站上的安裝指示進行。</span><span class="sxs-lookup"><span data-stu-id="91afe-140">Follow the installation instructions on the Web site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91afe-141">請參閱</span><span class="sxs-lookup"><span data-stu-id="91afe-141">See Also</span></span>  
 [<span data-ttu-id="91afe-142">快速入門</span><span class="sxs-lookup"><span data-stu-id="91afe-142">Getting Started</span></span>](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)
