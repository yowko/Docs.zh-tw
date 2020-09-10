---
title: ASP.NET 應用程式中的 SqlDependency
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ff226ce3-f6b5-47a1-8d22-dc78b67e07f5
ms.openlocfilehash: 2ec9415f63151443d5008fbce471fabeb89cdb91
ms.sourcegitcommit: 1e8382d0ce8b5515864f8fbb178b9fd692a7503f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2020
ms.locfileid: "89656167"
---
# <a name="sqldependency-in-an-aspnet-application"></a>ASP.NET 應用程式中的 SqlDependency
此節的範例示範如何利用 ASP.NET <xref:System.Web.Caching.SqlCacheDependency> 物件，間接使用 <xref:System.Data.SqlClient.SqlDependency>。 <xref:System.Web.Caching.SqlCacheDependency> 物件會使用 <xref:System.Data.SqlClient.SqlDependency> 來接聽通知，並正確更新快取。  
  
> [!NOTE]
> 範例程式碼假設您已啟用查詢通知，方法是在 [啟用查詢通知](enabling-query-notifications.md)的情況下執行腳本。  
  
## <a name="about-the-sample-application"></a>關於範例應用程式  
 此範例應用程式會使用單一 ASP.NET 網頁，在 <xref:System.Web.UI.WebControls.GridView> 控制項中顯示 **AdventureWorks** SQL Server 資料庫的產品資訊。 當頁面載入時，程式碼會將目前的時間寫入至 <xref:System.Web.UI.WebControls.Label> 控制項。 然後會定義 <xref:System.Web.Caching.SqlCacheDependency> 物件，並在 <xref:System.Web.Caching.Cache> 物件上設定屬性，以儲存快取資料長達三分鐘。 然後，程式碼會連線到資料庫並擷取資料。 當頁面載入且應用程式正在執行時，ASP.NET 將從快取中擷取資料，您可以透過注意頁面上的時間不會變更來驗證這一點。 如果監視的資料變更，ASP.NET 就會讓快取失效，並以全新的資料重新填入 `GridView` 控制項，進而更新 `Label` 控制項中顯示的時間。  
  
## <a name="creating-the-sample-application"></a>建立範例應用程式  
 遵循下列步驟，以建立並執行範例應用程式：  
  
1. 建立新的 ASP.NET 網站。  
  
2. 將 <xref:System.Web.UI.WebControls.Label> 和 <xref:System.Web.UI.WebControls.GridView> 控制項新增至 Default.aspx 頁面。  
  
3. 開啟頁面的類別模組並新增下列指示詞：  
  
    ```vb  
    Option Strict On  
    Option Explicit On  
  
    Imports System.Data.SqlClient  
    ```  
  
    ```csharp  
    using System.Data.SqlClient;  
    using System.Web.Caching;  
    ```  
  
4. 在頁面的 `Page_Load` 事件中新增下列程式碼：  
  
     [!code-csharp[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#1)]
     [!code-vb[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#1)]  
  
5. 新增兩個協助程式方法：`GetConnectionString` 和 `GetSQL`。 定義的連接字串會使用整合式安全性。 您需要驗證所使用的帳戶具有必要的資料庫使用權限，且範例資料庫 **AdventureWorks** 已啟用通知。
  
     [!code-csharp[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#2)]
     [!code-vb[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#2)]  
  
### <a name="testing-the-application"></a>測試應用程式  
 應用程式會快取 Web 表單上顯示的資料，如果沒有任何活動，則每隔三分鐘就會重新整理一次。 如果資料庫發生變更，就會立即重新整理快取。 從 Visual Studio 執行應用程式，以將頁面載入瀏覽器。 顯示的快取重新整理時間表示上次重新整理快取的時間。 等候三分鐘，然後重新整理頁面，即會導致回傳事件發生。 請注意，頁面上顯示的時間已經變更。 如果您在三分鐘內重新整理頁面，則頁面上顯示的時間將維持不變。  
  
 現在，使用 Transact-SQL UPDATE 命令來更新資料庫中的資料，並重新整理頁面。 顯示的時間現在表示已使用資料庫的新資料來重新整理快取。 請注意，雖然快取已更新，但在發生回傳事件之前，頁面上顯示的時間不會變更。  

## <a name="distributed-cache-synchronization-using-sql-dependency"></a>使用 SQL 相依性的分散式快取同步處理

某些協力廠商分散式快取（例如 [NCache](https://www.alachisoft.com/ncache) ）提供使用 [sql](https://www.alachisoft.com/resources/docs/ncache/prog-guide/sql-dependency.html)相依性來同步處理 SQL database 和快取的支援。 如需詳細資訊和原始程式碼執行範例，請參閱 [分散式](https://github.com/Alachisoft/NCache-Samples/tree/master/dotnet/Dependencies/SQLDependency)快取 SQL 相依性範例。

## <a name="see-also"></a>另請參閱

- [SQL Server 中的查詢通知](query-notifications-in-sql-server.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
