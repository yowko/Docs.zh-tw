---
title: 陣列
ms.date: 12/06/2017
f1_keywords:
- vb.Array
helpviewer_keywords:
- arrays [Visual Basic]
- Visual Basic, arrays
ms.assetid: dbf29737-b589-4443-bee6-a27588d9c67e
ms.openlocfilehash: 5093f28f05c5b72294dce9a4e69723acafb31a9f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413088"
---
# <a name="arrays-in-visual-basic"></a>Visual Basic 中的陣列

陣列是一組稱為*元素*的值，它們在邏輯上彼此相關。 例如，陣列可能是由文法學校中每一年級的學生人數所組成;陣列的每個元素都是單一等級的學生數目。 同樣地，陣列也可能包含學生的課程等級;陣列的每個元素都是單一等級。

您可以個別的變數來儲存每個資料項目目。 例如，如果我們的應用程式分析學生成績，我們可以針對每個學生的成績使用個別的變數，例如 `englishGrade1` 、等等 `englishGrade2` 。此方法有三個主要限制：

- 我們必須在設計階段知道我們必須處理多少成績等級。
- 處理大量的成績很快會變得很困難。 這會讓應用程式更容易遇到嚴重的錯誤。
- 難以維護。 我們新增的每個新等級都需要修改、重新編譯及重新部署應用程式。

藉由使用陣列，您可以透過相同的名稱來參考這些相關的值，並使用稱為「*索引*」或「注*標*」的數位，根據其在陣列中的位置來識別個別元素。 陣列的索引範圍從0到小於陣列中的元素總數。 當您使用 Visual Basic 語法定義陣列的大小時，您可以指定其最高的索引，而不是陣列中的元素總數。 您可以使用陣列做為一個單位，而且能夠逐一查看其專案，讓您不需要知道它在設計階段所包含的確切元素數目。

開始說明前，先提供一些簡單的範例：

