---
title: "類型關聯性的查詢作業 (Visual Basic) |Microsoft 文件"
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
- variable relationships [LINQ in Visual Basic]
- type information inferred [LINQ in Visual Basic]
- type relationships [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], type relationships
- data sources [LINQ in Visual Basic], type relationships
- LINQ [Visual Basic], type relationships
- inferring type information [LINQ in Visual Basic]
- relationships [LINQ in Visual Basic]
ms.assetid: b5ff4da5-f3fd-4a8e-aaac-1cbf52fa16f6
caps.latest.revision: 34
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: a966b69feca7a7021cafbccb7971913ea781c479
ms.lasthandoff: 03/13/2017

---
# <a name="type-relationships-in-query-operations-visual-basic"></a>查詢作業中的類型關聯性 (Visual Basic)
使用變數[!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)]查詢作業強型別，而且必須彼此相容。 強型別會使用資料來源、 查詢本身，以及執行查詢。 下圖識別用來描述[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]查詢。 如需查詢的組件的詳細資訊，請參閱[基本查詢作業 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md)。  
  
 ![反白顯示項目的虛擬程式碼查詢。](../../../../visual-basic/programming-guide/concepts/linq/media/sjltyperels.png "SJLtypeRels")  
LINQ 查詢中的部分  
  
 在查詢中的範圍變數的型別必須與資料來源中的項目型別相容。 查詢變數的型別必須是相容的序列項目中定義`Select`子句。 最後，序列項目的型別也必須與使用中的迴圈控制變數的型別相容`For Each`執行查詢的陳述式。 這個強型別，可協助在編譯時期型別錯誤的識別碼。  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]可以輸入強式方便實作區域型別推斷，也就是*隱含型別*。 在上述範例中，使用功能，和您會看見它用於整個[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]範例與文件。 在 Visual Basic 中區域型別推斷就會經由直接`Dim`陳述式，而不需要`As`子句。 在下列範例中，`city`強型別為字串。  
  
 [!code-vb[VbLINQTypeRels #&1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_1.vb)]  
  
> [!NOTE]
>  區域型別推斷運作時，才`Option Infer`設為`On`。 如需詳細資訊，請參閱[Option Infer 陳述式](../../../../visual-basic/language-reference/statements/option-infer-statement.md)。  
  
 不過，即使您在查詢中使用區域型別推斷，相同的型別關聯性會出現在資料來源中的變數時，查詢變數和查詢執行迴圈。 對於有基本了解這些型別關聯性的當您撰寫[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]查詢或使用範例和文件中的程式碼範例。  
  
 若要指定資料來源傳回的型別不符的範圍變數的明確型別。 您可以使用指定的範圍變數的型別`As`子句。 不過，這會導致錯誤如果轉換[縮小轉換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)和`Option Strict`設為`On`。 因此，我們建議您從資料來源擷取的值上執行轉換。 您可以將值從資料來源明確範圍變數型別使用<xref:System.Linq.Enumerable.Cast%2A>方法。</xref:System.Linq.Enumerable.Cast%2A> 您也可以轉換中所選取的值`Select`範圍變數的型別不同的明確型別子句。 這些點是以下列程式碼所示。  
  
 [!code-vb[VbLINQTypeRels #&4;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_2.vb)]  
  
## <a name="queries-that-return-entire-elements-of-the-source-data"></a>傳回來源資料的整個項目查詢  
 下列範例所示[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]查詢傳回的資料來源選取的項目序列的作業。 來源`names`，包含字串、 陣列和查詢輸出是序列，其中包含以字母 M 開頭的字串。  
  
 [!code-vb[VbLINQTypeRels #&2;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_3.vb)]  
  
 這相當於下列程式碼，但是比較簡短也更容易撰寫。 在查詢中的區域類型推斷依賴是 Visual Basic 中慣用的樣式。  
  
 [!code-vb[VbLINQTypeRels #&3;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_4.vb)]  
  
 下列關聯性存在於這兩個先前的程式碼範例中，是否隱含或明確決定型別。  
  
1.  資料來源中的項目類型`names`，是範圍變數的型別`name`，在查詢中。  
  
2.  已選取的物件型別`name`，查詢變數的型別，決定`mNames`。 這裡`name`是一個字串，因此查詢變數是在 Visual Basic 的 IEnumerable (Of String)。  
  
3.  中定義的查詢`mNames`中執行`For Each`迴圈。 迴圈會逐一執行查詢的結果。 因為`mNames`，當它執行時，會傳回字串，迴圈反覆運算變數序列`nm`，也是一個字串。  
  
## <a name="queries-that-return-one-field-from-selected-elements"></a>從選取的項目傳回一個欄位的查詢  
 下列範例所示[!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)]查詢傳回的序列則包含每個項目的選取自資料來源只有一個部分的作業。 查詢需要耗費大量`Customer`做為資料來源物件，並只專案`Name`結果中的屬性。 因為客戶名稱是字串，此查詢會產生一系列字串做為輸出。  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 變數之間的關聯性就像是在更簡單的範例。  
  
1.  資料來源中的項目類型`customers`，是範圍變數的型別`cust`，在查詢中。 在此範例中，型別是`Customer`。  
  
2.  `Select`陳述式會傳回`Name`每個屬性`Customer`而不是整個物件的物件。 因為`Name`為字串時，查詢變數`custNames`，會一次是 IEnumerable (Of String)，不`Customer`。  
  
3.  因為`custNames`代表序列的字串，`For Each`迴圈的反覆運算變數`custName`，必須為字串。  
  
 區域型別推斷，如果沒有上一個範例是較為撰寫，以及了解，如下列範例所示。  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
## <a name="queries-that-require-anonymous-types"></a>需要匿名型別的查詢  
 下列範例顯示更複雜的情況。 在上述範例中，很不方便明確地指定所有變數的型別。 在此範例中，就不可能。 而非選取整個`Customer`從資料來源或從每個元素的單一欄位的項目`Select`子句在此查詢會傳回兩個屬性的原始`Customer`物件︰`Name`和`City`。 為了回應`Select`子句，編譯器會定義匿名型別，其中包含這兩個屬性。 執行結果`nameCityQuery`中`For Each`迴圈是新的匿名型別的執行個體的集合。 因為匿名型別沒有可用的名稱，您無法指定的型別`nameCityQuery`或`custInfo`明確。 也就是匿名型別，有了您要用來取代任何型別名稱`String`中`IEnumerable(Of String)`。 如需詳細資訊，請參閱[匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
 雖然您不可以指定前一個範例中的所有變數的型別，關聯性維持不變。  
  
1.  資料來源中的項目類型是一次在查詢中的範圍變數的型別。 在此範例中，`cust`的執行個體`Customer`。  
  
2.  因為`Select`陳述式會產生匿名型別，查詢變數`nameCityQuery`，必須為匿名型別隱含型別。 匿名型別沒有可用的名稱，因此無法明確地指定。  
  
3.  在反覆項目變數的型別`For Each`迴圈是在步驟 2 中建立的匿名型別。 因為該型別沒有可用的名稱，必須以隱含方式決定迴圈反覆項目變數的型別。  
  
## <a name="see-also"></a>另請參閱  
 [在 Visual Basic 中撰寫 LINQ 入門](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)   
 [區域型別推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [在 Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [查詢](../../../../visual-basic/language-reference/queries/queries.md)
