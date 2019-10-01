---
title: 擴充方法 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ExtensionMethods
helpviewer_keywords:
- extending data types [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: b8020aae-374d-46a9-bcb7-8cc2390b93b6
ms.openlocfilehash: b5ad066fe9ec40d715702ed99537f45b21c558cf
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701047"
---
# <a name="extension-methods-visual-basic"></a>擴充方法 (Visual Basic)

擴充方法可讓開發人員將自訂功能加入至已定義的資料類型，而不需要建立新的衍生類型。 擴充方法可讓您撰寫方法，如同現有類型的實例方法一樣，可以呼叫它。
  
## <a name="remarks"></a>備註

擴充方法只能是 @no__t 0 程式或 @no__t 1 程式。 您不能定義擴充屬性、欄位或事件。 所有擴充方法都必須以 <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> 命名空間中的擴充屬性 `<Extension>` 標記，而且必須在[模組](../../../language-reference/statements/module-statement.md)中定義。 如果在模組外部定義擴充方法，Visual Basic 編譯器會產生錯誤[BC36551](../../../misc/bc36551.md)「擴充方法只能在模組中定義」。

擴充方法定義中的第一個參數會指定方法擴充的資料類型。 當執行方法時，第一個參數會系結至叫用方法之資料類型的實例。

@No__t-0 屬性只能套用至 Visual Basic [`Module`](../../../language-reference/statements/module-statement.md)、 [`Sub`](../../../language-reference/statements/sub-statement.md)或[`Function`](../../../language-reference/statements/function-statement.md)。 如果您將它套用至 `Class` 或 `Structure`，則 Visual Basic 編譯器會產生錯誤[BC36550](../../../language-reference/error-messages/extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations.md)，"Extension ' 屬性只能套用到 ' Module '、' Sub ' 或 ' Function ' 宣告。

## <a name="example"></a>範例

下列範例會定義 <xref:System.String> 資料類型的 `Print` 延伸模組。 方法會使用 `Console.WriteLine` 來顯示字串。 @No__t-0 方法的參數（`aString`）會建立方法擴充 @no__t 2 類別。
  
[!code-vb[VbVbalrExtensionMethods#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/StringExtensions.vb#1)]

請注意，擴充方法定義已標記 `<Extension()>` 的延伸模組屬性。 標記方法定義所在的模組是選擇性的，但每個擴充方法都必須標記為。 必須匯入 <xref:System.Runtime.CompilerServices>，才能存取擴充屬性。

擴充方法只能在模組內宣告。 一般而言，在其中定義擴充方法的模組，與呼叫它的模組不同。 相反地，會匯入包含擴充方法的模組（如果需要的話），使其成為範圍。 在包含 `Print` 的模組位於範圍內之後，就可以呼叫方法，就像是不採用任何引數的一般實例方法，例如 `ToUpper`：

[!code-vb[VbVbalrExtensionMethods#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class1.vb#2)]

下一個範例 `PrintAndPunctuate`，也是 <xref:System.String> 的延伸模組，這次是以兩個參數定義。 第一個參數 `aString`，會建立擴充方法擴充 <xref:System.String>。 第二個參數 `punc`，其目的是在呼叫方法時當做引數傳入的標點符號字串。 方法會顯示後面接著標點符號的字串。

[!code-vb[VbVbalrExtensionMethods#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class2.vb#3)]

方法的呼叫方式是傳送 `punc` 的字串引數： `example.PrintAndPunctuate(".")`

下列範例會顯示已定義和呼叫 `Print` 和 @no__t 1。 <xref:System.Runtime.CompilerServices> 會匯入定義模組中，以便啟用擴充屬性的存取。


```vb
Imports System.Runtime.CompilerServices

Module StringExtensions

    <Extension()>
    Public Sub Print(aString As String)
        Console.WriteLine(aString)
    End Sub

    <Extension()>
    Public Sub PrintAndPunctuate(aString As String, punc As String)
        Console.WriteLine(aString & punc)
    End Sub
End Module
```

接下來，擴充方法會帶入範圍並呼叫：

```vb
Imports ConsoleApplication2.StringExtensions

Module Module1

    Sub Main()
        Dim example As String = "Example string"
        example.Print()

        example = "Hello"
        example.PrintAndPunctuate(".")
        example.PrintAndPunctuate("!!!!")
    End Sub
End Module
```

能夠執行這些或類似的擴充方法所需的一切，都是在範圍內。 如果包含擴充方法的模組在範圍內，它會顯示在 IntelliSense 中，而且可以如同一般實例方法一樣呼叫。

請注意，當叫用方法時，不會在中針對第一個參數傳送任何引數。 先前方法定義中的參數 `aString` 系結至 `example`，也就是呼叫它們的 @no__t 的實例。 編譯器會使用 `example` 做為傳送至第一個參數的引數。

如果針對設定為 `Nothing` 的物件呼叫擴充方法，則會執行擴充方法。 這並不適用于一般實例方法。 您可以明確地檢查擴充方法中的 `Nothing`。

## <a name="types-that-can-be-extended"></a>可以擴充的類型

您可以在可在 Visual Basic 參數清單中表示的大部分類型上定義擴充方法，包括下列各項：

- 類別（參考型別）
- 結構（實數值型別）
- 介面
- 委派
- ByRef 和 ByVal 引數
- 泛型方法參數
- 陣列

因為第一個參數指定擴充方法所擴充的資料類型，所以它是必要的，而且不能是選擇性的。 基於這個理由，`Optional` 參數和 @no__t 1 參數不可以是參數清單中的第一個參數。

延伸方法不會被視為晚期繫結。 在下列範例中，`anObject.PrintMe()` 的語句會引發 <xref:System.MissingMemberException> 例外狀況，這是您在第二個 `PrintMe` 擴充方法定義已刪除時所看到的相同例外狀況。

[!code-vb[VbVbalrExtensionMethods#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class6.vb#9)]

## <a name="best-practices"></a>最佳做法

擴充方法提供了一個方便且功能強大的方式來擴充現有的類型。 不過，若要成功使用它們，有一些重點需要考慮。 這些考慮主要適用于類別庫的作者，但它們可能會影響任何使用擴充方法的應用程式。

最常見的情況是，您新增至您未擁有之類型的擴充方法，會比新增至您所控制之類型的擴充方法更容易受到攻擊。 您不擁有的類別可能會發生一些問題，這可能會干擾您的擴充方法。

- 如果有任何可存取的實例成員存在，且其簽章與呼叫語句中的引數相容，而且引數至參數不需要任何縮小轉換，則實例方法將會在任何擴充方法的喜好設定中使用。 因此，如果在某個時間點將適當的實例方法加入至類別，則您依賴的現有延伸模組成員可能會變成無法存取。

- 擴充方法的作者無法防止其他程式設計人員撰寫衝突的擴充方法，其優先順序可能高於原始的延伸模組。

- 您可以藉由將擴充方法放在自己的命名空間中，來改善穩定性。 您的程式庫取用者可以包含命名空間或將其排除，或在命名空間之間，與程式庫的其餘部分分開。

- 擴充介面可能會比擴充類別更安全，特別是當您沒有擁有介面或類別時。 介面中的變更會影響每個執行它的類別。 因此，作者可能比較不可能在介面中新增或變更方法。 不過，如果類別所執行的兩個介面具有相同簽章的擴充方法，則不會顯示任何擴充方法。

- 擴充您可以的最特定類型。 在類型的階層架構中，如果您選取衍生許多其他類型的類型，可能會有一些層級的導入實例方法或其他可能會干擾您的的擴充方法。

## <a name="extension-methods-instance-methods-and-properties"></a>擴充方法、實例方法和屬性

當範圍內的實例方法具有與呼叫語句的引數相容的簽章時，會將實例方法選擇為任何擴充方法的喜好設定。 即使擴充方法更符合，實例方法仍具有優先權。 在下列範例中，`ExampleClass` 包含名為 `ExampleMethod` 的實例方法，其具有 `Integer` 類型的一個參數。 擴充方法 `ExampleMethod` 會延伸 `ExampleClass`，並具有 `Long` 類型的一個參數。

[!code-vb[VbVbalrExtensionMethods#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class4.vb#4)]

在下列程式碼中，第一次呼叫 `ExampleMethod` 時，會呼叫擴充方法，因為 `arg1` 是 `Long`，而且僅與擴充方法中的 `Long` 參數相容。 第二次對 `ExampleMethod` 的呼叫具有 `Integer` 引數，`arg2`，而且它會呼叫實例方法。

[!code-vb[VbVbalrExtensionMethods#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class4.vb#5)]

現在，請在兩個方法中反轉參數的資料類型：

[!code-vb[VbVbalrExtensionMethods#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class5.vb#6)]

這次 @no__t 中的程式碼會呼叫實例方法兩次。 這是因為 `arg1` 和 `arg2` 都有 `Long` 的擴輾轉換，而實例方法的優先順序高於這兩種情況下的擴充方法。

[!code-vb[VbVbalrExtensionMethods#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class5.vb#7)]

因此，擴充方法無法取代現有的實例方法。 不過，當擴充方法的名稱與實例方法相同，但是簽章不衝突時，可以存取這兩種方法。 例如，如果類別 `ExampleClass` 包含名為 `ExampleMethod` 且不接受引數的方法，則會允許具有相同名稱但具有不同簽章的擴充方法，如下列程式碼所示。

[!code-vb[VbVbalrExtensionMethods#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Module3.vb#8)]

這段程式碼的輸出如下所示：

```console
Extension method
Instance method
```

屬性的情況較簡單：如果擴充方法的名稱與它所擴充之類別的屬性相同，則不會顯示擴充方法，而且無法存取。

## <a name="extension-method-precedence"></a>擴充方法優先順序

當具有相同簽章的兩個擴充方法在範圍內且可供存取時，將會叫用具有較高優先順序的延伸模組。 擴充方法的優先順序是以用來將方法帶入範圍的機制為基礎。 下列清單顯示優先順序階層，從最高到最低。

1. 在目前模組內定義的擴充方法。

2. 在目前命名空間中的資料類型或其任何一個父系內定義的擴充方法，其子命名空間的優先順序高於父命名空間。

3. 在目前檔案中的任何類型匯入內定義的擴充方法。

4. 在目前檔案中的任何命名空間匯入內定義的擴充方法。

5. 定義于任何專案層級類型匯入內的擴充方法。

6. 在任何專案層級命名空間匯入中定義的擴充方法。

如果優先順序無法解決不明確的問題，您可以使用完整名稱來指定您要呼叫的方法。 如果先前範例中的 `Print` 方法是在名為 `StringExtensions` 的模組中定義，則完整名稱會是 `StringExtensions.Print(example)`，而不是 `example.Print()`。

## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.CompilerServices>
- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [擴充方法](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
- [Module 陳述式](../../../language-reference/statements/module-statement.md)
- [程序參數和引數](procedure-parameters-and-arguments.md)
- [選擇性參數](optional-parameters.md)
- [參數陣列](parameter-arrays.md)
- [屬性概觀](../../concepts/attributes/index.md)
- [Visual Basic 中的範圍](../declared-elements/scope.md)
