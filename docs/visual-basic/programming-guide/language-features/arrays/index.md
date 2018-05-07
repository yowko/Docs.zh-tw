---
title: Visual Basic 中的陣列
ms.date: 12/06/2017
f1_keywords:
- vb.Array
helpviewer_keywords:
- arrays [Visual Basic]
- Visual Basic, arrays
ms.assetid: dbf29737-b589-4443-bee6-a27588d9c67e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3b6c1db0131f2a150dc1b00dd5e6dafc3a418f05
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="arrays-in-visual-basic"></a>Visual Basic 中的陣列
陣列是一組值，會稱為*元素*，邏輯上彼此相關的。 例如，陣列可能包含文法學校中; 每一年級學生數目陣列的每個項目是單一年級的學生數目。 同樣地，陣列可能包含一位學生成績類別;陣列的每個項目是單一的等級。    

它是可能的個別變數來儲存每個我們資料的項目。 例如，如果我們的應用程式會分析學生成績，我們可以使用個別的變數的每一位學生成績，例如`englishGrade1`，`englishGrade2`等等。這個方法有三個主要的限制：
- 我們必須在執行階段知道我們必須處理完全多少等級。
- 快速處理大量的等級會變得不便。 這反而能夠讓應用程式更有可能有嚴重的錯誤。
- 它是難以維護。 我們將加入每個新等級需要，修改、 重新編譯，並重新部署應用程式。  
 
 藉由使用陣列，您可以參考相同的名稱，這些相關的值，並使用數字，會呼叫*索引*或*註標*來識別個別的項目，根據其在陣列中的位置。 其中一個陣列中的項目總數大於或等於 0 的陣列範圍內的索引。 當您使用 Visual Basic 語法來定義陣列的大小時，您會指定其最高的索引，不在陣列中的項目總數。 您可以使用陣列做為一個單位，而且能夠逐一查看其項目可讓您不必知道完全多少項目包含在設計階段。
  
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
  
 ## <a name="in-this-article"></a>本文內容
  
