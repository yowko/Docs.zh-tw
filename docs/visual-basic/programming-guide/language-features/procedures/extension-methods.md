---
title: "擴充方法 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ExtensionMethods
dev_langs:
- VB
helpviewer_keywords:
- extending data types
- extension methods [Visual Basic]
ms.assetid: b8020aae-374d-46a9-bcb7-8cc2390b93b6
caps.latest.revision: 41
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 381fa0db2d92590d23ebd71a7823a8465e94a6e6
ms.lasthandoff: 03/13/2017

---
# <a name="extension-methods-visual-basic"></a>擴充方法 (Visual Basic)
擴充方法可讓開發人員將自訂功能加入到已經不需要建立新的衍生型別定義的資料型別。 擴充方法可讓撰寫方法，就好像現有型別的執行個體方法呼叫。  
  
## <a name="remarks"></a>備註  
 擴充方法只能是`Sub`程序或`Function`程序。 您無法定義擴充屬性、 欄位或事件。 所有的擴充方法必須標記為延伸屬性`<Extension()>`從<xref:System.Runtime.CompilerServices?displayProperty=fullName>命名空間。</xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 擴充方法定義中的第一個參數會指定方法要擴充的資料型別。 當方法執行時，第一個參數是繫結至叫用方法的資料類型的執行個體。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>說明  
 下列範例會定義`Print`延伸<xref:System.String>資料型別。</xref:System.String> 此方法會使用`Console.WriteLine`顯示字串。 參數的`Print`方法， `aString`，建立方法，延伸<xref:System.String>類別。</xref:System.String>  
  
 [!code-vb[VbVbalrExtensionMethods #&1;](./codesnippet/VisualBasic/extension-methods_1.vb)]  
  
 請注意，擴充方法定義使用擴充屬性標記為`<Extension()>`。 標示方法定義的模組是選擇性的但必須標示為每個擴充方法。 <xref:System.Runtime.CompilerServices>必須在匯入，才能存取此延伸模組屬性。</xref:System.Runtime.CompilerServices>  
  
 擴充方法可以只在模組內宣告。 一般而言，擴充方法定義的模組不呼叫它的一個相同的模組。 相反地，包含擴充方法的模組匯入，如果需要才能將它帶入範圍。 包含的模組後`Print`是在範圍內，可以呼叫方法，就像是一般的執行個體方法，例如採用任何引數，好像`ToUpper`:  
  
 [!code-vb[VbVbalrExtensionMethods #&2;](./codesnippet/VisualBasic/extension-methods_2.vb)]  
  
 下一個範例中， `PrintAndPunctuate`，也是延伸<xref:System.String>，此時兩個參數定義。</xref:System.String> 第一個參數， `aString`，會建立擴充方法，延伸<xref:System.String>.</xref:System.String> 第二個參數， `punc`，就是要標點符號的字串時，會傳遞做為引數呼叫該方法。 此方法會顯示後面的標點符號的字串。  
  
 [!code-vb[VbVbalrExtensionMethods #&3;](./codesnippet/VisualBasic/extension-methods_3.vb)]  
  
 方法由傳送中的字串引數呼叫`punc`:`example.PrintAndPunctuate(".")`  
  
 下列範例所示`Print`和`PrintAndPunctuate`定義和呼叫。 <xref:System.Runtime.CompilerServices>匯入定義模組中若要啟用延伸模組屬性的存取權。</xref:System.Runtime.CompilerServices>  
  
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
 所有必要時可以執行這些或類似的擴充方法是它們是在範圍內。 當在範圍內包含的擴充方法的模組，它會顯示在 IntelliSense 中，並可以如同一般的執行個體方法呼叫。  
  
 請注意，方法會叫用時，未傳送引數第一個參數。 參數`aString`在前一個方法定義為繫結至`example`，執行個體`String`用來呼叫它們。 編譯器會使用`example`當做引數傳送至第一個參數。  
  
 如果設定為物件呼叫擴充方法`Nothing`，擴充方法會執行。 這並不適用於一般的執行個體方法。 您可以明確檢查是否有`Nothing`中擴充方法。  
  
## <a name="types-that-can-be-extended"></a>可延伸的型別  
 您可以定義擴充方法的大部分型別可以用來表示 Visual Basic 的參數清單，包括下列︰  
  
-   類別 （參考型別）  
  
-   結構 （數值型別）  
  
-   介面  
  
-   委派  
  
-   ByRef 和 ByVal 引數  
  
-   泛型方法的參數  
  
-   陣列  
  
 第一個參數指定的擴充方法擴充的資料型別，因為它需要，而且不得為選擇性。 基於這個理由，`Optional`參數和`ParamArray`參數不可以是參數清單中的第一個參數。  
  
 擴充方法不會視為在晚期繫結。 在下列範例中，陳述式`anObject.PrintMe()`引發<xref:System.MissingMemberException>例外狀況，如果您會看到相同的例外狀況，第二個`PrintMe`擴充方法定義已刪除。</xref:System.MissingMemberException>  
  
 [!code-vb[VbVbalrExtensionMethods #&9;](./codesnippet/VisualBasic/extension-methods_4.vb)]  
  
## <a name="best-practices"></a>最佳作法  
 擴充方法會提供方便且功能強大的方式來擴充現有的型別。 不過，若要順利使用這些方法，有一些要考慮的事項。 這些考量適用於主要是為了類別庫的作者，但可能會影響使用擴充方法的任何應用程式。  
  
 一般來說，擴充方法，讓您將新增至不屬於您的型別會比您所控制的型別中加入的擴充方法更容易遭受攻擊。 有幾個可能會發生不屬於您可能會干擾您的擴充方法的類別。  
  
-   如果已經不需要引數至參數的縮小轉換與呼叫的陳述式中的引數與相容的簽章存在任何可存取的執行個體成員，將任何擴充方法使用的執行個體方法。 因此，如果在某個時間點的類別中加入適當的執行個體方法，您將依賴的現有擴充成員可能無法存取。  
  
-   擴充方法的作者無法避免其他程式設計人員撰寫衝突可能高於原始副檔名的擴充方法。  
  
-   您可以將放在自己的命名空間的擴充方法，以改善強固性。 您的程式庫的取用者可以包含命名空間或排除在外，或在命名空間，獨立於其餘的程式庫之中選取。  
  
-   它可能比擴充類別，尤其是如果您並未擁有介面或類別擴充介面更安全。 在介面中的變更會影響實作它的每個類別。 因此，作者可能會比較不可能加入或變更介面中的方法。 不過，如果類別實作兩個具有相同簽章的擴充方法的介面，會顯示這兩種擴充方法。  
  
-   延伸您可以最特定的型別。 在階層中的型別，如果您選取要從中衍生許多其他類型，類型有執行個體方法或與您可能會妨礙其他延伸方法的各種層面。  
  
## <a name="extension-methods-instance-methods-and-properties"></a>擴充方法、 執行個體方法和屬性  
 當範圍內的執行個體方法具有與呼叫的陳述式的引數相容的簽章時，執行個體方法是選擇任何擴充方法。 執行個體方法具有優先順序，即使此擴充方法是較佳的相符項目。 在下列範例中，`ExampleClass`包含名為執行個體方法`ExampleMethod`具有一個參數的型別`Integer`。 擴充方法`ExampleMethod`擴充`ExampleClass`，有一個參數的型別和`Long`。  
  
 [!code-vb[VbVbalrExtensionMethods #&4;](./codesnippet/VisualBasic/extension-methods_5.vb)]  
  
 第一次呼叫`ExampleMethod`下列程式碼會呼叫延伸方法，因為`arg1`是`Long`只能與相容和`Long`中擴充方法的參數。 第二次呼叫`ExampleMethod`有`Integer`引數， `arg2`，而且它會呼叫執行個體方法。  
  
 [!code-vb[VbVbalrExtensionMethods #&5;](./codesnippet/VisualBasic/extension-methods_6.vb)]  
  
 現在反向兩種方法中參數的資料型別︰  
  
 [!code-vb[VbVbalrExtensionMethods #&6;](./codesnippet/VisualBasic/extension-methods_7.vb)]  
  
 但這次中的程式碼`Main`呼叫的執行個體方法兩次。 這是因為兩者`arg1`和`arg2`具有擴展轉換`Long`，和執行個體方法優先於延伸方法，這兩種情況。  
  
 [!code-vb[VbVbalrExtensionMethods #&7;](./codesnippet/VisualBasic/extension-methods_8.vb)]  
  
 因此，擴充方法無法取代現有的執行個體方法。 不過，當擴充方法有同名的執行個體方法，但是不會發生衝突之簽章，可存取這兩種方法。 例如，如果類別`ExampleClass`包含一個名為方法`ExampleMethod`採用任何引數，具有相同名稱的擴充方法，但允許不同的簽章，如下列程式碼所示。  
  
 [!code-vb[VbVbalrExtensionMethods #&8;](./codesnippet/VisualBasic/extension-methods_9.vb)]  
  
 此程式碼的輸出如下所示︰  
  
 `Extension method`  
  
 `Instance method`  
  
 這種情況會更容易使用的屬性︰ 擴充方法的擴充方法具有相同的名稱做為其擴充的類別屬性，如果看不到，而且無法存取。  
  
## <a name="extension-method-precedence"></a>擴充方法優先順序  
 兩個具有相同簽章的擴充方法是在範圍內且可存取，則具有較高的優先順序會叫用。 擴充方法的優先順序根據用來將方法帶入範圍的機制。 下列清單顯示優先順序階層架構中的，從最高到最低。  
  
1.  目前的模組內所定義的擴充方法。  
  
2.  擴充方法定義內的資料類型在目前命名空間或任何一種其父代的優先順序高於父命名空間的子命名空間。  
  
3.  目前的檔案中的任何型別匯入定義的擴充方法。  
  
4.  目前的檔案中任何命名空間匯入定義的擴充方法。  
  
5.  任何專案層級類型匯入定義的擴充方法。  
  
6.  任何專案層級命名空間匯入定義的擴充方法。  
  
 如果優先順序無法解決模稜兩可，您可以使用完整限定的名稱來指定您要呼叫的方法。 如果`Print`前面範例中的方法定義於名為模組`StringExtensions`，完整的名稱是`StringExtensions.Print(example)`而不是`example.Print()`。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Runtime.CompilerServices></xref:System.Runtime.CompilerServices>   
 <xref:System.Runtime.CompilerServices.ExtensionAttribute></xref:System.Runtime.CompilerServices.ExtensionAttribute>   
 [擴充方法](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)   
 [Module 陳述式](../../../../visual-basic/language-reference/statements/module-statement.md)   
 [程序參數和引數](./procedure-parameters-and-arguments.md)   
 [選擇性參數](./optional-parameters.md)   
 [參數陣列](./parameter-arrays.md)   
 [屬性概觀](../../../../visual-basic/programming-guide/concepts/attributes/index.md)   
 [在 Visual Basic 中的範圍](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
