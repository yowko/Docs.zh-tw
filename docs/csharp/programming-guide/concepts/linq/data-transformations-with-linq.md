---
title: "使用 LINQ 轉換資料 (C#) | Microsoft Docs"
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
  - "LINQ [C#]，資料轉換"
  - "來源項目 [C# 中的 LINQ]"
  - "聯結多個輸入 [C# 中的 LINQ]"
  - "多個輸入用於一個輸出序列 [C# 中的 LINQ]"
  - "來源項目的子集 [C# 中的 LINQ]"
  - "資料來源 [C# 中的 LINQ]，資料轉換"
  - "資料轉換 [C# 中的 LINQ]"
ms.assetid: 674eae9e-bc72-4a88-aed3-802b45b25811
caps.latest.revision: 17
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 使用 LINQ 轉換資料 (C#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[vbteclinqext](../../../../csharp/programming-guide/concepts/linq/includes/vbteclinqext_md.md)] 不只可以擷取資料，  它同時還是強大的資料轉換工具。  使用 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 查詢，您可以使用來源序列做為輸入，並且用許多方式來修改來源序列，以建立新的輸出序列。  您可以修改序列，而不用修改項目將排序和群組。可能是 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] ，但是查詢最強的功能可能是建立新的。  這項作業是在 [select](../../../../csharp/language-reference/keywords/select-clause.md) 子句中完成。  例如，您可以進行下列工作：  
  
-   將多個輸入序列合併成具有新型別的單一輸出序列。  
  
-   建立輸出序列，其中的項目只由來源序列中每個項目的一個或多個屬性組成。  
  
-   建立輸出序列，其中的項目只由對來源資料執行作業後的結果組成。  
  
-   建立不同格式的輸出序列。  例如，您可以將資料從 SQL 資料列或文字檔轉換為 XML。  
  
 以下提供一些範例。  當然，這些轉換也可以用各種方式合併至相同查詢中。  甚至，某個查詢的輸出序列可以當成新查詢的輸入序列。  
  
## 將多個輸入聯結成一個輸出序列  
 您可以使用 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 查詢，建立項目來自多個輸入序列的輸出序列。  下列範例顯示如何合併兩個記憶體中資料結構，而相同的準則也適用於合併來自 XML 或 SQL 或 DataSet 來源的資料。  假設有下列兩個類別 \(Class\) 型別：  
  
 [!code-cs[CsLINQGettingStarted#7](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_1.cs)]  
  
 下列範例會顯示查詢：  
  
 [!code-cs[CSLinqGettingStarted#8](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_2.cs)]  
  
 如需詳細資訊，請參閱[join 子句](../../../../csharp/language-reference/keywords/join-clause.md)與[select 子句](../../../../csharp/language-reference/keywords/select-clause.md)。  
  
## 選取每個來源項目的子集  
 有兩種主要方式可以用來選取來源序列中每個項目的子集。  
  
1.  若只要選取來源項目的一個成員，請使用點運算。  在下列範例中，假設 `Customer` 物件含有多個公用 \(Public\) 屬性 \(包括名為 `City` 的字串\)。  執行時，這個查詢會產生字串的輸出序列。  
  
    ```  
    var query = from cust in Customers  
                select cust.City;  
    ```  
  
2.  若要建立的項目包含多個來自來源項目的屬性，則可以將物件初始設定式與具名物件或匿名型別搭配使用。  下列範例顯示如何使用匿名型別來封裝每個 `Customer` 項目的兩個屬性：  
  
    ```  
    var query = from cust in Customer  
                select new {Name = cust.Name, City = cust.City};  
    ```  
  
 如需詳細資訊，請參閱[物件和集合初始設定式](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)與[匿名類型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。  
  
## 將記憶體中物件轉換為 XML  
 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 查詢簡化了在記憶體中資料結構、SQL 資料庫、[!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)] Dataset 和 XML 資料流或文件之間的資料轉換。  下列範例會將記憶體中資料結構內的物件轉換為 XML 項目。  
  
 [!code-cs[CsLINQGettingStarted#9](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_3.cs)]  
  
 這個程式碼會產生下列 XML 輸出：  
  
```  
< Root>  
  <student>  
    <First>Svetlana</First>  
    <Last>Omelchenko</Last>  
    <Scores>97,92,81,60</Scores>  
  </student>  
  <student>  
    <First>Claire</First>  
    <Last>O'Donnell</Last>  
    <Scores>75,84,91,39</Scores>  
  </student>  
  <student>  
    <First>Sven</First>  
    <Last>Mortensen</Last>  
    <Scores>88,94,65,91</Scores>  
  </student>  
</Root>  
```  
  
 如需詳細資訊，請參閱[在 C\# 中建立 XML 樹狀結構](../Topic/Creating%20XML%20Trees%20in%20C%23%20\(LINQ%20to%20XML\)1.md)。  
  
## 在來源項目上執行作業  
 輸出序列可能不會包含來源序列的任何項目或項目屬性。  輸出序列可能只是使用來源項目做為輸入引數計算而得的值序列。  下列簡單查詢在執行時會輸出字串序列，其中的值是根據 `double` 型別的來源項目序列計算而得的結果。  
  
> [!NOTE]
>  如果查詢會轉譯為另一個領域，則不支援在查詢運算式中呼叫方法。  例如，因為 SQL Server 沒有一般 C\# 方法所需的內容，所以不可以在 [!INCLUDE[vbtecdlinq](../../../../csharp/language-reference/keywords/includes/vbtecdlinq_md.md)] 中呼叫一般 C\# 方法。  但可以將預存程序 \(Stored Procedure\) 對應至方法，再呼叫預存程序。  如需詳細資訊，請參閱[預存程序](../Topic/Stored%20Procedures.md)。  
  
 [!code-cs[CsLINQGettingStarted#10](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_4.cs)]  
  
## 請參閱  
 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [LINQ to DataSet](../Topic/LINQ%20to%20DataSet.md)   
 [LINQ to XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)   
 [LINQ 查詢運算式](../../../../visual-basic/reference/command-line-compiler/index.md)   
 [select 子句](../../../../csharp/language-reference/keywords/select-clause.md)   
 [How to: Combine Data with Joins](../../../../visual-basic/programming-guide/language-features/linq/how-to-combine-data-with-linq-by-using-joins.md)