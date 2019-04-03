---
title: 查詢作業中的類型關聯性 (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: fd2bcfad0ae24288887500ae6286e6ac73fddac5
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822332"
---
# <a name="type-relationships-in-query-operations-visual-basic"></a>查詢作業中的類型關聯性 (Visual Basic)
在中使用變數[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]查詢作業強型別，且必須彼此相容。 資料來源、 查詢本身，及執行查詢，則會使用強型別。 下圖識別用來描述[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]查詢。 如需查詢的組件的詳細資訊，請參閱[基本查詢作業 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md)。  
  
 ![顯示反白顯示的項目使用的虛擬程式碼查詢的螢幕擷取畫面。](./media/type-relationships-in-query-operations/linq-query-description-terms.png)  
  
 在查詢中範圍變數的類型必須相容於資料來源中的項目型別。 查詢變數的類型必須是相容的序列項目中定義`Select`子句。 最後，序列項目類型也必須與用於迴圈控制變數的型別相容`For Each`執行查詢的陳述式。 這個強型別，可協助識別在編譯時期類型錯誤。  
  
 Visual Basic 就可以輸入強式方便也就實作區域型別推斷*隱含型別*。 功能可在上述範例中，而且您會看到它用在整個[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]範例與文件。 在 Visual Basic 中的區域型別推斷透過來完成只要`Dim`陳述式不含`As`子句。 在下列範例中，`city`強型別為字串。  
  
 [!code-vb[VbLINQTypeRels#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#1)]  
  
> [!NOTE]
>  區域類型推斷運作時，才`Option Infer`設為`On`。 如需詳細資訊，請參閱 < [Option Infer 陳述式](../../../../visual-basic/language-reference/statements/option-infer-statement.md)。  
  
 不過，即使您在查詢中使用區域型別推斷，相同的型別關聯性會出現在資料來源中的變數，查詢變數，以及查詢執行迴圈。 您最好具備的這些型別關聯性的基本知識，當您撰寫[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]查詢或使用的範例和文件中的程式碼範例。  
  
 若要指定明確的類型不符合資料來源傳回的型別之範圍變數。 您可以使用，以指定範圍變數的型別`As`子句。 不過，這會導致錯誤轉換是否[的縮小轉換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)並`Option Strict`設定為`On`。 因此，我們建議您執行轉換，從資料來源擷取的值。 您可以將值轉換從資料來源為明確的範圍變數的型別使用<xref:System.Linq.Enumerable.Cast%2A>方法。 您也可以轉型的值中選取`Select`子句來明確的類型不同的範圍變數的型別。 這些點是以下列程式碼所示。  
  
 [!code-vb[VbLINQTypeRels#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#4)]  
  
## <a name="queries-that-return-entire-elements-of-the-source-data"></a>傳回整個項目之來源資料的查詢  
 下列範例所示[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]查詢傳回的資料來源選取的項目序列的作業。 來源、 `names`，包含陣列的字串，並將查詢輸出是序列，其中包含以字母 M 為開頭的字串。  
  
 [!code-vb[VbLINQTypeRels#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#2)]  
  
 這相當於下列程式碼，但較短，而且更容易撰寫。 依賴在查詢中的區域類型推斷是慣用的樣式，在 Visual Basic 中。  
  
 [!code-vb[VbLINQTypeRels#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#3)]  
  
 下列關聯性會存在於這兩個先前的程式碼範例中，是否決定類型的隱含或明確的範圍。  
  
1.  在資料來源中，元素的型別`names`，為範圍變數的型別`name`，在查詢中。  
  
2.  已選取的物件型別`name`，決定查詢變數的型別`mNames`。 這裡`name`是一個字串，因此查詢變數是在 Visual Basic 的 IEnumerable (Of String)。  
  
3.  中定義的查詢`mNames`中執行`For Each`迴圈。 迴圈會逐一執行查詢的結果。 因為`mNames`，當它執行時，會傳回一系列的字串，迴圈反覆運算變數`nm`，也是一個字串。  
  
## <a name="queries-that-return-one-field-from-selected-elements"></a>從選取的項目傳回一個欄位的查詢  
 下列範例所示[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]查詢傳回的序列包含每個資料來源的已選取的項目只有一個部分的作業。 查詢需要耗費的集合`Customer`物件做為其資料來源，並僅限專案`Name`結果中的屬性。 因為客戶名稱是字串，此查詢會產生一序列的字串做為輸出。  
  
```vb  
' Method GetTable returns a table of Customer objects.  
Dim customers = db.GetTable(Of Customer)()  
Dim custNames = From cust In customers   
                Where cust.City = "London"   
                Select cust.Name  
  
For Each custName In custNames  
    Console.WriteLine(custName)  
Next  
```  
  
 就像是較簡單的範例中的變數之間的關聯性。  
  
1.  在資料來源中，元素的型別`customers`，為範圍變數的型別`cust`，在查詢中。 在此範例中，類型`Customer`。  
  
2.  `Select`陳述式會傳回`Name`每個屬性`Customer`而不是整個物件的物件。 因為`Name`是一個字串，查詢變數`custNames`，將會一次是 IEnumerable (Of String)，不`Customer`。  
  
3.  因為`custNames`代表字串的一連串`For Each`迴圈的反覆運算變數， `custName`，必須是字串。  
  
 區域型別推斷，如果沒有上一個範例是較為撰寫，並了解，如下列範例所示。  
  
```vb  
' Method GetTable returns a table of Customer objects.  
 Dim customers As Table(Of Customer) = db.GetTable(Of Customer)()  
 Dim custNames As IEnumerable(Of String) =  
     From cust As Customer In customers   
     Where cust.City = "London"   
     Select cust.Name  
  
 For Each custName As String In custNames  
     Console.WriteLine(custName)  
 Next  
```  
  
## <a name="queries-that-require-anonymous-types"></a>要求匿名類型的查詢  
 下列範例會示範一個比較複雜狀況。 在上述範例中，很不方便明確指定類型的所有變數。 在此範例中，它是不可能。 而非選取整個`Customer`從資料來源或從每個元素的單一欄位的項目`Select`，在此查詢中的子句會傳回兩個屬性的原始`Customer`物件：`Name`和`City`。 以回應`Select`子句，編譯器會定義匿名型別，其中包含這兩個屬性。 執行的結果`nameCityQuery`在`For Each`迴圈是新的匿名型別的執行個體的集合。 因為匿名型別沒有可用的名稱，您無法指定的型別`nameCityQuery`或`custInfo`明確。 也就是以匿名型別，您有任何型別名稱，以用來取代`String`在`IEnumerable(Of String)`。 如需詳細資訊，請參閱[匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。  
  
```vb  
' Method GetTable returns a table of Customer objects.  
Dim customers = db.GetTable(Of Customer)()  
Dim nameCityQuery = From cust In customers   
                    Where cust.City = "London"   
                    Select cust.Name, cust.City  
  
For Each custInfo In nameCityQuery  
    Console.WriteLine(custInfo.Name)  
Next  
```  
  
 雖然您不能在上述範例中指定的所有變數的型別，關聯性維持不變。  
  
1.  資料來源中項目的類型一次是在查詢中範圍變數的類型。 在此範例中，`cust`的執行個體`Customer`。  
  
2.  因為`Select`陳述式會產生匿名型別，查詢變數`nameCityQuery`，必須為匿名型別隱含型別。 匿名型別沒有可用的名稱，並因此無法明確地指定。  
  
3.  在反覆項目變數的型別`For Each`迴圈是步驟 2 中建立匿名型別。 因為類型沒有可用的名稱，必須以隱含方式決定迴圈的反覆項目變數的型別。  
  
## <a name="see-also"></a>另請參閱

- [使用 Visual Basic 撰寫 LINQ 入門](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [匿名類型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [區域類型推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [查詢](../../../../visual-basic/language-reference/queries/index.md)
