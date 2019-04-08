---
title: 處理 Null 值
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f18b288f-b265-4bbe-957f-c6833c0645ef
ms.openlocfilehash: fe48c8a2a7df74b1a9e28b514ba9258d2aa23ae9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59191462"
---
# <a name="handling-null-values"></a>處理 Null 值
當資料行中的值未知或遺失時，便會使用關聯式資料庫中的 Null 值。 Null 既不是空字串 (針對字元或 datetime 資料型別)，也不是零值 (針對數值資料型別)。 根據 ANSI SQL-92 規格的內容，對所有的資料型別而言，Null 必須都是相同的，以便可一致處理所有的 Null。 藉由實作 <xref:System.Data.SqlTypes> 介面，<xref:System.Data.SqlTypes.INullable> 命名空間可以提供 Null 語意。 <xref:System.Data.SqlTypes> 中的每個資料型別都具有自己的 `IsNull` 屬性及 `Null` 值，而該值可以指派給該資料型別的執行個體 (Instance)。  
  
> [!NOTE]
>  .NET Framework 2.0 版開始支援可為 Null 型別，這讓程式設計人員得以擴充實值型別，以表示基礎型別所有的值。 這些 CLR 可為 Null 的型別代表 <xref:System.Nullable> 結構的執行個體。 當實質型別為 boxed 和 unboxed 時，這項功能特別有用，可強化與物件型別的相容性。 CLR 可為 Null 的型別不適用於儲存資料庫 Null，因為 ANSI SQL Null 的行為方式與 `null` 參考不同 (在 Visual Basic 中為 `Nothing`)。 若要使用資料庫 ANSI SQL Null 值，請利用 <xref:System.Data.SqlTypes> Null 而非 <xref:System.Nullable>。 如需有關使用 CLR 的詳細資訊可為 null 的類型，在 Visual Basic 中，請參閱[可為 Null 的實值型別](~/docs/visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)，以及 C#，請參閱[使用可為 Null 的型別](~/docs/csharp/programming-guide/nullable-types/using-nullable-types.md)。  
  
## <a name="nulls-and-three-valued-logic"></a>Null 及三種值的邏輯  
 在資料行定義中允許 Null 值會將三種值的邏輯引進應用程式。 比較可評估為下列三個條件之一：  
  
-   True  
  
-   False  
  
-   不明  
  
 因為 Null 會視為 Unknown，所以比較兩個 Null 值時，並不會視為相等的。 在使用算術運算子的運算式中，如果有任何運算元為 Null，其結果也會是 Null。  
  
