---
title: 查詢作業中的類型關聯性
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
ms.openlocfilehash: 73a287541ddf115510bf6ab5c830eafac370cc3a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406725"
---
# <a name="type-relationships-in-query-operations-visual-basic"></a>查詢作業中的類型關聯性 (Visual Basic)

用於語言整合式查詢（LINQ）查詢作業的變數是強型別，而且必須彼此相容。 強型別會用於資料來源、查詢本身和查詢執行中。 下圖識別用來描述 LINQ 查詢的詞彙。 如需查詢各部分的詳細資訊，請參閱[基本查詢作業（Visual Basic）](basic-query-operations.md)。

![顯示反白顯示專案之虛擬代碼查詢的螢幕擷取畫面。](./media/type-relationships-in-query-operations/linq-query-description-terms.png)

查詢中的範圍變數類型必須與資料來源中的元素類型相容。 查詢變數的類型必須與子句中定義的 sequence 元素相容 `Select` 。 最後，順序元素的類型也必須與執行查詢的語句中所使用之迴圈控制變數的類型相容 `For Each` 。 這種強型別有助於在編譯時期識別類型錯誤。

Visual Basic 藉由實作為區欄位型別推斷（也稱為*隱含*類型），讓強型別變得方便。 上述範例中會使用該功能，您會在整個 LINQ 範例和檔中看到其使用方式。 在 Visual Basic 中，只會使用不含子句的語句來完成區欄位型別推斷 `Dim` `As` 。 在下列範例中， `city` 是強型別（string）。

[!code-vb[VbLINQTypeRels#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#1)]

> [!NOTE]
> 區欄位型別推斷只有在設為時才適用 `Option Infer` `On` 。 如需詳細資訊，請參閱[Option 推斷語句](../../../language-reference/statements/option-infer-statement.md)。

不過，即使您在查詢中使用區欄位型別推斷，資料來源中的變數、查詢變數和查詢執行迴圈中都會出現相同的類型關聯性。 當您撰寫 LINQ 查詢，或使用檔中的範例和程式碼範例時，對這些型別關聯性有基本瞭解非常有用。

針對不符合從資料來源傳回之類型的範圍變數，您可能需要指定明確的類型。 您可以使用子句來指定範圍變數的類型 `As` 。 不過，如果轉換是[縮小轉換](../../language-features/data-types/widening-and-narrowing-conversions.md)，而且設定為，這會導致錯誤 `Option Strict` `On` 。 因此，我們建議您在從資料來源抓取的值上執行轉換。 您可以使用方法，將資料來源中的值轉換成明確範圍變數類型 <xref:System.Linq.Enumerable.Cast%2A> 。 您也可以將子句中選取的值 `Select` ，轉換成與範圍變數類型不同的明確類型。 下列程式碼說明這些點。

[!code-vb[VbLINQTypeRels#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#4)]

## <a name="queries-that-return-entire-elements-of-the-source-data"></a>傳回來源資料之整個元素的查詢

下列範例顯示的 LINQ 查詢作業會傳回從來源資料選取的一系列元素。 來源（ `names` ）包含字串陣列，而查詢輸出則是包含以字母 M 開頭之字串的序列。

[!code-vb[VbLINQTypeRels#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#2)]

這相當於下列程式碼，但更短且更容易撰寫。 在 Visual Basic 中，依賴查詢中的區欄位型別推斷是慣用的樣式。

[!code-vb[VbLINQTypeRels#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#3)]

下列關聯性存在於上述程式碼範例中，不論是隱含或明確地決定類型。

1. 資料來源中的專案類型， `names` 是查詢中範圍變數的類型 `name` 。

2. 所選取物件的類型會 `name` 決定查詢變數的類型 `mNames` 。 以下 `name` 是字串，因此查詢變數是 Visual Basic 中的 IEnumerable （Of string）。

3. 在中定義的查詢 `mNames` 會在迴圈中執行 `For Each` 。 迴圈會逐一查看執行查詢的結果。 因為 `mNames` 在執行時，會傳回一連串的字串，所以迴圈反覆運算變數 `nm` 也是字串。

## <a name="queries-that-return-one-field-from-selected-elements"></a>從選取的元素傳回一個欄位的查詢

下列範例顯示的 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 查詢作業會傳回一個序列，其中包含從資料來源選取之每個元素的一個部分。 查詢會接受物件的集合 `Customer` 做為其資料來源，並僅投射 `Name` 結果中的屬性。 因為客戶名稱是字串，所以查詢會產生一連串的字串做為輸出。

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

1. 資料來源中的專案類型， `customers` 是查詢中範圍變數的類型 `cust` 。 在此範例中，該類型為 `Customer` 。

2. 語句會傳回 `Select` `Name` 每個物件的屬性， `Customer` 而不是整個物件。 因為 `Name` 是字串，所以查詢變數 `custNames` 會再次是 IEnumerable （of string），而不是 `Customer` 。

3. 因為 `custNames` 代表字串序列，所以 `For Each` 迴圈的反復專案變數 `custName` 必須是字串。

如果沒有區欄位型別推斷，上一個範例會更難以撰寫和瞭解，如下列範例所示。

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

下列範例會顯示更複雜的情況。 在上述範例中，明確地指定所有變數的類型並不方便。 在此範例中，這是不可能的。 `Customer`此查詢中的子句會傳回原始物件的兩個屬性，而不是從資料來源中選取整個專案，或從每個專案中選取單一欄位 `Select` `Customer` ： `Name` 和 `City` 。 為了回應 `Select` 子句，編譯器會定義包含這兩個屬性的匿名型別。 `nameCityQuery`在迴圈中執行的結果 `For Each` 是新的匿名型別之實例的集合。 因為匿名型別沒有可用的名稱，所以您不能明確地指定或的型別 `nameCityQuery` `custInfo` 。 也就是說，如果使用匿名型別，您就不需要使用型別名稱來取代 `String` 中的 `IEnumerable(Of String)` 。 如需詳細資訊，請參閱[匿名](../../language-features/objects-and-classes/anonymous-types.md)型別。

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

雖然無法針對上述範例中的所有變數指定類型，但關聯性仍然相同。

1. 資料來源中的專案類型再次是查詢中的範圍變數類型。 在此範例中， `cust` 是的實例 `Customer` 。

2. 因為 `Select` 語句會產生匿名型別，所以查詢變數 `nameCityQuery` 必須以匿名型別隱含地輸入。 匿名型別沒有可用的名稱，因此無法明確指定。

3. 迴圈中的反覆運算變數類型 `For Each` 是在步驟2中建立的匿名型別。 因為類型沒有可用的名稱，所以必須隱含地判斷迴圈反覆運算變數的類型。

## <a name="see-also"></a>另請參閱

- [使用 Visual Basic 撰寫 LINQ 入門](getting-started-with-linq.md)
- [匿名類型](../../language-features/objects-and-classes/anonymous-types.md)
- [區域型別推斷](../../language-features/variables/local-type-inference.md)
- [Visual Basic 中的 LINQ 簡介](../../language-features/linq/introduction-to-linq.md)
- [LINQ](../../language-features/linq/index.md)
- [查詢](../../../language-reference/queries/index.md)
