---
title: "基本查詢作業 (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "資料來源 [Visual Basic 中的 LINQ]"
  - "Join 子句 [Visual Basic 中的 LINQ]"
  - "排序資料 [Visual Basic 中的 LINQ]"
  - "投影 [Visual Basic 中的 LINQ]"
  - "LINQ [Visual Basic]，查詢作業"
  - "Order By 子句 [Visual Basic 中的 LINQ]"
  - "聯結資料 [Visual Basic 中的 LINQ]"
  - "查詢 [Visual Basic 中的 LINQ]，基本作業"
  - "選取資料 [Visual Basic 中的 LINQ]"
  - "Group By 子句 [Visual Basic 中的 LINQ]"
  - "分組資料 [Visual Basic 中的 LINQ]"
  - "Select 子句 [Visual Basic 中的 LINQ]"
ms.assetid: 1146f6d0-fcb8-4f4d-8223-c9db52620d21
caps.latest.revision: 37
caps.handback.revision: 35
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 基本查詢作業 (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

本主題簡介 Visual Basic 中的 [!INCLUDE[vbteclinqext](../../../../csharp/programming-guide/concepts/linq/includes/vbteclinqext_md.md)] 運算式，以及一些可以在查詢中執行的一般作業。  如需詳細資訊，請參閱下列主題：  
  
 [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [Queries](../../../../visual-basic/language-reference/queries/queries.md)  
  
 [逐步解說：在 Visual Basic 中撰寫查詢](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## 指定資料來源 \(From\)  
 在 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 查詢中，第一步是指定想要查詢的資料來源。  因此，查詢中的 `From` 子句一定排在最前面的位置。查詢運算子來選取和塑造會根據來源類型的結果。  
  
 [!code-vb[VbLINQBasicOps#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_1.vb)]  
  
 `From` 子句會指定資料來源、`customers` 和「*範圍變數*」\(Range Variable\) `cust`。  範圍變數與迴圈 \(Loop\) 反覆運算變數類似，不同處在於查詢運算式不會實際反覆運算。  執行查詢時 \(通常是使用 `For Each` 迴圈\)，範圍變數會提供 `customers` 中之每個連續項目的參考。  因為編譯器 \(Compiler\) 會推斷 `cust` 的型別，所以您不需要明確指定型別。  如需撰寫含和不含明確型別的查詢範例，請參閱[Type Relationships in Query Operations \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md)。  
  
 如需如何在 Visual Basic 中使用 `From` 子句的詳細資訊，請參閱 [From Clause](../../../../visual-basic/language-reference/queries/from-clause.md)。  
  
## 篩選資料 \(Where\)  
 最常見的查詢作業可能是套用布林值運算式 \(Boolean\) 形式的篩選條件。  這個查詢接著只會傳回運算式為 true 的項目。  `Where` 子句會用來執行篩選。  篩選條件會指定要將資料來源中的哪些項目併入所產生的序列。  在下列範例中，只會併入地址在 London 的客戶。  
  
 [!code-vb[VbLINQBasicOps#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_2.vb)]  
  
 您可以使用邏輯運算子 \(如 `And` 和 `Or`\) 來合併 `Where` 子句中的篩選條件運算式。  例如，若只要傳回來自 London 而且名稱為 Devon 的客戶，請使用下列程式碼：  
  
```vb#  
Where cust.City = "London" And cust.Name = "Devon"   
```  
  
 若要傳回來自 London 或 Paris 的客戶，請使用下列程式碼：  
  
```vb#  
Where cust.City = "London" Or cust.City = "Paris"   
```  
  
 如需如何在 Visual Basic 中使用 `Where` 子句的詳細資訊，請參閱 [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md)。  
  
## 排序資料 \(Order By\)  
 通常將傳回的資料排序為特定順序會很方便。  `Order By` 子句會根據指定的一個或多個欄位來排序所傳回序列中的項目。  例如，下列查詢會根據 `Name` 屬性來排序結果。  因為 `Name` 是字串，所以傳回的資料會依字母順序 \(從 A 到 Z\) 排序。  
  
 [!code-vb[VbLINQBasicOps#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_3.vb)]  
  
 若要以相反方向排序結果 \(從 Z 到 A\)，請使用 `Order By...Descending` 子句。  不指定 `Ascending` 和 `Descending` 時，預設值是 `Ascending`。  
  
 如需如何在 Visual Basic 中使用 `Order By` 子句的詳細資訊，請參閱 [Order By Clause](../../../../visual-basic/language-reference/queries/order-by-clause.md)。  
  
## 選取資料 \(Select\)  
 `Select` 子句會指定所傳回項目的格式和內容。  例如，您可以指定結果要包含完整 `Customer` 物件、只包含一個 `Customer` 屬性、包含屬性子集、包含各種資料來源中之屬性的組合，還是包含計算而來的新結果型別。  如果 `Select` 子句的產物不是來源項目的複本，則這項作業稱為「*投影*」\(Projection\)。  
  
 若要擷取包含完整 `Customer` 物件的集合，請選取範圍變數本身：  
  
 [!code-vb[VbLINQBasicOps#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_4.vb)]  
  
 如果 `Customer` 執行個體 \(Instance\) 是擁有多個欄位的大型物件，而您只要擷取名稱，則可以選取 `cust.Name` \(如下列範例所示\)。  區域型別推斷會知道要將結果的型別從 `Customer` 物件的集合變更為字串的集合。  
  
 [!code-vb[VbLINQBasicOps#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_5.vb)]  
  
 若要選取資料來源中的多個欄位，您有兩個選擇：  
  
-   在 `Select` 子句中，指定想要併入結果中的欄位。  編譯器會在定義匿名型別時，將那些欄位當成該型別的屬性。  如需詳細資訊，請參閱[Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。  
  
     因為在下列範例中傳回的項目是匿名型別執行個體，所以無法在程式碼的別處依名稱來參考該型別。  編譯器指定的型別名稱會包含一般 Visual Basic 程式碼中無效的字元。  在下列範例中，由 `londonCusts4` 內的查詢所傳回之集合中的項目會是匿名型別執行個體。  
  
     [!code-vb[VbLINQBasicOps#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_6.vb)]  
  
     \-或\-  
  
-   定義具名型別並使其內含想要併入結果中的特定欄位，然後在 `Select` 子句中建立和初始化該型別的執行個體。  只有當必須在包含所傳回結果的集合外部使用個別結果，或者必須在方法呼叫中將個別結果當成參數傳遞時，才使用這個選項。  下列範例中 `londonCusts5` 的型別是 IEnumerable\(Of NamePhone\)。  
  
     [!code-vb[VbLINQBasicOps#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_7.vb)]  
  
     [!code-vb[VbLINQBasicOps#8](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_8.vb)]  
  
 如需如何在 Visual Basic 中使用 `Select` 子句的詳細資訊，請參閱 [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md)。  
  
## 聯結資料 \(Join 和 Group Join\)  
 有多種方式可以在 `From` 子句中合併多個資料來源。  例如，下列程式碼會使用兩個資料來源，並以隱含方式將它們的屬性合併至結果中。  這個查詢會選取姓氏開頭為母音的學生。  
  
 [!code-vb[VbLINQBasicOps#9](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_9.vb)]  
  
> [!NOTE]
>  您可以使用 [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)中建立的學生名單來執行這個程式碼。  
  
 `Join` 關鍵字相當於 SQL 中的 `INNER JOIN`。  它會根據兩個集合中項目的相符索引鍵值來合併兩個集合。  查詢會傳回所有或部分具有相符索引鍵值的集合項目。  例如，下列程式碼會複製上一個隱含聯結 \(Join\) 的動作。  
  
 [!code-vb[VbLINQBasicOps#10](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_10.vb)]  
  
 `Group Join` 會將多個集合合併成單一階層式集合，這與 SQL 中的 `LEFT JOIN` 類似。  如需詳細資訊，請參閱[Join Clause](../../../../visual-basic/language-reference/queries/join-clause.md)與[Group Join Clause](../../../../visual-basic/language-reference/queries/group-join-clause.md)。  
  
## 分組資料 \(Group By\)  
 您可以加入 `Group By` 子句，根據項目的一個或多個欄位來分組查詢結果中的項目。  例如，下列程式碼會根據年級來分組學生。  
  
 [!code-vb[VbLINQBasicOps#11](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_11.vb)]  
  
 如果使用 [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)中建立的學生名單來執行這個程式碼，則 `For Each` 陳述式的輸出是：  
  
 Year: Junior  
  
 Tucker, Michael  
  
 Garcia, Hugo  
  
 Garcia, Debra  
  
 Tucker, Lance  
  
 Year: Senior  
  
 Omelchenko, Svetlana  
  
 Osada, Michiko  
  
 Fakhouri, Fadi  
  
 Feng, Hanying  
  
 Adams, Terry  
  
 Year: Freshman  
  
 Mortensen, Sven  
  
 Garcia, Cesar  
  
 下列程式碼則做了變化，會先依年級再依姓氏排序每個年級的學生。  
  
 [!code-vb[VbLINQBasicOps#12](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_12.vb)]  
  
 如需 `Group By` 的詳細資訊，請參閱 [Group By 子句](../../../../visual-basic/language-reference/queries/group-by-clause.md)。  
  
## 請參閱  
 <xref:System.Collections.Generic.IEnumerable%601>   
 [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [Queries](../../../../visual-basic/language-reference/queries/queries.md)   
 [Standard Query Operators Overview](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Basic LINQ Query Operations](../../../../csharp/programming-guide/concepts/linq/basic-linq-query-operations.md)