## <a name="nulls-and-sqlboolean"></a>Null 及 SqlBoolean  
 任何 <xref:System.Data.SqlTypes> 之間的比較都將傳回 <xref:System.Data.SqlTypes.SqlBoolean>。 每個 `IsNull` 的 `SqlType` 函式都會傳回 <xref:System.Data.SqlTypes.SqlBoolean>，並可用於檢查是否有 Null 值。 下列 True 值資料表顯示存在 Null 值時，AND、OR 及 NOT 運算子將如何運作。 (T=true、F=false 及 U=unknown 或 Null)。  
  
 ![Truth Table](../../../../../docs/framework/data/adonet/sql/media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")  
  
### <a name="understanding-the-ansinulls-option"></a>瞭解 ANSI_NULLS 選項  
 <xref:System.Data.SqlTypes> 在 SQL Server 上設定 ANSI_NULLS 選項時，請提供相同的語意。 所有算術運算子 (+、-，*，/、 %)，位元運算子 (~、 &、 &#124;)，以及大部分函數都會傳回 null，如果任何運算元或引數是 null，但屬性除外`IsNull`。  
  
 ANSI SQL-92 標準不支援*columnName* = null，則 WHERE 子句中。 在 SQL Server 中，ANSI_NULLS 選項可控制資料庫中的預設 Null 屬性及針對 Null 值的比較評估。 如果啟用 ANSI_NULLS (預設值)，則當測試 Null 值時，必須在運算式中使用 IS NULL 運算子。 例如，當啟用 ANSI_NULLS 時，下列比較永遠會產生 Unknown：  
  
```  
colname > NULL  
```  
  
 對包含 Null 值的變數進行比較也會產生 Unknown：  
  
```  
colname > @MyVariable  
```  
  
 使用 IS NULL 或 IS NOT NULL 述詞來測試 Null 值。 如此會增加 WHERE 子句的複雜性。 例如，AdventureWorks Customer 資料表中的 TerritoryID 資料行允許 Null 值。 如果 SELECT 陳述式除測試其他項目之外，還要測試 Null 值，則其必須包括 IS NULL 述詞：  
  
```  
SELECT CustomerID, AccountNumber, TerritoryID  
FROM AdventureWorks.Sales.Customer  
WHERE TerritoryID IN (1, 2, 3)  
   OR TerritoryID IS NULL  
```  
  
 如果在 SQL Server 中將 ANSI_NULLS 設為停用，則可以建立使用相等運算子的運算式，以與 Null 進行比較。 不過，您無法阻止不同連接設定該連接的 Null 選項。 不論連接的 ANSI_NULLS 設定為何，都可以使用 IS NULL 來測試 Null 值。  
  
 在 `DataSet` 中不支援將 ANSI_NULLS 設為停用，因為它永遠會遵循 ANSI SQL-92 標準來處理 <xref:System.Data.SqlTypes> 中的 Null 值。  
  
## <a name="assigning-null-values"></a>指派 Null 值  
 Null 值較特殊，其儲存及指派語意在不同類型系統及儲存系統之間會有所不同。 `Dataset` 是設計為與不同類型及儲存系統搭配使用。  
  
 本節將說明 Null 語意，其可指派 Null 值給跨不同類型系統之 <xref:System.Data.DataColumn> 的 <xref:System.Data.DataRow>。  
  
 `DBNull.Value`  
 此指派針對任何型別的 `DataColumn` 都有效。 如果型別實作 `INullable`，則 `DBNull.Value` 會強制轉型為適當的強型別 (Strongly Typed) Null 值。  
  
 `SqlType.Null`  
 所有 <xref:System.Data.SqlTypes> 資料型別都可實作 `INullable`。 如果使用隱含轉換運算子，將強型別 Null 值轉換成資料行的資料型別，指派就應該能夠順利完成。 否則，將擲回無效轉換例外狀況。  
  
 `null`  
 如果 'null' 是指定之 `DataColumn` 資料型別的合法值，它就會強制轉型為與 `DbNull.Value` 型別 (`Null`) 相關聯的適當 `INullable` 或 `SqlType.Null`。  
  
 `derivedUdt.Null`  
 若為 UDT 資料行，則永遠會依據與 `DataColumn` 相關聯的型別來儲存 Null。 請考量下列情況：UDT 與不實作 `DataColumn` 的 `INullable` (而其子類別實作) 相關聯。 在此情況下，如果指派了與衍生類別相關聯的強型別 Null 值，它就會儲存為不具型別的 `DbNull.Value`，因為 Null 儲存永遠會與 DataColumn 的資料型別一致。  
  
> [!NOTE]
>  目前在 `Nullable<T>` 中不支援 <xref:System.Nullable> 或 `DataSet` 結構。  
  
### <a name="multiple-column-row-assignment"></a>多個資料行 (資料列) 指派  
 `DataTable.Add``DataTable.LoadDataRow`，或接受的其他 Api <xref:System.Data.DataRow.ItemArray%2A> ，取得對應至一個資料列，其對應至 DataColumn 的預設值的 ' null'。 如果陣列中的物件包含 `DbNull.Value` 或其強型別的對應項，則會套用上述相同規則。  
  
 此外，下列規則可套用至 `DataRow.["columnName"]` Null 指派的執行個體：  
  
1.  預設值*預設*值是`DbNull.Value`所有除了強型別 null 資料行適當的強型別 null 值。  
  
2.  在序列化為 XML 檔案期間永遠不會寫出 Null 值 (如同在 xsi:nil 中)。  
  
3.  在序列化為 XML 時，永遠會寫出所有非 Null 值 (包括預設值)。 這與 XSD/XML 語意不同，在 XSD/XML 語意中 Null 值 (xsi:nil) 是明確的，而預設值是隱含的 (如果不存在於 XML 中，則驗證剖析器可以從相關聯的 XSD 結構描述中取得它)。 `DataTable` 的情況則相反：Null 值是隱含的，而預設值則是明確的。  
  
4.  針對從 XML 輸入讀取之資料列的所有遺漏資料行值都會指派 NULL。 使用 <xref:System.Data.DataTable.NewRow%2A> 或類似方法建立的資料列會指派為 DataColumn 的預設值。  
  
5.  <xref:System.Data.DataRow.IsNull%2A> 方法會針對 `true` 和 `DbNull.Value` 傳回 `INullable.Null`。  
  
## <a name="assigning-null-values"></a>指派 Null 值  
 任何 <xref:System.Data.SqlTypes> 執行個體的預設值都為 Null。  
  
 <xref:System.Data.SqlTypes> 中的 Null 是型別特定的，因此無法由單一值 (如 `DbNull`) 表示。 請使用 `IsNull` 屬性來檢查 Null。  
  
 Null 值可指派給 <xref:System.Data.DataColumn>，如下列程式碼範例中所示： 您可直接將 Null 值指派給 `SqlTypes` 變數，而不會觸發例外狀況。  
  
### <a name="example"></a>範例  
 下列程式碼範例會建立 <xref:System.Data.DataTable>，其包含兩個定義為 <xref:System.Data.SqlTypes.SqlInt32> 及 <xref:System.Data.SqlTypes.SqlString> 的資料行。 程式碼會加入一個已知值的資料列及一個 Null 值的資料列，然後在 <xref:System.Data.DataTable> 中重複，以將值指派給變數並在主控台視窗中顯示輸出。  
  
 [!code-csharp[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/VB/source.vb#1)]  
  
 此範例會顯示出下列結果：  
  
```  
isColumnNull=False, ID=123, Description=Side Mirror  
isColumnNull=True, ID=Null, Description=Null  
```  
  
## <a name="comparing-null-values-with-sqltypes-and-clr-types"></a>將 Null 值與 SqlType 及 CLR 型別進行比較  
 比較 Null 值時，瞭解 `Equals` 方法評估 <xref:System.Data.SqlTypes> 中 Null 值的方式，與其處理 CLR 型別之方式相比較的差異很重要。 所有<xref:System.Data.SqlTypes>`Equals`方法是使用資料庫語意來評估 null 值： 如果其中一個或兩個值是 null，則該比較會產生 null。 另一方面，針對兩個 `Equals` 使用 CLR <xref:System.Data.SqlTypes> 方法時，如果二者都為 Null，則會產生 True。 這反映出使用執行個體方法 (例如 CLR `String.Equals` 方法) 與使用靜態/共用方法 (`SqlString.Equals`) 之間的差異。  
  
 下列範例示範當針對每個方法傳遞一對 Null 值，然後傳遞一對空字串時，`SqlString.Equals` 方法及 `String.Equals` 方法之間結果的差異。  
  
 [!code-csharp[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/VB/source.vb#1)]  
  
 該程式碼會產生下列輸出：  
  
```  
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

- [SQL Server 資料類型和 ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)
- [ADO.NET Managed 提供者和DataSet開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
