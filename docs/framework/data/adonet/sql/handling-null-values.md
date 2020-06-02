---
title: 處理 Null 值
description: 瞭解 SQL Server 如何處理 null 的 .NET Framework Data Provider，並閱讀有關 null 和 SqlBoolean、三值邏輯，以及指派 null 值的資訊。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f18b288f-b265-4bbe-957f-c6833c0645ef
ms.openlocfilehash: a4d086d81f1c2c959780366cfeb59f2d265bc40c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286451"
---
# <a name="handling-null-values"></a>處理 Null 值
在關聯式資料庫中，當資料行中的值為未知或遺漏時，就會使用 Null 值。 Null 不是空字串 (針對字元或日期時間資料類型)，也不是零值 (針對數值資料類型)。 ANSI SQL-92 規格指出，所有資料類型的 Null 都必須相同，因此，所有 Null 都會以一致的方式來處理。 <xref:System.Data.SqlTypes> 命名空間會藉由實作 <xref:System.Data.SqlTypes.INullable> 介面來提供 Null 語意。 <xref:System.Data.SqlTypes> 中的每個資料類型都有自己的 `IsNull` 屬性，以及可指派給該資料類型之執行個體的 `Null` 值。  
  
> [!NOTE]
> .NET Framework 版本2.0 引進了可為 null 實數值型別的支援，可讓程式設計師擴充實值型別，以代表基礎類型的所有值。 這些 CLR 可為 null 的實數值型別代表 <xref:System.Nullable> 結構的實例。 已將數值類型 Boxed 和 Unboxed 時，此功能特別有用，可提供與物件類型的增強相容性。 CLR 可為 null 的實數值型別不適合用來儲存資料庫 null，因為 ANSI SQL null 的行為與參考相同 `null` （或 `Nothing` Visual Basic）。 若要使用資料庫 ANSI SQL Null 值，請使用 <xref:System.Data.SqlTypes> Null，而不是 <xref:System.Nullable>。 如需在 Visual Basic 中使用 CLR 值可為 null 型別的詳細資訊，請參閱[可為 null](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)的實值型別，而針對 c #，請參閱[可](../../../../csharp/language-reference/builtin-types/nullable-value-types.md)  
  
## <a name="nulls-and-three-valued-logic"></a>Null 及三種值的邏輯  
 在資料行定義中允許 Null 值，會在您的應用程式中引進三值邏輯。 比較可以評估為三個條件的其中一個：  
  
- True  
  
- False  
  
- Unknown  
  
 因為 Null 會被視為未知，所以不會將彼此相比較的兩個 Null 值視為相等。 在使用算術運算子的運算式中，如果有任何運算元是 Null，結果也會是 Null。  
  
