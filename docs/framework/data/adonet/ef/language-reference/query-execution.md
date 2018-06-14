---
title: 查詢執行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c0e6cf23-63ac-47dd-bfe9-d5bdca826fac
ms.openlocfilehash: f152146e7483c6b3c162fd81f20f359e6c82123a
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33804816"
---
# <a name="query-execution"></a>查詢執行
使用者建立 LINQ 查詢之後，查詢就會轉換成命令樹。 命令樹一種可與 Entity Framework 比較的查詢表示方式。 接下來命令樹會針對資料來源執行。 查詢執行期間會評估所有查詢運算式 (也就是查詢的所有元件)，包括結果具體化中使用的運算式。  
  
 查詢運算式執行的時間點可能會變動。 LINQ 查詢一定是在重複處理查詢變數時執行，而不是在查詢變數建立後執行。 這稱為*延後執行*。 您也可以強制查詢立即執行，這對於快取查詢結果很有用處。 本主題稍後將提供這方面的說明。  
  
 執行 LINQ to Entities 查詢時，查詢中的某些運算式可能會在伺服器上執行，而某些部分則可能在本機用戶端上執行。 在伺服器上執行查詢以前，會先在用戶端評估運算式。 如果運算式是在用戶端上評估，該評估的結果會代替查詢中的運算式，然後會在伺服器上執行查詢。 由於查詢會在資料存來源執行，所以資料來源組態會覆寫用戶端中指定的行為。 例如，null 值的處理和數值的有效位數都會因伺服器設定而異。 在伺服器上執行查詢的期間擲回的任何例外狀況，都會直接傳遞給用戶端。  
 
