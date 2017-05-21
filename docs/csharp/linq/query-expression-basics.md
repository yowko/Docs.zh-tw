---
title: "查詢運算式基本概念"
description: "介紹查詢運算式的相關概念"
keywords: ".NET、.NET Core、C#"
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 027db1f8-346f-44d2-a16e-043fcea3a4e0
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9fd0ef3c71d66ceca28d3ae7025058df469655c2
ms.lasthandoff: 03/13/2017

---
# <a name="query-expression-basics"></a>查詢運算式基本概念

## <a name="what-is-a-query-and-what-does-it-do"></a>什麼是查詢？它有哪些功能？ 

 *「查詢」*是一組指令，描述要從一個或多個指定資料來源擷取的資料以及所傳回資料應該具有的組織結構和組織。 查詢與其產生的結果不同。  
  
 一般而言，來源資料也會以邏輯方式組織成一系列相同類型的項目。 例如，SQL 資料庫資料表包含一系列的資料列。 在 XML 檔案中，有一「序列」的 XML 項目 (雖然這些都是以階層方式組織成樹狀結構)。 記憶體內部集合包含一系列的物件。 
  
 從應用程式的觀點來看，原始來源資料的特定類型和結構並不重要。 應用程式一律會將來源資料看成 <xref:System.Collections.Generic.IEnumerable%601> 或 <xref:System.Linq.IQueryable%601> 集合。 例如，在 LINQ to XML 中，來源資料就會顯示為 `IEnumerable`\<<xref:System.Xml.Linq.XElement>>。  
  
 如果指定此來源序列，則查詢可能會執行三個事項之一︰  
  
