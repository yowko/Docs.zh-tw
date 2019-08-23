---
title: 常見問題集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 252ed666-0679-4eea-b71b-2f14117ef443
ms.openlocfilehash: 4b06ebd5b77331d63fc250a91a72c553ec2b737f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950350"
---
# <a name="frequently-asked-questions"></a>常見問題集
下列各節將解答實作 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] 時可能會遇到的一些常見問題。  
  
 [疑難排解](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md)中有其他問題可解決。  
  
## <a name="cannot-connect"></a>無法連接  
 問： 我無法連接到資料庫。  
  
 答： 請確定您的連接字串正確, 且您的 SQL Server 實例正在執行。 另外也請注意，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 需要具名管道 (Named Pipe) 通訊協定才能啟用。 如需詳細資訊, 請參閱[依逐步解說學習](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)。  
  
## <a name="changes-to-database-lost"></a>遺失對資料庫所做的變更  
 問： 我變更了資料庫中的資料，但重新執行應用程式時，變更不見了。  
  
 答： 請確定您呼叫 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 來儲存結果到資料庫。  
  
## <a name="database-connection-open-how-long"></a>資料庫連接:要開啟多久？  
 問： 我的資料庫連接會維持開啟的狀態多久？  
  
 答： 連接通常會一直維持開啟的狀態，直到您使用查詢結果為止。 如果您預期會花時間處理所有結果，而且也不反對快取結果，請將 <xref:System.Linq.Enumerable.ToList%2A> 套用到查詢。 在每個物件只處理一次的常見情況中，在 `DataReader` 和 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中使用資料流 (Streaming) 模型較有利。  
  
 連接使用方式的確切詳細資訊會取決於下列各項：  
  
- 連接狀態 (如果 <xref:System.Data.Linq.DataContext> 是使用連接物件建構的)。  
  
