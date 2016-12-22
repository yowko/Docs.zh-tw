---
title: "查詢運算式基本概念 (C# 程式設計手冊) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "查詢 [C# 中的 LINQ], 基本知識"
  - "查詢運算式 [C# 中的 LINQ], 基本知識"
  - "查詢運算式 [C# 中的 LINQ], 查詢執行"
ms.assetid: d3e1f4e6-1cf0-4066-87e3-1a42387223a6
caps.latest.revision: 32
caps.handback.revision: 32
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 查詢運算式基本概念 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

## 查詢的意義與用途  
 「*查詢*」\(Query\) 是一組指令，用於敘述哪些資料要從資料來源擷取，以及擷取的資料應該採用何種形式和組織方式呈現。  查詢與其本身所產生的結果並不同。  
  
 一般來說，來源資料都會按照邏輯組織成同一類型的項目序列。  SQL 資料庫資料表包含資料行序列。  同樣地，[!INCLUDE[vstecado](../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)] <xref:System.Data.DataTable> 包含 <xref:System.Data.DataRow> 物件的序列，  XML 檔案中有 XML 項目的「序列」\(不過這些項目是排列成階層式的樹狀結構\)；  而記憶體中的集合則包含物件的序列。  
  
 從應用程式的觀點來看，原始來源資料的特定型別和結構並不重要。  應用程式一定會將來源資料視為 <xref:System.Collections.Generic.IEnumerable%601> 或 <xref:System.Linq.IQueryable%601> 集合。  在 [!INCLUDE[sqltecxlinq](../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 中，來源資料會顯示成 `IEnumerable`\<<xref:System.Xml.Linq.XElement>\>。  在 [!INCLUDE[linq_dataset](../../../csharp/programming-guide/linq-query-expressions/includes/linq_dataset_md.md)] 中則是 `IEnumerable`\<<xref:System.Data.DataRow>\>。  在 [!INCLUDE[vbtecdlinq](../../../csharp/language-reference/keywords/includes/vbtecdlinq_md.md)] 中則是您定義之任何自訂物件 \(用來表示 SQL 資料表中的資料\) 的 `IEnumerable` 或 `IQueryable`。  
  
 若指定這種來源序列，查詢可以執行下列三項工作的其中一項：  
  
-   擷取項目的子集以產生新序列，而不修改個別的項目。  接著，查詢可以使用各種方式將傳回的序列排序或分組，如下列範例所示 \(假設 `scores` 是 `int[]`\)：  
  
     [!code-cs[csrefQueryExpBasics#45](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/query-expression-basics_1.cs)]  
  
-   依前述範例的相同方式擷取項目的序列，但是將它們轉換成新的物件型別。  例如，查詢可能只會從資料來源的特定客戶記錄中擷取姓氏，  也可能擷取完整的記錄，接著用它來建構另一種記憶體中物件型別或是 XML 資料，然後再產生最終的結果序列。  下列範例示範如何將 `int` 轉換為 `string`。  請注意 `highScoresQuery` 的新型別。  
  
     [!code-cs[csrefQueryExpBasics#46](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/query-expression-basics_2.cs)]  
  
-   擷取有關來源資料的單一值，例如：  
  
    -   符合特定條件的項目數目。  
  
    -   具有最大值或最小值的項目。  
  
    -   符合條件的第一個項目，或是指定的一組項目中特定值的總和。  例如，下列查詢會從 `scores` 整數陣列中，傳回分數高於 80 分的成績筆數。  
  
     [!code-cs[csrefQueryExpBasics#47](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/query-expression-basics_3.cs)]  
  
     在前面的範例中，請注意在呼叫 `Count` 方法之前，以括號括住查詢運算式的用法。  您也可以使用新變數儲存具體結果。  這種方法比較容易理解，因為它會將儲存查詢的變數與儲存結果的查詢分開。  
  
     [!code-cs[csrefQueryExpBasics#48](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/query-expression-basics_4.cs)]  
  
 在前面的範例中，查詢是在呼叫 `Count` 時執行，因為 `Count` 必須反覆查看結果，才能確定 `highScoresQuery` 所傳回的項目數目。  
  
## 什麼是查詢運算式？  
 「*查詢運算式*」\(Query Expression\) 是以查詢語法表示的查詢。  查詢運算式是第一級的語言建構，  它就像其他任何運算式一樣，而且可以在 C\# 運算式適用的任何內容中使用。  查詢運算式是由一組子句組成，而這些子句都是以類似 SQL 或 XQuery 的宣告式語法撰寫而成。  每個子句也會包含一個或多個 C\# 運算式，而這些運算式可能本身就是查詢運算式，或是包含查詢運算式。  
  
 查詢運算式必須以 [from](../../../csharp/language-reference/keywords/from-clause.md) 子句開頭，並以 [select](../../../csharp/language-reference/keywords/select-clause.md) 或 [group](../../../csharp/language-reference/keywords/group-clause.md) 子句結尾。  在第一個 `from` 子句和最後的 `select` 或 `group` 子句中間，也可以包含下列一個或多個子句：[where](../../../csharp/language-reference/keywords/where-clause.md)、[orderby](../../../csharp/language-reference/keywords/orderby-clause.md)、[join](../../../csharp/language-reference/keywords/join-clause.md)、[let](../../../csharp/language-reference/keywords/let-clause.md)，甚至是額外的 [from](../../../csharp/language-reference/keywords/from-clause.md) 子句。  您也可以使用 [into](../../../csharp/language-reference/keywords/into.md) 關鍵字，讓 `join` 或 `group` 子句的結果變成同一個查詢運算式中其他查詢子句的來源。  
  
### 查詢變數  
 在 [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] 中，查詢變數是儲存「*查詢*」\(Query\) 而非儲存查詢之「*結果*」\(Result\) 的變數。更具體來說，查詢變數一定是可列舉的型別，當您在 `foreach` 陳述式中反覆查看這個型別，或是直接呼叫其 `IEnumerator.MoveNext` 方法時，這個型別就會產生項目序列。  
  
 下列程式碼範例示範的簡單查詢運算式具有一個資料來源、一個篩選子句、一個排序子句，而且不會轉換來源項目。  查詢的結尾則是 `select` 子句。  
  
 [!code-cs[csrefQueryExpBasics#49](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/query-expression-basics_5.cs)]  
  
 在前面的範例中，`scoreQuery` 是「*查詢變數*」\(Query Variable\)，有時也簡稱為「*查詢*」\(Query\)。  查詢變數並未儲存 `foreach` 迴圈所產生的任何實際結果資料。  當 `foreach` 陳述式執行時，查詢結果不會透過查詢變數 `scoreQuery` 傳回，  而會透過反覆運算變數 `testScore` 傳回。  `scoreQuery` 變數可以在第二個 `foreach` 迴圈中反覆查看。  只要變數和資料來源都沒有修改過，就會產生相同的結果。  
  
 查詢變數可以儲存以查詢語法、方法語法或兩種語法組合來表示的查詢。  在下面的範例中，`queryMajorCities` 和 `queryMajorCities2` 都是查詢變數：  
  
 [!code-cs[csrefQueryExpBasics#50](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/query-expression-basics_6.cs)]  
  
 另外，雖然下列兩個範例顯示的每個變數都是以查詢進行初始化，但是它們不是查詢變數。  因為這些變數儲存的是結果，所以它們並不是查詢變數：  
  
 [!code-cs[csrefQueryExpBasics#51](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/query-expression-basics_7.cs)]  
  
> [!NOTE]
>  在 [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] 文件中，儲存查詢的變數的名稱中都會包含 "query" 這個字；  如果是儲存實際結果的變數，它們的名稱中就不會有 "query" 這個字。  
  
 如需各種表示查詢之方法的詳細資訊，請參閱[Query Syntax and Method Syntax in LINQ](../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)。  
  
#### 查詢變數的明確和隱含型別  
 本文件通常都會提供查詢變數的明確型別，以顯示查詢變數和 [select 子句](../../../csharp/language-reference/keywords/select-clause.md)的型別關聯性。  不過，您也可以使用 [var](../../../csharp/language-reference/keywords/var.md) 關鍵字，指示編譯器在編譯時期推斷查詢變數 \(或其他任何區域變數\) 的型別。  例如，本主題前面所示的查詢範例也可以使用隱含型別來表示：  
  
 [!code-cs[csrefQueryExpBasics#52](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/query-expression-basics_8.cs)]  
  
 如需詳細資訊，請參閱 [隱含類型區域變數](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)和 [Type Relationships in LINQ Query Operations](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)。  
  
### 起始查詢運算式  
 查詢運算式必須以 `from` 子句開頭。  這個子句同時指定了資料來源和範圍變數。  在周遊來源序列的同時，範圍變數代表來源序列中的每個連續項目。  範圍變數是強型別 \(Strongly Typed\)，以資料來源中項目的型別做為依據。  在下面的範例中，因為 `countries` 是 `Country` 物件的陣列，所以範圍變數的型別也是 `Country`。  由於範圍變數是強型別，因此您可以使用點運算子存取該型別的任何可用成員。  
  
 [!code-cs[csrefQueryExpBasics#53](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/query-expression-basics_9.cs)]  
  
 在以分號或「*接續*」\(Continuation\) 子句結束查詢之前，範圍變數都會在範圍中。  
  
 查詢運算式可以包含多個 `from` 子句。  當來源序列中的每個項目本身就是集合或者包含了集合時，請使用額外的 `from` 子句。  例如，假設您有一個 `Country` 物件的集合，而每個物件都包含一個名為 `Cities` 的 `City` 物件集合。  如果要查詢每個 `Country` 中的 `City` 物件，請依照以下所示，使用兩個 `from` 子句：  
  
 [!code-cs[csrefQueryExpBasics#54](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/query-expression-basics_10.cs)]  
  
 如需詳細資訊，請參閱 [from 子句](../../../csharp/language-reference/keywords/from-clause.md)。  
  
### 結束查詢運算式  
 查詢運算式必須以 `select` 子句或 `group` 子句結尾。  
  
#### group 子句  
 請使用 `group` 子句產生依您指定之索引鍵組織的群組序列。  這個索引鍵可以是任何資料型別。  例如，下列查詢會建立包含一個或多個 `Country` 物件的群組序列，而這些物件的索引鍵是 `char` 值。  
  
 [!code-cs[csrefQueryExpBasics#55](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/query-expression-basics_11.cs)]  
  
 如需群組的詳細資訊，請參閱 [group 子句](../../../csharp/language-reference/keywords/group-clause.md)。  
  
#### select 子句  
 請使用 `select` 子句產生其他所有類型的序列。  簡單的 `select` 子句只會產生與資料來源中的物件相同之物件序列。  在這個範例中，資料來源包含 `Country` 物件。  `orderby` 子句只會將項目排序成新的順序，而 `select` 子句則會產生重新排序過的 `Country` 物件序列。  
  
 [!code-cs[csrefQueryExpBasics#56](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/query-expression-basics_12.cs)]  
  
 `select` 子句可以用來將來源資料轉換成新型別的序列。  這種轉換也稱為「*投影*」\(Projection\)。  在下面的範例中，`select` 子句會「*投影*」\(Project\) 匿名型別的序列，而該序列中只包含原始項目中的欄位子集。  請注意，新的物件是使用物件初始設定式來初始化。  
  
 [!code-cs[csrefQueryExpBasics#57](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/query-expression-basics_13.cs)]  
  
 如需使用 `select` 子句轉換來源資料之所有方法的詳細資訊，請參閱 [select 子句](../../../csharp/language-reference/keywords/select-clause.md)。  
  
#### 使用 into 進行接續  
 您可以在 `select` 或 `group` 子句中使用 `into` 關鍵字，建立用來儲存查詢的暫存識別項。  當您必須在群組或選取作業完成之後對查詢執行額外的查詢作業時，請執行上述作業。  在下面的範例中，`countries` 會根據 1 千萬的人口範圍來分組。  在建立這些群組之後，其他子句會篩選掉某些群組，然後再依遞增順序排序剩下的群組。  為了執行這些額外的作業，必須使用 `countryGroup` 所代表的接續。  
  
 [!code-cs[csrefQueryExpBasics#58](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/query-expression-basics_14.cs)]  
  
 如需詳細資訊，請參閱 [into](../../../csharp/language-reference/keywords/into.md)。  
  
### 篩選、排序和聯結  
 在開頭的 `from` 子句以及結尾的 `select` 或 `group` 子句之間，其他所有的子句 \(`where`、`join`、`orderby`、`from`、`let`\) 都是選擇性的子句。  任何選擇性子句在查詢主體中的使用次數可以是零次，也可以是多次。  
  
#### where 子句  
 請使用 `where` 子句，依據一個或多個述詞運算式，篩選掉來源資料中的項目。  下列範例中的 `where` 子句有兩個述詞。  
  
 [!code-cs[csrefQueryExpBasics#59](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/query-expression-basics_15.cs)]  
  
 如需詳細資訊，請參閱 [where 子句](../../../csharp/language-reference/keywords/where-clause.md)。  
  
#### orderby 子句  
 請使用 `orderby` 子句，依遞增或遞減順序排序結果。  您也可以指定次要排序順序。  下列範例使用 `Area` 屬性對 `country` 物件執行主要排序，  接著再使用 `Population` 屬性執行次要排序。  
  
 [!code-cs[csrefQueryExpBasics#60](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/query-expression-basics_16.cs)]  
  
 `ascending` 關鍵字是選擇性的；如果沒有指定順序，它就是預設的排序順序。  如需詳細資訊，請參閱 [orderby 子句](../../../csharp/language-reference/keywords/orderby-clause.md)。  
  
#### join 子句  
 請使用 `join` 子句，依據各項目中特定索引鍵的相等比較，讓某個資料來源的項目和另一個資料來源的項目產生關聯和 \(或\) 合併在一起。  在 [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] 中，聯結作業是在物件序列上執行，而這些物件的項目分屬於不同的型別。  在您聯結兩個序列之後，必須使用 `select` 或 `group` 陳述式，指定要儲存在輸出序列中的項目。  您也可以使用匿名型別，將每一組相關項目的屬性合併成輸出序列的新型別。  下列範例會讓 `Category` 屬性符合 `categories` 字串陣列中其中一個分類的 `prod` 物件產生關聯，  並篩選掉 `Category` 不符合 `categories` 中任何字串的產品。  `select` 陳述式會投影新的型別，而這個新型別的屬性同時取自 `cat` 和 `prod`。  
  
 [!code-cs[csrefQueryExpBasics#61](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/query-expression-basics_17.cs)]  
  
 您也可以執行群組聯結，方法是使用 [into](../../../csharp/language-reference/keywords/into.md) 關鍵字，將 `join` 作業的結果儲成為暫時變數。  如需詳細資訊，請參閱 [join 子句](../../../csharp/language-reference/keywords/join-clause.md)。  
  
#### let 子句  
 請使用 `let` 子句儲存運算式的結果，例如新範圍變數中的方法呼叫。  在下列範例中，範圍變數 `firstName` 會儲存 `Split` 傳回之字串陣列的第一個元素。  
  
 [!code-cs[csrefQueryExpBasics#62](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/query-expression-basics_18.cs)]  
  
 如需詳細資訊，請參閱 [let 子句](../../../csharp/language-reference/keywords/let-clause.md)。  
  
### 查詢運算式中的子查詢  
 查詢子句本身可以包含查詢運算式，而這個運算式也稱為「*子查詢*」\(Subquery\)。  每個子查詢都以自己的 `from` 子句開頭，而這個子句不一定會指向與第一個 `from` 子句相同的資料來源。  例如，下列查詢顯示的是 select 陳述式中用來擷取群組作業結果的查詢運算式。  
  
 [!code-cs[csrefQueryExpBasics#63](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/query-expression-basics_19.cs)]  
  
 如需詳細資訊，請參閱 [如何：在分組作業上執行子查詢](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-a-subquery-on-a-grouping-operation.md)。  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [LINQ 查詢運算式](../../../visual-basic/reference/command-line-compiler/index.md)   
 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)   
 [查詢關鍵字 \(LINQ\)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [Standard Query Operators Overview](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)