---
title: LINQ to SQL 多層式架構與 Web 服務
ms.date: 03/30/2017
ms.assetid: 9cb10eb8-957f-4beb-a271-5f682016fed2
ms.openlocfilehash: e621063a2bd38b8ed473b8092c65a2aa9a645511
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/12/2019
ms.locfileid: "56092718"
---
# <a name="linq-to-sql-n-tier-with-web-services"></a>LINQ to SQL 多層式架構與 Web 服務
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 被專為中介層，例如 Web 服務鬆散結合的資料存取層 (DAL) 上使用。 如果展示層是 ASP.NET 網頁，那麼您可以使用 <xref:System.Web.UI.WebControls.LinqDataSource> Web 伺服器控制項，管理使用者介面與中介層上的 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 之間的資料傳輸。 如果展示層不是 ASP.NET 網頁，則中介層和展示層都必須額外執行一些工作，以管理資料的序列化 (Serialization) 和還原序列化 (Deserialization)。  
  
## <a name="setting-up-linq-to-sql-on-the-middle-tier"></a>設定中介層上的 LINQ to SQL  
 在 Web 服務或 N-Tier 應用程式中，中介層包含資料內容和實體類別。 您可以手動建立這些類別，或者使用 SQLMetal.exe 或[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]建立類別 (如文件他處所述)。 在設計階段，您可以選擇是否要將實體類別設為可序列化。 如需詳細資訊，請參閱[＜How to：讓實體可序列化](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md)。 另一個選擇是另外建立一組類別來封裝要序列化的資料，然後當您在 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] 查詢中傳回資料時，投影到這些可序列化的型別中。  
  
 您接著可以定義介面以及用戶端將呼叫來擷取、插入和更新資料的方法。 這些介面方法會包裝您的 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] 查詢。 您可以使用任何一種序列化機制來處理遠端方法呼叫和序列化資料。 唯一的要求是，如果物件模型中存在循環或雙向關係，例如標準 Northwind 物件模型中的 Customers 與 Orders 之間的關係，那麼就必須使用支援此關係的序列化程式。 Windows Communication Foundation (WCF) <xref:System.Runtime.Serialization.DataContractSerializer> 支援雙向關聯性，但用於非 WCF Web 服務的 XmlSerializer 則否。 如果您選擇使用 XmlSerializer，就必須確定物件模型沒有循環關聯性。  
  
 如需有關 Windows Communication Foundation 的詳細資訊，請參閱 < [Windows Communication Foundation 服務和 Visual Studio 中的 WCF Data Services](/visualstudio/data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio)。  
  
 在 <xref:System.Data.Linq.DataContext> 和實體類別上使用部分類別和方法連結 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 執行階段事件，以實作商務規則 (Business Rule) 或定義域特定邏輯。 如需詳細資訊，請參閱 <<c0> [ 實作多層式架構商務邏輯](../../../../../../docs/framework/data/adonet/sql/linq/implementing-business-logic-linq-to-sql.md)。  
  
## <a name="defining-the-serializable-types"></a>定義可序列化的型別  
 用戶端或展示層必須有將從中介層接收之類別的型別定義。 這些型別可以是實體類別本身，也可以是特殊類別，其中只包裝實體類別中用以遠端處理的特定欄位。 在任何情況下，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]一概不管展示層如何取得這些型別定義的相關。 例如，展示層可以使用 WCF 自動產生型別，或可以在 DLL 複本中定義這些型別，甚或是可以定義自己的型別版本。  
  
## <a name="retrieving-and-inserting-data"></a>擷取和插入資料  
 中介層會定義介面，而此介面會指定展示層要如何存取資料。 例如 `GetProductByID(int productID)` 或 `GetCustomers()`。 在中介層上，方法主體通常會建立新的 <xref:System.Data.Linq.DataContext> 執行個體，然後對它的一個或多個資料表執行查詢。 中介層接著會以 <xref:System.Collections.Generic.IEnumerable%601> 傳回結果，其中 `T` 是實體類別或其他用來序列化的型別。 展示層絕不會直接傳送查詢變數給中介層，或直接從中介層接收查詢變數。 這兩層會交換值、物件和具體資料集合。 在收到集合之後，如有需要，展示層就可使用 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] to Objects 來查詢它。  
  
 插入資料時，展示層可建構新物件並將它傳送到中介層，或可以讓中介層根據其所提供的值建構物件。 一般來說，在 N-Tier 應用程式中擷取和插入資料，與在 2 層應用程式中的程序沒有太大差異。 如需詳細資訊，請參閱 <<c0> [ 查詢資料庫](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)並[制定和提交資料變更](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)。  
  
## <a name="tracking-changes-for-updates-and-deletes"></a>追蹤變更以更新和刪除  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 支援以時間戳記為基礎的開放式並行存取 (Optimistic Concurrency) (也稱為 RowVersions) 和以原始值為基礎的開放式並行存取。 如果資料庫資料表有時間戳記，則更新和刪除無論在中介層或展示層都不需要額外工作。 不過，如果必須使用原始值來進行開放式並行存取檢查，那麼展示層就必須負責追蹤這些值，並在更新時送回這些值。 這是因為對展示層上的實體所做的變更並不會在中介層上追蹤。 事實上，原始擷取實體的動作與最後更新它的動作，通常是由兩個完全不同的 <xref:System.Data.Linq.DataContext> 執行個體所執行。  
  
 展示層所做的變更愈多，追蹤這些變更並封裝送回中介層的工作就愈複雜。 溝通變更的機制如何實作，端視應用程式而定。 唯一的要求是，開放式並行存取檢查所需的這些原始值必須提供給 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]。  
  
 如需詳細資訊，請參閱 <<c0> [ 資料擷取和 CUD 作業 (LINQ to SQL) 的多層式架構應用程式中](../../../../../../docs/framework/data/adonet/sql/linq/data-retrieval-and-cud-operations-in-n-tier-applications.md)。  
  
## <a name="see-also"></a>另請參閱
- [使用 LINQ to SQL 的多層式架構和遠端應用程式](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)
- [LinqDataSource Web 伺服器控制項概觀](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100))
