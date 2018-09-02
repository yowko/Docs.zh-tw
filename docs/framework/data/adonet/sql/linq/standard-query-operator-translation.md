---
title: 標準查詢運算子轉譯
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a60c30fa-1e68-45fe-b984-f6abb9ede40e
ms.openlocfilehash: fb4910e48af58463c5c851173f8e3caf4594cc3a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43424226"
---
# <a name="standard-query-operator-translation"></a>標準查詢運算子轉譯
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會將標準查詢運算子轉譯為 SQL 命令。 資料庫的查詢處理器會決定執行語意的 SQL 轉譯。  
  
 標準查詢運算子中定義*序列*。 是一連串*排序*而且依賴序列的每個元素的參考識別。 如需詳細資訊，請參閱 <<c0> [ 標準查詢運算子概觀](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)。  
  
 SQL 主要負責處理*未排序的一組值*。 排序通常是一項明確陳述的後置處理作業，會套用至最終查詢結果 (而非中繼結果)。 識別是以值來定義。 基於這個理由，SQL 查詢來了解處理用於多重集 (*包*) 而非*設定*。  
  
 下列段落說明標準查詢運算子和其因為 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 針對 SQL Server 提供者進行的 SQL 轉譯之間的差異。  
  
## <a name="operator-support"></a>運算子支援  
  
### <a name="concat"></a>Concat  
 <xref:System.Linq.Enumerable.Concat%2A> 方法在定義上適用於已排序的多重集，也就是說接收器的順序和引數的順序相同。 <xref:System.Linq.Enumerable.Concat%2A> 的運作原理，是對採用共通順序的多重集執行 `UNION ALL`。  
  
 最後一步就是在產生結果前於 SQL 中排序。 <xref:System.Linq.Enumerable.Concat%2A> 不會保留其引數的順序。 若要確保適當的排序，您必須明確排序 <xref:System.Linq.Enumerable.Concat%2A> 的結果。  
  
### <a name="intersect-except-union"></a>Intersect、Except、Union  
 <xref:System.Linq.Enumerable.Intersect%2A> 和 <xref:System.Linq.Enumerable.Except%2A> 方法在定義上僅適用於集合。 尚未定義多重集 (Multiset) 的語意 (Semantics)。  
  
 <xref:System.Linq.Enumerable.Union%2A> 方法在定義上適用於多重集，可對多重集做未排序的串連 (其實就是 SQL 中 UNION ALL 子句的結果)。  
  
### <a name="take-skip"></a>Take、Skip  
 <xref:System.Linq.Enumerable.Take%2A> 並<xref:System.Linq.Enumerable.Skip%2A>方法在定義只針對適用於*ordered set*。 未定義適用於未排序集合或多重集的語意 (Semantics)。  
  
