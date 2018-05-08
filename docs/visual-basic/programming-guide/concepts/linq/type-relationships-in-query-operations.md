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
ms.openlocfilehash: ed0072eeb44a17201ddab2af6f6a44fd14461029
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="type-relationships-in-query-operations-visual-basic"></a>查詢作業中的類型關聯性 (Visual Basic)
在中使用變數[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]查詢作業強型別，而且必須為彼此相容。 強型別會使用資料來源、 查詢本身，以及執行查詢。 如下圖所識別的詞彙用於描述[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]查詢。 如需查詢的組件的詳細資訊，請參閱[基本查詢作業 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md)。  
  
 ![虛擬程式碼查詢反白顯示的項目。] (../../../../visual-basic/programming-guide/concepts/linq/media/sjltyperels.png "SJLtypeRels")  
LINQ 查詢的組件  
  
 在查詢中範圍變數的類型必須是相容的資料來源中的項目類型。 查詢變數的型別必須與所定義的序列項目相容`Select`子句。 最後，序列項目的型別也必須相容於迴圈控制變數中所使用的型別`For Each`執行查詢的陳述式。 這個強型別，可協助識別在編譯時期型別錯誤。  
  
 Visual Basic 中，可以輸入強式方便藉由實作區域類型推斷，也稱為*隱含型別*。 在上述範例中，使用功能，您會看到它用於整個[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]範例與文件。 在 Visual Basic 中，區域類型推斷只使用達成`Dim`陳述式不含`As`子句。 在下列範例中，`city`強型別為字串。  
  
 [!code-vb[VbLINQTypeRels#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_1.vb)]  
  
> [!NOTE]
>  區域類型推斷運作時，才`Option Infer`設`On`。 如需詳細資訊，請參閱[Option Infer 陳述式](../../../../visual-basic/language-reference/statements/option-infer-statement.md)。  
  
 不過，即使您在查詢中使用區域類型推斷，相同的類型關聯性會出現在資料來源中的變數、 查詢變數和查詢執行迴圈。 對於有這些類型關聯性的基本了解，當您撰寫[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]查詢或使用範例和文件中的程式碼範例。  
  
 若要指定明確的類型不符合資料來源傳回的型別範圍變數。 您可以使用，以指定範圍變數的型別`As`子句。 不過，這會導致錯誤如果轉換[縮小轉換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)和`Option Strict`設`On`。 因此，我們建議您執行轉換，從資料來源擷取的值。 您可以將值從資料來源明確範圍變數型別使用<xref:System.Linq.Enumerable.Cast%2A>方法。 您也可以轉型的值中選取`Select`子句來明確的類型不同的範圍變數的型別。 這些點是以下列程式碼所示。  
  
 [!code-vb[VbLINQTypeRels#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_2.vb)]  
  
## <a name="queries-that-return-entire-elements-of-the-source-data"></a>傳回來源資料的整個項目查詢  
 下列範例所示[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]查詢傳回的資料來源選取的項目序列的作業。 來源`names`，包含陣列的字串，並查詢輸出會包含字串字母 M 開頭的順序。  
  
 [!code-vb[VbLINQTypeRels#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_3.vb)]  
  
 這相當於下列程式碼，但更短也更容易撰寫。 在查詢中的區域類型推斷，因而會是在 Visual Basic 中的慣用的樣式。  
  
 [!code-vb[VbLINQTypeRels#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_4.vb)]  
  
 下列關聯性存在於這兩個先前的程式碼範例中，類型在隱含或明確地決定是否。  
  
1.  資料來源中的項目類型`names`，是的範圍變數的型別`name`，在查詢中。  
  
2.  已選取的物件型別`name`，查詢變數的類型會決定`mNames`。 這裡`name`是一個字串，因此查詢變數是在 Visual Basic 的 IEnumerable (Of String)。  
  
3.  中定義的查詢`mNames`中執行`For Each`迴圈。 迴圈會逐一執行查詢的結果。 因為`mNames`、 當它執行時，會傳回字串，迴圈反覆運算變數序列`nm`，也是字串。  
  
## <a name="queries-that-return-one-field-from-selected-elements"></a>從選取的項目傳回一個欄位的查詢  
 下列範例所示[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]查詢傳回序列，包含選取自資料來源的每個項目只能有一個部分的作業。 查詢使用的集合`Customer`物件當做它的資料來源，並只投射`Name`結果中的屬性。 因為客戶名稱是字串，此查詢會產生一連串的字串做為輸出。  
  
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
  
1.  資料來源中的項目類型`customers`，是的範圍變數的型別`cust`，在查詢中。 在此範例中，類型`Customer`。  
  
2.  `Select`陳述式會傳回`Name`每個屬性`Customer`而不是整個物件的物件。 因為`Name`為字串時，查詢變數`custNames`，一次會 IEnumerable (Of String) 不屬於`Customer`。  
  
3.  因為`custNames`代表序列的字串，`For Each`迴圈的反覆運算變數， `custName`，必須是字串。  
  
 區域類型推斷，如果沒有上一個範例是比較麻煩，若要撰寫，而且了解，如下列範例所示。  
  
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
  
## <a name="queries-that-require-anonymous-types"></a>需要匿名類型的查詢  
 下列範例會示範更複雜的情況。 在上述範例中，它不方便明確指定類型的所有變數。 在此範例中，就不可能。 而非選取整個`Customer`項目從資料來源或從每個元素的單一欄位`Select`子句在此查詢會傳回兩個屬性的原始`Customer`物件：`Name`和`City`。 以回應`Select`子句，編譯器會定義包含這兩個屬性的匿名型別。 執行結果`nameCityQuery`中`For Each`迴圈是新的匿名型別的執行個體的集合。 因為匿名型別沒有可用的名稱，您無法指定的型別`nameCityQuery`或`custInfo`明確。 也就是以匿名型別，您有沒有型別名稱，可使用取代`String`中`IEnumerable(Of String)`。 如需詳細資訊，請參閱[匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。  
  
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
  
 雖然您不可以指定在上述範例中的所有變數的型別，關聯性維持不變。  
  
1.  資料來源中的項目類型是一次在查詢中範圍變數的類型。 在此範例中，`cust`的執行個體`Customer`。  
  
2.  因為`Select`陳述式會產生匿名型別，查詢變數`nameCityQuery`，必須為匿名型別隱含型別。 匿名型別沒有可用的名稱，因此無法明確地指定。  
  
3.  在反覆項目變數的型別`For Each`迴圈是步驟 2 中建立匿名型別。 由於類型具有沒有可用的名稱，必須以隱含方式決定迴圈的反覆項目變數的型別。  
  
## <a name="see-also"></a>另請參閱  
 [使用 Visual Basic 撰寫 LINQ 入門](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [匿名類型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [區域類型推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [查詢](../../../../visual-basic/language-reference/queries/queries.md)
