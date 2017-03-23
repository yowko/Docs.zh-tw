---
title: "Query Syntax and Method Syntax in LINQ (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "LINQ [C#], query syntax vs. method syntax"
  - "queries [LINQ in C#], syntax comparisons"
ms.assetid: eedd6dd9-fec2-428c-9581-5b8783810ded
caps.latest.revision: 30
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 28
---
# Query Syntax and Method Syntax in LINQ (C#)
在簡介語言整合查詢 \([!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)]\) 使用 LINQ 宣告式查詢語法，文件的大部分撰寫查詢。  不過，，編譯程式碼時，必須轉譯查詢語法成方法呼叫 .NET Common Language Runtime \(CLR\)。  這些方法會叫用標準查詢運算子的名稱，例如 `Where`、 `Select`、 `GroupBy`、 `Join`、 `Max`和 `Average`。  您可以呼叫它們直接使用方法語法 \(而不是查詢語法。  
  
 查詢語法與方法語法在語意上是相同的，不過，許多人尋找查詢語法更簡單且更容易讀取。  必須表示查詢時呼叫方法。  例如，您必須使用呼叫方法以擷取元素數目符合指定條件的查詢。  您也必須使用方法呼叫擷取項目具有最大值位於來源序列的查詢。  <xref:System.Linq> 命名空間 \(Namespace\) 中標準查詢運算子的相關參考文件一般是使用方法語法。  因此，即使是撰寫 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] 查詢的新手，熟悉如何在查詢和查詢運算式本身中使用方法語法還是十分有用的。  
  
## 標準查詢運算子擴充方法  
 下列範例顯示簡單的「*查詢運算式*」\(Query Expression\)，以及在語意上相等，以「*方法架構查詢*」\(Method\-Based Query\) 撰寫的對等查詢。  
  
 [!code-cs[csLINQGettingStarted#22](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/query-syntax-and-method-syntax-in-linq_1.cs)]  
  
 這兩個範例的輸出是相同的。  您可以看到在這兩種形式中查詢變數的型別都是相同的：<xref:System.Collections.Generic.IEnumerable%601>。  
  
 為了了解方法架構查詢，讓我們更仔細地看看它。  在運算式右邊，您會發現 `where` 子句現在是以 `numbers` 物件上的執行個體方法 \(instance method\) 表示，這個物件的型別就是剛剛的 `IEnumerable<int>`。  如果您熟悉泛型 <xref:System.Collections.Generic.IEnumerable%601> 介面，就會知道這個介面並沒有 `Where` 方法。  不過，如果在 Visual Studio IDE 中叫用 \(Invoke\) IntelliSense 完成清單，就會不只看到 `Where` 方法，還會看到其他許多方法，例如 `Select`、`SelectMany`、`Join` 和 `Orderby`\)。  這些都是標準查詢運算子。  
  
 ![Intellisense 中的標準查詢運算子](../../../../csharp/programming-guide/concepts/linq/media/standardqueryops.png "StandardQueryOps")  
  
 雖然看起來像是已將 <xref:System.Collections.Generic.IEnumerable%601> 重新定義為包含這些額外方法，但是實際上並非如此。  標準查詢運算子是以稱為「*擴充方法*」\(Extension Method\) 的一種新方法來實作。  擴充方法會「擴充」現有的型別，而您可以把它們當做型別上的執行個體方法一樣呼叫。  標準查詢運算子會擴充 <xref:System.Collections.Generic.IEnumerable%601>，這就是為何您可以寫 `numbers.Where(...)` 的原因。  
  
 若要開始使用 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)]，在擴充方法方面您只需要知道如何使用正確的 `using` 指示詞，將擴充方法帶入應用程式的範圍內。  這在 [How to: Create a LINQ Project](../Topic/How%20to:%20Create%20a%20LINQ%20Project.md)中會有額外說明。  對應用程式而言，擴充方法和一般執行個體方法是相同的。  
  
 如需擴充方法的詳細資訊，請參閱[擴充方法](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)。  如需標準查詢運算子的詳細資訊，請參閱[Standard Query Operators Overview](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)。  部分 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] 提供者 \(Provider\) \(例如 [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq-md.md)] 和 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)]\) 除了針對 <xref:System.Collections.Generic.IEnumerable%601> 之外，還會針對其他型別實作自己的標準查詢運算子和其他擴充方法。  
  
## Lambda 運算式  
 在上述範例中，請注意條件運算式 \(`num % 2 == 0`\) 會當做內嵌引數傳遞給 `Where` 方法: `Where(num => num % 2 == 0).`的這個內嵌運算式呼叫 Lambda 運算式。  用這個方式撰寫程式碼很方便，原因是不需要撰寫冗長的匿名方法 \(Anonymous Method\)、泛型委派或運算式樹狀架構。  在 C\# 中，`=>` 是 Lambda 運算子，意思為「移至」。  運算子左邊的 `num` 是輸入變數，對應至查詢運算式中的 `num`。  編譯器 \(Compiler\) 因為知道 `numbers` 是泛型 <xref:System.Collections.Generic.IEnumerable%601> 型別，所以可以推斷 `num` 的型別。  Lambda 主體與在查詢語法或其他任何 C\# 運算式或陳述式中表示的運算式相同，可以包含方法呼叫和其他複雜邏輯。  而「傳回值」就是運算式結果。  
  
 開始使用 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] 時，並不需要廣泛使用 Lambda。  不過，某些查詢只能以方法語法表示，而其中有些又需要使用 Lambda 運算式。  在更熟悉 Lambda 之後，您會發現它們是您 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] 工具箱中強大而有彈性的工具。  如需詳細資訊，請參閱[Lambda 運算式](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)。  
  
## 查詢撰寫性  
 在上一個程式碼範例中，請注意 `OrderBy` 方法是在 `Where` 的呼叫中使用點運算子來呼叫。  `Where` 會產生篩選後的序列，然後 `Orderby` 就會將該序列進行排序。  因為查詢會傳回 `IEnumerable`，所以撰寫查詢時，必須以方法語法將方法呼叫鏈結在一起。  這就是當您使用查詢語法撰寫查詢時，編譯器在幕後執行的作業。  而且，因為查詢變數不會儲存查詢的結果，所以您隨時可以修改查詢變數或將它當做新查詢的基礎，即使已經執行查詢變數也一樣。  
  
## 請參閱  
 [Getting Started with LINQ in C\#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)