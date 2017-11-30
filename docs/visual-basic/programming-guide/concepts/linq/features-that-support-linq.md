---
title: "支援 LINQ 的 Visual Basic 功能"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Basic, LINQ features
- LINQ [Visual Basic], features supporting LINQ
ms.assetid: c821bb50-b6f6-4cf9-8aba-2717e465bd3a
caps.latest.revision: "51"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 42465dbb168b7961792aec6b3c2bb7ae8f0a3355
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="visual-basic-features-that-support-linq"></a>支援 LINQ 的 Visual Basic 功能
名稱[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]指的是在 Visual Basic 中支援的查詢語法，並直接在語言中的其他語言建構的技術。 與[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]，您不必學習新語言對外部資料來源進行查詢。 您可以使用 Visual Basic 查詢針對關聯式資料庫、 XML 存放區或物件中的資料。 這項整合的查詢語言功能可讓編譯時間檢查語法錯誤和型別安全。 這項整合也可確保您已經知道大部分的您必須知道要在 Visual Basic 中撰寫豐富多變的查詢。  
  
 下列章節說明支援 LINQ 足夠的詳細資料，您可以開始閱讀簡介文件、 程式碼範例和範例應用程式中的語言建構。 您也可以按一下連結，詳細的說明如何語言功能共同啟用語言整合式查詢。 若要啟動很好的起點[逐步解說： 在 Visual Basic 中撰寫查詢](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)。  
  
## <a name="query-expressions"></a>查詢運算式  
 在 Visual Basic 中的查詢運算式可以類似的 SQL 或 XQuery 的宣告式語法來表示。 在編譯時期的查詢語法會轉換成標準查詢運算子擴充方法的 LINQ 提供者實作的方法呼叫。 標準查詢運算子，藉以指定具有適當的命名空間是在範圍內的應用程式控制項`Imports`陳述式。 Visual Basic 查詢運算式語法看起來像這樣：  
  
 [!code-vb[VbLINQVbFeatures#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_1.vb)]  
  
 如需詳細資訊，請參閱[Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)。  
  
## <a name="implicitly-typed-variables"></a>隱含類型的變數  
 而不是明確指定型別，如果您宣告並初始化的變數，您可以啟用編譯器推斷並指派類型。 這指*區域類型推斷*。  
  
 強類型推斷其類型的變數，就像您明確指定的型別的變數。 區域類型推斷僅適用於您正在定義的方法主體內的本機變數。 如需詳細資訊，請參閱[Option Infer 陳述式](../../../../visual-basic/language-reference/statements/option-infer-statement.md)和[區域類型推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。  
  
 下列範例說明區域類型推斷。 若要使用此範例中，您必須設定`Option Infer`至`On`。  
  
 [!code-vb[VbLINQVbFeatures#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_2.vb)]  
  
 區域類型推斷也可以建立匿名型別，會在這一節稍後描述和所需的 LINQ 查詢。  
  
 在下列 LINQ 範例中，型別推斷如果就會發生`Option Infer`是`On`或`Off`。 如果會發生編譯時間錯誤`Option Infer`是`Off`和`Option Strict`是`On`。  
  
 [!code-vb[VbLINQVbFeatures#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_3.vb)]  
  
## <a name="object-initializers"></a>物件初始設定式  
 當您必須建立匿名型別來保留查詢的結果查詢運算式中使用物件初始設定式。 它們也可用來初始化外部查詢的具名類型的物件。 藉由使用物件初始設定式，您可以初始化單一行中的物件，而不需明確呼叫建構函式。 假設您有類別，名為`Customer`具有公用`Name`和`Phone`屬性，以及其他內容中，物件初始設定式可用於這種方式：  
  
 [!code-vb[VbLINQVbFeatures#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_4.vb)]  
  
 如需詳細資訊，請參閱[物件初始設定式： 具名和匿名類型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)。  
  
## <a name="anonymous-types"></a>匿名類型  
 匿名型別提供便利的方式，可以暫時將一組屬性到您想要在查詢結果中包含的項目。 這可讓您在查詢中，依任何順序選擇可用的欄位的任意組合，但未定義具名的資料類型的項目。  
  
 *匿名型別*由編譯器所動態建構。 編譯器，系統會指派類型的名稱，它可能會變更與每個新的編譯。 因此，名稱不能直接使用。 初始化匿名型別是以下列方式：  
  
 [!code-vb[VbLINQVbFeatures#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_5.vb)]  
  
 如需詳細資訊，請參閱[匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。  
  
## <a name="extension-methods"></a>擴充方法  
 擴充方法可讓您將方法加入至資料類型或從外部定義的介面。 這項功能可讓您，但不修改類型，作用中，將新方法新增至現有的類型。 標準查詢運算子本身是擴充方法，可提供一組[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]的查詢功能實作的任何類型<xref:System.Collections.Generic.IEnumerable%601>。 其他擴充功能<xref:System.Collections.Generic.IEnumerable%601>包含<xref:System.Linq.Enumerable.Count%2A>， <xref:System.Linq.Enumerable.Union%2A>，和<xref:System.Linq.Enumerable.Intersect%2A>。  
  
 下列擴充方法會加入列印方法至<xref:System.String>類別。  
  
 [!code-vb[VbLINQVbFeatures#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_6.vb)]  
  
 此方法會像一般的執行個體方法的呼叫<xref:System.String>:  
  
 [!code-vb[VbLINQVbFeatures#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_7.vb)]  
  
 如需詳細資訊，請參閱[擴充方法](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)。  
  
## <a name="lambda-expressions"></a>Lambda 運算式  
 Lambda 運算式是函式不會計算並傳回單一值的名稱。 不同於具名函式，可定義並在相同時間執行的 lambda 運算式。 下列範例會顯示 4。  
  
 [!code-vb[VbLINQVbFeatures#8](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_8.vb)]  
  
 您可以將 lambda 運算式定義指派給變數的名稱，然後呼叫函式中使用的名稱。 下列範例也會顯示 4。  
  
 [!code-vb[VbLINQVbFeatures#12](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_9.vb)]  
  
 在[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]，lambda 運算式的基礎許多標準查詢運算子。 編譯器會建立 lambda 運算式來擷取這類定義於基本查詢方法的計算`Where`， `Select`， `Order By`， `Take While`，和其他人。  
  
 例如，下列程式碼定義學員清單中傳回所有高年級的學生的查詢。  
  
 [!code-vb[VbLINQVbFeatures#9](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_10.vb)]  
  
 查詢定義會編譯到程式碼類似下列的範例中，使用兩個 lambda 運算式來指定的引數的`Where`和`Select`。  
  
 [!code-vb[VbLINQVbFeatures#10](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_11.vb)]  
  
 其中一個版本可以執行使用`For Each`迴圈：  
  
 [!code-vb[VbLINQVbFeatures#11](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_12.vb)]  
  
 如需詳細資訊，請參閱 [Lambda 運算式](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。  
  
## <a name="see-also"></a>另請參閱  
 [Language-Integrated Query (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 [使用 Visual Basic 撰寫 LINQ 入門](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [LINQ 和字串 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)  
 [Option Infer 陳述式](../../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
