---
title: 使用 CommandBuilder 產生命令
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6e3fb8b5-373b-4f9e-ab03-a22693df8e91
ms.openlocfilehash: e1071261f45c56655f8e6fb5fec6fccb08fd13c6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43415759"
---
# <a name="generating-commands-with-commandbuilders"></a>使用 CommandBuilder 產生命令
當 `SelectCommand` 屬性是在執行階段時以動態方式指定 (例如透過能接收使用者下達文字命令的查詢工具)，則您可能無法於設計階段指定適當的 `InsertCommand`、`UpdateCommand` 或 `DeleteCommand`。 如果您的 <xref:System.Data.DataTable> 對應至或產生自單一資料庫資料表，則可以利用 <xref:System.Data.Common.DbCommandBuilder> 物件來自動產生 `DeleteCommand` 的 `InsertCommand`、`UpdateCommand` 和 <xref:System.Data.Common.DbDataAdapter>。  
  
 根據最小需求，您必須設定 `SelectCommand` 屬性，才能使用自動命令產生功能。 `SelectCommand` 屬性擷取的資料表結構描述則決定自動產生的 INSERT、UPDATE 和 DELETE 陳述式語法。  
  
 <xref:System.Data.Common.DbCommandBuilder> 必須執行 `SelectCommand`，才能傳回必要的中繼資料來建構 INSERT、UPDATE 和 DELETE SQL 命令。 因此必須要另外連至資料來源，但這可能會降低效能。 若要達到最佳效能，請明確地指定命令，而不要使用 <xref:System.Data.Common.DbCommandBuilder>。  
  
 `SelectCommand` 還必須傳回至少一個主索引鍵或唯一的資料行。 如果兩個都不存在，便會發生 `InvalidOperation` 例外狀況 (Exception)，且不會產生命令。  
  
 與 `DataAdapter` 產生關聯時，<xref:System.Data.Common.DbCommandBuilder> 會自動產生 `InsertCommand` 的 `UpdateCommand`、`DeleteCommand` 和 `DataAdapter` 屬性 (如果它們是 Null 參考)。 如果屬性的 `Command` 已經存在，則會使用現有的 `Command`。  
  
 您不能將兩個或多個資料表合併所建立的資料庫檢視視為單一資料庫資料表。 在這個執行個體中，您無法使用 <xref:System.Data.Common.DbCommandBuilder> 自動產生命令，而且必須明確指定命令。 如需明確設定命令以更新解析`DataSet`回到 資料來源，請參閱[使用 Dataadapter 更新資料來源](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)。  
  
 您可能想要把輸出參數對應回 `DataSet` 已更新的資料列。 一項通用工作便是從資料來源擷取自動產生的識別欄位值或時間戳記值。 <xref:System.Data.Common.DbCommandBuilder> 預設不會將輸出參數對應到已更新資料列中的資料行。 在這種情形下，您必須明確地指定命令。 回到 插入資料列的資料行對應會自動產生的識別欄位的範例，請參閱[擷取識別或自動編號值](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md)。  
  
## <a name="rules-for-automatically-generated-commands"></a>自動產生命令的規則  
 下列表格顯示產生自動產生命令的規則。  
  
|命令|規則|  
|-------------|----------|  
|`InsertCommand`|針對含 <xref:System.Data.DataRow.RowState%2A> 的 <xref:System.Data.DataRowState.Added> 之資料表的所有資料列，插入資料來源上的資料列。 插入所有可更新的資料行值 (但非識別、運算式或時間籤記等資料行)。|  
|`UpdateCommand`|針對含 `RowState` 的 <xref:System.Data.DataRowState.Modified> 之資料表的所有資料列，更新資料來源上的資料列。 除了無法更新的資料行 (例如識別或運算式) 之外，更新所有可更新的資料行值。 並且在資料來源中，找出資料行值與資料列主索引鍵資料行值相符的資料列，以及剩餘資料行與資料列原始資料相符的資料列，將這些資料列全都更新。 如需詳細資訊，請參閱這個主題稍後的＜更新和刪除的開放式同步存取模式＞。|  
|`DeleteCommand`|針對含 `RowState` 的 <xref:System.Data.DataRowState.Deleted> 之資料表的所有資料列，刪除資料來源上的資料列。 在資料來源中，找出其資料行值與資料列的主索引鍵資料行值相符的所有資料列，以及剩餘資料行與原始資料列值相符的所有資料列，並將這些資料列全都刪除。 如需詳細資訊，請參閱這個主題稍後的＜更新和刪除的開放式同步存取模式＞。|  
  
## <a name="optimistic-concurrency-model-for-updates-and-deletes"></a>更新和刪除開放式同步存取模式  
 自動替 UPDATE 和 DELETE 陳述式產生命令的邏輯根據*開放式並行存取*-也就是說，記錄進行編輯，不鎖定，而且可以隨時修改其他使用者或處理程序。 記錄從 SELECT 陳述式傳回後可能已經修改，但是發出 UPDATE 或 DELETE 陳述式之前，自動產生的 UPDATE 或 DELETE 陳述式會包含 WHERE 子句，指定只有資料列包含所有原始值且尚未從資料來源刪除時，才會更新該資料列。 這樣是為了避免覆寫新資料。 自動產生的更新嘗試更新已刪除的資料列或未包含 <xref:System.Data.DataSet> 中所找到之原始值的資料列時，該命令不會影響任何記錄，且會擲回 <xref:System.Data.DBConcurrencyException>。  
  
 如果您想完成 UPDATE 或 DELETE (不管是否為原始值)，則您必須明確設定 `UpdateCommand` 的 `DataAdapter`，而不是依賴自動命令產生功能。  
  
