---
title: "Visual Basic Features That Support LINQ | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Visual Basic, LINQ features"
  - "LINQ [Visual Basic], features supporting LINQ"
ms.assetid: c821bb50-b6f6-4cf9-8aba-2717e465bd3a
caps.latest.revision: 51
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 49
---
# Visual Basic Features That Support LINQ
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

[!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext-md.md)] 這個名稱是指 Visual Basic 中的一項技術，這項技術可直接支援語言中的查詢語法和其他語言建構。  透過 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)]，您不需要學習新語言即可查詢外部資料來源。  您可以使用 Visual Basic 查詢關聯式資料庫、XML 存放區或物件中的資料。  這種將查詢功能與語言整合的方式可以讓您在編譯時期檢查語法錯誤和型別安全 \(Type Safety\)。  這項整合也可以確保您已經大致了解在 Visual Basic 中撰寫豐富又多樣化的查詢時所必須具備的知識。  
  
 下列各節詳細說明支援 LINQ 的語言建構，使您能夠開始閱讀簡介文件、程式碼範例和範例應用程式。  您也可以按一下連結，找出語言功能如何共同啟用語言整合查詢的詳細說明。  其中最佳的入門是[逐步解說：在 Visual Basic 中撰寫查詢](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)。  
  
## 查詢運算式  
 Visual Basic 中的查詢運算式可以透過類似 SQL 或 XQuery 的宣告式語法來表示。  編譯期間查詢語法會轉換為對 LINQ 提供者實作的標準查詢運算子擴充方法進行的方法呼叫。  應用程式可透過使用 `Imports` 陳述式 \(Statement\) 指定適當的命名空間 \(Namespace\)，控制哪些標準查詢運算子會在範圍之內。  Visual Basic 查詢運算式的語法與下面所示類似：  
  
 [!code-vb[VbLINQVbFeatures#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/visualbasic/features-that-support-linq_1.vb)]  
  
 如需詳細資訊，請參閱 [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)。  
  
## 隱含型別變數  
 您可以讓編譯器推斷並指派型別，而不是在宣告及初始化變數時明確指定型別。  這種方法稱為「*區域型別推斷*」\(Local Type Inference\)。  
  
 藉由推斷取得型別的變數和明確指定型別的變數一樣，都是強型別 \(Strongly Typed\) 的變數。  只有在方法主體內定義區域變數，才可以進行區域型別推斷。  如需詳細資訊，請參閱 [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md)和[Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。  
  
 下列範例說明區域型別推斷。  若要使用此範例，您必須將 `Option Infer` 設為 `On`。  
  
 [!code-vb[VbLINQVbFeatures#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/visualbasic/features-that-support-linq_2.vb)]  
  
 區域型別推斷也可以讓建立匿名型別，以便在本章節稍後說明，以及所需的 LINQ 查詢。  
  
 在下列 LINQ 範例中，型別推斷會在 `Option Infer` 為 `On` 或 `Off` 時發生。  如果 `Option Infer` 為 `Off` 且 `Option Strict` 為 `On`，則會發生編譯時期錯誤。  
  
 [!code-vb[VbLINQVbFeatures#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/visualbasic/features-that-support-linq_3.vb)]  
  
## 物件初始設定式  
 當您必須建立用來保存查詢結果的匿名型別時，可以在查詢運算式中使用物件初始設定式。  物件初始設定式也可以用來初始化查詢外部之具名型別的物件。  使用物件初始設定式，您可以在單行中初始化物件，而不需要明確呼叫建構函式。  假設您有一個名為 `Customer` 的類別具有公用的 `Name` 和 `Phone` 屬性，以及其他屬性，則可以透過下列方式來使用物件初始設定式：  
  
 [!code-vb[VbLINQVbFeatures#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/visualbasic/features-that-support-linq_4.vb)]  
  
 如需詳細資訊，請參閱[Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)。  
  
## 匿名型別  
 匿名型別提供一種簡便的方式，可以暫時將一組屬性群組成您想包含在查詢結果的項目。  透過這種方式，您可以依照任何順序選擇查詢中可用欄位的任意組合，而不需要定義該項目的具名資料型別。  
  
 「*匿名型別*」\(Anonymous Type\) 是由編譯器以動態方式建構的型別。  型別的名稱由編譯器指定，而且可能隨著每次進行新的編譯而改變。  因此，您不能直接使用這個名稱。  匿名型別初始化的方式如下：  
  
 [!code-vb[VbLINQVbFeatures#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/visualbasic/features-that-support-linq_5.vb)]  
  
 如需詳細資訊，請參閱[Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。  
  
## 擴充方法  
 擴充方法可讓您從定義外部將方法加入至資料型別或介面。  這項功能實際上可讓您將新的方法加入至現有型別，而不需要實際修改該型別。  標準查詢運算子本身就是一組擴充方法，可為實作 <xref:System.Collections.Generic.IEnumerable%601> 的任何型別提供 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] 查詢功能。<xref:System.Collections.Generic.IEnumerable%601> 的其他擴充項目包括 <xref:System.Linq.Enumerable.Count%2A>、<xref:System.Linq.Enumerable.Union%2A> 和 <xref:System.Linq.Enumerable.Intersect%2A>。  
  
 下列擴充方法會將列印方法加入至 <xref:System.String> 類別。  
  
 [!code-vb[VbLINQVbFeatures#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/visualbasic/features-that-support-linq_6.vb)]  
  
 呼叫此方法的方式與 <xref:System.String> 的一般執行個體方法 \(Instance Method\) 相同：  
  
 [!code-vb[VbLINQVbFeatures#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/visualbasic/features-that-support-linq_7.vb)]  
  
 如需詳細資訊，請參閱 [擴充方法](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)。  
  
## Lambda 運算式  
 「Lambda 運算式」\(Lambda Expression\) 是沒有名稱的函式，會計算並傳回單一值。  不同於具名函式，Lambda 運算式可以同時定義及執行。  下列範例顯示的是 4。  
  
 [!code-vb[VbLINQVbFeatures#8](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/visualbasic/features-that-support-linq_8.vb)]  
  
 您可以將 Lambda 運算式定義指派成變數名稱，然後使用該名稱來呼叫函式。  下列範例也會顯示 4。  
  
 [!code-vb[VbLINQVbFeatures#12](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/visualbasic/features-that-support-linq_9.vb)]  
  
 在 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] 中，Lambda 運算式是許多標準查詢運算子的基礎。  編譯器會建立 Lambda 運算式以擷取基本查詢方法 \(例如 `Where`、`Select`、`Order By`、`Take While` 等等\) 中定義的計算。  
  
 例如，下列程式碼定義的查詢會從學生清單中傳回所有的高年級學生。  
  
 [!code-vb[VbLINQVbFeatures#9](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/visualbasic/features-that-support-linq_10.vb)]  
  
 查詢定義會編譯成與下列範例類似的程式碼，而範例中則使用兩個 Lambda 運算式來指定 `Where` 和 `Select` 的引數。  
  
 [!code-vb[VbLINQVbFeatures#10](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/visualbasic/features-that-support-linq_11.vb)]  
  
 這兩個版本都可以使用 `For Each` 迴圈 \(Loop\)：  
  
 [!code-vb[VbLINQVbFeatures#11](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/visualbasic/features-that-support-linq_12.vb)]  
  
 如需詳細資訊，請參閱 [Lambda Expressions](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。  
  
## 請參閱  
 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)   
 [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [LINQ 和字串](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)   
 [C\# Features That Support LINQ](../../../../csharp/programming-guide/concepts/linq/features-that-support-linq.md)   
 [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md)   
 [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)