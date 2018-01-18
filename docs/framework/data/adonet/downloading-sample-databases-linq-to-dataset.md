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
# <a name="downloading-sample-databases-linq-to-dataset"></a>下載範例資料庫 (LINQ to DataSet)
範例和逐步解說中的[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]文件會使用 AdventureWorks 範例資料庫。 您可以從 Microsoft 下載網站免費下載這個產品。 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 文件中的範例和逐步解說會使用 SQL Server 當做資料存放區。 除了 SQL Server 以外，可免費取得的 SQL Server Express Edition 也可以當做資料存放區使用。  
  
## <a name="downloading-and-installing-the-adventureworks-database"></a>下載和安裝 AdventureWorks 資料庫  
  
#### <a name="to-download-and-install-the-adventureworks-sample-database-for-sql-server"></a>若要下載和安裝 SQL Server 的 AdventureWorks 範例資料庫  
  
1.  開啟 Internet Explorer。  
  
2.  移至[SQL Server 2005 範例和範例資料庫](http://go.microsoft.com/fwlink/?linkid=31046)網站。  
  
3.  請遵循指示進行，以便下載適用於您處理器類型的 AdventureWorks 範例資料庫 (例如 AdventureWorksDB.msi)，並將 .MSI 檔儲存至本機電腦。  
  
4.  如果您先前已經透過下載或在 SQL Server 安裝期間安裝過舊版 AdventureWorks，就必須先移除它，然後再執行 AdventureWorks.msi。  
  
#### <a name="to-remove-a-previous-download-of-an-adventureworks-sample-database"></a>若要移除先前下載的 AdventureWorks 範例資料庫  
  
1.  卸除 AdventureWorks 或 AdventureWorksDW 資料庫。  
  
2.  從**新增或移除程式**，選取**AdventureWorksDB**或**AdventureWorksBI**按一下**移除**。  
  
#### <a name="to-remove-an-adventureworks-sample-database-previously-installed-using-setup"></a>若要移除先前使用安裝程式安裝的 AdventureWorks 範例資料庫  
  
1.  卸除 AdventureWorks 或 AdventureWorksDW 資料庫。  
  
2.  從**新增或移除程式**，選取**Microsoft SQL Server 2005**按一下**變更**。  
  
3.  從**元件選擇**，選取**工作站元件**，然後按一下 **下一步**。  
  
4.  從**歡迎使用 SQL Server 安裝精靈**，按一下 **下一步**。  
  
5.  從**系統組態檢查**，按一下 **下一步**。  
  
6.  從**變更或移除執行個體**，按一下 **變更安裝的元件**。  
  
7.  從**特徵選取**，依序展開**文件、 範例和範例資料庫**節點。  
  
8.  選取**範例程式碼和應用程式**。 展開**範例資料庫**，選取要移除，然後選取的範例資料庫**整個功能將無法使用**。 按 [ **下一步**]。  
  
9. 按一下**安裝**並完成安裝精靈。  
  
#### <a name="to-attach-the-adventureworks-sample-database-files-to-an-instance-of-sql-server"></a>若要將 AdventureWorks 範例資料庫檔案附加至 SQL Server 的執行個體  
  
1.  下載範例資料庫安裝程式檔案之後，按兩下**AdventureWorksDB.msi**檔案 （或您所下載的檔案） 來安裝資料庫。 根據預設，此資料庫會安裝在 c:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data。  
  
2.  執行下列指令碼 SQLCMD 或 SQL Server Management Studio，將 AdventureWorks 資料庫檔案附加至 SQL Server 的執行個體 (Instance)：  
  
    ```  
    exec sp_attach_db @dbname=N'AdventureWorks', @filename1=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_Data.mdf', @filename2=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_log.ldf'  
    ```  
  
     如果您已將這些檔案安裝至不同的磁碟機或目錄，就必須先適當地修訂路徑，然後再執行 `sp_attach_db` 預存程序 (Stored Procedure)。  
  
## <a name="downloading-sql-server-express-edition"></a>下載 SQL Server Express Edition  
 範例和逐步解說中的[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]區段使用 SQL Server 2005 做為資料存放區，而改為使用 SQL Server Express Edition，則可修改。 SQL Server Express Edition 可免費取得，而且可以將它連同應用程式一起轉散發。 如果您正使用 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]，SQL Server Express Edition 會隨附於專業版和更高階的版本中。  
  
#### <a name="to-download-and-install-sql-server-express-edition"></a>若要下載並安裝 SQL Server Express Edition  
  
1.  啟動 Internet Explorer。  
  
2.  移至[Microsoft SQL Server 2005 Express 的 Edition](http://go.microsoft.com/fwlink/?LinkID=31070)下載頁面。  
  
3.  請遵循網站上的安裝指示進行。  
  
## <a name="see-also"></a>請參閱  
 [快速入門](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)
