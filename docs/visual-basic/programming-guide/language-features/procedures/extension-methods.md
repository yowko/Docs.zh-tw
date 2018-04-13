---
title: 擴充方法 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ExtensionMethods
helpviewer_keywords:
- extending data types [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: b8020aae-374d-46a9-bcb7-8cc2390b93b6
caps.latest.revision: 41
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d3db3bc2b213b78ef2dceebcf56c9d5fbfa3016e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="extension-methods-visual-basic"></a>擴充方法 (Visual Basic)
擴充方法可讓開發人員將自訂功能加入至已定義而不需要建立新的衍生的類型的資料類型。 擴充方法可讓撰寫方法，這個方法，就好像現有類型的執行個體方法呼叫。  
  
## <a name="remarks"></a>備註  
 擴充方法可以只`Sub`程序或`Function`程序。 您無法定義延伸模組屬性、 欄位或事件。 所有擴充方法必須標示都為使用擴充屬性`<Extension()>`從<xref:System.Runtime.CompilerServices?displayProperty=nameWithType>命名空間。  
  
 擴充方法定義中的第一個參數指定方法可擴充的資料類型。 當方法執行時，第一個參數是繫結至叫用方法的資料類型的執行個體。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 下列範例會定義`Print`延伸<xref:System.String>資料型別。 此方法會使用`Console.WriteLine`顯示字串。 參數`Print`方法， `aString`，建立方法可擴充<xref:System.String>類別。  
  
 [!code-vb[VbVbalrExtensionMethods#1](./codesnippet/VisualBasic/extension-methods_1.vb)]  
  
 請注意，標記為使用擴充屬性的擴充方法定義`<Extension()>`。 將標示方法定義的模組是選擇性的但必須標記每個擴充方法。 <xref:System.Runtime.CompilerServices>必須先匯入，才能存取此延伸模組屬性。  
  
 擴充方法可以只在模組內宣告。 一般而言，擴充方法定義所在的模組不是相同的模組呼叫它的一個。 相反地，包含擴充方法的模組匯入時，如果它必須是，若要將它帶到範圍。 包含的模組之後`Print`是在範圍內，呼叫此方法可以如同一般的執行個體方法，不接受引數，例如`ToUpper`:  
  
 [!code-vb[VbVbalrExtensionMethods#2](./codesnippet/VisualBasic/extension-methods_2.vb)]  
  
 下一個範例中， `PrintAndPunctuate`，也是延伸<xref:System.String>，這次定義具有兩個參數。 第一個參數， `aString`，建立擴充方法，延伸<xref:System.String>。 第二個參數， `punc`，要用的字串時，會傳遞做為引數呼叫該方法的標點符號。 此方法會顯示後面的標點符號的字串。  
  
 [!code-vb[VbVbalrExtensionMethods#3](./codesnippet/VisualBasic/extension-methods_3.vb)]  
  
 傳送中的字串引數呼叫的方法`punc`:`example.PrintAndPunctuate(".")`  
  
 下列範例所示`Print`和`PrintAndPunctuate`定義和呼叫。 <xref:System.Runtime.CompilerServices>在匯入定義模組以啟用擴充功能屬性的存取權。  
  
### <a name="code"></a>程式碼  
  
```vb  
Imports System.Runtime.CompilerServices  
  
Module StringExtensions  
  
    <Extension()>   
    Public Sub Print(ByVal aString As String)  
        Console.WriteLine(aString)  
    End Sub  
  
    <Extension()>   
    Public Sub PrintAndPunctuate(ByVal aString As String,   
                                 ByVal punc As String)  
        Console.WriteLine(aString & punc)  
    End Sub  
  
End Module  
```  
  
 接下來，擴充方法帶入範圍，而且呼叫。  
  
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
  
### <a name="comments"></a>註解  
 所有，並在需要能夠執行這些或類似的擴充方法是它們是在範圍內。 如果在範圍內包含的擴充方法的模組，它會顯示在 IntelliSense 中，並可以如同一般的執行個體方法呼叫。  
  
 請注意，方法會叫用時，未傳送引數第一個參數。 參數`aString`在上一個方法定義為繫結至`example`，執行個體`String`呼叫它們。 編譯器將使用`example`為傳送至第一個參數的引數。  
  
 如果設為物件呼叫擴充方法`Nothing`，擴充方法會執行。 這不適用於一般的執行個體方法。 您可以明確檢查是否有`Nothing`中擴充方法。  
  
## <a name="types-that-can-be-extended"></a>可延伸的型別  
 您可以定義擴充方法的大部分型別可以用來表示 Visual Basic 的參數清單，包括下列：  
  
-   類別 （參考類型）  
  
-   結構 （實值類型）  
  
-   介面  
  
-   委派  
  
-   ByRef 和 ByVal 引數  
  
-   泛型方法的參數  
  
-   陣列  
  
 第一個參數會指定擴充方法所擴充的資料類型，因為它需要而不得為選用。 基於這個原因，`Optional`參數和`ParamArray`參數不可以是參數清單中的第一個參數。  
  
 擴充方法不會視為在晚期繫結。 在下列範例中，陳述式`anObject.PrintMe()`引發<xref:System.MissingMemberException>例外狀況，如果您會看到相同的例外狀況，第二個`PrintMe`擴充方法定義已刪除。  
  
 [!code-vb[VbVbalrExtensionMethods#9](./codesnippet/VisualBasic/extension-methods_4.vb)]  
  
## <a name="best-practices"></a>最佳作法  
 擴充方法提供方便且功能強大的方式，來擴充現有的類型。 不過，若要順利使用，有一些要考慮的事項。 這些考量主要適用於類別庫的作者，但它們可能會影響使用擴充方法的任何應用程式。  
  
 一般來說，您將加入至您並未擁有的型別的擴充方法是擴充方法新增至您所控制的型別比更容易遭受的。 有許多種，可能會發生在您並未擁有的類別可能會干擾您的擴充方法。  
  
-   有任何可存取的執行個體成員具有所需的引數至參數沒有縮小轉換中呼叫的陳述式的引數與相容的簽章，執行個體方法會使用任何擴充方法。 因此，在某個時間點的類別加入適當的執行個體方法，如果您依賴的現有擴充成員可能會無法存取。  
  
-   擴充方法的作者無法防止其他程式設計師撰寫衝突可能高於原始副檔名的擴充方法。  
  
-   您可以將擴充方法放在自己的命名空間中改善健全性。 您的程式庫的取用者可以再命名空間或包含或排除它，在命名空間，分開其餘的程式庫之中選取。  
  
-   它可能、 更安全地擴充介面，而不是擴充類別，尤其是如果您並未擁有介面或類別。 在介面中的變更會影響實作它的每個類別。 因此，作者可能會比較容易新增或變更介面中的方法。 不過，如果類別實作相同的簽章的擴充方法的兩個介面，會顯示這兩種擴充方法。  
  
-   延伸您可以最特定的型別。 在階層中的型別，如果您選取要從中衍生許多其他類型，類型有圖層的執行個體方法或其他可能會干擾您的擴充方法的簡介的可能性。  
  
## <a name="extension-methods-instance-methods-and-properties"></a>擴充方法、 執行個體方法和屬性  
 是呼叫陳述式的引數與相容的簽章的範圍內執行個體方法時，執行個體方法是選擇任何擴充方法。 執行個體方法具有優先順序，即使此擴充方法是較佳的相符項目。 在下列範例中，`ExampleClass`包含名為的執行個體方法`ExampleMethod`具有型別的一個參數`Integer`。 擴充方法`ExampleMethod`擴充`ExampleClass`，且具有一個參數的型別`Long`。  
  
 [!code-vb[VbVbalrExtensionMethods#4](./codesnippet/VisualBasic/extension-methods_5.vb)]  
  
 第一次呼叫`ExampleMethod`在下列程式碼會呼叫擴充方法，因為`arg1`是`Long`和僅與相容`Long`中擴充方法的參數。 第二個呼叫`ExampleMethod`具有`Integer`引數， `arg2`，而且它會呼叫執行個體方法。  
  
 [!code-vb[VbVbalrExtensionMethods#5](./codesnippet/VisualBasic/extension-methods_6.vb)]  
  
 現在反向兩個方法中參數的資料的類型：  
  
 [!code-vb[VbVbalrExtensionMethods#6](./codesnippet/VisualBasic/extension-methods_7.vb)]  
  
 這次中的程式碼`Main`呼叫的執行個體方法兩次。 這是因為同時`arg1`和`arg2`能夠擴展轉換成`Long`，和執行個體方法的優先順序高於在這兩種情況下擴充方法。  
  
 [!code-vb[VbVbalrExtensionMethods#7](./codesnippet/VisualBasic/extension-methods_8.vb)]  
  
 因此，擴充方法無法取代現有的執行個體方法。 不過，當擴充方法的執行個體方法名稱相同，但簽章不發生衝突，可以存取這兩種方法。 例如，如果類別`ExampleClass`包含方法，名為`ExampleMethod`採用任何引數，具有相同名稱的擴充方法，但允許不同的簽章，如下列程式碼所示。  
  
 [!code-vb[VbVbalrExtensionMethods#8](./codesnippet/VisualBasic/extension-methods_9.vb)]  
  
 此程式碼的輸出如下所示：  
  
 `Extension method`  
  
 `Instance method`  
  
 這種情況是簡單屬性： 如果擴充方法具有相同屬性的名稱相同的類別，它會擴充，擴充方法不可見，且無法存取。  
  
## <a name="extension-method-precedence"></a>擴充方法優先順序  
 兩個具有相同的簽章的擴充方法是在範圍內，而且可存取，則具有較高的優先順序會叫用。 擴充方法的優先順序根據用來將方法帶到範圍的機制。 下列清單顯示優先順序階層中的，從最高到最低。  
  
1.  目前的模組內定義的擴充方法。  
  
2.  擴充方法定義內的資料類型在目前命名空間，或其父代的任何一個的優先順序高於父命名空間的子命名空間。  
  
3.  任何型別中的匯入目前的檔案內定義的擴充方法。  
  
4.  在任何命名空間中的匯入目前的檔案內定義的擴充方法。  
  
5.  任何專案層級類型匯入定義的擴充方法。  
  
6.  任何專案層級命名空間匯入定義的擴充方法。  
  
 如果優先順序無法解決模稜兩可，您可以使用完整限定的名稱來指定您要呼叫的方法。 如果`Print`前面範例中的方法定義中名為`StringExtensions`，完整的名稱是`StringExtensions.Print(example)`而不是`example.Print()`。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Runtime.CompilerServices>  
 <xref:System.Runtime.CompilerServices.ExtensionAttribute>  
 [擴充方法](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
 [Module 陳述式](../../../../visual-basic/language-reference/statements/module-statement.md)  
 [程序參數和引數](./procedure-parameters-and-arguments.md)  
 [選擇性參數](./optional-parameters.md)  
 [參數陣列](./parameter-arrays.md)  
 [屬性概觀](../../../../visual-basic/programming-guide/concepts/attributes/index.md)  
 [在 Visual Basic 中的範圍](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