```vb
' Declare a single-dimension array of 5 numbers.
Dim numbers(4) As Integer

' Declare a single-dimension array and set its 4 values.
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

## <a name="array-elements-in-a-simple-array"></a>簡單陣列中的陣列元素

讓我們建立名為的陣列 `students` ，以在文法學校中儲存每一年級的學生人數。 項目的索引範圍從 0 到 6。 使用此陣列比宣告七個變數簡單。

下圖顯示 `students` 陣列。 對於陣列的每一項目︰

- 項目的索引代表年級 (索引 0 代表幼稚園)。

- 項目包含的值代表該年級的學生數目。

![顯示學生數目陣列的圖表](./media/index/students-array-elements.gif)

下列範例包含建立和使用陣列的 Visual Basic 程式碼：

[!code-vb[simple-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/simple-array.vb)]

此範例會執行三件事：

- 它會宣告 `students` 具有七個元素的陣列。 陣列宣告 `6` 中的數位表示陣列中的最後一個索引，它小於陣列中的元素數目。
- 它會將值指派給陣列中的每個元素。 陣列元素的存取方式是使用陣列名稱，並在括弧中包含個別元素的索引。
- 它會列出陣列的每個值。 此範例會使用 [`For`](../../../language-reference/statements/for-next-statement.md) 語句，依索引編號存取陣列的每個元素。

`students`前述範例中的陣列是一維陣列，因為它使用一個索引。 使用一個以上索引或注標的陣列稱為多*維度*。 如需詳細資訊，請參閱本文的其餘部分和[Visual Basic 中的陣列維度](array-dimensions.md)。

## <a name="creating-an-array"></a>建立陣列

您可以用數種方式定義陣列的大小：

- 您可以在宣告陣列時指定大小：

  [!code-vb[creating1](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#1)]

- 建立陣列時，您可以使用 `New` 子句來提供它的大小：

  [!code-vb[creating2](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#2)]

如果您有現有的陣列，您可以使用語句重新定義其大小 [`ReDim`](../../../language-reference/statements/redim-statement.md) 。 您可以指定 `ReDim` 語句保留陣列中的值，也可以指定它建立空陣列。 下列範例顯示 `ReDim` 陳述式的不同使用方法，以修改現有陣列的大小。

[!code-vb[redimensioning](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#3)]

如需詳細資訊，請參閱[ReDim 語句](../../../language-reference/statements/redim-statement.md)。

## <a name="storing-values-in-an-array"></a>將值儲存在陣列中

您可以使用類型為 `Integer`的索引來存取陣列中的每一個位置。 使用括弧內的陣列索引即可參照各陣列的位置，從而儲存並擷取陣列中的值。 多維陣列的索引會以逗號（，）分隔。 各個陣列維度皆需一個索引。

下列範例顯示一些語句，可儲存和抓取陣列中的值。

[!code-vb[store-and-retrieve](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/store-and-retrieve.vb)]

## <a name="populating-an-array-with-array-literals"></a>以陣列常值填入陣列

藉由使用陣列常值，您可以在建立陣列時，于其中填入一組初始值。 陣列常值由大括弧 (`{}`) 括住的逗點分隔值清單構成。

當您使用陣列常值來建立陣列時，可以提供陣列類型，或者使用類型推斷來判別陣列類型。 下列範例會顯示這兩個選項。

[!code-vb[create-with-literals](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#4)]

當您使用型別推斷時，陣列的型別是由常值清單中的*主要型*別所決定。 主要類型是陣列中所有其他類型都可以擴展的類型。 如果無法決定此唯一類型，則主類型將成為陣列中其他類型皆可縮小而成的唯一類型。 如果這些類型皆無法決定，則主類型為 `Object`。 例如，如果提供給陣列常值的值清單含有類型值 `Integer`、 `Long`和 `Double`，則結果陣列的類型是 `Double`。 因為 `Integer` 和 `Long` 只會擴展為 `Double` ，所以 `Double` 是主要類型。 如需詳細資訊，請參閱 [Widening and Narrowing Conversions](../data-types/widening-and-narrowing-conversions.md)。

> [!NOTE]
> 您只能針對在型別成員中定義為區域變數的陣列使用型別推斷。 如果沒有明確的型別定義，在類別層級使用陣列常值定義的陣列就屬於型別 `Object[]` 。 如需詳細資訊，請參閱[區欄位型別推斷](../variables/local-type-inference.md)。

請注意，上述範例會將定義 `values` 為類型的陣列， `Double` 即使所有陣列常值都是類型也是一樣 `Integer` 。 您可以建立此陣列，因為陣列常值中的值可以擴展成 `Double` 值。

您也可以使用*嵌套陣列常*值來建立及填入多維陣列。 嵌套陣列常值必須具有與產生的陣列一致的維度數目。 下列範例會使用嵌套陣列常值，建立整數的二維陣列。

[!code-vb[nested-array-literals](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#5)]

使用嵌套陣列常值來建立和填入陣列時，如果嵌套陣列常值中的專案數目不相符，就會發生錯誤。 如果您明確宣告陣列變數與陣列常值的維度數目不同，也會發生錯誤。

就像一維陣列一樣，您可以在使用嵌套陣列常值來建立多維陣列時，依賴型別推斷。 針對所有的嵌套層級，推斷的類型是所有陣列常值中所有值的主要類型。 下列範例 `Double[,]` 會從類型為和的值建立類型為的二維陣列 `Integer` `Double` 。

[!code-vb[nested-type-inference](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#6)]

如需其他範例，請參閱[如何：在 Visual Basic 中初始化陣列變數](how-to-initialize-an-array-variable.md)。

## <a name="iterating-through-an-array"></a>逐一查看陣列

當您逐一查看陣列時，會將陣列中的每個元素從最低索引存取至最高，或從最高到最低。 一般來說，請使用[For .。。下一個語句](../../../language-reference/statements/for-next-statement.md)或[For Each .。。下一個語句](../../../language-reference/statements/for-each-next-statement.md)，以逐一查看陣列的元素。 當您不知道陣列的上限時，可以呼叫 <xref:System.Array.GetUpperBound%2A?displayProperty=nameWithType> 方法來取得索引的最大值。 雖然最小的索引值幾乎一律為0，但是您可以呼叫 <xref:System.Array.GetLowerBound%2A?displayProperty=nameWithType> 方法來取得索引的最低值。

下列範例會使用語句，逐一查看一維陣列 [`For...Next`](../../../language-reference/statements/for-next-statement.md) 。

[!code-vb[iterate-one-dimensional-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate1d.vb)]

下列範例會使用語句來逐一查看多維陣列 [`For...Next`](../../../language-reference/statements/for-next-statement.md) 。 <xref:System.Array.GetUpperBound%2A> 方法具有可指定維度的參數。 `GetUpperBound(0)`傳回第一個維度的最高索引，並傳回 `GetUpperBound(1)` 第二個維度的最高索引。

[!code-vb[iterate-two-dimensional-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate2d.vb)]

下列範例會使用[For Each .。。下一個語句](../../../language-reference/statements/for-each-next-statement.md)，逐一查看一維陣列和二維陣列。

[!code-vb[iterate-for-each-next](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate-for-each-next.vb)]

## <a name="array-size"></a>陣列大小

陣列大小為其所有維度長度之乘積。 它代表目前包含於陣列中的項目總數。  例如，下列範例會宣告一個二維陣列，其中包含每個維度中的四個元素。 如範例的輸出所示，陣列的大小為16（或（3 + 1） * （3 + 1）。

[!code-vb[array-size](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-size.vb)]

> [!NOTE]
> 陣列大小的討論並不適用于不規則陣列。 如需不規則陣列和判斷不規則陣列大小的詳細資訊，請參閱[不規則陣列](#jagged-arrays)一節。

您可以使用 <xref:System.Array.Length%2A?displayProperty=nameWithType> 屬性來尋找陣列的大小。 您可以使用方法來尋找多維陣列的每個維度長度 <xref:System.Array.GetLength%2A?displayProperty=nameWithType> 。

您可以藉由指派新的陣列物件或使用[ `ReDim` 語句](../../../language-reference/statements/redim-statement.md)語句，來調整陣列變數的大小。 下列範例會使用 `ReDim` 語句，將100元素陣列變更為51元素陣列。

[!code-vb[resize-an-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-size2.vb)]

處理陣列大小時，請注意幾點︰

|||
|---|---|
|維度長度|每個維度的索引都是以0為基礎，這表示它的範圍是從0到其上限。 因此，指定維度的長度會大於該維度宣告的上限。|
|長度限制|陣列的每個維度長度限制為資料類型的最大值 `Integer` ，也就是 <xref:System.Int32.MaxValue?displayProperty=nameWithType> （2 ^ 31）-1。 然而，陣列之總大小也同時受限於系統可用的記憶體。 如果您嘗試初始化超過可用記憶體數量的陣列，執行時間會擲回 <xref:System.OutOfMemoryException> 。|
|大小及項目大小|陣列大小與其項目的資料類型無關。 大小一律代表元素的總數，而不是它們在記憶體中耗用的位元組數目。|
|記憶體消耗量|對陣列在記憶體中的儲存方式做任何假設都是不安全的。 儲存體會因不同資料寬度的平台而有差異，所以相同陣列於 64 位元系統上所佔記憶體將較 32 位元系統來的多。 當您初始化陣列時，隨著系統組態不同，通用語言執行平台 (CLR) 會指派儲存體盡可能將項目存放在一起，或是根據實體硬體界限全部加以調整。 同時，陣列需要耗用儲存體以供其控制資訊使用，此消耗量會隨著維度增加而增加。|

## <a name="the-array-type"></a>陣列類型

每個陣列都有一種資料類型，不同于其元素的資料類型。 沒有任何單一的資料類型適用於所有的陣列。 陣列的類型反而是由陣列的維度數目，或稱為 *「順位」*(rank) 以及陣列項目的資料類型所決定。 只有當兩個數組變數具有相同的次序，而且其元素具有相同的資料類型時，才會有相同的資料類型。 陣列維度的長度不會影響陣列資料類型。

每個陣列都繼承自 <xref:System.Array?displayProperty=nameWithType> 類別，而您可以將變數宣告為類型 `Array`，但不能建立類型為 `Array` 的陣列。 例如，雖然下列程式碼 `arr` 會將變數宣告為型別， `Array` 並呼叫 <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> 方法來具現化陣列，但陣列的型別證明為 Object []。

[!code-vb[array-class](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-class.vb)]

此外，[ReDim 陳述式](../../../language-reference/statements/redim-statement.md)無法在宣告為 `Array` 型別的變數上運作。 基於這些理由，和型別安全，建議您將每個陣列宣告為特定類型。

有幾個方法可以找出陣列或其項目的資料類型。

- 您可以 <xref:System.Object.GetType%2A> 在變數上呼叫方法，以取得 <xref:System.Type> 代表變數之執行時間類型的物件。 <xref:System.Type> 物件在其屬性和方法中保留了大量的資訊。
- 您可以將變數傳遞給函 <xref:Microsoft.VisualBasic.Information.TypeName%2A> 式，以取得 `String` 具有執行時間類型名稱的。

下列範例會呼叫 `GetType` 方法和函 `TypeName` 式，以判斷陣列的類型。 陣列類型為 `Byte(,)` 。 請注意， <xref:System.Type.BaseType%2A?displayProperty=nameWithType> 屬性也會指出位元組陣列的基底類型是 <xref:System.Array> 類別。

[!code-vb[array-type](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-type.vb)]

## <a name="arrays-as-return-values-and-parameters"></a>做為傳回值和參數的陣列

若要從 `Function` 程序傳回陣列，請將陣列資料型別和維度數目指定為 [Function 陳述式](../../../language-reference/statements/function-statement.md)的傳回型別。 在該函式內，使用相同的資料類型和維度數目來宣告區域陣列變數。 在 [Return 陳述式](../../../language-reference/statements/return-statement.md)中，包含沒有括弧的區域陣列變數。

若要將陣列指定為 `Sub` 程序或 `Function` 程序的參數，請為參數定義所指定的資料類型和維度數目。 在程式的呼叫中，傳遞具有相同資料類型和維度數目的陣列變數。

在下列範例中，函式會傳回一個型別為 `GetNumbers` `Integer()` 的一維陣列 `Integer` 。 `ShowNumbers` 程序接受 `Integer()` 引數。

[!code-vb[return-value-and-params](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/return-values-and-params.vb)]

在下列範例中，函式會傳回型別為的 `GetNumbersMultiDim` `Integer(,)` 二維陣列 `Integer` 。  `ShowNumbersMultiDim` 程序接受 `Integer(,)` 引數。

[!code-vb[multidimensional-return-value](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/return-values-and-params-2d.vb)]

## <a name="jagged-arrays"></a>不規則陣列

有時候應用程式中的資料結構會是非矩形的二維陣列。 例如，您可以使用陣列來儲存有關當月每一天高溫度的資料。 陣列的第一個維度代表月份，但第二個維度代表天數，而月份中的天數則不是統一的。 *不規則陣列*（也稱為陣列*陣列*）是針對這類案例所設計。 不規則陣列是其元素也是陣列的陣列。 不規則陣列和不規則陣列中的每個項目都可以有一或多個維度。

下列範例使用月份陣列，其中的每個元素都是天數陣列。 此範例會使用不規則陣列，因為不同的月份有不同的日數。  此範例示範如何建立不規則陣列、為其指派值，以及取得和顯示其值。

[!code-vb[jagged-arrays](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged.vb)]

先前的範例會使用迴圈，將值指派給每個元素的不規則陣列 `For...Next` 。 您也可以使用嵌套陣列常值，將值指派給不規則陣列的元素。 不過，嘗試使用嵌套陣列常值（例如 `Dim valuesjagged = {{1, 2}, {2, 3, 4}}` ）會產生編譯器錯誤[BC30568](../../../misc/bc30568.md)。 若要更正錯誤，請將內部陣列常值括在括弧中。 括弧會強制評估陣列常值運算式，而產生的值會用於外部陣列常值，如下列範例所示。

[!code-vb[jagged-array-initialization](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged-assign.vb)]

不規則陣列是一維陣列，其元素包含陣列。 因此， <xref:System.Array.Length%2A?displayProperty=nameWithType> 屬性和 `Array.GetLength(0)` 方法會傳回一維陣列中的專案數，並擲回， `Array.GetLength(1)` <xref:System.IndexOutOfRangeException> 因為不規則陣列不是多維的。 您可以藉由抓取每個子陣列的屬性值，來判斷每個子陣列中的元素數目 <xref:System.Array.Length%2A?displayProperty=nameWithType> 。 下列範例說明如何判斷不規則陣列中的元素數目。

[!code-vb[jagged-array-size](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged-length.vb)]

## <a name="zero-length-arrays"></a>長度為零的陣列

Visual Basic 區分未初始化的陣列（值為的陣列 `Nothing` ）和*長度為零的陣列*或空陣列（沒有元素的陣列）。未初始化的陣列是指尚未進行維度或指派任何值的陣列。 例如：

```vb
Dim arr() As String
```

以-1 的維度宣告長度為零的陣列。 例如：

```vb
Dim arrZ(-1) As String
```

在下列情況中，您可能需要建立長度為零的陣列：

- 如果沒有風險 <xref:System.NullReferenceException> ，您的程式碼必須存取類別的成員（ <xref:System.Array> 例如 <xref:System.Array.Length%2A> 或 <xref:System.Array.Rank%2A> ），或呼叫 Visual Basic <xref:Microsoft.VisualBasic.Information.UBound%2A> 函式，例如。

- 您想要讓程式碼保持簡單，不需要檢查是否為 `Nothing` 特殊案例。

- 程式碼會與應用程式開發介面互動，這個介面會要求您傳遞長度為零的陣列給一個或多個程序，或從一個或多個程序傳回長度為零的陣列。

## <a name="splitting-an-array"></a>分割陣列

在某些情況下，您可能需要將單一陣列分割成多個陣列。 這包括識別要分割之陣列的點或點，然後將陣列分隔為兩個或多個不同的陣列。

> [!NOTE]
> 本節不會討論以某個分隔符號為基礎，將單一字串分割成字串陣列。 如需分割字串的詳細資訊，請參閱 <xref:System.String.Split%2A?displayProperty=nameWithType> 方法。

分割陣列最常見的準則包括：

- 陣列中的項目數。 例如，您可能會想要將超過指定專案數的陣列分割成幾個大約相等的部分。 基於此目的，您可以使用或方法所傳回的值 <xref:System.Array.Length%2A?displayProperty=nameWithType> <xref:System.Array.GetLength%2A?displayProperty=nameWithType> 。

- 元素的值，做為表示應分割陣列位置的分隔符號。 您可以藉由呼叫和方法來搜尋特定的值 <xref:System.Array.FindIndex%2A?displayProperty=nameWithType> <xref:System.Array.FindLastIndex%2A?displayProperty=nameWithType> 。

一旦決定了陣列應分割的索引或索引之後，您就可以藉由呼叫方法來建立個別陣列 <xref:System.Array.Copy%2A?displayProperty=nameWithType> 。

下列範例會將陣列分割成大約大小相等的兩個數組。 （如果陣列元素的總數是奇數，則第一個陣列具有比第二個更多的元素）。

[!code-vb[splitting-an-array-by-length](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/split1.vb)]

下列範例會將字串陣列分割成兩個數組，其值為 "zzz" 的元素是否存在，做為陣列分隔符號。 新的陣列不包含包含分隔符號的元素。

[!code-vb[splitting-an-array-by-delimiter](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/split2.vb)]

## <a name="joining-arrays"></a>聯結陣列

您也可以將一些陣列結合成一個較大的陣列。 若要這麼做，您也可以使用 <xref:System.Array.Copy%2A?displayProperty=nameWithType> 方法。

> [!NOTE]
> 本節不會討論將字串陣列聯結至單一字串。 如需聯結字串陣列的詳細資訊，請參閱 <xref:System.String.Join%2A?displayProperty=nameWithType> 方法。

將每個陣列的元素複製到新陣列之前，您必須先確定您已初始化陣列，使其夠大，足以容納新的陣列。 您可以使用下列其中一種作法：

- 您 [`ReDim Preserve`](../../../language-reference/statements/redim-statement.md) 可以使用語句，在將新專案加入至陣列之前，以動態方式展開陣列。 這是最簡單的技巧，但它可能會導致效能降低，而且當您複製大型陣列時，記憶體耗用量也會過高。
- 計算新的大型陣列所需的專案總數，然後在其中新增每個來源陣列的元素。

下列範例會使用第二個方法，將四個具有10個元素的陣列新增至單一陣列。

[!code-vb[joining-an-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/join.vb)]

因為在此情況下，來源陣列全都很小，所以我們也可以動態地展開陣列，因為我們會將每個新陣列的元素新增至其中。 下列範例正是如此。

[!code-vb[joining-an-array-dynamically](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/join2.vb)]

## <a name="collections-as-an-alternative-to-arrays"></a>集合作為陣列的替代方案

陣列是最適用於建立和處理固定數目的強類型物件。 集合會提供較具彈性的方式來使用物件群組。 不同于陣列，這需要您使用[ `ReDim` 語句](../../../language-reference/statements/redim-statement.md)來明確變更陣列的大小，集合會隨著應用程式變更的需求而動態成長和縮減。

當您使用 `ReDim` 來重設陣列的維度時，Visual Basic 會建立新的陣列，並釋放上一個陣列。 這將佔用執行時間。 因此，如果您處理的專案數經常變更，或您無法預測所需的最大專案數，則通常會使用集合取得較佳的效能。

對於某些集合，您可以將索引鍵值指派給您放入集合的任何物件，讓您可以藉由使用索引鍵快速擷取物件。

如果集合包含只有一個資料類型的項目，則可使用 <xref:System.Collections.Generic?displayProperty=nameWithType> 命名空間內的其中一個類別。 泛型集合會強制類型安全，如此就不會加入其他資料類型。

如需集合的詳細資訊，請參閱[集合](../../concepts/collections.md)。

## <a name="related-topics"></a>相關主題

|詞彙|定義|
|----------|----------------|
|[Array Dimensions in Visual Basic](array-dimensions.md)|說明陣列中的順位和維度。|
|[如何：在 Visual Basic 中初始化陣列變數](how-to-initialize-an-array-variable.md)|描述如何在陣列中填入初始值。|
|[如何：在 Visual Basic 中排序陣列](how-to-sort-an-array.md)|示範如何依字母順序排列陣列中的項目。|
|[如何：指派一個陣列至另一個陣列](how-to-assign-one-array-to-another-array.md)|描述將陣列指派給另一個陣列變數的規則和步驟。|
|[針對陣列進行疑難排解](troubleshooting-arrays.md)|討論在使用陣列時會引發的一些常見問題。|

## <a name="see-also"></a>另請參閱

- <xref:System.Array?displayProperty=nameWithType>
- [Dim 陳述式](../../../language-reference/statements/dim-statement.md)
- [ReDim 陳述式](../../../language-reference/statements/redim-statement.md)
