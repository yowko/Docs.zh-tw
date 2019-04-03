---
title: 擴充方法 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ExtensionMethods
helpviewer_keywords:
- extending data types [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: b8020aae-374d-46a9-bcb7-8cc2390b93b6
ms.openlocfilehash: aca8f18c4bc53318792a119617b1ca0d6c4cc32e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822072"
---
# <a name="extension-methods-visual-basic"></a>擴充方法 (Visual Basic)
擴充方法可讓開發人員將自訂功能加入至已定義而不需要建立新的衍生的類型的資料類型。 擴充方法可使您能夠撰寫可視為現有類型的執行個體方法呼叫的方法。  
  
## <a name="remarks"></a>備註  
 只能是擴充方法`Sub`程序或`Function`程序。 您無法定義擴充屬性、 欄位或事件。 所有擴充方法必須都標記為擴充屬性`<Extension()>`從<xref:System.Runtime.CompilerServices?displayProperty=nameWithType>命名空間。  
  
 擴充方法定義中的第一個參數會指定方法所擴充的資料類型。 執行方法時，第一個參數會繫結至叫用方法的資料類型的執行個體。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 下列範例會定義`Print`延伸模組<xref:System.String>資料型別。 此方法會使用`Console.WriteLine`顯示字串。 參數`Print`方法中， `aString`，建立方法所擴充<xref:System.String>類別。  
  
 [!code-vb[VbVbalrExtensionMethods#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/StringExtensions.vb#1)]  
  
 請注意此擴充方法定義標記為以擴充屬性`<Extension()>`。 標記的方法已定義的模組是選擇性的但必須標示每個擴充方法。 <xref:System.Runtime.CompilerServices> 必須先匯入，才能存取此延伸模組屬性。  
  
 擴充方法只能在模組內宣告。 一般而言，在其中定義擴充方法的模組不是呼叫它的一個相同的模組。 相反地，包含擴充方法的模組匯入，如果它必須是，將它帶入範圍內。 包含的模組後`Print`是在範圍內，可以呼叫方法，就像是一般的執行個體方法不接受引數，例如好像`ToUpper`:  
  
 [!code-vb[VbVbalrExtensionMethods#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class1.vb#2)]  
  
 下一個範例中， `PrintAndPunctuate`，也是延伸<xref:System.String>，這次定義具有兩個參數。 第一個參數， `aString`，會建立擴充方法擴充<xref:System.String>。 第二個參數， `punc`，旨在為標點符號字串時呼叫的方法中傳遞做為引數。 此方法會顯示標點符號之前的字串。  
  
 [!code-vb[VbVbalrExtensionMethods#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class2.vb#3)]  
  
 方法會呼叫中的字串引數傳送`punc`: `example.PrintAndPunctuate(".")`  
  
 下列範例所示`Print`和`PrintAndPunctuate`定義和呼叫。 <xref:System.Runtime.CompilerServices> 在匯入定義模組以啟用擴充功能屬性的存取權。  
  
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
  
 接下來，擴充方法是帶入範圍，並呼叫。  
  
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
 是要能夠執行這些或類似的擴充方法是它們是在範圍內。 如果包含擴充方法的模組在範圍內，它會在 IntelliSense 中，並可在一般執行個體方法一樣呼叫。  
  
 請注意，方法會叫用時，未傳送引數第一個參數。 參數`aString`在前一個方法定義為繫結至`example`，執行個體`String`呼叫它們。 編譯器會使用`example`為傳送至第一個參數的引數。  
  
 如果設定為物件呼叫擴充方法`Nothing`，擴充方法會執行。 這不適用於一般的執行個體方法。 您可以明確檢查是否有`Nothing`中擴充方法。  
  
## <a name="types-that-can-be-extended"></a>可延伸的型別  
 您可以定義可以用來表示 Visual Basic 的參數清單，包括下列的大部分類型的擴充方法：  
  
-   類別 （參考型別）  
  
-   結構 （實值類型）  
  
-   介面  
  
-   委派  
  
-   ByRef 和 ByVal 引數  
  
-   泛型方法參數  
  
-   陣列  
  
 第一個參數會指定擴充方法要擴充的資料類型，因為它會是必要的連線，而且不能選擇性。 基於這個理由，`Optional`參數和`ParamArray`參數不可以是參數清單中的第一個參數。  
  
 擴充方法不會考慮晚期繫結。 在下列範例中，陳述式`anObject.PrintMe()`引發<xref:System.MissingMemberException>例外狀況，如果您會看到相同的例外狀況，第二個`PrintMe`擴充方法定義已刪除。  
  
 [!code-vb[VbVbalrExtensionMethods#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class6.vb#9)]  
  
## <a name="best-practices"></a>最佳作法  
 擴充方法會提供方便且功能強大的方式，來擴充現有的類型。 不過，若要成功使用它們，有一些需要考慮的事項。 這些考量主要適用於類別庫的作者，但它們可能會影響使用擴充方法的任何應用程式。  
  
 一般來說，您將新增至不是您所擁有的類型的擴充方法會比新增至所控制之類型的擴充方法更容易遭受攻擊。 不屬於您可能會干擾您的擴充方法的類別中可能有許多種。  
  
-   如果已經沒有從引數參數所需的縮小轉換是與呼叫的陳述式中的引數相容的簽章存在任何可存取的執行個體成員，方法的執行個體將用於任何擴充方法。 因此，適當的執行個體方法加入至類別，以在某個時間點，如果您依賴的現有擴充成員可能變成無法存取。  
  
-   擴充方法的作者無法避免其他程式設計人員撰寫相衝突可能高於原始的擴充功能的擴充方法。  
  
-   您可以將擴充方法放在自己的命名空間，以改善健全性。 您的程式庫的取用者再包含命名空間或排除，或選取命名空間，獨立於其餘的程式庫。  
  
-   它可能是更安全地擴充介面比擴充類別，尤其是如果您未擁有介面或類別。 在介面中的變更會影響每一個實作它的類別。 因此，作者可能會比較不可能加入或變更介面中的方法。 不過，如果類別實作兩個介面具有相同的簽章的擴充方法，會顯示未擴充方法。  
  
-   擴充最特定的類型。 在階層中的型別，如果您選取要從中衍生許多其他類型，類型有了執行個體方法或其他可能會干擾您的擴充方法的各種層面。  
  
## <a name="extension-methods-instance-methods-and-properties"></a>擴充方法、 執行個體方法和屬性  
 當範圍內執行個體方法具有與呼叫的陳述式的引數相容的簽章時，執行個體方法會選擇任何擴充方法。 執行個體方法具有優先順序，即使擴充方法是較佳的相符項目。 在下列範例中，`ExampleClass`包含名為執行個體方法`ExampleMethod`具有一個參數的型別`Integer`。 擴充方法`ExampleMethod`擴充`ExampleClass`，而且有一個參數的型別`Long`。  
  
 [!code-vb[VbVbalrExtensionMethods#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class4.vb#4)]  
  
 第一次呼叫`ExampleMethod`下列程式碼會呼叫擴充方法，因為`arg1`是`Long`僅與相容和`Long`中擴充方法的參數。 第二次呼叫`ExampleMethod`已經`Integer`引數， `arg2`，而且它會呼叫執行個體方法。  
  
 [!code-vb[VbVbalrExtensionMethods#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class4.vb#5)]  
  
 現在反轉兩個方法中參數的資料類型：  
  
 [!code-vb[VbVbalrExtensionMethods#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class5.vb#6)]  
  
 這次中的程式碼`Main`呼叫的執行個體方法兩次。 這是因為兩者`arg1`並`arg2`要能夠擴展轉換成`Long`，和執行個體方法優先於延伸方法，這兩種情況。  
  
 [!code-vb[VbVbalrExtensionMethods#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class5.vb#7)]  
  
 因此，擴充方法無法取代現有的執行個體方法。 不過，當擴充方法具有相同名稱的執行個體方法，但不是會衝突簽章，就可以存取這兩種方法。 例如，如果類別`ExampleClass`包含一個名為方法`ExampleMethod`採用任何引數，具有相同名稱的擴充方法，但允許不同的簽章，如下列程式碼所示。  
  
 [!code-vb[VbVbalrExtensionMethods#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Module3.vb#8)]  
  
 此程式碼的輸出如下所示：  
  
 `Extension method`  
  
 `Instance method`  
  
 這種情況是使用屬性更簡單： 如果擴充方法有相同名稱與其擴充的類別的屬性，擴充方法都看不見的且無法存取。  
  
## <a name="extension-method-precedence"></a>擴充方法優先順序  
 當兩個具有相同簽章的擴充方法是在範圍內且可供存取時，就會叫用具有較高的優先順序。 擴充方法優先順序根據用來將方法帶入範圍的機制。 下列清單顯示優先順序階層中的，從最高到最低。  
  
1.  目前的模組內定義的擴充方法。  
  
2.  擴充方法內定義資料類型在目前命名空間或任何其父代，其子命名空間的優先順序高於父命名空間。  
  
3.  在目前的檔案類型匯入內定義的擴充方法。  
  
4.  目前的檔案中，命名空間匯入內定義的擴充方法。  
  
5.  專案層級類型匯入內定義的擴充方法。  
  
6.  專案層級命名空間匯入內定義的擴充方法。  
  
 如果優先順序無法解決模稜兩可，您可以使用完整格式的名稱來指定您要呼叫的方法。 如果`Print`方法，在前面範例中的名為模組中定義`StringExtensions`，完整的名稱是`StringExtensions.Print(example)`而不是`example.Print()`。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.CompilerServices>
- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [擴充方法](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
- [Module 陳述式](../../../../visual-basic/language-reference/statements/module-statement.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [選擇性參數](./optional-parameters.md)
- [參數陣列](./parameter-arrays.md)
- [屬性概觀](../../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [在 Visual Basic 中的範圍](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
