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
ms.openlocfilehash: 4851d0a74de38f0fb6b6deee34cf7b3e66eb11b4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937484"
---
# <a name="type-relationships-in-query-operations-visual-basic"></a>查詢作業中的類型關聯性 (Visual Basic)
查詢作業中[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]使用的變數是強型別, 而且必須彼此相容。 強型別會用於資料來源、查詢本身和查詢執行中。 下圖識別用來描述[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]查詢的詞彙。 如需查詢各部分的詳細資訊, 請參閱[基本查詢作業 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md)。  
  
 ![顯示反白顯示專案之虛擬代碼查詢的螢幕擷取畫面。](./media/type-relationships-in-query-operations/linq-query-description-terms.png)  
  
 查詢中的範圍變數類型必須與資料來源中的元素類型相容。 查詢變數的類型必須與`Select`子句中定義的 sequence 元素相容。 最後, 順序元素的類型也必須與執行查詢的`For Each`語句中所使用之迴圈控制變數的類型相容。 這種強型別有助於在編譯時期識別類型錯誤。  
  
 Visual Basic 藉由實作為區欄位型別推斷 (也稱為*隱含*類型), 讓強型別變得方便。 在上述範例中, 會使用該功能, 您會在整個[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]範例和檔中看到其使用方式。 在 Visual Basic 中, 只會使用`Dim` `As`不含子句的語句來完成區欄位型別推斷。 在下列範例中, `city`是強型別 (string)。  
  
 [!code-vb[VbLINQTypeRels#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#1)]  
  
> [!NOTE]
> 區欄位型別推斷只有在設`Option Infer`為`On`時才適用。 如需詳細資訊, 請參閱[Option 推斷語句](../../../../visual-basic/language-reference/statements/option-infer-statement.md)。  
  
 不過, 即使您在查詢中使用區欄位型別推斷, 資料來源中的變數、查詢變數和查詢執行迴圈中都會出現相同的類型關聯性。 當您撰寫[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]查詢, 或使用檔中的範例和程式碼範例時, 對這些型別關聯性有基本瞭解非常有用。  
  
 針對不符合從資料來源傳回之類型的範圍變數, 您可能需要指定明確的類型。 您可以使用`As`子句來指定範圍變數的類型。 不過, 如果轉換是[縮小轉換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md), 而且`Option Strict`設定為`On`, 這會導致錯誤。 因此, 我們建議您在從資料來源抓取的值上執行轉換。 您可以使用<xref:System.Linq.Enumerable.Cast%2A>方法, 將資料來源中的值轉換成明確範圍變數類型。 您也可以將`Select`子句中選取的值, 轉換成與範圍變數類型不同的明確類型。 下列程式碼說明這些點。  
  
 [!code-vb[VbLINQTypeRels#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#4)]  
  
## <a name="queries-that-return-entire-elements-of-the-source-data"></a>傳回來源資料之整個元素的查詢  
 下列範例顯示[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]的查詢作業會傳回從來源資料選取的一系列元素。 來源 ( `names`) 包含字串陣列, 而查詢輸出則是包含以字母 M 開頭之字串的序列。  
  
 [!code-vb[VbLINQTypeRels#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#2)]  
  
 這相當於下列程式碼, 但更短且更容易撰寫。 在 Visual Basic 中, 依賴查詢中的區欄位型別推斷是慣用的樣式。  
  
 [!code-vb[VbLINQTypeRels#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#3)]  
  
 下列關聯性存在於上述程式碼範例中, 不論是隱含或明確地決定類型。  
  
1. 資料來源`names`中的專案類型, 是查詢中範圍`name`變數的類型。  
  
2. 所選取`name`物件的類型會決定查詢`mNames`變數的類型。 以下`name`是字串, 因此查詢變數是 Visual Basic 中的 IEnumerable (of string)。  
  
3. 在中`mNames`定義的查詢會`For Each`在迴圈中執行。 迴圈會逐一查看執行查詢的結果。 因為`mNames`在執行時, 會傳回一連串的字串, 所以迴圈反覆運算`nm`變數也是字串。  
  
## <a name="queries-that-return-one-field-from-selected-elements"></a>從選取的元素傳回一個欄位的查詢  
 下列範例顯示[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]的查詢作業會傳回一個序列, 其中包含從資料來源選取之每個元素的一個部分。 查詢會接受`Customer`物件的集合做為其資料來源, 並僅投射`Name`結果中的屬性。 因為客戶名稱是字串, 所以查詢會產生一連串的字串做為輸出。  
  
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
  
 變數之間的關聯性類似于較簡單的範例。  
  
1. 資料來源`customers`中的專案類型, 是查詢中範圍`cust`變數的類型。 在此範例中, 該類型`Customer`為。  
  
2. 語句會傳回每`Name`個`Customer`物件的屬性, 而不是整個物件。 `Select` 因為`Name`是字串, 所以查詢`custNames`變數會再次是 IEnumerable (of `Customer`string), 而不是。  
  
3. 因為`custNames`代表字串序列`For Each` , 所以`custName`迴圈的反復專案變數必須是字串。  
  
 如果沒有區欄位型別推斷, 上一個範例會更難以撰寫和瞭解, 如下列範例所示。  
  
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
  
## <a name="queries-that-require-anonymous-types"></a>需要匿名型別的查詢  
 下列範例會顯示更複雜的情況。 在上述範例中, 明確地指定所有變數的類型並不方便。 在此範例中, 這是不可能的。 此查詢中的`Customer` `Select`子句會傳回原始`Customer`物件的兩個屬性, 而不是從資料來源中選取整個專案, 或從每個專案中`Name`選取`City`單一欄位: 和。 為了回應`Select`子句, 編譯器會定義包含這兩個屬性的匿名型別。 在迴圈中執行`nameCityQuery`的結果是新的匿名型別之實例的集合。`For Each` 因為匿名型別沒有可用的名稱, 所以您不能明確地`nameCityQuery`指定`custInfo`或的型別。 也就是說, 如果使用匿名型別, 您就不需要使用型別名稱來取代`String`中`IEnumerable(Of String)`的。 如需詳細資訊，請參閱[匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。  
  
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
  
 雖然無法針對上述範例中的所有變數指定類型, 但關聯性仍然相同。  
  
1. 資料來源中的專案類型再次是查詢中的範圍變數類型。 在此範例中`cust` , 是的`Customer`實例。  
  
2. 因為語句會產生匿名型別, 所以查詢`nameCityQuery`變數必須以匿名型別隱含地輸入。 `Select` 匿名型別沒有可用的名稱, 因此無法明確指定。  
  
3. `For Each`迴圈中的反覆運算變數類型是在步驟2中建立的匿名型別。 因為類型沒有可用的名稱, 所以必須隱含地判斷迴圈反覆運算變數的類型。  
  
## <a name="see-also"></a>另請參閱

- [使用 Visual Basic 撰寫 LINQ 入門](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [匿名類型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [區域類型推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [查詢](../../../../visual-basic/language-reference/queries/index.md)
