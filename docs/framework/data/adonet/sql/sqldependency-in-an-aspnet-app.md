---
title: "ASP.NET 應用程式中的 SqlDependency | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ff226ce3-f6b5-47a1-8d22-dc78b67e07f5
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# ASP.NET 應用程式中的 SqlDependency
本節中的範例將顯示如何藉由使用 ASP.NET <xref:System.Web.Caching.SqlCacheDependency> 物件，間接使用 <xref:System.Data.SqlClient.SqlDependency>。  <xref:System.Web.Caching.SqlCacheDependency> 物件會使用 <xref:System.Data.SqlClient.SqlDependency> 來接聽通知並正確地更新快取。  
  
> [!NOTE]
>  如果執行[啟用查詢通知](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md)中的指令碼，則範例程式碼會假設您已啟用查詢通知。  
  
## 關於範例應用程式  
 此範例應用程式會使用單一 ASP.NET 網頁，在 <xref:System.Web.UI.WebControls.GridView> 控制項中顯示 **AdventureWorks** SQL Server 資料庫的產品資訊。  載入頁面時，此程式碼會將目前時間寫入 <xref:System.Web.UI.WebControls.Label> 控制項。  然後會定義 <xref:System.Web.Caching.SqlCacheDependency> 物件，並在 <xref:System.Web.Caching.Cache> 物件上設定屬性，以儲存快取資料長達三分鐘。  然後，此程式碼會連接到資料庫並擷取資料。  當頁面已載入而且應用程式正在執行時，ASP.NET 將從快取中擷取資料，而且您可以注意頁面上的時間沒有變更來確認這點。  如果正在監視的資料有變更，ASP.NET 會讓快取無效並將新資料重新填入 `GridView` 控制項，而且更新 `Label` 控制項中顯示的時間。  
  
## 建立範例應用程式  
 請遵循下列步驟來建立並執行範例應用程式：  
  
1.  建立新的 ASP.NET 網站。  
  
2.  將 <xref:System.Web.UI.WebControls.Label> 和 <xref:System.Web.UI.WebControls.GridView> 控制項加入至 Default.aspx 頁面。  
  
3.  開啟頁面的類別模組，並加入下列指示詞：  
  
    ```vb  
  
    Option Strict On  
    Option Explicit On  
  
    Imports System.Data.SqlClient  
    ```  
  
    ```csharp  
    using System.Data.SqlClient;  
    using System.Web.Caching;  
    ```  
  
4.  將下列程式碼加入至頁面的 `Page_Load` 事件：  
  
     [!code-csharp[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#1)]
     [!code-vb[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#1)]  
  
5.  加入兩個 Helper 方法：`GetConnectionString` 及 `GetSQL`。  定義的連接字串會使用整合安全性。  您需要驗證所使用之帳戶具有必要的資料庫使用權限，且範例資料庫 **AdventureWorks** 已啟用通知。  如需詳細資訊，請參閱[Special Considerations When Using Query Notifications](http://msdn.microsoft.com/zh-tw/a83c8dc8-4fb9-4ffd-a2a5-c07cf4a203c7)。  
  
     [!code-csharp[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#2)]
     [!code-vb[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#2)]  
  
### 測試應用程式  
 應用程式會快取顯示在 Web Form 上的資料，並每隔三分鐘重新整理它一次 \(如果沒有任何活動的話\)。  如果資料庫發生變更，就會立即重新整理快取。  從 Visual Studio 執行應用程式，以便將頁面載入瀏覽器。  顯示的快取重新整理時間表示上次重新整理快取的時間。  等候三分鐘，然後重新整理頁面，以便發生回傳事件。  請注意，顯示在頁面上的時間已經變更。  如果您在三分鐘以內便重新整理頁面，顯示在頁面上的時間將維持不變。  
  
 現在，請使用 Transact\-SQL UPDATE 命令來更新資料庫中的資料，並重新整理頁面。  此時顯示的時間表示已使用資料庫的新資料來重新整理快取。  請注意，雖然快取已更新，但是顯示在頁面上的時間要等到發生回傳事件之後才會變更。  
  
## 請參閱  
 [SQL Server 中的查詢通知](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)