## <a name="limitations-of-automatic-command-generation-logic"></a>自動命令產生的邏輯限制  
 下列限制適用於自動命令產生。  
  
### <a name="unrelated-tables-only"></a>僅限不相關的資料表  
 自動命令產生邏輯為獨立資料表產生 INSERT、UPDATE 或 DELETE 陳述式，而不顧及任何與資料來源中其他資料表的關聯性。 所以，如果呼叫 `Update` 將變更送出至資料行，而這個資料行又擔任資料庫的外部索引鍵條件約束，則可能會發生錯誤。 為了避免發生這種例外狀況，請勿使用 <xref:System.Data.Common.DbCommandBuilder> 來更新外部索引鍵條件約束所牽涉的資料行，而應該明確地指定用於執行作業的陳述式。  
  
### <a name="table-and-column-names"></a>資料表和資料行名稱  
 如果資料行名稱或資料表名稱包含任何特殊字元，例如空格、句號、引號或其他非英數的字元，則即使以括弧分隔，自動命令產生邏輯仍可能會失敗。 根據提供者而定，設定 QuotePrefix 和 QuoteSuffix 參數可能會允許產生邏輯以處理空格，不過，卻不能逸出特殊字元。 完整資料表名稱的形式*catalog.schema.table*支援。  
  
## <a name="using-the-commandbuilder-to-automatically-generate-an-sql-statement"></a>使用 CommandBuilder 自動產生 SQL 陳述式  
 若要自動產生 `DataAdapter` 的 SQL 陳述式，請首先設定 `SelectCommand` 的 `DataAdapter` 屬性，然後建立 `CommandBuilder` 物件，再指定為引數，該引數則是 `DataAdapter` 將自動為其產生 SQL 陳述式的 `CommandBuilder`。  
  
```vb  
' Assumes that connection is a valid SqlConnection object   
' inside of a Using block.  
Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM dbo.Customers", connection)  
Dim builder As SqlCommandBuilder = New SqlCommandBuilder(adapter)  
builder.QuotePrefix = "["  
builder.QuoteSuffix = "]"  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection object  
// inside of a using block.  
SqlDataAdapter adapter = new SqlDataAdapter(  
  "SELECT * FROM dbo.Customers", connection);  
SqlCommandBuilder builder = new SqlCommandBuilder(adapter);  
builder.QuotePrefix = "[";  
builder.QuoteSuffix = "]";  
```  
  
## <a name="modifying-the-selectcommand"></a>修改 SelectCommand  
 如果您在 INSERT、UPDATE 或 DELETE 命令自動產生後，修改 `CommandText` 的 `SelectCommand`，便可能發生例外狀況。 如果已修改的 `SelectCommand.CommandText` 包含的結構描述資訊與插入、更新或刪除命令自動產生時使用的 `SelectCommand.CommandText` 不一致，日後呼叫的 `DataAdapter.Update` 方法便可能會到 `SelectCommand` 參考的目前資料表中，嘗試存取已不存在的資料行，這樣就會擲回例外狀況。  
  
 您可以藉由重新整理 `CommandBuilder` 使用的結構描述資訊，呼叫 `RefreshSchema` 的 `CommandBuilder` 方法以自動產生命令。  
  
 若您想要知道自動產生的命令為何，可以使用 `GetInsertCommand` 物件的 `GetUpdateCommand`、`GetDeleteCommand` 和 `CommandBuilder` 方法，取得自動產生命令的參考，然後檢查相關命令的 `CommandText` 屬性。  
  
 下列程式碼範例將自動產生的更新命令寫入主控台。  
  
```  
Console.WriteLine(builder.GetUpdateCommand().CommandText)  
```  
  
 下列範例會在 `Customers` 資料集中重新建立 `custDS` 資料表。 **RefreshSchema**呼叫方法來重新整理自動產生的命令，這個新的資料行資訊。  
  
```vb  
' Assumes an open SqlConnection and SqlDataAdapter inside of a Using block.  
adapter.SelectCommand.CommandText = _  
  "SELECT CustomerID, ContactName FROM dbo.Customers"  
builder.RefreshSchema()  
  
custDS.Tables.Remove(custDS.Tables("Customers"))  
adapter.Fill(custDS, "Customers")  
```  
  
```csharp  
// Assumes an open SqlConnection and SqlDataAdapter inside of a using block.  
adapter.SelectCommand.CommandText =   
  "SELECT CustomerID, ContactName FROM dbo.Customers";  
builder.RefreshSchema();  
  
custDS.Tables.Remove(custDS.Tables["Customers"]);  
adapter.Fill(custDS, "Customers");  
```  
  
## <a name="see-also"></a>另請參閱  
 [命令和參數](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [執行命令](../../../../docs/framework/data/adonet/executing-a-command.md)  
 [DbConnection、DbCommand 和 DbException](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
