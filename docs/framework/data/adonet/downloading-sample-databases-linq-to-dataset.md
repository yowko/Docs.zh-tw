---
title: "下載範例資料庫 (LINQ to DataSet) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eb42a7af-d410-4b7f-b4a8-13c72ce6fd09
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 下載範例資料庫 (LINQ to DataSet)
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 文件中的範例和逐步解說都會使用 AdventureWorks 範例資料庫。  您可以從 Microsoft 下載網站免費下載這個產品。[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 文件中的範例和逐步解說會使用 SQL Server 當做資料存放區。  除了 SQL Server 以外，可免費取得的 SQL Server Express Edition 也可以當做資料存放區使用。  
  
## 下載和安裝 AdventureWorks 資料庫  
  
#### 若要下載和安裝 SQL Server 的 AdventureWorks 範例資料庫  
  
1.  開啟 Internet Explorer。  
  
2.  請移至 [SQL Server 2005 範例和範例資料庫](http://go.microsoft.com/fwlink/?linkid=31046) 網站 \(英文\)。  
  
3.  請遵循指示進行，以便下載適用於您處理器類型的 AdventureWorks 範例資料庫 \(例如 AdventureWorksDB.msi\)，並將 .MSI 檔儲存至本機電腦。  
  
4.  如果您先前已經透過下載或在 SQL Server 安裝期間安裝過舊版 AdventureWorks，就必須先移除它，然後再執行 AdventureWorks.msi。  
  
#### 若要移除先前下載的 AdventureWorks 範例資料庫  
  
1.  卸除 AdventureWorks 或 AdventureWorksDW 資料庫。  
  
2.  在 \[**新增或移除程式**\] 中，選取 \[**AdventureWorksDB**\] 或 \[**AdventureWorksBI**\]，然後按一下 \[**移除**\]。  
  
#### 若要移除先前使用安裝程式安裝的 AdventureWorks 範例資料庫  
  
1.  卸除 AdventureWorks 或 AdventureWorksDW 資料庫。  
  
2.  在 \[**新增或移除程式**\] 中，選取 \[**Microsoft SQL Server 2005**\]，然後按一下 \[**變更**\]。  
  
3.  在 \[**元件選擇**\] 中，選取 \[**工作站元件**\]，然後按 \[**下一步**\]。  
  
4.  在 \[**歡迎使用 SQL Server 安裝精靈**\] 中，按 \[**下一步**\]。  
  
5.  在 \[**系統組態檢查**\] 中，按 \[**下一步**\]。  
  
6.  在 \[**變更或移除執行個體**\] 中，按一下 \[**變更安裝的元件**\]。  
  
7.  在 \[**功能選擇**\] 中，展開 \[**文件集、範例和範例資料庫**\] 節點。  
  
8.  選取 \[**範例程式碼和應用程式**\]。  展開 \[**範例資料庫**\]、選取要移除的範例資料庫，然後選取 \[**完整功能將無法使用**\]。  按 \[**下一步**\]。  
  
9. 按一下 \[**安裝**\] 並完成安裝精靈。  
  
#### 若要將 AdventureWorks 範例資料庫檔案附加至 SQL Server 的執行個體  
  
1.  在範例資料庫安裝程式檔案下載完成之後，請按兩下 **AdventureWorksDB.msi** 檔 \(或您所下載的檔案\) 即可安裝資料庫。  根據預設，此資料庫會安裝在 c:\\Program Files\\Microsoft SQL Server\\MSSQL.1\\MSSQL\\Data。  
  
2.  執行下列指令碼 SQLCMD 或 SQL Server Management Studio，將 AdventureWorks 資料庫檔案附加至 SQL Server 的執行個體 \(Instance\)：  
  
    ```  
    exec sp_attach_db @dbname=N'AdventureWorks', @filename1=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_Data.mdf', @filename2=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_log.ldf'  
    ```  
  
     如果您已將這些檔案安裝至不同的磁碟機或目錄，就必須先適當地修訂路徑，然後再執行 `sp_attach_db` 預存程序 \(Stored Procedure\)。  
  
## 下載 SQL Server Express Edition  
 雖然 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 章節中的範例和逐步解說會使用 SQL Server 2005 當做資料存放區，但是您可以將它修改成改用 SQL Server Express Edition。  SQL Server Express Edition 可免費取得，而且可以將它連同應用程式一起轉散發。  如果您正使用 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]，SQL Server Express Edition 會隨附於專業版和更高階的版本中。  
  
#### 若要下載並安裝 SQL Server Express Edition  
  
1.  啟動 Internet Explorer。  
  
2.  移至 [Microsoft SQL Server 2005 Express Edition](http://go.microsoft.com/fwlink/?LinkID=31070) 下載頁面。  
  
3.  請遵循網站上的安裝指示進行。  
  
## 請參閱  
 [使用者入門](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)