> [!NOTE]
>  <xref:System.Linq.Enumerable.Take%2A> 和 <xref:System.Linq.Enumerable.Skip%2A> 在用於對 SQL Server 2000 進行的查詢中時會有一些限制。 如需詳細資訊，請參閱中的"Skip 和 Take 例外狀況在 SQL Server 2000"項目[疑難排解](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md)。  
  
 由於在 SQL 中，排序的限制[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]嘗試將移至方法的結果，這些方法的引數的順序。 例如，請考量下列 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 查詢：  
  
 [!code-csharp[DLinqSQOTranslation#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#1)]
 [!code-vb[DLinqSQOTranslation#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#1)]  
  
 這個程序碼產生的 SQL 會將排序移至結尾，如下所示：  
  
```  
SELECT TOP 1 [t0].[CustomerID], [t0].[CompanyName],  
FROM [Customers] AS [t0]  
WHERE (NOT (EXISTS(  
    SELECT NULL AS [EMPTY]  
    FROM (  
        SELECT TOP 1 [t1].[CustomerID]  
        FROM [Customers] AS [t1]  
        WHERE [t1].[City] = @p0  
        ORDER BY [t1].[CustomerID]  
        ) AS [t2]  
    WHERE [t0].[CustomerID] = [t2].[CustomerID]  
    ))) AND ([t0].[City] = @p1)  
ORDER BY [t0].[CustomerID]  
```  
  
 很明顯地，當 <xref:System.Linq.Enumerable.Take%2A> 和 <xref:System.Linq.Enumerable.Skip%2A> 鏈結在一起時，所有指定的排序都必須一致。 否則，會有未定義的結果。  
  
 根據標準查詢運算子的規格，<xref:System.Linq.Enumerable.Take%2A> 和 <xref:System.Linq.Enumerable.Skip%2A> 在定義上適用於非負數的固定整數引數。  
  
### <a name="operators-with-no-translation"></a>不轉譯的運算子  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 不會轉譯下列方法。 最常見的原因在於未排序的多重集與序列之間有差異。  
  
|運算子|基本原理|  
|---------------|---------------|  
|<xref:System.Linq.Enumerable.TakeWhile%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A>|SQL 查詢可用於多重集而非序列上。 `ORDER BY` 必須是最後一個對結果套用的子句。 因此，這兩個方法不需要普遍受到轉譯。|  
|<xref:System.Linq.Enumerable.Reverse%2A>|如果是未排序的集合，則要轉譯這個方法是可行的，但 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 目前不會加以轉譯。|  
|<xref:System.Linq.Enumerable.Last%2A>, <xref:System.Linq.Enumerable.LastOrDefault%2A>|如果是未排序的集合，則要轉譯這些方法是可行的，但 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 目前不會加以轉譯。|  
|<xref:System.Linq.Enumerable.ElementAt%2A>, <xref:System.Linq.Enumerable.ElementAtOrDefault%2A>|SQL 查詢是用於多重集，而非可建立索引的序列上。|  
|<xref:System.Linq.Enumerable.DefaultIfEmpty%2A> (以預設引數多載)|一般而言，如果是任意 Tuple，就不能指定預設值。 在某些情況下，可以透過外部聯結 (Outer Join) 指定 Null 值給 Tuple。|  
  
## <a name="expression-translation"></a>運算式轉譯  
  
### <a name="null-semantics"></a>Null 語意  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 不會對 SQL 加上 null 比較語意。 比較運算子會轉譯為語法上的 SQL 對等用法。 基於這個理由，語意會反映伺服器或連接設定所定義的 SQL 語意。 例如，兩個 null 值會視為不相等，在預設 SQL Server 設定 下，但您可以變更設定來變更語意。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 在轉譯查詢時不會考慮伺服器設定。  
  
 與常值 null 的比較會轉譯為適當的 SQL 版本 (`is null` 或 `is not null`)。  
  
 定序 (Collation) 中的值 `null` 是由 SQL Server 所定義。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 不會變更這個定序。  
  
### <a name="aggregates"></a>彙總  
 標準查詢運算子彙總方法 <xref:System.Linq.Enumerable.Sum%2A> 會將空序列或只包含 null 的序列評估為零。 中[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]，SQL 的語意會保留不變，並<xref:System.Linq.Enumerable.Sum%2A>評估為`null`而不是零，將空序列或只包含 null 的序列。  
  
 SQL 對中繼結果的限制會套用至 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中的彙總。 32 位元整數量值的 <xref:System.Linq.Enumerable.Sum%2A> 不會用 64 位元的結果來計算。 即使標準查詢運算子實作並未造成對應的記憶體中序列發生溢位，進行 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的 <xref:System.Linq.Enumerable.Sum%2A> 轉譯仍可能會發生溢位。  
  
 同樣地，轉譯整數值的 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的 <xref:System.Linq.Enumerable.Average%2A> 時，會以 `integer` 而非 `double` 計算。  
  
### <a name="entity-arguments"></a>實體引數  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 可讓實體類型，以供<xref:System.Linq.Enumerable.GroupBy%2A>和<xref:System.Linq.Enumerable.OrderBy%2A>方法。 在轉譯這些運算子時，使用型別引數會視為指定該型別的所有成員。 例如，下列程式碼為對等用法：  
  
 [!code-csharp[DLinqSQOTranslation#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#2)]
 [!code-vb[DLinqSQOTranslation#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#2)]  
  
### <a name="equatable--comparable-arguments"></a>可相等 / 可比較的引數  
 實作下列方法時，必須進行引數的等號比較：  
  
 <xref:System.Linq.Enumerable.Contains%2A>  
  
 <xref:System.Linq.Enumerable.Skip%2A>  
  
 <xref:System.Linq.Enumerable.Union%2A>  
  
 <xref:System.Linq.Enumerable.Intersect%2A>  
  
 <xref:System.Linq.Enumerable.Except%2A>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 支援和不等比較*一般*引數，而不是或包含序列的引數。 扁平引數是一種可以對應至 SQL 資料列的型別。 如果一個或多個實體型別的投影可以透過靜態方式判斷為不含序列，則這個投影即為扁平引數。  
  
 下列是扁平引數的範例：  
  
 [!code-csharp[DLinqSQOTranslation#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#3)]
 [!code-vb[DLinqSQOTranslation#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#3)]  
  
 下列是非扁平 (階層式) 引數的範例：  
  
 [!code-csharp[DLinqSQOTranslation#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#4)]
 [!code-vb[DLinqSQOTranslation#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#4)]  
  
### <a name="visual-basic-function-translation"></a>Visual Basic 函式轉譯  
 Visual Basic 編譯器 (Compiler) 所用的下列 Helper 函式會轉譯為對應的 SQL 運算子和函式：  
  
 `CompareString`  
  
 `DateTime.Compare`  
  
 `Decimal.Compare`  
  
 `IIf (in Microsoft.VisualBasic.Interaction)`  
  
 轉換方法：  
  
|||||  
|-|-|-|-|  
|ToBoolean|ToSByte|ToByte|ToChar|  
|ToCharArrayRankOne|ToDate|ToDecimal|ToDouble|  
|ToInteger|ToUInteger|ToLong|ToULong|  
|ToShort|ToUShort|ToSingle|ToString|  
  
## <a name="inheritance-support"></a>繼承支援  
  
### <a name="inheritance-mapping-restrictions"></a>繼承對應限制  
 如需詳細資訊，請參閱 <<c0> [ 如何： 對應繼承階層架構](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md)。  
  
### <a name="inheritance-in-queries"></a>查詢中的繼承  
 僅支援在投影中使用 C# 轉換 (Cast)。 其他地方使用的轉換 (Cast) 不會受到轉譯而且會予以忽略。 事實上，除了 SQL 函式名稱之外，SQL 只會執行 Common Language Runtime (CLR) <xref:System.Convert> 的對等用法。 也就是說，SQL 可以將某個型別的值變更為另一個值。 因為沒有將相同位元的型別重新解譯為另一個型別的概念，CLR 轉換 (Cast) 沒有對等用法。 這就是 C# 轉換只能在區域執行的原因。 無法遠端處理。  
  
 運算子 (`is` 和 `as`) 與 `GetType` 方法不僅能用於 `Select` 運算子中， 也可用於其他查詢運算子中。  
  
## <a name="sql-server-2008-support"></a>SQL Server 2008 支援  
 從 .NET Framework 3.5 SP1 開始，LINQ to SQL 便支援對應至 SQL Server 2008 所導入的新日期和時間型別。 但是，針對對應至這些新型別的值進行作業時，您可以使用的 LINQ to SQL 查詢運算子有一些限制。  
  
### <a name="unsupported-query-operators"></a>不支援的查詢運算子  
 對應至新 SQL Server 日期和時間型別的值不支援下列查詢運算子：`DATETIME2`、`DATE`、`TIME` 和 `DATETIMEOFFSET`。  
  
-   `Aggregate`  
  
-   `Average`  
  
-   `LastOrDefault`  
  
-   `OfType`  
  
-   `Sum`  
  
 如需對應至這些 SQL Server 日期和時間類型的詳細資訊，請參閱[SQL-CLR 類型對應](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)。  
  
## <a name="sql-server-2005-support"></a>SQL Server 2005 支援  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 不支援下列 SQL Server 2005 功能：  
  
-   針對 SQL CLR 撰寫的預存程序 (Stored Procedure)。  
  
-   使用者定義型別。  
  
-   XML 查詢功能。  
  
## <a name="sql-server-2000-support"></a>SQL Server 2000 支援  
 下列 [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] 限制 (相較於 [!INCLUDE[sqprsqext](../../../../../../includes/sqprsqext-md.md)]) 會影響 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 支援。  
  
### <a name="cross-apply-and-outer-apply-operators"></a>Cross Apply 和 Outer Apply 運算子  
 這些運算子不適用於 [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)]。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會嘗試進行一連串重寫作業，以便將它們取代成適當的聯結 (Join)。  
  
 `Cross Apply` 和 `Outer Apply` 是為了關聯性 (Relationship) 巡覽而產生的。 會進行這類重寫的查詢集還沒整理出來。 因此，對於 [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] 而言，最基本可支援的查詢集就是與關聯性巡覽無關的查詢集。  
  
### <a name="text--ntext"></a>text / ntext  
 資料型別`text`  /  `ntext`不適用於某些查詢作業`varchar(max)`  /  `nvarchar(max)`，所支援的[!INCLUDE[sqprsqext](../../../../../../includes/sqprsqext-md.md)]。  
  
 這項限制沒有解決方案。 具體來說，如果結果中含有對應至 `Distinct()` 或 `text` 資料行的成員，就不能對該結果使用 `ntext`。  
  
### <a name="behavior-triggered-by-nested-queries"></a>巢狀查詢觸發的行為  
 [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] （透過 SP4) 繫結器會有巢狀查詢觸發的某些特性。 無法妥善定義的 SQL 查詢集，就會觸發這些特性。 基於這個理由，您不能定義一組[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]查詢可能會導致 SQL Server 例外狀況。  
  
### <a name="skip-and-take-operators"></a>Skip 和 Take 運算子  
 <xref:System.Linq.Enumerable.Take%2A> 和 <xref:System.Linq.Enumerable.Skip%2A> 在用於對 [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] 進行的查詢中時會有一些限制。 如需詳細資訊，請參閱中的"Skip 和 Take 例外狀況在 SQL Server 2000"項目[疑難排解](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md)。  
  
## <a name="object-materialization"></a>物件具體化  
 Materialization 作業會針對一個或多個 SQL 查詢傳回的資料列建立 CLR 物件。  
  
-   下列呼叫會*本機執行*具體化的一部分：  
  
    -   建構函式  
  
    -   投影中的 `ToString` 方法  
  
    -   投影中的型別轉換  
  
-   請遵循的方法<xref:System.Linq.Enumerable.AsEnumerable%2A>方法會*在本機執行*。 這個方法不會造成立即執行。  
  
-   您可以使用 `struct` 做為查詢結果的傳回型別或是結果型別的成員。 實體必須為類別。 匿名型別會具體化成為類別執行個體，但具名 struct (非實體) 則可以用於投影中。  
  
-   查詢結果所傳回型別的成員可以屬於型別 <xref:System.Linq.IQueryable%601>。 它會具體化成為本機集合。  
  
-   下列方法會造成*立即 materialization*方法會套用至序列的：  
  
    -   <xref:System.Linq.Enumerable.ToList%2A>  
  
    -   <xref:System.Linq.Enumerable.ToDictionary%2A>  
  
    -   <xref:System.Linq.Enumerable.ToArray%2A>  
  
## <a name="see-also"></a>另請參閱  
 [參考資料](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)  
 [傳回或略過序列中的項目](../../../../../../docs/framework/data/adonet/sql/linq/return-or-skip-elements-in-a-sequence.md)  
 [串連兩個序列](../../../../../../docs/framework/data/adonet/sql/linq/concatenate-two-sequences.md)  
 [傳回兩個序列之間的集合差異](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-difference-between-two-sequences.md)  
 [傳回兩個序列的集合交集](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-intersection-of-two-sequences.md)  
 [傳回兩個序列的集合聯集](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-union-of-two-sequences.md)