> [!TIP]
> 為方便摘要查詢運算子，以資料表格式，可讓您快速識別操作員的執行行為，請參閱[分類的標準查詢運算子的執行方式 (C#) 所](../../../../../csharp/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)。

## <a name="deferred-query-execution"></a>延後查詢執行  
 在傳回值序列的查詢中，查詢變數本身絕不會保存查詢結果，只會儲存查詢命令而已。 查詢的執行會延後，直到在 `foreach` 或 `For Each` 迴圈 (Loop) 中反覆查看查詢變數為止。 這稱為*延後執行*; 也就是查詢執行會在建構查詢後一些時間。 這表示您可以隨時都可以執行查詢。 例如，當您擁有一個正由其他應用程式更新的資料庫時，這就很有用。 您可以在應用程式中建立擷取最新資訊的查詢，然後重複執行此查詢，以便每次都傳回更新的資訊。  
  
 延後執行可結合多個查詢或擴充單一查詢。 擴充單一查詢時，它會修改成包含新的作業，而且最終的執行將反映這些變更。 在下列範例中，第一個查詢會傳回所有產品。 第二個查詢會使用 `Where` 來擴充第一個查詢，以便傳回大小為 "L" 的所有產品：  
  
 [!code-csharp[DP L2E Conceptual Examples#Composing1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#composing1)]
 [!code-vb[DP L2E Conceptual Examples#Composing1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#composing1)]  
  
 在查詢執行之後，所有後續查詢都會使用記憶體中的 LINQ 運算子。 使用 `foreach` 或 `For Each` 陳述式或呼叫其中一個 LINQ 轉換運算子來重複處理查詢變數，將會造成立即執行。 這些轉換運算子包咶：<xref:System.Linq.Enumerable.ToList%2A>、<xref:System.Linq.Enumerable.ToArray%2A>、<xref:System.Linq.Enumerable.ToLookup%2A> 和 <xref:System.Linq.Enumerable.ToDictionary%2A>。  
  
## <a name="immediate-query-execution"></a>立即執行查詢  
 產生一連串值的查詢會延後執行，但是傳回單一值的查詢則是立即執行。 單一子句查詢的某些範例包括 <xref:System.Linq.Enumerable.Average%2A>、<xref:System.Linq.Enumerable.Count%2A>、<xref:System.Linq.Enumerable.First%2A> 和 <xref:System.Linq.Enumerable.Max%2A>。 這些查詢會立即執行是因為查詢必須產生用來計算單一結果的序列。 您也可以用強制方式立即執行。 如果您要快取查詢結果，這種方式就很有用處。 如果要強制不是產生單一值的查詢立即執行，您可以在查詢或查詢變數上呼叫 <xref:System.Linq.Enumerable.ToList%2A> 方法、<xref:System.Linq.Enumerable.ToDictionary%2A> 方法，或 <xref:System.Linq.Enumerable.ToArray%2A> 方法。 以下範例使用 <xref:System.Linq.Enumerable.ToArray%2A> 方法將序列立即評估為陣列。  
  
 [!code-csharp[DP L2E Examples#ToArray](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#toarray)]
 [!code-vb[DP L2E Examples#ToArray](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#toarray)]  
  
 您也可以將 `foreach` 或 `For Each` 迴圈緊接在查詢運算式之後，用這種方式來強制執行，但是呼叫 <xref:System.Linq.Enumerable.ToList%2A> 或 <xref:System.Linq.Enumerable.ToArray%2A> 必須快取單一集合物件中的所有資料。  
  
## <a name="store-execution"></a>存放區執行  
 一般而言，LINQ to Entities 中的運算式是在伺服器上評估，而運算式的行為也不會依照 Common Language Runtime (CLR) 語意，而是依照資料來源的語意。 不過這種情況也有例外，例如運算式在用戶端上執行時就不是這種情況。 舉例來講，如果伺服器與用戶端是在不同的時區，這種情況可能會導致無法預期的結果。  
  
 查詢中的某些運算式可能會在用戶端上執行。 一般而言，大部分查詢執行應該都是發生在伺服器上。 除了針對對應到資料來源的查詢項目執行的方法之外，查詢中也常常有可以在本機執行的運算式。 查詢運算式的本機執行會產生可以使用在查詢執行或結果建構中的值。  
  
 某些運算永遠是在用戶端執行，例如值的繫結、子運算式、來自結束的子查詢，以及物件具體化成為查詢結果。 這種情況的最終效果就是這些項目 (例如參數值) 無法在執行期間更新。 匿名型別可以用內嵌方式建構在資料來源上，但不應視為必須如此。 內嵌群組也可以建構在資料來源中，但這並不適用於每個執行個體。 一般而言，最好不要假設何者是建構在伺服器上。  
  
 本節說明程式碼在用戶端上以本機方式執行的案例。 如需詳細資訊，了解哪種類型的運算式會在本機執行，請參閱[LINQ to Entities 查詢中的運算式](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)。  
  
### <a name="literals-and-parameters"></a>常值和參數  
 區域變數 (例如以下範例中的 `orderID` 變數) 會在用戶端上評估。  
  
 [!code-csharp[DP L2E Conceptual Examples#LiteralParameter1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#literalparameter1)]
 [!code-vb[DP L2E Conceptual Examples#LiteralParameter1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#literalparameter1)]  
  
 方法參數也是在用戶端上評估。 以下傳入 `orderID` 方法的 `MethodParameterExample` 參數就是這種範例。  
  
 [!code-csharp[DP L2E Conceptual Examples#MethodParameterExample](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#methodparameterexample)]
 [!code-vb[DP L2E Conceptual Examples#MethodParameterExample](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#methodparameterexample)]  
  
### <a name="casting-literals-on-the-client"></a>在用戶端上將常值轉型  
 從 `null` 轉型為 CLR 型別是在用戶端上執行：  
  
 [!code-csharp[DP L2E Conceptual Examples#NullCastToString](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#nullcasttostring)]
 [!code-vb[DP L2E Conceptual Examples#NullCastToString](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#nullcasttostring)]  
  
 轉型為某種型別 (例如何為 null 的 <xref:System.Decimal>) 是在用戶端上執行：  
  
 [!code-csharp[DP L2E Conceptual Examples#CastToNullable](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#casttonullable)]
 [!code-vb[DP L2E Conceptual Examples#CastToNullable](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#casttonullable)]  
  
### <a name="constructors-for-literals"></a>常值的建構函式  
 可以對應到概念模型類型的新 CLR 類型是在用戶端上執行：  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstructorForLiteral](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constructorforliteral)]
 [!code-vb[DP L2E Conceptual Examples#ConstructorForLiteral](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constructorforliteral)]  
  
 新陣列也是在用戶端上執行。  
  
## <a name="store-exceptions"></a>存放區例外狀況  
 在查詢執行期間遭遇的任何存放區錯誤都會傳遞到用戶端，不予對應或處理。  
  
## <a name="store-configuration"></a>存放區組態  
 查詢在存放區上執行時，存放區組態會取代所有用戶端行為，並且對所有運算和運算式表示存放區語意。 這可能會在 null 比較、GUID 順序、涉及非精確資料型別 (例如浮點數型別或 <xref:System.DateTime>) 之運算的有效位數和精確度，以及字串運算等範圍造成 CLR 和存放區執行之間的行為差異。 檢查查詢結果時請務必留意這些情況。  
  
 例如，下面是 CLR 與 SQL Server 之間的一些行為差異：  
  
-   SQL Server 排序 GUID 的方式與 CLR 不同。  
  
-   在 SQL Server 上處理 Decimal 型別時也會有結果有效位數的差異。 這是因為 SQL Server 的 decimal 型別要求固定有效位數所造成。 舉例來講，<xref:System.Decimal> 值 0.0、0.0 和 1.0 的平均在用戶端的記憶體中為 0.3333333333333333333333333333，但是在存放區則為 0.333333 (依據 SQL Server 之 decimal 型別的預設有效位數)。  
  
-   某些字串比較運算在 SQL Server 中的處理方式也不同於 CLR。 字串比較行為會因伺服器上的定序設定而異。  
  
-   函式或方法呼叫包含在 LINQ to Entities 查詢中時會對應到 Entity Framework 中的標準函式，然後再轉譯成 Transact-SQL 並且在 SQL Server 資料庫上執行。 但在某些情況下這些對應函式所表現的行為可能會不同於基底類別庫中的實作。 舉例來講，以空字串為參數呼叫 <xref:System.String.Contains%2A>、<xref:System.String.StartsWith%2A> 和 <xref:System.String.EndsWith%2A> 方法，在 CLR 中執行時將會傳回 `true`，但是在 SQL Server 中執行時卻會傳回 `false`。 <xref:System.String.EndsWith%2A> 方法也會傳回不同的結果，因為假如兩個字串只有結尾泛空白字元不同，SQL Server 會將它們視為相等，但 CLR 卻會將它們視為不相等。 以下範例就是說明這種情況：  
  
 [!code-csharp[DP L2E Conceptual Examples#CanonicalFuncVsCLRBaseType](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#canonicalfuncvsclrbasetype)]
 [!code-vb[DP L2E Conceptual Examples#CanonicalFuncVsCLRBaseType](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#canonicalfuncvsclrbasetype)]
