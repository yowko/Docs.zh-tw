---
title: 基本 LINQ 查詢作業 (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- orderby clause [LINQ in C#]
- ordering data [LINQ in C#]
- selecting data [LINQ in C#]
- queries [LINQ in C#], basic operations
- grouping data [LINQ in C#]
- data sources [LINQ in C#]
- sorting data [LINQ in C#]
- projections [LINQ in C#]
- filtering data [LINQ in C#]
- joining data [LINQ in C#]
- select clause [LINQ in C#]
- LINQ [C#], basic query operations
- join clause [LINQ in C#]
- group clause [LINQ in C#]
ms.assetid: a7ea3421-1cf4-4df7-832a-aa22fe6379e9
ms.openlocfilehash: 2825b79c9638fff050522da43184a8d95a3fe02f
ms.sourcegitcommit: bd4fa78f5a46133efdead1bc692a9aa2811d7868
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/23/2018
ms.locfileid: "42752175"
---
# <a name="basic-linq-query-operations-c"></a>基本 LINQ 查詢作業 (C#)
本主題簡介 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢運算式以及在查詢中執行的一些一般類型的作業。 下列各主題提供更詳細的資訊：  
  
 [LINQ 查詢運算式](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
  
 [標準查詢運算子概觀 (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
  
 [逐步解說：在 C# 中撰寫查詢](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)  
  
> [!NOTE]
>  如果您已經熟悉 SQL 或 XQuery 這類查詢語言，則可以略過本主題的大部分內容。 閱讀下一節中的＜`from` 子句＞，以了解 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢運算式中的子句順序。  
  
## <a name="obtaining-a-data-source"></a>取得資料來源  
 在 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢中，第一個步驟是指定資料來源。 在 C# 中，如同大多數程式設計語言一樣，必須先宣告變數，才能使用變數。 在 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢中，依序會先出現 `from` 子句來引進資料來源 (`customers`) 和「範圍變數」(`cust`)。  
  
 [!code-csharp[csLINQGettingStarted#23](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_1.cs)]  
  
 範圍變數就像 `foreach` 迴圈中的反覆項目變數，差異在於查詢運算式中沒有實際反覆項目。 執行查詢時，範圍變數將會作為 `customers` 中每個後續項目的參考。 因為編譯器可以推斷 `cust` 的類型，所以您不需要明確予以指定。 `let` 子句可以引進其他範圍變數。 如需詳細資訊，請參閱 [let 子句](../../../../csharp/language-reference/keywords/let-clause.md)。  
  
> [!NOTE]
>  針對 <xref:System.Collections.ArrayList> 這類非泛型資料來源，必須明確範圍變數的類型。 如需詳細資訊，請參閱[如何：使用 LINQ 查詢 ArrayList (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md) 和 [from 子句](../../../../csharp/language-reference/keywords/from-clause.md)。  
  
## <a name="filtering"></a>篩選  
 最常見的查詢作業可能是以 Boolean 運算式的形式套用篩選條件。 篩選會導致查詢僅傳回運算式成立的項目。 結果是使用 `where` 子句所產生。 篩選實際上會指定要從來源序列中排除的項目。 在下列範例中，只會傳回地址在倫敦的 `customers`。  
  
 [!code-csharp[csLINQGettingStarted#24](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_2.cs)]  
  
 您可以使用熟悉的 C# 邏輯 `AND` 和 `OR` 運算式，在 `where` 子句中套用所需的篩選運算式。 例如，若只要傳回來自 "London" `AND` 名稱為 "Devon" 的客戶，請撰寫下列程式碼︰  
  
 [!code-csharp[csLINQGettingStarted#25](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_3.cs)]  
  
 若要傳回來自 London 或 Paris 的客戶，請撰寫下列程式碼︰  
  
 [!code-csharp[csLINQGettingStarted#26](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_4.cs)]  
  
 如需詳細資訊，請參閱 [where 子句](../../../../csharp/language-reference/keywords/where-clause.md)。  
  
## <a name="ordering"></a>排序  
 通常很方便就可以排序所傳回的資料。 `orderby` 子句會根據所排序類型的預設比較子來排序所傳回序列中的項目。 例如，可以擴充下列查詢，以根據 `Name` 屬性來排序結果。 因為 `Name` 是字串，所以預設比較子會執行從 A 到 Z 依字母順序排列的排序。  
  
 [!code-csharp[csLINQGettingStarted#27](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_5.cs)]  
  
 若要以相反順序排序結果 (從 Z 到 A)，請使用 `orderby…descending` 子句。  
  
 如需詳細資訊，請參閱 [orderby 子句](../../../../csharp/language-reference/keywords/orderby-clause.md)。  
  
## <a name="grouping"></a>群組  
 `group` 子句可讓您根據指定的索引鍵，將結果分組。 例如，您可以指定應該依 `City` 來群組結果；因此，來自 London 或 Paris 的所有客戶位於個別的群組中。 在此情況下，`cust.City` 是索引鍵。  
  
 [!code-csharp[csLINQGettingStarted#28](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_6.cs)]  
  
 使用 `group` 子句結束查詢時，結果的形式是一或多個清單。 清單中的每個項目都是一個物件，內含 `Key` 成員和群組在該索引鍵下的項目清單。 逐一查看產生一序列群組的查詢時，必須使用巢狀 `foreach` 迴圈。 外部迴圈會逐一查看每個群組，內部迴圈則會逐一查看每個群組的成員。  
  
 如果您必須參照群組作業的結果，則可以使用 `into` 關鍵字來建立可供進一步查詢的識別碼。 下列查詢只會傳回包含兩個以上客戶的群組︰  
  
 [!code-csharp[csLINQGettingStarted#29](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_7.cs)]  
  
 如需詳細資訊，請參閱 [group 子句](../../../../csharp/language-reference/keywords/group-clause.md)。  
  
## <a name="joining"></a>聯結  
 聯結作業會建立資料來源中未明確模型化之序列間的關聯。 例如，您可以執行聯結來尋找位置相同的所有客戶和經銷商。 在 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 中，`join` 子句一律會作用於物件集合，而不是直接作用於資料庫資料表。  
  
 [!code-csharp[csLINQGettingStarted#36](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_8.cs)]  
  
 在 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 中，您不需要像在 SQL 中經常地使用 `join`，因為 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 中的外部索引鍵在物件模型中會呈現為保存項目集合的屬性。 例如，包含 `Order` 物件集合的 `Customer` 物件。 您可以使用點標記法來存取順序，而不是執行聯結：  
  
```  
from order in Customer.Orders...  
```  
  
 如需詳細資訊，請參閱 [join 子句](../../../../csharp/language-reference/keywords/join-clause.md)。  
  
## <a name="selecting-projections"></a>選取 (投影)  
 `select` 子句會產生查詢的結果，並指定每個所傳回項目的「圖形」或類型。 例如，您可以根據計算或新物件建立指定結果包含完整 `Customer` 物件、僅一個成員、成員子集，還是某個完全不同的結果類型。 `select` 子句不只產生一份來源項目時，作業稱為「投影」。 使用投影來轉換資料是 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢運算式的強大功能。 如需詳細資訊，請參閱[使用 LINQ 轉換資料 (C#)](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md) 和 [select 子句](../../../../csharp/language-reference/keywords/select-clause.md)。  
  
## <a name="see-also"></a>請參閱  
 [開始使用 C# 中的 LINQ](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [LINQ 查詢運算式](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [逐步解說：在 C# 中撰寫查詢](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)  
 [查詢關鍵字 (LINQ)](../../../../csharp/language-reference/keywords/query-keywords.md)  
 [匿名類型](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
