---
title: Visual Basic 中的陣列
ms.date: 12/06/2017
f1_keywords:
- vb.Array
helpviewer_keywords:
- arrays [Visual Basic]
- Visual Basic, arrays
ms.assetid: dbf29737-b589-4443-bee6-a27588d9c67e
ms.openlocfilehash: 6b131d073e10f99feaf770fe5fd3c393551fa5a3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61907165"
---
# <a name="arrays-in-visual-basic"></a>Visual Basic 中的陣列

陣列是一組值，都稱為*項目*，以邏輯方式彼此相關。 例如，陣列可能包含中含有文法學校中; 每一年級學生數目陣列的每個項目是單一的年級的學生數目。 同樣地，陣列可能包含學生的成績類別;陣列的每個項目是一個單一的等級。

這是可能的個別變數，以儲存每個資料項目。 例如，如果我們的應用程式分析學生成績，我們可以使用個別的變數的每個學生的成績等級，例如`englishGrade1`，`englishGrade2`等等。這個方法有三個主要限制：

- 我們必須在執行階段知道我們必須處理正好多少成績。
- 快速處理大量的等級會變得不便。 接著，這可讓應用程式很有可能有嚴重的錯誤。
- 很難維護。 我們將新增的每個新級需要應用程式可修改、 重新編譯和重新部署。

藉由使用陣列，您可以參考相同的名稱，這些相關的值，並使用數字，稱為*index*或*註標*來識別個別的項目，根據在陣列中的位置。 陣列範圍從 0 到小於陣列中的項目總數的索引。 當您使用 Visual Basic 語法定義陣列的大小時，您會指定其最高的索引，不在陣列中的項目總數。 您可以使用將陣列視為一個單位，而且能夠逐一查看其項目可讓您不需要知道確切多少項目包含在設計階段。

開始說明前，先提供一些簡單的範例：

```vb
' Declare a single-dimension array of 5 numbers.
Dim numbers(4) As Integer

'Declare a single-dimension array and set its 4 values.
Dim numbers = New Integer() {1, 2, 4, 8}

' Change the size of an existing array to 16 elements and retain the current values.
ReDim Preserve numbers(15)

' Redefine the size of an existing array and reset the values.
ReDim numbers(15)

' Declare a 6 x 6 multidimensional array.
Dim matrix(5, 5) As Double

' Declare a 4 x 3 multidimensional array and set array element values.
Dim matrix = New Integer(3, 2) {{1, 2, 3}, {2, 3, 4}, {3, 4, 5}, {4, 5, 6}}

' Declare a jagged array
Dim sales()() As Double = New Double(11)() {}
```

## <a name="array-elements-in-a-simple-array"></a>簡單陣列中的陣列項目

讓我們建立名為陣列`students`儲存含有文法學校中每一年級的學生數目。 項目的索引範圍從 0 到 6。 使用這個陣列是簡單較宣告七個變數。

下圖顯示`students`陣列。 對於陣列的每一項目︰

- 項目的索引代表年級 (索引 0 代表幼稚園)。

- 項目包含的值代表該年級的學生數目。

![此圖顯示學生人數的陣列](./media/index/students-array-elements.gif)

下列範例包含建立及使用陣列的 Visual Basic 程式碼：

[!code-vb[simple-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/simple-array.vb)]

此範例會執行三件事：

- 它會宣告`students`七個元素的陣列。 數字`6`陣列中的宣告表示陣列中的最後一個索引，而其中一個陣列中的項目數大於或等於。
- 它會將值指派到陣列中每個項目。 陣列元素存取使用陣列名稱，並包括括號括住的個別項目的索引。
- 它會列出每個值的陣列。 此範例會使用[ `For` ](../../../language-reference/statements/for-next-statement.md)陳述式來存取陣列的每個項目依其索引編號。

`students`在上述範例中的陣列是一維陣列，因為它會使用一個索引。 陣列，其中會使用一個以上的索引或註標稱為*多維度*。 如需詳細資訊，請參閱本文的其餘部分並[Array Dimensions in Visual Basic](../../language-features/arrays/array-dimensions.md)。