- [簡單陣列中的陣列項目](#array-elements-in-a-simple-array)  
  
- [建立陣列](#creating-an-array)  
  
- [在陣列中儲存值](#storing-values-in-an-array)  
  
- [填入陣列常值的陣列](#populating-an-array-with-array-literals)  
  
- [逐一查看陣列](#iterating-through-an-array)  
  
- [陣列大小](#BKMK_ArraySize)  

- [陣列類型](#the-array-type)  
  
- [以陣列做為傳回值和參數](#arrays-as-return-values-and-parameters)  
- [不規則的陣列](#jagged-arrays)  
  
- [零長度陣列](#zero-length-arrays)  

- [分割陣列](#splitting-an-array)
  
- [使用集合取代陣列](#collections-as-an-alternative-to-arrays)  
  
##  <a name="array-elements-in-a-simple-array"></a>簡單陣列中的陣列項目  

讓我們來建立名為陣列`students`儲存文法學校中每一年級的學生總數一樣。 項目的索引範圍從 0 到 6。 使用此陣列是簡單較宣告七個變數。

下圖顯示`students`陣列。 對於陣列的每一項目︰  
  
-   項目的索引代表年級 (索引 0 代表幼稚園)。
  
-   項目包含的值代表該年級的學生數目。
  
 ![顯示學生人數的陣列圖](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexampleschool.gif "ArrayExampleSchool")  
"students" 陣列的項目  
 
下列範例包含建立及使用陣列的 Visual Basic 程式碼：

 [!code-vb[simple-array](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/simple-array.vb)]  

此範例會執行三個動作：

- 它會宣告`students`七個元素的陣列。 數目`6`在陣列宣告表示陣列中的最後一個索引，這是一個陣列中的項目數大於或等於。
- 它會將值指派給陣列中每個元素。 陣列元素的存取使用的陣列名稱，包括在括號中的個別項目的索引。
- 它會列出每個值的陣列。 此範例會使用[ `For` ](../../../language-reference/statements/for-next-statement.md)陳述式來存取陣列的每個項目依其索引編號。
  
 `students`在上述範例中的陣列是一維陣列，因為它會使用一個索引。 陣列，其中會使用一個以上的索引或註標稱為*多維度*。 如需詳細資訊，請參閱本文的其餘部分和[在 Visual Basic 中的陣列維度](../../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md)。  
  
##  <a name="creating-an-array"></a>建立陣列  
 
您可以數種方式來定義陣列的大小： 

- 宣告陣列時，您可以指定大小：
  
    [!code-vb[creating1](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#1)]  
  
 - 您可以使用`New`子句提供陣列的大小，在建立時：  
  
    [!code-vb[creating2](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#2)]  
  
 如果您有現有的陣列，您可以重新定義其大小使用[ `Redim` ](../../../../visual-basic/language-reference/statements/redim-statement.md)陳述式。 您可以指定`Redim`陳述式保留陣列中的值，或您可以指定它建立的空陣列。 下列範例顯示 `Redim` 陳述式的不同使用方法，以修改現有陣列的大小。  
  
 [!code-vb[redimensioning](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#3)]  
  
 如需詳細資訊，請參閱[ReDim 陳述式](../../../../visual-basic/language-reference/statements/redim-statement.md)。  
  
##  <a name="storing-values-in-an-array"></a>在陣列中儲存值
 
 您可以使用類型為 `Integer`的索引來存取陣列中的每一個位置。 使用括弧內的陣列索引即可參照各陣列的位置，從而儲存並擷取陣列中的值。 多維陣列的索引會以逗號 （，） 分隔。 各個陣列維度皆需一個索引。 

下列範例顯示一些儲存和擷取值，在陣列中的陳述式。
  
 [!code-vb[store-and-retrieve](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/store-and-retrieve.vb)]  
  
## <a name="populating-an-array-with-array-literals"></a>填入陣列常值的陣列
 藉由使用陣列常值，您可以同時建立填入一組初始的值陣列。 陣列常值由大括弧 (`{}`) 括住的逗點分隔值清單構成。  
  
 當您使用陣列常值來建立陣列時，可以提供陣列類型，或者使用類型推斷來判別陣列類型。 下列範例會示範這兩個選項。  
  
 [!code-vb[create-with-literals](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#4)]  
  
 當您使用類型推斷時，陣列的類型由*主類型*常值的清單中。 主控項的類型是陣列中的所有其他類型可以擴大範圍類型。 如果無法決定此唯一類型，則主類型將成為陣列中其他類型皆可縮小而成的唯一類型。 如果這些類型皆無法決定，則主類型為 `Object`。 例如，如果提供給陣列常值的值清單含有類型值 `Integer`、 `Long`和 `Double`，則結果陣列的類型是 `Double`。 因為`Integer`和`Long`只加寬`Double`，`Double`是主類型。 如需詳細資訊，請參閱 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。 
 
> [!NOTE] 
> 您可以使用類型推斷只對定義為型別成員中的本機變數的陣列。 如果沒有明確的類型定義，定義與類別層級的陣列常值的陣列是屬於型別`Object[]`。 如需詳細資訊，請參閱[區域類型推斷](../variables/local-type-inference.md)。 

請注意，前一個範例會定義`values`類型的陣列為`Double`即使所有陣列常值型別的`Integer`。 您可以建立此陣列，因為陣列常值中的值可以擴展為`Double`值。 
  
 您也可以建立及擴展的多維度陣列使用*巢狀陣列常值*。 巢狀的陣列常值必須有維度的數目的結果陣列一致。 下列範例會使用巢狀的陣列常值建立整數的二維陣列。  
  
 [!code-vb[nested-array-literals](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#5)]  
  
當使用巢狀的陣列常值來建立和填入的陣列，如果巢狀的陣列常值中的項目數目不相符，也會發生錯誤。 如果您明確宣告要有不同數量的維度多於陣列常值的陣列變數，也會發生錯誤。 
  
就如同您可以為一維陣列，您可以依賴類型推斷使用巢狀的陣列常值建立多維陣列時。 推斷的型別是主控項的所有巢狀層級的所有陣列常值中的所有值的類型。 下列範例會建立類型的二維陣列`Double[,]`類型的值從`Integer`和`Double`。  
  
 [!code-vb[nested-type-inference](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#6)]  
  
 如需其他範例，請參閱[如何：在 Visual Basic 中初始化陣列變數](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)。  
  
##  <a name="iterating-through-an-array"></a>逐一查看陣列  
 當您逐一查看陣列時，您存取陣列中的每個項目從最低到最高的索引，或從最高到最低。 一般而言，請使用使用[For...下一個陳述式](../../../../visual-basic/language-reference/statements/for-next-statement.md)或[每個...下一個陳述式](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)來逐一查看陣列的項目。 當您不知道陣列的上限時，您可以呼叫<xref:System.Array.GetUpperBound%2A?displayProperty=nameWithType>方法來取得索引的最大值。 雖然幾乎是最低的索引值永遠為 0，您就可以呼叫<xref:System.Array.GetLowerBound%2A?displayProperty=nameWithType>方法來取得索引的最小值。   
  
 下列範例逐一查看一維陣列使用[ `For...Next` ](../../../../visual-basic/language-reference/statements/for-next-statement.md)陳述式。 
  
 [!code-vb[iterate-one-dimensional-array](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate1d.vb)]  
  
 下列範例逐一查看多維陣列使用[ `For...Next` ](../../../../visual-basic/language-reference/statements/for-next-statement.md)陳述式。 <xref:System.Array.GetUpperBound%2A> 方法具有可指定維度的參數。 `GetUpperBound(0)` 傳回第一個維度中，最高的索引和`GetUpperBound(1)`傳回第二個維度的最高的索引。
  
 [!code-vb[iterate-two-dimensional-array](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate2d.vb)]  
  
 下列範例會使用[每個...下一個陳述式](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)來逐一查看一維陣列和二維陣列。  
  
 [!code-vb[iterate-for-each-next](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate-for-each-next.vb)]  
  
## <a name="array-size"></a>陣列大小  

 陣列大小為其所有維度長度之乘積。 它代表目前包含於陣列中的項目總數。  例如，下列範例會宣告具有四個項目，每個維度中的 2 維度陣列。 範例輸出所示，陣列的大小為 16 (或 (3 + 1) * (3 + 1)。

 [!code-vb[array-size](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/array-size.vb)]  

> [!NOTE] 
> 這裡討論的陣列大小不適用於不規則陣列。 如需不規則的陣列，決定不規則陣列的大小資訊，請參閱[不規則陣列](#jagged-arrays)> 一節。
  
  您可以使用 <xref:System.Array.Length%2A?displayProperty=nameWithType> 屬性來尋找陣列的大小。 您可以使用，以尋找每個維度的多維陣列的長度<xref:System.Array.GetLength%2A?displayProperty=nameWithType>方法。  
  
 藉由指派新的陣列物件，或使用，您可以調整大小的陣列變數[`ReDim`陳述式](../../../../visual-basic/language-reference/statements/redim-statement.md)陳述式。 下列範例會使用`ReDim`陳述式來變更 51 元素陣列的 100 個元素的陣列。

 [!code-vb[resize-an-array](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/array-size2.vb)]  
  
 處理陣列大小時，請注意幾點︰  
  
|||  
|---|---|  
|維度長度|每個維度的索引是以 0 為基礎，這表示它範圍從 0 到它的上限。 因此，指定維度的長度是比該維度的宣告上限大一。|  
|長度限制|每個維度陣列的長度是限制的最大值為`Integer`資料類型，這是<xref:System.Int32.MaxValue?displayProperty=nameWithType>或 (2 ^31)-1。 然而，陣列之總大小也同時受限於系統可用的記憶體。 如果您嘗試初始化陣列，超過可用記憶體數量，執行階段會擲回<xref:System.OutOfMemoryException>。|  
|大小及項目大小|陣列大小與其項目的資料類型無關。 大小一律代表項目，不是，它們會耗用記憶體中位元組的數目總數。|  
|記憶體消耗量|對陣列在記憶體中的儲存方式做任何假設都是不安全的。 儲存體會因不同資料寬度的平台而有差異，所以相同陣列於 64 位元系統上所佔記憶體將較 32 位元系統來的多。 當您初始化陣列時，隨著系統組態不同，通用語言執行平台 (CLR) 會指派儲存體盡可能將項目存放在一起，或是根據實體硬體界限全部加以調整。 同時，陣列需要耗用儲存體以供其控制資訊使用，此消耗量會隨著維度增加而增加。|  

## <a name="the-array-type"></a>陣列類型 
 每個陣列都是資料類型，這不同於其項目的資料類型。 沒有任何單一的資料類型適用於所有的陣列。 陣列的類型反而是由陣列的維度數目，或稱為 *「順位」*(rank) 以及陣列項目的資料類型所決定。 兩個陣列變數屬於相同的資料類型具有相同的陣序，其項目包含相同的資料類型。 陣列維度的長度不會影響陣列資料類型。  
  
 每個陣列都繼承自 <xref:System.Array?displayProperty=nameWithType> 類別，而您可以將變數宣告為類型 `Array`，但不能建立類型為 `Array` 的陣列。 例如，雖然下列程式碼會宣告`arr`變數型別`Array`並呼叫<xref:System.Array.CreateInstance%2A?displayProperty=nameWithType>方法來具現化的陣列，陣列的型別證明是 Object []。

 [!code-vb[array-class](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/array-class.vb)] 

此外，[ReDim 陳述式](../../../../visual-basic/language-reference/statements/redim-statement.md)無法在宣告為 `Array` 型別的變數上運作。 基於這些原因，以及型別安全，建議每個陣列為特定型別宣告。  
  
 有幾個方法可以找出陣列或其項目的資料類型。 
  
-   您可以呼叫<xref:System.Object.GetType%2A>上變數，以取得方法<xref:System.Type>物件，表示執行階段變數的型別。 <xref:System.Type> 物件在其屬性和方法中保留了大量的資訊。  
  
-   您可以將變數傳遞給<xref:Microsoft.VisualBasic.Information.TypeName%2A>函式可取得`String`與執行階段類型的名稱。  
  
 下列範例會呼叫二者`GetType`方法和`TypeName`函式來判斷陣列的類型。 陣列類型是`Byte(,)`。 請注意，<xref:System.Type.BaseType%2A?displayProperty=nameWithType>屬性也會指出的位元組陣列的基底類型是<xref:System.Array>類別。  
  
 [!code-vb[array-type](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/array-type.vb)]  
  
##  <a name="arrays-as-return-values-and-parameters"></a>以陣列做為傳回值和參數  
 若要從 `Function` 程序傳回陣列，請將陣列資料型別和維度數目指定為 [Function 陳述式](../../../../visual-basic/language-reference/statements/function-statement.md)的傳回型別。 在該函式內，使用相同的資料類型和維度數目來宣告區域陣列變數。 在 [Return 陳述式](../../../../visual-basic/language-reference/statements/return-statement.md)中，包含沒有括弧的區域陣列變數。  
  
 若要將陣列指定為 `Sub` 程序或 `Function` 程序的參數，請為參數定義所指定的資料類型和維度數目。 在程序的呼叫，傳遞相同的資料類型和維度數目的陣列變數。  
  
 在下列範例中，`GetNumbers`函式會傳回`Integer()`，類型的一維陣列`Integer`。 `ShowNumbers` 程序接受 `Integer()` 引數。 
  
 [!code-vb[return-value-and-params](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/return-values-and-params.vb)]  
  
 在下列範例中，`GetNumbersMultiDim`函式會傳回`Integer(,)`，類型的二維陣列`Integer`。  `ShowNumbersMultiDim` 程序接受 `Integer(,)` 引數。  
  
 [!code-vb[multidimensional-return-value](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/return-values-and-params-2d.vb)]  
  
## <a name="jagged-arrays"></a>不規則陣列  
 
有時候應用程式中的資料結構會是非矩形的二維陣列。 例如，您可能會使用陣列來儲存有關每個月份的天數高溫度資料。 陣列的第一個維度來表示月份，但是第二個維度則代表天數，而且在一個月的日數不是統一。 A*不規則的陣列*，也稱為*陣列的陣列*，適合使用這種情況。 不規則的陣列是的陣列，其元素也是陣列。 不規則陣列和不規則陣列中的每個項目都可以有一或多個維度。  
  
 下列範例會使用一個月份陣列，其中每個項目是陣列的天數。 由於不同月份的天數內的不同數字，此範例會使用不規則的陣列。  此範例示範如何建立不規則的陣列、 指派值給它，並擷取並顯示其值。
  
 [!code-vb[jagged-arrays](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged.vb)]  

前一個範例將值指派給逐一元件為基礎的不規則陣列使用`For...Next`迴圈。 您也可以使用巢狀的陣列常值，以不規則陣列的項目指派值。 不過，嘗試使用巢狀陣列常值 (例如， ```Dim valuesjagged = {{1, 2}, {2, 3, 4}}```) 會產生編譯器錯誤[BC30568](../../../,,/../misc/bc30568.md)。 若要更正錯誤，請以括弧括住內部陣列常值。 括號會強制陣列常值運算式會評估，並產生的值則用於外部陣列常值，如下列範例所示。  
  
 [!code-vb[jagged-array-initialization](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged-assign.vb)] 

不規則的陣列是一維陣列，其項目包含的陣列。 因此，<xref:System.Array.Length%2A?displayProperty=nameWithType>屬性和`Array.GetLength(0)`方法傳回一維陣列中的項目數和`Array.GetLength(1)`會擲回<xref:System.IndexOutOfRangeException>因為不規則的陣列不是多維度。 您擷取每個子陣列的值來判斷每個子陣列中的項目數<xref:System.Array.Length%2A?displayProperty=nameWithType>屬性。 下列範例說明如何判斷不規則陣列中的項目數。

[!code-vb[jagged-array-size](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged-length.vb)] 

## <a name="zero-length-arrays"></a>零長度陣列  
Visual Basic 區分未初始化的陣列 (其值是的陣列`Nothing`) 和*零長度陣列*或空陣列 （不含任何元素的陣列）。未初始化的陣列是不被建立維度，或已指派給它的任何值。 例如: 

```vb
Dim arr() As String
```
零長度陣列是以-1 的維度宣告。 例如: 

```vb
Dim arrZ(-1) As String
```
在下列情況中，您可能需要建立長度為零的陣列：  
  
-   不必擔心<xref:System.NullReferenceException>例外狀況，您的程式碼必須存取的成員<xref:System.Array>類別，例如<xref:System.Array.Length%2A>或<xref:System.Array.Rank%2A>，或呼叫 Visual Basic 函式，例如<xref:Microsoft.VisualBasic.Information.UBound%2A>。  
  
-   您想要保留您的程式碼不需要檢查是否有簡單`Nothing`做為特殊案例。  
  
-   程式碼會與應用程式開發介面互動，這個介面會要求您傳遞長度為零的陣列給一個或多個程序，或從一個或多個程序傳回長度為零的陣列。

## <a name="splitting-an-array"></a>分割陣列

在某些情況下，您可能需要分成多個陣列的單一陣列。 這牽涉到的點或點陣列需要分割，是用來識別，然後吐陣列痰到兩個或多個不同的陣列。 

> [!NOTE] 
> 本節將不會討論將單一字串分割成字串陣列，根據某些分隔符號。 如需將字串分割資訊，請參閱<xref:System.String.Split%2A?displayProperty=nameWithType>方法。

將分割陣列最常用的準則如下：

- 陣列中的項目數。 比方說，您可能想要分割數目大約等於組件的多個指定的項目數的陣列。 基於此目的，您可以使用任一方法所傳回的值<xref:System.Array.Length%2A?displayProperty=nameWithType>或<xref:System.Array.GetLength%2A?displayProperty=nameWithType>方法。

- 做為分隔符號，指出陣列分岔的位置的項目值。 您可以搜尋特定的值，藉由呼叫<xref:System.Array.FindIndex%2A?displayProperty=nameWithType>和<xref:System.Array.FindLastIndex%2A?displayProperty=nameWithType>方法。
 
一旦您判定索引或索引的分割陣列，您可以藉由呼叫，然後建立個別的陣列<xref:System.Array.Copy%2A?displayProperty=nameWithType>方法。 

下列範例會分割成大約相同大小的兩個陣列的陣列。 （如果陣列項目總數是奇數，第一個陣列有一個第二個的多個項目）。 

[!code-vb[splitting-an-array-by-length](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/split1.vb)] 

下列範例會分割成兩個陣列根據存在的元素，其值為"zzz"，會做為陣列分隔符號的字串陣列。 新的陣列不包含的項目，其中包含分隔符號。

[!code-vb[splitting-an-array-by-delimiter](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/split2.vb)] 

## <a name="joining-arrays"></a>加入陣列

您也可以結合成單一大型陣列的數目的陣列。 若要這樣做，您也使用<xref:System.Array.Copy%2A?displayProperty=nameWithType>方法。 

> [!NOTE] 
> 本節將不會討論結合成單一字串的字串陣列。 聯結字串陣列的資訊，請參閱<xref:System.String.Join%2A?displayProperty=nameWithType>方法。

然後再將每個陣列元素複製到新的陣列，您必須先確定，您已初始化陣列，使其足以 accompodate 新陣列。 您可以使用下列其中一種做法：

- 使用[ `ReDim Preserve` ](../../../../visual-basic/language-reference/statements/redim-statement.md)陳述式，以動態方式加入新項目之前先展開陣列。 這是最簡單的技巧，但它可能會導致效能降低與過多的記憶體耗用量當您複製大型陣列。
- 計算新的大型陣列所需的項目總數，然後將每個來源陣列的項目加入到它。

下列範例會使用第二種方法，將四個陣列有十個項目加入至單一陣列。  

[!code-vb[joining-an-array](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/join.vb)] 

在此情況下，原始陣列是所有小型的因為我們可以也會動態展開陣列，因為我們將每個新的陣列項目的新增。 下列範例正是如此。

[!code-vb[joining-an-array-dynamically](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/join2.vb)] 

##  <a name="collections-as-an-alternative-to-arrays"></a>使用集合取代陣列  
 陣列是最適用於建立和處理固定數目的強類型物件。 集合會提供較具彈性的方式來使用物件群組。 不同於陣列，而這需要您明確地變更與陣列的大小[`ReDim`陳述式](../../../../visual-basic/language-reference/statements/redim-statement.md)，集合成長和壓縮動態為應用程式變更的需要。  
  
 當您使用`ReDim`重新維度化陣列，Visual Basic 建立新的陣列，並釋放前一個。 這將佔用執行時間。 因此，如果您正在經常變更，或您使用的項目數目無法預測您需要的項目數目上限，您通常會取得更佳的效能集合。  
  
 對於某些集合，您可以將鍵值指派給您放入集合的任何物件，讓您可以藉由使用鍵值快速擷取物件。  
  
 如果集合包含只有一個資料類型的項目，則可使用 <xref:System.Collections.Generic?displayProperty=nameWithType> 命名空間內的其中一個類別。 泛型集合會強制類型安全，如此就不會加入其他資料類型。  
  
 如需集合的詳細資訊，請參閱[集合](../../concepts/collections.md)。
  
## <a name="related-topics"></a>相關主題  
  
|詞彙|定義|  
|----------|----------------|  
|[Array Dimensions in Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md)|說明陣列中的順位和維度。|  
|[如何：在 Visual Basic 中初始化陣列變數](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)|描述如何在陣列中填入初始值。|  
|[如何：在 Visual Basic 中排序陣列](../../../../visual-basic/programming-guide/language-features/arrays/how-to-sort-an-array.md)|示範如何依字母順序排列陣列中的項目。|  
|[如何：指派一個陣列至另一個陣列](../../../../visual-basic/programming-guide/language-features/arrays/how-to-assign-one-array-to-another-array.md)|描述將陣列指派給另一個陣列變數的規則和步驟。|  
|[陣列的疑難排解](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)|討論在使用陣列時會引發的一些常見問題。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Array?displayProperty=nameWithType>  
 [Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [ReDim 陳述式](../../../../visual-basic/language-reference/statements/redim-statement.md)