## <a name="nulls-and-sqlboolean"></a>Null 和 SqlBoolean  
 任何 <xref:System.Data.SqlTypes> 間的比較都將傳回 <xref:System.Data.SqlTypes.SqlBoolean>。 每個 `SqlType` 的 `IsNull` 函數都會傳回 <xref:System.Data.SqlTypes.SqlBoolean>，而且可用來檢查 Null 值。 下列事實資料表示範 AND、OR 及 NOT 運算子如何在出現 Null 值的情況下運作 (T=true、F=false 及 U=unknown，或 Null)。  
  
 ![事實資料表](./media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")  
  
### <a name="understanding-the-ansi_nulls-option"></a>瞭解 ANSI_NULLS 選項  
 <xref:System.Data.SqlTypes> 提供的語意與在 SQL Server 中設定 ANSI_NULLS 選項時相同。 如果任何運算元或引數為 null （屬性除外），則所有算術運算子（+、-、 \* 、/、%）、位運算子（~、&、 \| ）和大部分函數都會傳回 null `IsNull` 。  
  
 ANSI SQL-92 標準不支援 WHERE 子句中的 *columnName* = NULL。 在 SQL Server 中，ANSI_NULLS 選項會控制資料庫中預設的可 NULL 性，以及對 Null 值的比較評估。 如果 ANSI_NULLS 已開啟 (預設值)，則在測試 Null 值時，必須在運算式中使用 IS NULL 運算子。 例如，當 ANSI_NULLS 是 ON 時，下列比較永遠都會產生未知：  
  
```sql
colname > NULL  
```  
  
 與包含 Null 值的變數進行比較也會產生未知：  
  
```sql
colname > @MyVariable  
```  
  
 使用 IS NULL 或 IS NOT NULL 述詞可以測試是否為 NULL 值。 不過這樣會增加 WHERE 子句的複雜度。 例如，AdventureWorks Customer 資料表中的 TerritoryID 資料行允許 Null 值。 如果 SELECT 陳述式要測試其他資料行是否有 Null 值，必須包含 IS NULL 述詞：  
  
```sql
SELECT CustomerID, AccountNumber, TerritoryID  
FROM AdventureWorks.Sales.Customer  
WHERE TerritoryID IN (1, 2, 3)  
   OR TerritoryID IS NULL  
```  
  
 如果您將 SQL Server 中的 ANSI_NULLS 設定為 off，則可建立使用等號比較運算子來比較 Null 的運算式。 不過，您無法防止不同的連線來為該連線設定 Null 選項。 不論連線的 ANSI_NULLS 設定為何，使用 IS NULL 來測試 Null 值一律可行。  
  
 `DataSet` 中不支援將 ANSI_NULLS 設定為 off，其始終會遵循 ANSI SQL-92 標準來處理 <xref:System.Data.SqlTypes> 中的 Null 值。  
  
## <a name="assigning-null-values"></a>指派 Null 值  
 Null 值是特殊的，它們的儲存和指派語意在不同類型系統和儲存系統之間各不相同。 `Dataset` 是設計來搭配不同的類型和儲存系統使用。  
  
 此節描述在不同類型系統間的 <xref:System.Data.DataRow> 中，將 Null 值指派給 <xref:System.Data.DataColumn> 的 Null 語意。  
  
 `DBNull.Value`  
 此指派適用於任何類型的 `DataColumn`。 如果類型實作 `INullable`，就會將 `DBNull.Value` 強制轉型為適當的強型別 Null 值。  
  
 `SqlType.Null`  
 所有 <xref:System.Data.SqlTypes> 資料類型都會實作 `INullable`。 如果強型別 Null 值可以使用隱含轉換運算子轉換為資料行的資料類型，則指派應可順利完成。 否則會擲回轉換無效的例外狀況。  
  
 `null`  
 如果 'null' 是指定 `DataColumn` 資料類型的合法值，就會強制轉型為適當的 `DbNull.Value` 或與 `INullable` 類型 (`SqlType.Null`) 相關聯的 `Null`。  
  
 `derivedUdt.Null`  
 如果是 UDT 資料行，一律會根據與 `DataColumn` 相關聯的類型來儲存 Null。 請考慮與 `DataColumn` 相關聯的 UDT 案例，其不會實作 `INullable`，但其子類別會。 在此案例中，如果已指派與衍生類別相關聯的強型別 Null 值，它就會儲存為不具類型的 `DbNull.Value`，因為 Null 儲存一律會與 DataColumn 的資料類型一致。  
  
> [!NOTE]
> `DataSet` 中目前不支援 `Nullable<T>` 或 <xref:System.Nullable> 結構。  
  
### <a name="multiple-column-row-assignment"></a>多個資料行 (資料列) 指派  
 `DataTable.Add`、`DataTable.LoadDataRow` 或其他接受對應到資料列之 <xref:System.Data.DataRow.ItemArray%2A> 的 API，會將 'null' 對應到 DataColumn 的預設值。 如果陣列中的物件包含 `DbNull.Value` 或其強型別的對應項，即會套用前述的相同規則。  
  
 此外，下列規則適用於 `DataRow.["columnName"]` Null 指派的執行個體：  
  
1. 除了強型別 Null 資料行具有適當的強型別 Null 值之外，所有其他項目的預設 *default* 值都為 `DbNull.Value`。  
  
2. 絕對不會在序列化到 XML 檔案期間寫出 Null 值 (就像 "xsi:nil")。  
  
3. 序列化到 XML 時，一律會寫出所有非 Null 值 (包括預設值)。 這不同於 XSD/XML 語意，其中 Null 值 (xsi:nil) 是明確的，而預設值是隱含的 (如果未出現在 XML 中，驗證剖析器就能夠從相關聯的 XSD 結構描述中取得它)。 如果是 `DataTable`，則情況恰恰相反：Null 值是隱含的，而預設值是明確的。  
  
4. 從 XML 輸入讀取之資料列的所有遺漏資料行值都會指派為 Null。 使用 <xref:System.Data.DataTable.NewRow%2A> 或類似方法建立的資料列都會被指派 DataColumn 的預設值。  
  
5. <xref:System.Data.DataRow.IsNull%2A> 方法會針對 `DbNull.Value` 和 `INullable.Null` 傳回 `true`。  
  
## <a name="assigning-null-values"></a>指派 Null 值  
 所有 <xref:System.Data.SqlTypes> 執行個體的預設值均為 Null。  
  
 <xref:System.Data.SqlTypes> 中的 Null 是類型專屬的，無法以單一值表示，例如 `DbNull`。 使用 `IsNull` 屬性來檢查 Null。  
  
 Null 值可以指派給 <xref:System.Data.DataColumn>，如下列程式碼範例所示。 您可以直接將 Null 值指派給 `SqlTypes` 變數，而不會觸發例外狀況。  
  
### <a name="example"></a>範例  
 下列程式碼範例會建立 <xref:System.Data.DataTable>，其中包含兩個定義為 <xref:System.Data.SqlTypes.SqlInt32> 和 <xref:System.Data.SqlTypes.SqlString> 的資料行。 程式碼會新增一個已知值的資料列、一個 Null 值的資料列，然後逐一查看 <xref:System.Data.DataTable>，將值指派給變數，並在主控台視窗中顯示輸出。  
  
 [!code-csharp[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/VB/source.vb#1)]  
  
 此範例會顯示下列結果：  
  
```output
isColumnNull=False, ID=123, Description=Side Mirror  
isColumnNull=True, ID=Null, Description=Null  
```  
  
## <a name="comparing-null-values-with-sqltypes-and-clr-types"></a>將 Null 值與 SqlType 及 CLR 型別進行比較  
 比較 Null 值時，請務必了解 `Equals` 方法在 <xref:System.Data.SqlTypes> 中評估 Null 值之方式間的差異 (相較於其使用 CLR 類型的方式)。 所有 <xref:System.Data.SqlTypes>`Equals` 方法都會使用資料庫語意來評估 Null 值：如果其中一個或兩個值都是 Null，則比較會產生 Null。 另一方面，在兩個 <xref:System.Data.SqlTypes> 上使用 CLR `Equals` 方法，將會在兩者均為 Null 時產生 True。 這會反映使用執行個體方法 (例如 CLR `String.Equals` 方法) 和使用靜態/共用方法 (`SqlString.Equals`) 之間的差異。  
  
 下列範例示範在 `SqlString.Equals` 方法與 `String.Equals` 方法之間，分別傳遞一對 Null 值，然後傳遞一對空字串時的結果差異。  
  
 [!code-csharp[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/VB/source.vb#1)]  
  
 此程式碼會產生下列輸出：  
  
```output
SqlString.Equals shared/static method:  
  Two nulls=Null  
  
String.Equals instance method:  
  Two nulls=True  
  
SqlString.Equals shared/static method:  
  Two empty strings=True  
  
String.Equals instance method:  
  Two empty strings=True
```  
  
## <a name="see-also"></a>另請參閱

- [SQL Server 資料類型和 ADO.NET](sql-server-data-types.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