## <a name="creating-an-array"></a>建立陣列

您可以定義陣列的大小，以數種方式：

- 宣告陣列時，您可以指定大小：

  [!code-vb[creating1](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#1)]

- 您可以使用`New`子句提供陣列的大小，會在建立時：

  [!code-vb[creating2](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#2)]

如果您有現有的陣列，您可以重新定義其大小所使用[ `ReDim` ](../../../language-reference/statements/redim-statement.md)陳述式。 您可以指定`ReDim`陳述式保留陣列中的值，或您可以指定它建立的空陣列。 下列範例顯示 `ReDim` 陳述式的不同使用方法，以修改現有陣列的大小。

[!code-vb[redimensioning](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#3)]

如需詳細資訊，請參閱 < [ReDim 陳述式](../../../language-reference/statements/redim-statement.md)。

## <a name="storing-values-in-an-array"></a>陣列中儲存值

您可以使用類型為 `Integer`的索引來存取陣列中的每一個位置。 使用括弧內的陣列索引即可參照各陣列的位置，從而儲存並擷取陣列中的值。 多維陣列的索引是以逗號 （，） 分隔。 各個陣列維度皆需一個索引。

下列範例顯示一些儲存和擷取值，在陣列中的陳述式。

[!code-vb[store-and-retrieve](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/store-and-retrieve.vb)]

## <a name="populating-an-array-with-array-literals"></a>陣列常值在陣列填入

藉由使用陣列常值，您可以在同一時間建立填入一組初始的值陣列。 陣列常值由大括弧 (`{}`) 括住的逗點分隔值清單構成。

當您使用陣列常值來建立陣列時，可以提供陣列類型，或者使用類型推斷來判別陣列類型。 下列範例會示範這兩個選項。

[!code-vb[create-with-literals](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#4)]

當您使用型別推斷時，陣列的類型取決於*主類型*常值的清單中。 主控項的型別是陣列中的所有其他類型可以將加寬的型別。 如果無法決定此唯一類型，則主類型將成為陣列中其他類型皆可縮小而成的唯一類型。 如果這些類型皆無法決定，則主類型為 `Object`。 例如，如果提供給陣列常值的值清單含有類型值 `Integer`、 `Long`和 `Double`，則結果陣列的類型是 `Double`。 因為`Integer`並`Long`只會擴展為`Double`，`Double`是主類型。 如需詳細資訊，請參閱 [Widening and Narrowing Conversions](../../language-features/data-types/widening-and-narrowing-conversions.md)。

> [!NOTE]
> 您可以使用型別推斷，只對定義為型別成員中的本機變數的陣列。 如果沒有明確的類型定義，定義在類別層級的陣列常值的陣列都屬於型別`Object[]`。 如需詳細資訊，請參閱 <<c0> [ 區域型別推斷](../variables/local-type-inference.md)。

請注意，前一個範例會定義`values`的型別陣列`Double`即使所有陣列常值型別的`Integer`。 您可以建立此陣列，因為陣列常值中的值可以擴展為`Double`值。

您也可以建立及使用填入的多維陣列*巢狀陣列常值*。 巢狀的陣列常值必須是結果陣列一致維度的數目。 下列範例會使用巢狀的陣列常值建立整數的二維陣列。

[!code-vb[nested-array-literals](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#5)]

當使用巢狀的陣列常值來建立和填入的陣列，如果巢狀的陣列常值中的項目數不相符，也會發生錯誤。 如果您明確宣告陣列變數，以比陣列常值的維度數目不同，也會發生錯誤。

正如同您可以一維陣列，您可以依賴類型推斷使用巢狀的陣列常值建立多維陣列時。 推斷的型別是所有的巢狀層級的所有陣列常值中的所有值的主類型。 下列範例會建立二維陣列型別的`Double[,]`類型的值從`Integer`和`Double`。

[!code-vb[nested-type-inference](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#6)]

如需其他範例，請參閱[How to:初始化陣列變數在 Visual Basic 中的](../../language-features/arrays/how-to-initialize-an-array-variable.md)。

## <a name="iterating-through-an-array"></a>逐一查看陣列

當您逐一查看陣列時，您存取陣列中的每個項目從最低到最高的索引，或從最高到最低。 一般而言，使用[For...下一個陳述式](../../../language-reference/statements/for-next-statement.md)或[每個...下一個陳述式](../../../language-reference/statements/for-each-next-statement.md)來逐一查看陣列的元素。 當您不知道陣列的上限時，您可以呼叫<xref:System.Array.GetUpperBound%2A?displayProperty=nameWithType>方法來取得索引的最大值。 雖然最小的索引值幾乎一律為 0，您就可以呼叫<xref:System.Array.GetLowerBound%2A?displayProperty=nameWithType>方法來取得索引的最小值。

下列範例使用會逐一一維陣列[ `For...Next` ](../../../language-reference/statements/for-next-statement.md)陳述式。

[!code-vb[iterate-one-dimensional-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate1d.vb)]

下列範例使用會逐一多維陣列[ `For...Next` ](../../../language-reference/statements/for-next-statement.md)陳述式。 <xref:System.Array.GetUpperBound%2A> 方法具有可指定維度的參數。 `GetUpperBound(0)` 傳回第一個維度中，最高的索引和`GetUpperBound(1)`傳回第二個維度的最高的索引。

[!code-vb[iterate-two-dimensional-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate2d.vb)]

下列範例會使用[每個...下一個陳述式](../../../language-reference/statements/for-each-next-statement.md)來逐一查看一維陣列和二維陣列。

[!code-vb[iterate-for-each-next](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate-for-each-next.vb)]

## <a name="array-size"></a>陣列大小

陣列大小為其所有維度長度之乘積。 它代表目前包含於陣列中的項目總數。  例如，下列範例會宣告具有四個元素，每個維度中的 2 維度陣列。 如範例輸出所示，陣列的大小為 16 (或 (3 + 1) * (3 + 1)。

[!code-vb[array-size](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-size.vb)]

> [!NOTE]
> 本討論中陣列的大小不適用於不規則陣列。 如需不規則的陣列和決定不規則陣列的大小，請參閱 <<c0> [ 不規則陣列](#jagged-arrays)一節。

您可以使用 <xref:System.Array.Length%2A?displayProperty=nameWithType> 屬性來尋找陣列的大小。 您可以使用來尋找多維陣列中的每個維度的長度<xref:System.Array.GetLength%2A?displayProperty=nameWithType>方法。

指派新的陣列物件，或使用，您可以調整大小的陣列變數[`ReDim`陳述式](../../../language-reference/statements/redim-statement.md)陳述式。 下列範例會使用`ReDim`陳述式來變更到 51 個元素陣列的 100 個元素的陣列。

[!code-vb[resize-an-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-size2.vb)]

處理陣列大小時，請注意幾點︰

|||
|---|---|
|維度長度|每個維度的索引是以 0 為基礎，這表示其範圍從 0 到它的上限。 因此，指定維度的長度是一必須大於該維度的宣告上限。|
|長度限制|陣列的每個維度的長度是限制的最大值為`Integer`資料類型，這是<xref:System.Int32.MaxValue?displayProperty=nameWithType>或 (2 ^31)-1。 然而，陣列之總大小也同時受限於系統可用的記憶體。 如果您嘗試將初始化陣列超過可用記憶體數量、 執行階段會擲回<xref:System.OutOfMemoryException>。|
|大小及項目大小|陣列大小與其項目的資料類型無關。 大小一律是指項目，不，它們會消耗記憶體中的位元組數字總數。|
|記憶體消耗量|對陣列在記憶體中的儲存方式做任何假設都是不安全的。 儲存體會因不同資料寬度的平台而有差異，所以相同陣列於 64 位元系統上所佔記憶體將較 32 位元系統來的多。 當您初始化陣列時，隨著系統組態不同，通用語言執行平台 (CLR) 會指派儲存體盡可能將項目存放在一起，或是根據實體硬體界限全部加以調整。 同時，陣列需要耗用儲存體以供其控制資訊使用，此消耗量會隨著維度增加而增加。|

## <a name="the-array-type"></a>陣列類型

每個陣列有不同於其項目的資料類型的資料類型。 沒有任何單一的資料類型適用於所有的陣列。 陣列的類型反而是由陣列的維度數目，或稱為 *「順位」*(rank) 以及陣列項目的資料類型所決定。 兩個陣列變數屬於相同的資料類型具有相同的陣序規範，其項目包含相同的資料類型。 陣列的維度的長度不會影響陣列資料型別。

每個陣列都繼承自 <xref:System.Array?displayProperty=nameWithType> 類別，而您可以將變數宣告為類型 `Array`，但不能建立類型為 `Array` 的陣列。 比方說，雖然下列程式碼會宣告`arr`類型的變數`Array`，並呼叫<xref:System.Array.CreateInstance%2A?displayProperty=nameWithType>方法具現化的陣列，陣列的型別證實是 Object []。

[!code-vb[array-class](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-class.vb)]

此外，[ReDim 陳述式](../../../language-reference/statements/redim-statement.md)無法在宣告為 `Array` 型別的變數上運作。 基於這些理由，以及型別安全，建議您最好以宣告為特定類型的每個陣列。

有幾個方法可以找出陣列或其項目的資料類型。

- 您可以呼叫<xref:System.Object.GetType%2A>方法來取得變數<xref:System.Type>物件，表示變數的執行階段型別。 <xref:System.Type> 物件在其屬性和方法中保留了大量的資訊。
- 您可以將變數傳遞給<xref:Microsoft.VisualBasic.Information.TypeName%2A>函式可取得`String`的執行階段類型名稱。

下列範例會呼叫二者`GetType`方法和`TypeName`函式來判斷陣列的類型。 陣列型別是`Byte(,)`。 請注意，<xref:System.Type.BaseType%2A?displayProperty=nameWithType>屬性也會指出的位元組陣列的基底類型是<xref:System.Array>類別。

[!code-vb[array-type](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-type.vb)]

## <a name="arrays-as-return-values-and-parameters"></a>做為傳回值和參數陣列

若要從 `Function` 程序傳回陣列，請將陣列資料型別和維度數目指定為 [Function 陳述式](../../../language-reference/statements/function-statement.md)的傳回型別。 在該函式內，使用相同的資料類型和維度數目來宣告區域陣列變數。 在 [Return 陳述式](../../../language-reference/statements/return-statement.md)中，包含沒有括弧的區域陣列變數。

若要將陣列指定為 `Sub` 程序或 `Function` 程序的參數，請為參數定義所指定的資料類型和維度數目。 在程序的呼叫，傳遞相同的資料類型和維度數目的陣列變數。

在下列範例中，`GetNumbers`函式會傳回`Integer()`，類型的一維陣列`Integer`。 `ShowNumbers` 程序接受 `Integer()` 引數。

[!code-vb[return-value-and-params](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/return-values-and-params.vb)]

在下列範例中，`GetNumbersMultiDim`函式會傳回`Integer(,)`，類型的二維陣列`Integer`。  `ShowNumbersMultiDim` 程序接受 `Integer(,)` 引數。

[!code-vb[multidimensional-return-value](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/return-values-and-params-2d.vb)]

## <a name="jagged-arrays"></a>不規則陣列

有時候應用程式中的資料結構會是非矩形的二維陣列。 例如，您可能會使用陣列來儲存資料之每月每一天的高溫。 陣列的第一個維度來表示月份，但第二個維度代表天數，並在一個月的日數並不平均。 A*不規則的陣列*，這也稱為*陣列的陣列*，專為這類案例。 不規則的陣列是其項目也是陣列的陣列。 不規則陣列和不規則陣列中的每個項目都可以有一或多個維度。

下列範例會使用一個月份陣列，其中每個項目是陣列的天數。 由於不同月份的天數內的不同數字，此範例會使用不規則的陣列。  此範例示範如何建立不規則的陣列，將值指派給它，並擷取並顯示其值。

[!code-vb[jagged-arrays](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged.vb)]

前一個範例會將值指派不規則陣列元素的元素為基礎來使用`For...Next`迴圈。 您也可以使用巢狀的陣列常值，來指派的不規則陣列元素的值。 不過，嘗試使用巢狀陣列常值 (例如`Dim valuesjagged = {{1, 2}, {2, 3, 4}}`) 會產生編譯器錯誤[BC30568](../../../,,/../misc/bc30568.md)。 若要更正錯誤，請先括號括住內部陣列常值的物件。 括號會強制要評估陣列常值運算式，產生的值搭配外部陣列常值，如下列範例所示。

[!code-vb[jagged-array-initialization](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged-assign.vb)]

不規則的陣列是一維陣列，其項目包含的陣列。 因此，<xref:System.Array.Length%2A?displayProperty=nameWithType>屬性和`Array.GetLength(0)`方法傳回一維陣列中的項目數並`Array.GetLength(1)`就會擲回<xref:System.IndexOutOfRangeException>因為不規則的陣列不是多維度。 您擷取的每個子陣列的值來判斷每個子陣列中的項目數<xref:System.Array.Length%2A?displayProperty=nameWithType>屬性。 下列範例說明如何判斷不規則陣列中的項目數。

[!code-vb[jagged-array-size](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged-length.vb)]

## <a name="zero-length-arrays"></a>長度為零的陣列

Visual Basic 會區別未初始化的陣列 (其值是的陣列`Nothing`) 和*長度為零的陣列*或空陣列 （陣列沒有任何項目。）未初始化的陣列是不被建立維度，或已指派給它的任何值。 例如：

```vb
Dim arr() As String
```

長度為零的陣列宣告具有-1 的維度。 例如: 

```vb
Dim arrZ(-1) As String
```

在下列情況中，您可能需要建立長度為零的陣列：

- 不必擔心<xref:System.NullReferenceException>例外狀況，您的程式碼必須存取的成員<xref:System.Array>類別，例如<xref:System.Array.Length%2A>或是<xref:System.Array.Rank%2A>，或呼叫 Visual Basic 函式，例如<xref:Microsoft.VisualBasic.Information.UBound%2A>。

- 您想要保留您的程式碼的簡單，不需要檢查`Nothing`視為特殊案例。

- 程式碼會與應用程式開發介面互動，這個介面會要求您傳遞長度為零的陣列給一個或多個程序，或從一個或多個程序傳回長度為零的陣列。

## <a name="splitting-an-array"></a>分割陣列

在某些情況下，您可能需要分成多個陣列中的單一陣列。 這牽涉到的點或點陣列需要分割，是用來識別，然後吐陣列痰成兩個或多個不同的陣列。

> [!NOTE]
> 本節將不會討論將單一字串分割成字串陣列，根據某些分隔符號。 如需將字串分割資訊，請參閱<xref:System.String.Split%2A?displayProperty=nameWithType>方法。

最常用的準則來分割陣列如下：

- 陣列中的項目數。 例如，您可能要分成大約相等的部分數目超過指定的項目數的陣列。 基於此目的，您可以使用任一方法所傳回的值<xref:System.Array.Length%2A?displayProperty=nameWithType>或<xref:System.Array.GetLength%2A?displayProperty=nameWithType>方法。

- 做為分隔符號，指出應該將分割陣列項目的值。 您可以搜尋特定的值，藉由呼叫<xref:System.Array.FindIndex%2A?displayProperty=nameWithType>和<xref:System.Array.FindLastIndex%2A?displayProperty=nameWithType>方法。

一旦您判定應處分割陣列的索引，您可以藉由呼叫，然後建立個別的陣列<xref:System.Array.Copy%2A?displayProperty=nameWithType>方法。

下列範例會將陣列分成兩個陣列的大小大約相同。 （如果奇數的陣列項目總數，第一個陣列有一個元素，第二個）。

[!code-vb[splitting-an-array-by-length](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/split1.vb)]

下列範例會將字串陣列分成兩個陣列，根據其值為"zzz"，以做為陣列分隔符號的項目出現與否。 新的陣列不包含包含分隔符號的項目。

[!code-vb[splitting-an-array-by-delimiter](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/split2.vb)]

## <a name="joining-arrays"></a>加入陣列

您也可以結合數目的陣列合併為單一較大的陣列。 若要這樣做，您也使用<xref:System.Array.Copy%2A?displayProperty=nameWithType>方法。

> [!NOTE]
> 本節將不會討論聯結成單一字串的字串陣列。 如需有關聯結的字串陣列，請參閱<xref:System.String.Join%2A?displayProperty=nameWithType>方法。

之前每個陣列項目複製到新的陣列，您必須先確定，您就已初始化陣列，使它足夠大以容納新的陣列。 您可以使用下列其中一種做法：

- 使用[ `ReDim Preserve` ](../../../language-reference/statements/redim-statement.md)陳述式，以動態方式加入新項目之前展開的陣列。 這是最簡單的技巧，但它可能會導致效能降低，過多的記憶體耗用量當您複製大型陣列。
- 計算新的大型陣列所需的項目總數，然後將每個來源陣列的項目加入至它。

下列範例會使用第二種方法，將四個的陣列，具有十個項目新增至單一的陣列。

[!code-vb[joining-an-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/join.vb)]

在此情況下，來源陣列是所有小型的因為我們也會動態地可以展開陣列，因為我們將新增它的每個新的陣列項目。 下列範例正是如此。

[!code-vb[joining-an-array-dynamically](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/join2.vb)]

## <a name="collections-as-an-alternative-to-arrays"></a>使用集合取代陣列

陣列是最適用於建立和處理固定數目的強類型物件。 集合會提供較具彈性的方式來使用物件群組。 不同於陣列，而這需要您明確變更陣列的大小[`ReDim`陳述式](../../../language-reference/statements/redim-statement.md)，集合動態增長或縮減為應用程式變更的需要。

當您使用`ReDim`重訂維度陣列，Visual Basic 建立新的陣列和釋放前一個。 這將佔用執行時間。 因此，如果您正在使用經常變更，或您的項目數目無法預測您需要的項目數目上限，您會使用集合通常取得較佳的效能。

對於某些集合，您可以將鍵值指派給您放入集合的任何物件，讓您可以藉由使用鍵值快速擷取物件。

如果集合包含只有一個資料類型的項目，則可使用 <xref:System.Collections.Generic?displayProperty=nameWithType> 命名空間內的其中一個類別。 泛型集合會強制類型安全，如此就不會加入其他資料類型。

如需集合的詳細資訊，請參閱[集合](../../concepts/collections.md)。

## <a name="related-topics"></a>相關主題

|詞彙|定義|
|----------|----------------|
|[Array Dimensions in Visual Basic](../../language-features/arrays/array-dimensions.md)|說明陣列中的順位和維度。|
|[如何：初始化陣列變數在 Visual Basic](../../language-features/arrays/how-to-initialize-an-array-variable.md)|描述如何在陣列中填入初始值。|
|[如何：在 Visual Basic 中排序陣列](../../language-features/arrays/how-to-sort-an-array.md)|示範如何依字母順序排列陣列中的項目。|
|[如何：指派一個陣列至另一個陣列](../../language-features/arrays/how-to-assign-one-array-to-another-array.md)|描述將陣列指派給另一個陣列變數的規則和步驟。|
|[陣列的疑難排解](../../language-features/arrays/troubleshooting-arrays.md)|討論在使用陣列時會引發的一些常見問題。|

## <a name="see-also"></a>另請參閱

- <xref:System.Array?displayProperty=nameWithType>
- [Dim 陳述式](../../../language-reference/statements/dim-statement.md)
- [ReDim 陳述式](../../../language-reference/statements/redim-statement.md)
