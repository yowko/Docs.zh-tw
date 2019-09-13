---
title: Visual Basic 的新功能
ms.date: 10/24/2018
f1_keywords:
- VB.StartPage.WhatsNew
helpviewer_keywords:
- new features, Visual Basic
- what's new [Visual Basic]
- Visual Basic, what's new
ms.assetid: d7e97396-7f42-4873-a81c-4ebcc4b6ca02
ms.openlocfilehash: 3638deeafc052a2da3b438de2c504a9955a15ad3
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895267"
---
# <a name="whats-new-for-visual-basic"></a>Visual Basic 的新功能

此主題列出每個 Visual Basic 版本的主要功能名稱，並詳細說明該語言最新版本的新功能與增強功能。

## <a name="current-version"></a>目前版本

Visual Basic 16.0/Visual Studio 2019 版本16。0  
如需新功能，請參閱[Visual Basic 16.0](#visual-basic-160)

## <a name="previous-versions"></a>舊版本

Visual Basic 15.8 / Visual Studio 2017 版本 15.8 有關新功能，請參閱 [Visual Basic 15.8](#visual-basic-158)

Visual Basic 15.5 / Visual Studio 2017 版本 15.5 有關新功能，請參閱 [Visual Basic 15.5](#visual-basic-155)

Visual Basic 15.3 / Visual Studio 2017 版本 15.3 有關新功能，請參閱 [Visual Basic 15.3](#visual-basic-153)

Visual Basic 2017 / Visual Studio 2017 有關新功能，請參閱 [Visual Basic 2017](#visual-basic-2017)

Visual Basic / Visual Studio 2015 有關新功能，請參閱 [Visual Basic 14](#visual-basic-14)

Visual Basic / Visual Studio 2013 .NET 編譯器平台 ("Roslyn") 的技術預覽

Visual Basic / Visual Studio 2012 `Async` 和 `await` 關鍵字、迭代器、呼叫端資訊屬性

Visual Basic, Visual Studio 2010 自動實作的屬性、集合初始設定式、隱含行接續符號、動態、泛型共變數/反變數、全域命名空間存取

Visual Basic / Visual Studio 2008 Language Integrated Query (LINQ)、XML 常值、區域類型推斷、物件初始設定式、匿名類型、擴充方法、區域 `var` 類型推斷、Lambda 運算式、`if` 運算子、部分方法、可為 Null 的實值型別

Visual Basic / Visual Studio 2005 `My` 類型和協助程式類型 (應用程式、電腦、檔案系統、網路的存取)

Visual Basic / Visual Studio .NET 2003 位元移位運算子、迴圈變數宣告

Visual Basic / Visual Studio .NET 2002 第一版的 Visual Basic .NET

## <a name="visual-basic-160"></a>Visual Basic 16。0
Visual Basic 16.0 著重于為 .NET Core 提供 Visual Basic 執行時間（microsoft）的更多功能，而且是著重于 .NET Core Visual Basic 的第一個版本。 Visual Basic 執行時間的許多部分都取決於 WinForms，而這些會在較新版本的 Visual Basic 中新增。 

**語句中的多個位置允許的批註**在 Visual Basic 15.8 和更早版本中，只允許在空白行、語句結尾，或在允許隱含行接續的語句中的特定位置使用批註。 從 Visual Basic 16.0 開始，在明確的行接續之後，以及在行首加上底線的空格後面的語句內，也允許批註。

```vb
Public Sub Main()
    cmd.CommandText = ' Comment is allowed here without _
        "SELECT * FROM Titles JOIN Publishers " _ ' This is a comment
        & "ON Publishers.PubId = Titles.PubID " _
 _ ' This is a comment on a line without code
        & "WHERE Publishers.State = 'CA'"
End Sub
```

## <a name="visual-basic-158"></a>Visual Basic 15.8

**最佳化的浮點數至整數轉換**

在舊版的 Visual Basic 中，將 [Double](../language-reference/data-types/double-data-type.md) 和 [Single](../language-reference/data-types/single-data-type.md) 值轉換成整數會提供相對較差的效能。 當您將下列任一方法所傳回的值傳遞至其中一個[內建的 Visual Basic 整數轉換函式](../language-reference/functions/type-conversion-functions.md)(CByte、CShort、CInt、CLng、CSByte、CUShort、CUInt、CULng) 時，或在 [Option Strict](../language-reference/statements/option-strict-statement.md) 設定為 `Off` 的情況下，將下列任一方法所傳回的值隱含地轉換成整數類型時，Visual Basic 15.8 可大幅增強浮點數轉換成整數的效能：

- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Single)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Single)?displayProperty=nameWithType>
- <xref:System.Math.Ceiling(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Floor(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Round(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Truncate(System.Double)?displayProperty=nameWithType>

這項最佳化可讓程式碼執行速度更快，對於執行大量轉換 (目標為整數類型) 的程式碼，速度最快提高為兩倍。 下列範例說明一些受這項最佳化影響的簡單方法呼叫：

```vb
Dim s As Single = 173.7619
Dim d As Double = s

Dim i1 As Integer = CInt(Fix(s))               ' Result: 173
Dim b1 As Byte = CByte(Int(d))                 ' Result: 173
Dim s1 AS Short = CShort(Math.Truncate(s))     ' Result: 173
Dim i2 As Integer = CInt(Math.Ceiling(d))      ' Result: 174
Dim i3 As Integer = CInt(Math.Round(s))        ' Result: 174

```

請注意，這會截斷而不是四捨五入浮點值。

## <a name="visual-basic-155"></a>Visual Basic 15.5

[非後置具名引數](../programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md#mixing-arguments-by-position-and-by-name)

在 Visual Basic 15.3 和更早版本中，當方法呼叫同時包含位置和名稱引數時，位置引數必須在具名引數之前。 從 Visual Basic 15.5 開始，位置和具名引數可依任何順序顯示，但前提是最後一個位置引數之前的所有引數都位於正確位置。 當使用具名引數讓程式碼更容易閱讀時，這會特別有用。

例如，下列方法呼叫在具名引數之間有兩個位置引數。 具名引數清楚指出值 19 表示年齡。

```vb
StudentInfo.Display("Mary", age:=19, #9/21/1998#)
```

[`Private Protected` 成員存取修飾詞](../language-reference/modifiers/private-protected.md)

這個新的關鍵字組合能定義可由其包含類別中的所有成員，以及由衍生自該包含類別的類型 (但僅限於也能在包含組件中找到它們的情況下) 進行存取的成員。 由於結構無法被繼承，因此 `Private Protected` 只能套用至類別的成員。

**前置十六進位/二進位/八進位分隔符號**

Visual Basic 2017 新增了將底線字元 (`_`) 當作數字分隔符號的支援。 從 Visual Basic 15.5 開始，您可以使用底線字元作為前置字元與十六進位、二進位或八進位數字之間的前置分隔符號。 下列範例使用前置數字分隔符號，將 3,271,948,384 定義為十六進位數字：

```vb
Dim number As Integer = &H_C305_F860
```

若要使用底線字元作為前置分隔符號，您必須將下列項目新增至 Visual Basic 專案 (\*.vbproj) 檔：

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

## <a name="visual-basic-153"></a>Visual Basic 15.3

[**具名元組推斷**](../programming-guide/language-features/data-types/tuples.md#inferred-tuple-element-names)

當您從變數指派元組項目值時，Visual Basic 會從對應的變數名稱推斷元組項目的名稱；您不需要明確命名元組項目。 下列範例使用推斷來建立包含三個具名項目的元組：`state`、`stateName` 和 `capital`。

[!code-vb[Inferred tuple names](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#2)]

**其他編譯器參數**

Visual Basic 命令列編譯器現在支援 [ **-refout**](../reference/command-line-compiler/refout-compiler-option.md) 和 [ **-refonly**](../reference/command-line-compiler/refonly-compiler-option.md) 編譯器選項，來控制參考組件的輸出。 **-refout** 定義參考組件的輸出目錄，而 **-refonly** 指定編譯只會輸出參考組件。

## <a name="visual-basic-2017"></a>Visual Basic 2017

[**Tuple**](../programming-guide/language-features/data-types/tuples.md)

Tuple 是輕量的資料結構，最常用於從單一方法呼叫傳回多個值。 通常要從方法傳回多個值，您必須執行下列其中一項︰

- 定義自訂類型 (`Class` 或 `Structure`)。 這是重量級解決方案。

- 除了從方法傳回值外，定義一或多個 `ByRef` 參數。

Tuple 的 Visual Basic 支援可讓您快速定義 Tuple、選擇性地將語意名稱指派給它的值，並快速地擷取其值。 下列範例會包裝對 <xref:System.Int32.TryParse%2A> 方法的呼叫，並傳回 Tuple。

[!code-vb[Tuple](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#2)]

然後呼叫方法並使用類似下面的程式碼處理傳回的 Tuple。

[!code-vb[ReturnTuple](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#3)]

**二進位常值和數字分隔符號**

您可以使用前置詞 `&B` 或 `&b` 來定義二進位常值。 此外，還可以使用底線字元 `_` 當作數字分隔符號，提升可讀性。 下列範例會使用這兩種功能指派 `Byte` 值，並將它顯示為十進位、十六進位和二進位數字。

[!code-vb[Binary](../../../samples/snippets/visualbasic/getting-started/bin-example.vb#1)]

如需詳細資訊，請參閱 [Byte](../language-reference/data-types/byte-data-type.md#literal-assignments)、[Integer](../language-reference/data-types/integer-data-type.md#literal-assignments)、[Long](../language-reference/data-types/long-data-type.md#literal-assignments)、[Short](../language-reference/data-types/short-data-type.md#literal-assignments)、[SByte](../language-reference/data-types/sbyte-data-type.md#literal-assignments)、[UInteger](../language-reference/data-types/uinteger-data-type.md#literal-assignments)、[ULong](../language-reference/data-types/ulong-data-type.md#literal-assignments) 和 [UShort](../language-reference/data-types/ushort-data-type.md#literal-assignments) 資料類型的＜常值指派＞一節。

[**C# 參考傳回值的支援**](../programming-guide/language-features/procedures/ref-return-values.md)

從 C# 7.0 開始，C# 支援參考傳回值。 也就是說，當呼叫方法收到參考傳回的值時，它可以變更參考的值。 Visual Basic 不允許您撰寫使用參考傳回值的方法，但允許您使用和修改參考傳回值。

例如，以 C# 撰寫的下列 `Sentence` 類別包含 `FindNext` 方法，它可以在句子中尋找以指定子字串開頭的下一個文字。 字串會以參考傳回值傳回，而參考所傳遞至方法的 `Boolean` 變數會指出搜尋是否成功。 這表示，呼叫端不只可以讀取傳回值，還可以修改它，再將修改結果反映在 `Sentence` 類別中。

[!code-csharp[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

在最簡單的格式中，您可以使用類似下列的程式碼，修改句子中找到的字。 請注意，您不是將值指派給方法，而是指派給方法傳回的運算式，也就是參考傳回值。

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return.vb#1)]

但此程式碼有個問題，亦即如果找不到相符的項目，方法會傳回第一個字。 因為範例不會檢查 `Boolean` 引數的值來判斷是否找到相符項目，所以如果找不到相符的項目，就會修改第一個字。 如果找不到相符的項目，下列範例會用本身來取代第一個字，藉此更正這個問題。

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return.vb#2)]

更好的解決方案是使用參考所傳遞之參考傳回值對象的協助程式方法。 協助程式方法可以修改參考所傳遞給它的引數。 下列範例正是如此。

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

如需詳細資訊，請參閱[參考傳回值](../programming-guide/language-features/procedures/ref-return-values.md)。

## <a name="visual-basic-14"></a>Visual Basic 14

[Nameof](../../csharp/language-reference/operators/nameof.md)

您可以取得用於錯誤訊息之類型或成員的未限定字串名稱，而不需要對字串進行硬式編碼。  這可讓您的程式碼在重構時保持正確。  這項功能也可用來連接模型檢視控制器 MVC 連結，以及引發屬性已變更事件。

[字串內插補點](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md)

您可以使用字串插值運算式來建構字串。  字串插值運算式類似包含運算式的範本字串。  對於引數而言，字串插值比[複合格式](../../standard/base-types/composite-format.md)更容易了解。

[Null 條件式成員存取和索引](../language-reference/operators/null-conditional-operators.md)

您可以在執行成員存取 (`?.`) 或對 (`?[]`) 作業編製索引之前，透過非常精簡的語法來測試是否為 Null。  這些運算子可協助您撰寫較少的程式碼來處理 Null 檢查，特別是遞減至資料結構。  如果左運算元或物件參考為 Null，則作業會傳回 Null。

[多行字串常值](../../visual-basic/programming-guide/language-features/strings/string-basics.md)

字串常值可包含新行字元序列。  您不再需要使用 `<xml><![CDATA[...text with newlines...]]></xml>.Value` 的舊解決方法

**註解**

您可以將註解放到隱含行接續符號之後、初始設定式運算式之內和 LINQ 運算式詞彙之間。

**更聰明的完整名稱解析**

以程式碼 `Threading.Thread.Sleep(1000)` 為例，Visual Basic 之前會查詢命名空間 "Threading"，發現它在 System.Threading 和 System.Windows.Threading 之間模稜兩可，然後回報錯誤。  Visual Basic 現在會同時考慮這兩種可能的命名空間。  如果您顯示完成清單，Visual Studio 編輯器會在完成清單中列出這兩種類型的成員。

**以年起始的日期常值**

您可以有 yyyy-mm-dd 格式的日期常值 (`#2015-03-17 16:10 PM#`)。

**唯讀介面屬性**

您可以使用讀寫屬性來實作唯讀介面屬性。  這個介面可確保提供基本功能，並且不會防止實作類別允許設定屬性。

[TypeOf \<expr> IsNot \<類型>](../../visual-basic/language-reference/operators/typeof-operator.md)

為了增加程式碼的可讀性，您現在可以搭配使用 `TypeOf` 和 `IsNot`。

[#Disable Warning \<識別碼> 和 #Enable Warning \<識別碼>](../../visual-basic/language-reference/directives/index.md)

您可以停用及啟用原始程式檔中區域的特定警告。

**XML 文件註解改善**

撰寫文件註解時，您會取得智慧型編輯器，以及驗證參數名稱、適當處理 `crefs` (泛型、運算子等)、色彩標示和重構的建置支援。

[部分模組和介面定義](../../visual-basic/language-reference/modifiers/partial.md)

除了類別和結構之外，您還可以宣告部分模組和介面。

[方法主體內的 #Region 指示詞](../../visual-basic/language-reference/directives/region-directive.md)

您可以將 #Region…#End Region 分隔符號放到檔案的任何位置及函式內，甚至是橫跨不同的函式主體。

[Overrides 定義隱含為 Overloads](../../visual-basic/language-reference/modifiers/overrides.md)

如果您將 `Overrides` 修飾詞加入定義，編譯器會隱含加入 `Overloads`，讓您可以在一般情況下輸入較少的程式碼。

**屬性引數允許 CObj**

編譯器之前會提供錯誤，指出 CObj(…) 用於屬性建構時不是常數。

**從不同的介面宣告及使用模稜兩可的方法**

之前，下列程式碼會產生錯誤，使您無法宣告 `IMock` 或呼叫 `GetDetails` (如果已在 C# 中宣告這些項目)：

```vb
Interface ICustomer
  Sub GetDetails(x As Integer)
End Interface

Interface ITime
  Sub GetDetails(x As String)
End Interface

Interface IMock : Inherits ICustomer, ITime
  Overloads Sub GetDetails(x As Char)
End Interface

Interface IMock2 : Inherits ICustomer, ITime
End Interface
```

現在，編譯器會使用一般多載解析規則來選擇要呼叫的最適合 `GetDetails`，而且您可以在 Visual Basic 中宣告介面關聯性 (如範例所示)。

## <a name="see-also"></a>另請參閱

- [Visual Studio 2017 的新功能](/visualstudio/ide/whats-new-in-visual-studio)