- 連接字串設定 (例如，啟用 Multiple Active Result Set (MARS)。 如需詳細資訊，請參閱 [Multiple Active Result Sets (MARS)](../../../../../../docs/framework/data/adonet/sql/multiple-active-result-sets-mars.md)。  
  
## <a name="updating-without-querying"></a>更新但不查詢  
 問： 我可以不先查詢資料庫，就更新資料表資料嗎？  
  
 答： 雖然 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 沒有以設定為基礎的更新命令，不過您可以使用下列其中一種方式，就可以不先查詢即更新。  
  
- 使用 <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> 傳送 SQL 程式碼。  
  
- 建立物件的新執行個體，然後初始化所有影響更新的目前值 (欄位)。 接著使用 <xref:System.Data.Linq.DataContext> 附加物件至 <xref:System.Data.Linq.Table%601.Attach%2A>，然後修改要變更的欄位。  
  
## <a name="unexpected-query-results"></a>未預期的查詢結果  
 問： 我的查詢傳回未預期的結果。 我該如何檢查發生了什麼狀況？  
  
 答： [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 提供多項工具來檢查它所產生的 SQL 程式碼。 最重要的其中一項工具就是 <xref:System.Data.Linq.DataContext.Log%2A>。 如需詳細資訊, 請參閱[偵錯工具支援](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)。  
  
## <a name="unexpected-stored-procedure-results"></a>未預期的預存程序結果  
 問： 我有一個預存程序，它的傳回值是由 `MAX()` 計算的。 當我將預存程式拖曳至 O/R 設計工具介面時, 傳回值不正確。  
  
 答： [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 提供兩種方式來藉由預存程序傳回資料庫產生的值。  
  
- 藉由命名輸出結果。  
  
- 藉由明確指定輸出參數。  
  
 下面是輸出不正確的範例。 由於 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 無法對應結果，因此永遠會傳回 0：  
  
 `create procedure proc2`  
  
 `as`  
  
 `begin`  
  
 `select max(i) from t where name like 'hello'`  
  
 `end`  
  
 下面是使用輸出參數時，輸出正確的範例：  
  
 `create procedure proc2`  
  
 `@result int OUTPUT`  
  
 `as`  
  
 `select @result = MAX(i) from t where name like 'hello'`  
  
 `go`  
  
 下面是藉由命名輸出結果，輸出正確的範例：  
  
 `create procedure proc2`  
  
 `as`  
  
 `begin`  
  
 `select nax(i) AS MaxResult from t where name like 'hello'`  
  
 `end`  
  
 如需詳細資訊, 請參閱[使用預存程式自訂作業](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md)。  
  
## <a name="serialization-errors"></a>序列化錯誤  
 問： 當我嘗試序列化時, 收到下列錯誤:"ChangeTracker + 別 standardchangetracker" 的 "Type..。未標示為可序列化。」  
  
 答： [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中的程式碼產生支援 <xref:System.Runtime.Serialization.DataContractSerializer> 序列化。 但不支援 <xref:System.Xml.Serialization.XmlSerializer> 或 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>。 如需詳細資訊，請參閱[序列化](../../../../../../docs/framework/data/adonet/sql/linq/serialization.md)。  
  
## <a name="multiple-dbml-files"></a>多個 DBML 檔案  
 問： 當有多個 DBML 檔案共用一些資料表時，會發生編譯器錯誤。  
  
 答： 將 [**內容命名空間**] 和 [**實體命名空間**] 屬性從物件關聯式設計工具設定為每個 DBML 檔案的相異值。 這就可避免名稱/命名空間發生衝突。  
  
## <a name="avoiding-explicit-setting-of-database-generated-values-on-insert-or-update"></a>避免在插入或更新時明確設定資料庫產生的值  
 問： 我的資料庫資料表有個 `DateCreated` 資料行，它預設為 SQL `Getdate()`。 當我嘗試使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 插入新的資料錄時，值會設成 `NULL`。 但我本來預期它會設成資料庫預設值。  
  
 答： [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會自動針對識別 (自動遞增)、rowguidcol (資料庫產生的 GUID) 和時間戳記資料行處理這種情況。 在其他情況下, 您應該手動<xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>設定<xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> = `true` =和<xref:System.Data.Linq.Mapping.AutoSync.Always> / 屬性。/ <xref:System.Data.Linq.Mapping.AutoSync.OnInsert> <xref:System.Data.Linq.Mapping.AutoSync.OnUpdate>  
  
## <a name="multiple-dataloadoptions"></a>多個 DataLoadOptions  
 問： 我可以指定其他載入選項，而不覆寫第一個載入選項嗎？  
  
 答： 是的。 如下列範例所示，第一個選項不會被覆寫：  
  
```vb  
Dim dlo As New DataLoadOptions()  
dlo.LoadWith(Of Order)(Function(o As Order) o.Customer)  
dlo.LoadWith(Of Order)(Function(o As Order) o.OrderDetails)  
```  
  
```csharp  
DataLoadOptions dlo = new DataLoadOptions();  
dlo.LoadWith<Order>(o => o.Customer);  
dlo.LoadWith<Order>(o => o.OrderDetails);  
```  
  
## <a name="errors-using-sql-compact-35"></a>使用 SQL Compact 3.5 時發生錯誤  
 問： 當我將資料表從 SQL Server Compact 3.5 資料庫拖曳出來時, 出現錯誤。  
  
 答： 雖然[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]執行時間會執行, 但物件關聯式設計工具不支援 SQL Server Compact 3.5。 在此情況下，您必須建立自己的實體類別，然後加入適當的屬性。  
  
## <a name="errors-in-inheritance-relationships"></a>繼承關係發生錯誤  
 問： 我使用物件關聯式設計工具中的 [工具箱繼承] 圖形來連接兩個實體, 但卻收到錯誤。  
  
 答： 光是建立關係還不夠。 您還必須提供資訊，例如鑑別子資料行、基底類別鑑別子值以及衍生類別鑑別子值。  
  
## <a name="provider-model"></a>提供者模型  
 問： 是否有公用提供者模型可供使用？  
  
 答： 沒有公用提供者模型可以使用。 目前僅[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]支援 SQL Server 和 SQL Server Compact 3.5。  
  
## <a name="sql-injection-attacks"></a>SQL 插入攻擊  
 問： [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 如何保護不受 SQL 插入攻擊？  
  
 答： 對於以串連使用者輸入形成的傳統 SQL 查詢來說，SQL 插入一直是相當重大的風險。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 藉由在查詢中使用 <xref:System.Data.SqlClient.SqlParameter>，可避免這類插入。 使用者輸入會轉換成參數值。 如此一來，惡意命令就無法藉由客戶輸入來使用。  
  
## <a name="changing-read-only-flag-in-dbml-files"></a>變更 DBML 檔案中的唯讀旗標  
 問： 從 DBML 檔案建立物件模型時，要如何排除部分屬性的 setter？  
  
 答： 在這種進階案例中，請採取下列步驟：  
  
1. 在 .dbml 檔案中，藉由將 <xref:System.Data.Linq.ITable.IsReadOnly%2A> 旗標變更為 `True`，以修改屬性。  
  
2. 加入部分類別。 針對唯讀成員建立含參數的建構函式。  
  
3. 檢視預設 <xref:System.Data.Linq.Mapping.UpdateCheck> 值 (<xref:System.Data.Linq.Mapping.UpdateCheck.Never>)，判斷它是否為應用程式的正確值。  
  
    > [!CAUTION]
    >  如果您在 Visual Studio 中使用物件關聯式設計工具, 您的變更可能會遭到覆寫。  
  
## <a name="aptca"></a>APTCA  
 問： System.Data.Linq 是否標示為供部分信任的程式碼使用？  
  
 答： 是, system.object 元件是以<xref:System.Security.AllowPartiallyTrustedCallersAttribute>屬性標記的 .NET Framework 元件中。 若沒有這個標記, .NET Framework 中的元件僅供完全信任的程式碼使用。  
  
 中[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]允許部分信任的呼叫端的主要案例, 是為了[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]讓該元件能夠從 Web 應用程式存取, 其中的*信任*設定為「中」。  
  
## <a name="mapping-data-from-multiple-tables"></a>對應多個資料表的資料  
 問： 我的實體中的資料來自於多個資料表。 我該如何對應這些資料？  
  
 答： 您可以在資料庫中建立檢視，然後將實體對應到該檢視。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會針對檢視產生與資料表相同的 SQL。  
  
> [!NOTE]
> 在這種情況下使用檢視會有限制。 此方式在基礎檢視支援 <xref:System.Data.Linq.Table%601> 上所執行的作業時最安全。 只有您才知道會執行哪些作業。 例如, 大部分的應用程式都是唯讀的, 而另一個相當大`Create`號碼只會針對 views 使用預存程式來執行/ / `Update` `Delete`作業。  
  
## <a name="connection-pooling"></a>連接共用  
 問： 是否有可方便 <xref:System.Data.Linq.DataContext> 共用的建構？  
  
 答： 請不要嘗試重複使用 <xref:System.Data.Linq.DataContext> 的執行個體。 每個 <xref:System.Data.Linq.DataContext> 都會維持某一個特定編輯/查詢工作階段的狀態 (包括識別快取)。 若要取得以資料庫目前狀態為基礎的新執行個體，請使用新的 <xref:System.Data.Linq.DataContext>。  
  
 您仍然可以使用基礎 ADO.NET 連接共用。 如需詳細資訊，請參閱 [SQL Server 連共用ADO.NET)](../../../../../../docs/framework/data/adonet/sql-server-connection-pooling.md)。  
  
## <a name="second-datacontext-is-not-updated"></a>第二個 DataContext 未更新  
 問： 我使用一個 <xref:System.Data.Linq.DataContext> 執行個體來儲存資料庫中的值。 但是，相同資料庫上的第二個 <xref:System.Data.Linq.DataContext> 卻未反映更新的值。 第二個 <xref:System.Data.Linq.DataContext> 執行個體似乎傳回快取的值。  
  
 答： 這種行為是設計上的預期行為。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會繼續傳回您在第一個執行個體中看到的相同執行個體/值。 當您進行更新時，會使用開放式並行存取。 這時會使用原始資料來檢查目前資料庫狀態，以確認它實際上是否仍未變更。 如果變更，就會發生衝突，而應用程式必須解決此衝突。 應用程式可選擇的其中一種做法是將原始狀態重設為目前資料庫狀態，然後嘗試再次更新。 如需詳細資訊，請參閱[如何：管理變更衝突](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)。  
  
 您也可以將 <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> 設定為 false，以關閉快取和變更追蹤。 這樣每次查詢時，就能擷取最新的值。  
  
## <a name="cannot-call-submitchanges-in-read-only-mode"></a>無法在唯讀模式下呼叫 SubmitChanges  
 問： 當我嘗試在唯讀模式下呼叫 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 時，會發生錯誤。  
  
 答： 內容在唯讀模式下無法追蹤變更。  
  
## <a name="see-also"></a>另請參閱

- [參考資料](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
- [疑難排解](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md)
- [LINQ to SQL 中的安全性](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md)