-   擷取項目子集，以產生新序列，而不需要修改個別項目。 查詢接著可能會以各種方式排序或分組所傳回的序列，如下列範例所示 (假設 `scores` 是 `int[]`)：  
  
     [!code-cs[csrefQueryExpBasics#45](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_1.cs)]  
  
-   擷取上述範例中的一系列項目，但將它們轉換為新類型的物件。 例如，查詢只可能從資料來源的特定客戶記錄中擷取最後一個名稱。 或者，它可能會擷取完整記錄，接著先使用這筆記錄來建構另一個記憶體內部物件類型，或甚至 XML 資料，再產生最終結果序列。 下列範例示範從 `int` 到 `string` 的投影。 請注意 `highScoresQuery` 的新類型。  
  
     [!code-cs[csrefQueryExpBasics#46](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_2.cs)]  
  
-   擷取來源資料的單一值，例如︰  
  
    -   符合特定條件的項目數。  
  
    -   具有最大或最小值的項目。  
  
    -   符合條件或所指定項目集中特定值總和的第一個項目。 例如，下列查詢會傳回 `scores` 整數陣列中大於 80 的分數︰  
  
     [!code-cs[csrefQueryExpBasics#47](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_3.cs)]  
  
     在上述範例中，請記住使用括號括住查詢運算式，再呼叫 `Count` 方法。 您也可以使用新變數來儲存具體結果，以表示這項情況。 這項技術是更容易閱讀，因為它會區隔可儲存查詢的變數與可儲存結果的查詢。  
  
     [!code-cs[csrefQueryExpBasics#48](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_4.cs)]  
  
 在上述範例中，在呼叫 `Count` 時執行查詢，因為 `Count` 必須逐一查看結果，才能判斷 `highScoresQuery` 所傳回的項目數。  
  
## <a name="what-is-a-query-expression"></a>什麼是查詢運算式？  

 *「查詢運算式」*是以查詢語法表示的查詢。 查詢運算式是第一類語言建構。 它就像任何其他運算式一樣，可以用於 C# 運算式有效的任何內容。 查詢運算式包含以 SQL 或 XQuery 類似的宣告式語法所撰寫的一組子句。 每個子句接著會包含一個或多個 C# 運算式，而且這些運算式本身可能是查詢運算式或包含查詢運算式。  
  
 查詢運算式的開頭必須是 [from](../language-reference/keywords/from-clause.md) 子句，結尾則必須是 [select](../language-reference/keywords/select-clause.md) 或 [group](../language-reference/keywords/group-clause.md) 子句。 在第一個 `from` 子句與最後一個 `select` 或 `group` 子句之間，它可以包含下列其中一個或多個選擇性子句︰[where](../language-reference/keywords/where-clause.md)、[orderby](../language-reference/keywords/orderby-clause.md)、[join](../language-reference/keywords/join-clause.md)、[let](../language-reference/keywords/let-clause.md)，甚至是額外的 [from](../language-reference/keywords/from-clause.md) 子句。 您也可以使用 [into](../language-reference/keywords/into.md) 關鍵字，讓 `join` 或 `group` 子句的結果作為相同查詢運算式中其他查詢子句的來源。  
  
### <a name="query-variable"></a>查詢變數  
 
 在 LINQ 中，查詢變數是儲存*「查詢」* 而非查詢*「結果」* 的任何變數。 更具體來說，在 `foreach` 陳述式中逐一查看查詢變數或直接呼叫其 `IEnumerator.MoveNext` 方法時，查詢變數一律是將產生一序列項目的可列舉類型。  
  
 下列程式碼範例示範簡單查詢運算式，內含一個資料來源、一個篩選子句、一個排序子句，而且不需轉換來源項目。 `select` 子句會結束查詢。  
  
 [!code-cs[csrefQueryExpBasics#49](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_5.cs)]  
  
 在上述範例中，`scoreQuery` 是*「查詢變數」*，這有時指的就是*「查詢」*。 查詢變數不會儲存 `foreach` 迴圈中所產生的任何實際結果資料。 執行 `foreach` 陳述式時，透過查詢變數 `scoreQuery` 不會傳回查詢結果。 而是會透過反覆運算變數 `testScore` 傳回。 可以在第二個 `foreach` 迴圈中逐一查看 `scoreQuery` 變數。 只要未修改過它或資料來源，就會產生相同的結果。  
  
 查詢變數可能會儲存以查詢語法、方法語法或兩者組合表示的查詢。 在下列範例中，`queryMajorCities` 和 `queryMajorCities2` 都是查詢變數︰  
  
 [!code-cs[csrefQueryExpBasics#50](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_6.cs)]  
  
 換句話說，下列兩個範例示範不是查詢變數的變數，即使每個變數都是使用查詢進行初始化也是一樣。 它們會儲存結果，因此不是查詢變數：  
  
 [!code-cs[csrefQueryExpBasics#51](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_7.cs)]  
  
 如需以不同方式表達查詢的詳細資訊，請參閱 [LINQ 中的查詢語法及方法語法](../programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)。  
  
#### <a name="explicit-and-implicit-typing-of-query-variables"></a>查詢變數的明確和隱含類型  
 
 這份文件通常會提供查詢變數的明確類型，以顯示查詢變數與 [select 子句](../language-reference/keywords/select-clause.md)之間的類型關聯性。 不過，您也可以使用 [var](../language-reference/keywords/var.md)關鍵字，指示編譯器在編譯時期推斷查詢變數 (或任何其他區域變數) 的類型。 例如，也可以使用隱含類型來表示本主題先前所顯示的查詢範例︰  
  
 [!code-cs[csrefQueryExpBasics#52](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_8.cs)]  
  
 如需詳細資訊，請參閱[隱含類型區域變數](../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)和 [LINQ 查詢作業中的類型關聯性](../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)。  
  
### <a name="starting-a-query-expression"></a>啟動查詢運算式  
 
 查詢運算式的開頭必須是 `from` 子句。 它會同時指定資料來源和範圍變數。 範圍變數代表正在周遊來源序列時來源序列中的每個連續項目。 根據資料來源中的項目類型，範圍變數是強類型。 在下列範例中，因為 `countries` 是 `Country` 物件陣列，所以範圍變數的類型也是 `Country`。 因為範圍變數是強類型，所以您可以使用點運算子來存取該類型的任何可用成員。  
  
 [!code-cs[csrefQueryExpBasics#53](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_9.cs)]  
  
 除非使用分號或 *continuation* 子句結束查詢，否則範圍變數會在範圍內。  
  
 查詢運算式可能會包含多個 `from` 子句。 來源序列中的每個項目本身就是集合或包含集合時，請使用其他 `from` 子句。 例如，假設您有 `Country` 物件集合，各包含名為 `Cities`的 `City` 物件。 若要查詢每個 `Country` 中的 `City` 物件，請使用兩個 `from` 子句，如下所示︰  
  
 [!code-cs[csrefQueryExpBasics#54](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_10.cs)]  
  
 如需詳細資訊，請參閱 [from 子句](../language-reference/keywords/from-clause.md)。  
  
### <a name="ending-a-query-expression"></a>結束查詢運算式  
 
 查詢運算式的結尾必須是 `group` 子句或 `select` 子句。  
  
#### <a name="group-clause"></a>group 子句  
 
 使用 `group` 子句，產生依所指定的索引鍵所組織的一系列群組。 索引鍵可以是任何資料類型。 例如，下列查詢會建立一序列的群組，各包含一個或多個 `Country` 物件且其索引鍵是 `char` 值。  
  
 [!code-cs[csrefQueryExpBasics#55](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_11.cs)]  
  
 如需分組的詳細資訊，請參閱 [group 子句](../language-reference/keywords/group-clause.md)。  
  
#### <a name="select-clause"></a>select 子句  
 使用 `select` 子句來產生所有其他類型的序列。 簡單 `select` 子句只會產生一系列相同類型的物件，作為資料來源中所包含的物件。 在此範例中，資料成員包含 `Country` 物件。 `orderby` 子句只會將項目排序為新順序，而 `select` 子句會產生一系列的已排序 `Country` 物件。  
  
 [!code-cs[csrefQueryExpBasics#56](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_12.cs)]  
  
 `select` 子句可以用來將來源資料轉換為新類型的序列。 這項轉換也稱為*「投影」*。 在下列範例中，`select` 子句會*「投影」*一序列的匿名類型，只包含原始項目中欄位的子集。 請注意，使用物件初始設定式，可以初始化新物件。  
  
 [!code-cs[csrefQueryExpBasics#57](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_13.cs)]  
  
 如需 `select` 子句可用來轉換來源資料之所有方式的詳細資訊，請參閱 [select 子句](../language-reference/keywords/select-clause.md)。  
  
#### <a name="continuations-with-into"></a>"into" 的接續  
 
 您可以在 `select` 或 `group`子句中使用 `into` 關鍵字，以建立可儲存查詢的暫存識別碼。 必須在分組或選取作業之後對查詢執行其他查詢作業時，請這麼做。 在下列範例中，`countries` 會根據 1 千萬範圍中的個體進行分組。 建立這些群組之後，其他子句會篩選掉部分群組，接著依遞增順序排序群組。 若要執行這些其他作業，則需要 `countryGroup` 所代表的繼續。  
  
 [!code-cs[csrefQueryExpBasics#58](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_14.cs)]  
  
 如需詳細資訊，請參閱 [into](../language-reference/keywords/into.md)。  
  
### <a name="filtering-ordering-and-joining"></a>篩選、排序和聯結

 在開始 `from` 子句與結束 `select` 或 `group` 子句之間，所有其他子句 (`where`、`join`、`orderby`、`from`、`let`) 都是選擇性的。 在查詢主體中，可能不會使用任何選擇性子句或使用多次。  
  
#### <a name="where-clause"></a>where 子句  

 使用 `where` 子句，會根據一個或多個述詞運算式來篩選掉來源資料中的項目。 下列範例中的 `where` 子句會有一個具有兩個條件的述詞。  
  
 [!code-cs[csrefQueryExpBasics#59](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_15.cs)]  
  
 如需詳細資訊，請參閱 [where 子句](../language-reference/keywords/where-clause.md)。  
  
#### <a name="orderby-clause"></a>orderby 子句

 使用 `orderby` 子句，依遞增或遞減順序來排序結果。 您也可以指定次要排序順序。 下列範例會使用 `Area` 屬性，以對 `country` 物件執行主要排序。 它接著會使用 `Population` 屬性來執行次要排序。  
  
 [!code-cs[csrefQueryExpBasics#60](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_16.cs)]  
  
 `ascending` 是選擇性關鍵字；如果未指定任何順序，則為預設排序順序。 如需詳細資訊，請參閱 [orderby 子句](../language-reference/keywords/orderby-clause.md)。  
  
#### <a name="join-clause"></a>join 子句

 使用 `join` 子句，會根據每個項目中所指定索引鍵之間的相等比較來建立某個資料來源中的項目與另一個資料來源中的項目的關聯和 (或) 將它們合併。 在 LINQ 中，會對項目為不同類型的物件序列執行聯結作業。 聯結兩個序列之後，必須使用 `select` 或 `group` 陳述式來指定要儲存在輸出序列中的項目。 您也可以使用匿名類型，將每個相關聯項目集的屬性合併到輸出序列的新類型。 下列範例會關聯 `prod` 物件，而其 `Category` 屬性符合 `categories` 字串陣列中的其中一個分類。 會篩選掉 `Category` 不符合 `categories` 中任何字串的產品。 `select` 陳述式會投影其屬性取自 `cat` 和 `prod` 的新類型。  
  
 [!code-cs[csrefQueryExpBasics#61](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_17.cs)]  
  
 您也可以使用 [into](../language-reference/keywords/into.md) 關鍵字將 `join` 作業的結果儲存到暫存變數，來執行群組聯結。 如需詳細資訊，請參閱 [join 子句](../language-reference/keywords/join-clause.md)。  
  
#### <a name="let-clause"></a>let 子句 

 使用 `let` 子句，將運算式的結果 (例如方法呼叫) 儲存在新的範圍變數中。 在下列範例中，範圍變數 `firstName` 會儲存 `Split` 所傳回的字串陣列的第一個項目。  
  
 [!code-cs[csrefQueryExpBasics#62](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_18.cs)]  
  
 如需詳細資訊，請參閱 [let 子句](../language-reference/keywords/let-clause.md)。  
  
### <a name="subqueries-in-a-query-expression"></a>查詢運算式中的子查詢  

 查詢子句本身可能會包含查詢運算式，有時稱為*「子查詢」*。 每個子查詢的開頭都會是它自己的 `from` 子句，而子句不一定會指向第一個 `from` 子句中的相同資料來源。 例如，下列查詢示範用於 select 陳述式以擷取分組作業結果的查詢運算式。  
  
 [!code-cs[csrefQueryExpBasics#63](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_19.cs)]  
  
 如需詳細資訊，請參閱[如何：在分組作業上執行子查詢](perform-a-subquery-on-a-grouping-operation.md)。  
  
## <a name="see-also"></a>另請參閱  
 [C# 程式設計手冊](../programming-guide/index.md)   
 [LINQ 查詢運算式](index.md)   
 [查詢關鍵字 (LINQ)](../language-reference/keywords/query-keywords.md)   
 [標準查詢運算子概觀](../programming-guide/concepts/linq/standard-query-operators-overview.md)

