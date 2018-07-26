---
title: 支援 LINQ 的 Visual Basic 功能
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, LINQ features
- LINQ [Visual Basic], features supporting LINQ
ms.assetid: c821bb50-b6f6-4cf9-8aba-2717e465bd3a
ms.openlocfilehash: db2eff2f7c19a3c510e7b212f5bb406d7a885439
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2018
ms.locfileid: "39199143"
---
# <a name="visual-basic-features-that-support-linq"></a>支援 LINQ 的 Visual Basic 功能
名稱[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]指的是支援的查詢語法，並直接在語言中的其他語言建構的 Visual Basic 中的技術。 使用[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]，您不必學習新語言來查詢外部資料來源。 您可以使用 Visual Basic，就可查詢對關聯式資料庫、 XML 存放區或物件中的資料。 這項整合到語言的查詢功能可讓您編譯時間檢查有語法錯誤和型別安全。 這項整合也可確保您已經知道大部分的您必須知道要在 Visual Basic 中撰寫內容豐富且各種查詢。  
  
 下列各節說明在足夠的詳細資料，可讓您開始閱讀簡介文件、 程式碼範例和範例應用程式中支援 LINQ 的語言建構。 您也可以按一下連結，找出的語言功能即在一起的 language integrated query，以便更詳細的說明。 很好的起點開始[逐步解說： 在 Visual Basic 中撰寫查詢](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)。  
  
## <a name="query-expressions"></a>查詢運算式  
 在 Visual Basic 中的查詢運算式可以是以類似於 SQL 或 XQuery 的宣告式語法來表示。 在編譯時期，查詢語法會轉換成方法呼叫的標準查詢運算子擴充方法的 LINQ 提供者的實作。 藉由指定適當的命名空間與標準查詢運算子是在範圍內的應用程式控制項`Imports`陳述式。 Visual Basic 查詢運算式語法看起來像這樣：  
  
 [!code-vb[VbLINQVbFeatures#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_1.vb)]  
  
 如需詳細資訊，請參閱 <<c0> [ 在 Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)。  
  
## <a name="implicitly-typed-variables"></a>隱含類型的變數  
 而不是明確指定類型，當您宣告並初始化變數時，您可以讓編譯器推斷並指派類型。 這指*區域型別推斷*。  
  
 其型別推斷的變數是強型別，就像您明確地指定的型別的變數。 區域類型推斷僅適用於您要定義方法主體內區域變數。 如需詳細資訊，請參閱 < [Option Infer 陳述式](../../../../visual-basic/language-reference/statements/option-infer-statement.md)並[區域型別推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。  
  
 下列範例會說明區域類型推斷。 若要使用此範例中，您必須設定`Option Infer`至`On`。  
  
 [!code-vb[VbLINQVbFeatures#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_2.vb)]  
  
 區域類型推斷也讓您能夠建立匿名型別，而且在這一節稍後說明所需的 LINQ 查詢。  
  
 在下列 LINQ 範例中，型別推斷如果就會發生`Option Infer`可能`On`或`Off`。 如果，就會發生編譯時期錯誤`Option Infer`已`Off`並`Option Strict`是`On`。  
  
 [!code-vb[VbLINQVbFeatures#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_3.vb)]  
  
## <a name="object-initializers"></a>物件初始設定式  
 當您必須建立匿名型別來保存查詢的結果查詢運算式中使用物件初始設定式。 它們也可用來初始化查詢之外的具名類型的物件。 藉由使用物件初始設定式，您可以初始化單一行中的物件，而不需要明確呼叫建構函式。 假設您有一個名為類別`Customer`具有公用`Name`和`Phone`屬性，以及其他屬性，可以使用物件初始設定式以這種方式：  
  
 [!code-vb[VbLINQVbFeatures#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_4.vb)]  
  
 如需詳細資訊，請參閱 <<c0> [ 物件初始設定式： 具名和匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)。  
  
## <a name="anonymous-types"></a>匿名類型  
 匿名型別提供便利的方式，可以暫時將一組屬性，到您想要在查詢結果中包含的項目。 這可讓您選擇在查詢中，依任何順序的可用欄位的任何組合，而不定義具名的資料型別項目。  
  
 *匿名型別*由編譯器所動態建構。 由編譯器指派型別的名稱，它可能會變更與每個新的編譯。 因此，名稱不能直接使用。 匿名型別會以下列方式初始化：  
  
 [!code-vb[VbLINQVbFeatures#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_5.vb)]  
  
 如需詳細資訊，請參閱[匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。  
  
## <a name="extension-methods"></a>擴充方法  
 擴充方法可讓您將方法加入至資料型別或從外部定義的介面。 這項功能可讓您，而不需要實際修改型別，作用中，將新方法新增至現有的類型。 標準查詢運算子本身是一組提供的擴充方法[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]的查詢功能會實作任何型別<xref:System.Collections.Generic.IEnumerable%601>。 其他擴充功能<xref:System.Collections.Generic.IEnumerable%601>包括<xref:System.Linq.Enumerable.Count%2A>， <xref:System.Linq.Enumerable.Union%2A>，和<xref:System.Linq.Enumerable.Intersect%2A>。  
  
 下列擴充方法新增至列印方法<xref:System.String>類別。  
  
 [!code-vb[VbLINQVbFeatures#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_6.vb)]  
  
 類似的一般執行個體方法呼叫的方法<xref:System.String>:  
  
 [!code-vb[VbLINQVbFeatures#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_7.vb)]  
  
 如需詳細資訊，請參閱[擴充方法](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)。  
  
## <a name="lambda-expressions"></a>Lambda 運算式  
 Lambda 運算式是函式不會計算並傳回單一值的名稱。 不同於具名函式，lambda 運算式可定義並執行一次。 下列範例會顯示 4。  
  
 [!code-vb[VbLINQVbFeatures#8](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_8.vb)]  
  
 您可以將 lambda 運算式定義指派給變數的名稱，並接著使用名稱來呼叫函式。 下列範例也會顯示 4。  
  
 [!code-vb[VbLINQVbFeatures#12](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_9.vb)]  
  
 在  [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]，lambda 運算式，構成許多標準查詢運算子。 編譯器會建立 lambda 運算式來擷取這類定義基本的查詢方法中的計算`Where`， `Select`， `Order By`， `Take While`，和其他人。  
  
 例如，下列程式碼定義的查詢會傳回所有的資深學生從學生的清單。  
  
 [!code-vb[VbLINQVbFeatures#9](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_10.vb)]  
  
 查詢定義會編譯成類似於下列的範例中，使用指定的引數的兩個 lambda 運算式的程式碼`Where`和`Select`。  
  
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
