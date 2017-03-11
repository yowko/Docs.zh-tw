---
title: "Type Relationships in LINQ Query Operations (C#) | Microsoft Docs"
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
  - "inferring type information [LINQ in C#]"
  - "data sources [LINQ in C#], type relationships"
  - "queries [LINQ in C#], type relationships"
  - "relationships [LINQ in C#]"
  - "type relationships [LINQ in C#]"
  - "variable relationships [LINQ in C#]"
  - "type information inferred [LINQ in C#]"
  - "data transformations [LINQ in C#]"
  - "LINQ [C#], type relationships"
ms.assetid: 99118938-d47c-4d7e-bb22-2657a9f95268
caps.latest.revision: 25
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 23
---
# Type Relationships in LINQ Query Operations (C#)
若要有效撰寫查詢，您應該了解整個查詢作業中的變數類型如何互相關聯。  若能了解這些關聯性 \(Relationship\)，就更容易理解文件中的 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] 範例和程式碼範例。  此外，您還可以知道使用 `var` 對變數進行隱含類型處理時，系統在幕後執行的作業。  
  
 在資料來源、查詢本身和查詢執行中，[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] 查詢作業都為強類型 \(Strongly Typed\)。  查詢中變數的類型，必須與資料來源中項目的類型以及 `foreach` 陳述式 \(Statement\) 中反覆運算變數的類型相容。  這個強類型可確保系統能夠在編譯時期攔截到類型錯誤，以在使用者發生這類錯誤之前予以更正。  
  
 為了示範這些類型關聯性，在下面的大部分範例中，所有變數都是使用明確類型。  最後一個範例則會使用 [var](../../../../csharp/language-reference/keywords/var.md) 進行隱含類型處理，以證明相同的準則仍適用於隱含類型。  
  
## 未轉換來源資料的查詢  
 下圖顯示未執行資料轉換的 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] to Objects 查詢作業。  這個來源包含字串序列，而查詢輸出也會是字串序列。  
  
 ![LINQ 查詢中資料類型的關聯性](../../../../csharp/programming-guide/concepts/linq/media/linq-flow1.png "LINQ\_flow1")  
  
1.  資料來源的類型引數會決定範圍變數的類型。  
  
2.  所選取物件的類型會決定查詢變數的類型。  這裡的 `name` 是字串。  因此，查詢變數是 `IEnumerable`\<string\>。  
  
3.  `foreach` 陳述式中會逐一查看查詢變數。  因為查詢變數是字串序列，所以反覆運算變數也會是字串。  
  
## 轉換來源資料的查詢  
 下圖顯示執行簡單資料轉換的 [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq-md.md)] 查詢作業。  這個查詢會採用 `Customer` 物件的序列做為輸入，而且只會選取結果中的 `Name` 屬性。  因為 `Name` 是字串，所以查詢會產生字串序列做為輸出。  
  
 ![轉換資料類型的查詢](../../../../csharp/programming-guide/concepts/linq/media/linq-flow2.png "LINQ\_flow2")  
  
1.  資料來源的類型引數會決定範圍變數的類型。  
  
2.  `select` 陳述式會傳回 `Name` 屬性，而不是整個 `Customer` 物件。  因為 `Name` 是字串，所以 `custNameQuery` 的類型引數是 `string`，而不是 `Customer`。  
  
3.  因為 `custNameQuery` 是字串序列，所以 `foreach` 迴圈 \(Loop\) 的反覆運算變數也必須是 `string`。  
  
 下圖顯示稍微複雜一點的轉換。  `select` 陳述式會傳回匿名類型，這個匿名類型只會使用原始 `Customer` 物件的兩個成員做為屬性。  
  
 ![轉換資料類型的查詢](../../../../csharp/programming-guide/concepts/linq/media/linq-flow3.png "LINQ\_flow3")  
  
1.  資料來源的類型引數一律會是查詢中範圍變數的類型。  
  
2.  因為 `select` 陳述式會產生匿名類型，所以必須使用 `var` 對查詢變數進行隱含類型處理。  
  
3.  因為查詢變數的類型是隱含的，所以 `foreach` 迴圈中的反覆運算變數也必須是隱含的。  
  
## 讓編譯器推斷類型資訊  
 雖然您應該要知道查詢作業中的類型關聯性，但是也可以選擇讓編譯器幫您完成這一切工作。  關鍵字 [var](../../../../csharp/language-reference/keywords/var.md) 可以用於查詢作業中的任何區域變數。  下圖類似於先前討論過的範例 2。  不過，編譯器會提供查詢作業中之每個變數的強類型。  
  
 ![具有隱含類型功能的類型流程](../../../../csharp/programming-guide/concepts/linq/media/linq-flow4.png "LINQ\_flow4")  
  
 如需 `var` 的詳細資訊，請參閱 [隱含類型區域變數](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)。  
  
## 請參閱  
 [Getting Started with LINQ in C\#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [Type Relationships in Query Operations \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md)