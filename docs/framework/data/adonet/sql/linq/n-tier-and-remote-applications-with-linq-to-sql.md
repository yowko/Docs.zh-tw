---
title: 多層式架構和遠端應用程式以及 LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 854a1cdd-53cb-45f5-83ca-63962a9b3598
ms.openlocfilehash: 7af17500df9a0038ac4fa1eb3ad07a4c07190fa0
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43384256"
---
# <a name="n-tier-and-remote-applications-with-linq-to-sql"></a>多層式架構和遠端應用程式以及 LINQ to SQL
您可以建立使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的 N-Tier 或多層應用程式。 一般而言，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]資料內容、 實體類別和查詢建構邏輯位於中介層上為資料存取層 (DAL)。 商務邏輯以及任何非持續性資料則可完全實作在實體的部分類別和方法和資料內容，或可以實作在另外的類別中。  
  
 用戶端或展示層會在中介層的遠端介面上呼叫方法，而該層上的 DAL 將執行對應到 <xref:System.Data.Linq.DataContext> 方法的查詢或預存程序。 中介層一般會將資料以實體或 Proxy 物件的 XML 表示傳回用戶端。  
  
 在中介層上，實體是由資料內容建立的，資料內容會追蹤其狀態，以及管理資料庫的延後載入和提交變更。 這些實體會「附加」到 `DataContext`。 不過，實體在透過序列化 (Serialization) 傳送到另一層之後，就會中斷連結，表示 `DataContext` 不再追蹤其狀態。 用戶端傳回進行更新的實體必須重新附加到資料內容，如此 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 才能將變更提交至資料庫。 在開放式並行存取檢查需要的情況下，用戶端會負責將原始值和/或時間戳記送回中介層。  
  
 在 ASP.NET 應用程式中，<xref:System.Web.UI.WebControls.LinqDataSource> 會負責這其中大多數複雜的作業。 如需詳細資訊，請參閱 < [NIB: LinqDataSource Web Server Control Overview](https://msdn.microsoft.com/library/104cfc3f-7385-47d3-8a51-830dfa791136)。  
  
## <a name="additional-resources"></a>其他資源  
 如需如何實作使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的 N-Tier 應用程式，請參閱下列主題：  
  
-   [使用 ASP.NET 的 LINQ to SQL 多層式架構](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-aspnet.md)  
  
-   [使用 Web 服務的 LINQ to SQL 多層式架構](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-web-services.md)  
  
-   [LINQ to SQL 搭配緊密結合的用戶端-伺服器應用程式](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-with-tightly-coupled-client-server-applications.md)  
  
-   [實作多層式架構商務邏輯](../../../../../../docs/framework/data/adonet/sql/linq/implementing-business-logic-linq-to-sql.md)  
  
-   [多層式架構應用程式中的資料擷取和 CUD 作業 (LINQ to SQL)](../../../../../../docs/framework/data/adonet/sql/linq/data-retrieval-and-cud-operations-in-n-tier-applications.md)  
  
 如需有關使用 ADO.NET 資料集的多層式架構應用程式的詳細資訊，請參閱 <<c0> [ 使用多層式架構應用程式中的資料集](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications)。  
  
## <a name="see-also"></a>另請參閱  
 [背景資訊](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
