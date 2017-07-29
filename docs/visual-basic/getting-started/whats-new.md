---
title: "Visual Basic 的新功能"
ms.date: 2017-04-27
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- VB.StartPage.WhatsNew
dev_langs:
- VB
helpviewer_keywords:
- new features, Visual Basic
- what's new [Visual Basic]
- Visual Basic, what's new
ms.assetid: d7e97396-7f42-4873-a81c-4ebcc4b6ca02
caps.latest.revision: 145
author: rpetrusha
ms.author: ronpet
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 0a9379d5dd2d1c6b3ed6820e350c19fb346ac84c
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="whats-new-for-visual-basic"></a>Visual Basic 的新功能

本主題列出每個 Visual Basic 版本的主要功能名稱，並詳細說明該語言最新版本的新功能和增強功能。
  
## <a name="current-version"></a>目前版本

Visual Basic / Visual Studio .NET 2017   
如需了解新功能，請參閱 [Visual Basic 2017](#visual-basic-2017)。

## <a name="previous-versions"></a>舊版本

Visual Basic / Visual Studio .NET 2015   
如需了解新功能，請參閱 [Visual Basic 14](#visual-basic-14)。

Visual Basic / Visual Studio .NET 2013  
.NET 編譯器平台 ("Roslyn") 的技術預覽

Visual Basic / Visual Studio .NET 2012   
`Async` 和 `await` 關鍵字、迭代器、呼叫端資訊屬性

Visual Basic / Visual Studio .NET 2010   
自動實作的屬性、集合初始設定式、隱含行接續符號、動態、泛型共變數/反變數、全域命名空間存取

Visual Basic / Visual Studio .NET 2008   
Language Integrated Query (LINQ)、XML 常值、區域類型推斷、物件初始設定式、匿名類型、擴充方法、區域 `var` 類型推斷、Lambda 運算式、`if` 運算子、部分方法、可為 Null 的實值類型  

Visual Basic / Visual Studio .NET 2005   
`My` 類型和協助程式類型 (應用程式、電腦、檔案系統、網路的存取)

Visual Basic / Visual Studio .NET 2003   
位元移位運算子、迴圈變數宣告

Visual Basic / Visual Studio .NET 2002   
第一版的 Visual Basic .NET

## <a name="visual-basic-2017"></a>Visual Basic 2017

[元組](../programming-guide/language-features/data-types/tuples.md)

Tuple 是輕量的資料結構，最常用於從單一方法呼叫傳回多個值。 通常要從方法傳回多個值，您必須執行下列其中一項︰

- 定義自訂類型 (`Class` 或 `Structure`)。 這是重量級解決方案。

- 除了從方法傳回值外，定義一或多個 `ByRef` 參數。
 
Tuple 的 Visual Basic 支援可讓您快速定義 Tuple、選擇性地將語意名稱指派給它的值，並快速地擷取其值。 下列範例會包裝對 <xref:System.Int32.TryParse%2A> 方法的呼叫，並傳回 Tuple。

[!code-vb[Tuple](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#2)]

然後呼叫方法並使用類似下面的程式碼處理傳回的 Tuple。

[!code-vb[ReturnTuple](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#3)] 

**二進位常值和數字分隔符號**

您可以使用前置詞 `&B` 或 `&b` 來定義二進位常值。 此外，還可以使用底線字元 `_` 當作數字分隔符號，提升可讀性。 下列範例會使用這兩種功能指派 `Byte` 值，並將它顯示為十進位、十六進位和二進位數字。

[!code-vb[二進位](../../../samples/snippets/visualbasic/getting-started/bin-example.vb#1)]

如需詳細資訊，請參閱 [Byte](../language-reference/data-types/byte-data-type.md#literal-assignments)、[Integer](../language-reference/data-types/integer-data-type.md#literal-assignments)、[Long](../language-reference/data-types/long-data-type.md#literal-assignments)、[Short](../language-reference/data-types/short-data-type.md#literal-assignments)、[SByte](../language-reference/data-types/sbyte-data-type.md#literal-assignments)、[UInteger](../language-reference/data-types/uinteger-data-type.md#literal-assignments)、[ULong](../language-reference/data-types/ulong-data-type.md#literal-assignments) 和 [UShort](../language-reference/data-types/ushort-data-type.md#literal-assignments) 資料類型的＜常值指派＞一節。

**C# 參考傳回值的支援**

從 C# 7 開始，C# 支援參考傳回值。 也就是說，當呼叫方法收到參考傳回的值時，它可以變更參考的值。 Visual Basic 不允許您撰寫使用參考傳回值的方法，但允許您使用和修改參考傳回值。

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

[Nameof](../../csharp/language-reference/keywords/nameof.md)  
 您可以取得用於錯誤訊息之類型或成員的未限定字串名稱，而不需要對字串進行硬式編碼。  這可讓您的程式碼在重構時保持正確。  這項功能也可用來連接模型檢視控制器 MVC 連結，以及引發屬性已變更事件。  
  
[字串內插補點](../../csharp/language-reference/keywords/interpolated-strings.md)  
 您可以使用字串插值運算式來建構字串。  字串插值運算式類似包含運算式的範本字串。  對於引數而言，字串插值比[複合格式](../../standard/base-types/composite-format.md)更容易了解。  
  
[Null 條件式成員存取和索引](../../csharp/language-reference/operators/null-conditional-operators.md)  
您可以在執行成員存取 (`?.`) 或對 (`?[]`) 作業編製索引之前，透過非常精簡的語法來測試是否為 Null。  這些運算子可協助您撰寫較少的程式碼來處理 Null 檢查，特別是遞減至資料結構。  如果左運算元或物件參考為 Null，則作業會傳回 Null。  
  
[多行字串常值](../../visual-basic/programming-guide/language-features/strings/string-basics.md)  
 字串常值可包含新行字元序列。  您不再需要使用 `<xml><![CDATA[...text with newlines...]]></xml>.Value` 的舊解決方法  
  
註解  
您可以將註解放到隱含行接續符號之後、初始設定式運算式之內和 LINQ 運算式詞彙之間。  
  
 更聰明的完整名稱解析  
 以程式碼 `Threading.Thread.Sleep(1000)` 為例，Visual Basic 之前會查詢命名空間 "Threading"，發現它在 System.Threading 和 System.Windows.Threading 之間模稜兩可，然後回報錯誤。  Visual Basic 現在會同時考慮這兩種可能的命名空間。  如果您顯示完成清單，Visual Studio 編輯器會在完成清單中列出這兩種類型的成員。  
  
 以年起始的日期常值  
 您可以有 yyyy-mm-dd 格式的日期常值 (`#2015-03-17 16:10 PM#`)。  
  
 唯讀介面屬性  
 您可以使用讀寫屬性來實作唯讀介面屬性。  這個介面可確保提供基本功能，並且不會防止實作類別允許設定屬性。  
  
 [TypeOf \<expr> IsNot \<類型>](../../visual-basic/language-reference/operators/typeof-operator.md)  
 為了增加程式碼的可讀性，您現在可以搭配使用 `TypeOf` 和 `IsNot`。  
  
 [#Disable Warning \<識別碼> 和 #Enable Warning \<識別碼>](../../visual-basic/language-reference/directives/directives.md)  
 您可以停用及啟用原始程式檔中區域的特定警告。  
  
 XML 文件註解增強功能  
 撰寫文件註解時，您會取得智慧型編輯器，以及驗證參數名稱、適當處理 `crefs` (泛型、運算子等)、色彩標示和重構的建置支援。  
  
 [部分模組和介面定義](../../visual-basic/language-reference/modifiers/partial.md)  
 除了類別和結構之外，您還可以宣告部分模組和介面。  
  
 [方法主體內的 #Region 指示詞](../../visual-basic/language-reference/directives/region-directive.md)  
 您可以將 #Region…#End Region 分隔符號放到檔案的任何位置及函式內，甚至是橫跨不同的函式主體。  
  
 [Overrides 定義隱含為 Overloads](../../visual-basic/language-reference/modifiers/overrides.md)  
 如果您將 `Overrides` 修飾詞加入定義，編譯器會隱含加入 `Overloads`，讓您可以在一般情況下輸入較少的程式碼。  
  
 屬性引數允許 CObj  
 編譯器之前會提供錯誤，指出 CObj(…) 用於屬性建構時不是常數。  
  
 從不同的介面宣告及使用模稜兩可的方法  
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
  
## <a name="see-also"></a>請參閱  
 [Visual Studio 2017 的新功能](/visualstudio/ide/whats-new-in-visual-studio)

