---
title: "支援 LINQ 的 Visual Basic 功能 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic, LINQ features
- LINQ [Visual Basic], features supporting LINQ
ms.assetid: c821bb50-b6f6-4cf9-8aba-2717e465bd3a
caps.latest.revision: 51
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3bca15a07a88195589b9c9de5f9842eea42912f1
ms.lasthandoff: 03/13/2017

---
# <a name="visual-basic-features-that-support-linq"></a>支援 LINQ 的 Visual Basic 功能
名稱[!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)]指的是在 Visual Basic 中支援的查詢語法，並直接在語言中的其他語言建構的技術。 使用[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]，您不需要學習新語言對外部資料來源進行查詢。 您可以使用 Visual Basic 查詢對關聯式資料庫、 XML 存放區或物件中的資料。 這項整合的查詢語言功能可讓您編譯時期檢查語法錯誤和型別安全。 這項整合也可確保您已經知道大部分您必須知道要在 Visual Basic 中撰寫內容豐富且具有不同的查詢。  
  
 下列章節說明足夠的詳細資料，可讓您開始閱讀簡介文件、 程式碼範例和範例應用程式中支援 LINQ 的語言建構。 您也可以按一下連結，找出如何語言功能共同啟用語言整合查詢的詳細的說明。 很好的起點是[逐步解說︰ 在 Visual Basic 中撰寫查詢](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)。  
  
## <a name="query-expressions"></a>查詢運算式  
 Visual Basic 中的查詢運算式可以用類似的 SQL 或 XQuery 的宣告式語法來表示。 在編譯時期，查詢語法會轉換成標準查詢運算子擴充方法的 LINQ 提供者實作的方法呼叫。 標準查詢運算子是藉由指定具有適當的命名空間範圍中的應用程式控制`Imports`陳述式。 Visual Basic 查詢運算式語法看起來像這樣︰  
  
 [!code-vb[VbLINQVbFeatures #&1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_1.vb)]  
  
 如需詳細資訊，請參閱[Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)。  
  
## <a name="implicitly-typed-variables"></a>隱含型別的變數  
 而不是明確指定型別，當您宣告並初始化變數時，您可以啟用編譯器推斷並指派類型。 這指*區域型別推斷*。  
  
 變數的型別推斷是強型別，如同您明確地指定的型別的變數。 定義方法主體內的區域變數時，只有區域型別推斷的運作方式。 如需詳細資訊，請參閱[Option Infer 陳述式](../../../../visual-basic/language-reference/statements/option-infer-statement.md)和[本機的型別推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。  
  
 下列範例說明區域型別推斷。 若要使用此範例中，您必須設定`Option Infer`到`On`。  
  
 [!code-vb[VbLINQVbFeatures #&2;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_2.vb)]  
  
 區域型別推斷也可讓建立匿名型別，在本節稍後說明和所需的 LINQ 查詢。  
  
 在下列 LINQ 範例中，型別推斷起因於`Option Infer`是`On`或`Off`。 如果，就會發生編譯時期錯誤`Option Infer`是`Off`和`Option Strict`是`On`。  
  
 [!code-vb[VbLINQVbFeatures #&3;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_3.vb)]  
  
## <a name="object-initializers"></a>物件初始設定式  
 當您必須建立匿名型別來保存查詢結果的查詢運算式中使用物件初始設定式。 它們也可用來初始化物件的具名查詢之外的型別。 藉由使用物件初始設定式，您可以初始化單一行中的物件，而不需要明確呼叫建構函式。 假設您有一個名為的類別`Customer`具有公用`Name`和`Phone`屬性，以及其他內容，物件初始設定式可以使用這種方式︰  
  
 [!code-vb[VbLINQVbFeatures #&4;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_4.vb)]  
  
 如需詳細資訊，請參閱[物件初始設定式︰ 具名和匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)。  
  
## <a name="anonymous-types"></a>匿名類型  
 匿名型別提供便利的方式，可以暫時將一組屬性，您想要在查詢結果中包含的項目。 這可讓您在查詢中，依任何順序選擇可用的欄位的任意組合，而不定義項目的具名的資料型別。  
  
 *匿名型別*由編譯器所動態建構。 由編譯器指派型別的名稱，可能會變更與每個新的編譯。 因此，名稱不能直接使用。 初始化匿名型別是以下列方式︰  
  
 [!code-vb[VbLINQVbFeatures #&5;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_5.vb)]  
  
 如需詳細資訊，請參閱[匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。  
  
## <a name="extension-methods"></a>擴充方法  
 擴充方法可讓您將方法加入至資料型別或外部定義的介面。 這項功能可讓您能，作用中，將新方法加入現有的型別而不實際修改型別。 標準查詢運算子本身是一組延伸方法，提供[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]查詢實作<xref:System.Collections.Generic.IEnumerable%601>.</xref:System.Collections.Generic.IEnumerable%601>任何類型的功能 其他擴充功能<xref:System.Collections.Generic.IEnumerable%601>包括<xref:System.Linq.Enumerable.Count%2A>， <xref:System.Linq.Enumerable.Union%2A>，和<xref:System.Linq.Enumerable.Intersect%2A>.</xref:System.Linq.Enumerable.Intersect%2A> </xref:System.Linq.Enumerable.Union%2A> </xref:System.Linq.Enumerable.Count%2A> </xref:System.Collections.Generic.IEnumerable%601>  
  
 下列擴充方法會將列印的方法加入至<xref:System.String>類別。</xref:System.String>  
  
 [!code-vb[VbLINQVbFeatures #&6;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_6.vb)]  
  
 像<xref:System.String>::</xref:System.String>的一般執行個體方法呼叫方法  
  
 [!code-vb[VbLINQVbFeatures #&7;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_7.vb)]  
  
 如需詳細資訊，請參閱[擴充方法](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)。  
  
## <a name="lambda-expressions"></a>Lambda 運算式  
 Lambda 運算式是函式不會計算並傳回單一值的名稱。 不同於具名函式，可定義並執行一次的 lambda 運算式。 下列範例顯示的是 4。  
  
 [!code-vb[VbLINQVbFeatures #&8;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_8.vb)]  
  
 您可以將 lambda 運算式定義指派給變數的名稱，然後使用名稱來呼叫函式。 下列範例也會顯示 4。  
  
 [!code-vb[VbLINQVbFeatures #&12;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_9.vb)]  
  
 在[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]，lambda 運算式是許多標準查詢運算子的基礎。 編譯器會建立 lambda 運算式來擷取這類定義於基礎的查詢方法的計算`Where`， `Select`， `Order By`， `Take While`，等等。  
  
 例如，下列程式碼會定義傳回所有的資深學生的學生清單中的查詢。  
  
 [!code-vb[VbLINQVbFeatures #&9;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_10.vb)]  
  
 查詢定義會編譯成程式碼類似下列的範例中，使用兩個 lambda 運算式來指定的引數的`Where`和`Select`。  
  
 [!code-vb[VbLINQVbFeatures #&10;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_11.vb)]  
  
 其中一個版本可以執行使用`For Each`迴圈︰  
  
 [!code-vb[VbLINQVbFeatures #&11;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_12.vb)]  
  
 如需詳細資訊，請參閱[Lambda 運算式](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。  
  
## <a name="see-also"></a>另請參閱  
 [語言整合查詢 (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)   
 [在 Visual Basic 中撰寫 LINQ 入門](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [LINQ 和字串 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)   
 [Option Infer 陳述式](../../../../visual-basic/language-reference/statements/option-infer-statement.md)   
 [Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
