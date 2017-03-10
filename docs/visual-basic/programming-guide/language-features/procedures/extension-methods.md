---
title: "擴充方法 (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.ExtensionMethods"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "擴充資料類型"
  - "擴充方法 [Visual Basic]"
ms.assetid: b8020aae-374d-46a9-bcb7-8cc2390b93b6
caps.latest.revision: 41
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 41
---
# 擴充方法 (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

擴充方法可讓開發人員將自訂功能加入至已定義的資料類型中，而不需要建立新的衍生類型。  擴充方法可讓您撰寫可呼叫的方法，就如同是現有類型的執行個體方法一樣。  
  
## 備註  
 擴充方法可能只是 `Sub` 程序或 `Function` 程序。  您無法定義擴充屬性 \(Property\)、欄位或事件。  所有擴充方法都必須在 <xref:System.Runtime.CompilerServices?displayProperty=fullName> 命名空間 \(Namespace\) 中，以擴充屬性 \(Attribute\) `<Extension()>` 標記。  
  
 擴充方法定義的第一個參數會指定方法所擴充的資料類型。  執行此方法後，第一個參數就會繫結至叫用 \(Invoke\) 此方法之資料類型的執行個體。  
  
## 範例  
  
### 描述  
 下列範例會為 <xref:System.String> 資料類型定義 `Print` 擴充方法。  該方法會使用 `Console.WriteLine` 來顯示字串。  `Print` 方法的 `aString` 參數會建立擴充 <xref:System.String> 類別的方法。  
  
 [!code-vb[VbVbalrExtensionMethods#1](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/ConsoleApplication1/StringExtensions.vb#1)]  
  
 請注意，必須以擴充屬性 `<Extension()>` 標記擴充方法定義。  您可以選擇將其中包含已定義之方法的模組加上標記，但必須標記每個擴充方法。  必須匯入 <xref:System.Runtime.CompilerServices>，才能存取擴充屬性。  
  
 擴充方法只能在模組內宣告。  一般來說，在其中定義擴充方法的模組與擴充方法遭呼叫的模組不一樣。  必要時，而是會匯入包含擴充方法的模組，以在範圍內使用。  當包含 `Print` 的模組在範圍內之後，就可以將方法當做不使用任何引數的一般執行個體方法來呼叫，例如 `ToUpper`：  
  
 [!code-vb[VbVbalrExtensionMethods#2](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/ConsoleApplication1/Class1.vb#2)]  
  
 下一個範例 `PrintAndPunctuate` 也是 <xref:System.String> 的擴充部分，這次是以兩個參數來定義。  第一個參數 `aString` 會建立擴充 <xref:System.String> 的擴充方法。  第二個參數 `punc` 則為標點符號字串，會在呼叫方法時當做引數傳入。  方法會顯示標點符號之前的字串。  
  
 [!code-vb[VbVbalrExtensionMethods#3](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/ConsoleApplication1/Class2.vb#3)]  
  
 為 `punc` 傳送字串引數即可呼叫下列方法：`example.PrintAndPunctuate(".")`。  
  
 下列範例顯示如何定義和呼叫 `Print` 和 `PrintAndPunctuate`。  <xref:System.Runtime.CompilerServices> 會匯入定義模組中，以允許存取擴充屬性。  
  
### 程式碼  
  
```vb#  
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
  
 接著，擴充方法會集中進入範圍並遭呼叫。  
  
```vb#  
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
  
### 註解  
 若要執行上述擴充方法或類似的擴充方法，最重要的是這些擴充方法必須在範圍內。  如果包含擴充方法的模組在範圍內，就可以在 IntelliSense 中找到並呼叫該方法，就像一般執行個體方法一樣。  
  
 請注意，叫用方法時，不會針對第一個參數傳入引數。  先前方法定義中的參數 `aString` 會繫結至 `example`，這是呼叫這些方法的 `String` 執行個體。  編譯器 \(Compiler\) 會使用 `example` 做為傳送至第一個參數的引數。  
  
 如果針對設定為 `Nothing` 的物件呼叫擴充方法，則會執行擴充方法。  這不適用於一般執行個體方法。  您可以明確地檢查擴充方法中的 `Nothing` 。  
  
## 可以擴充的類型  
 您可以對大多數類型定義擴充方法 \(這些類型可以在 Visual Basic 的參數清單中呈現出來\)，包括下列各項：  
  
-   類別 \(參考類型\)  
  
-   結構 \(實值類型\)  
  
-   介面  
  
-   委派  
  
-   ByRef 和 ByVal 引數  
  
-   泛型方法參數  
  
-   陣列  
  
 由於第一個參數會指定擴充方法要擴充的資料類型，所以此為必要項而不可是選擇項。  因此，`Optional` 參數和 `ParamArray` 參數不可以是參數清單中的第一個參數。  
  
 晚期繫結不會考慮擴充方法。  在下列範例中，陳述式 `anObject.PrintMe()` 會引發 <xref:System.MissingMemberException> 例外狀況，如果刪除第二個 `PrintMe` 擴充方法定義，也會引發這個例外狀況。  
  
 [!code-vb[VbVbalrExtensionMethods#9](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/ConsoleApplication1/Class6.vb#9)]  
  
## 最佳作法  
 擴充方法可提供方便且功能強大的方法，讓您擴充現有的類型。  不過，若要順利使用這些方法，您必須考量幾個重點。  這些考量重點主要是針對類別庫的作者，但也可能影響使用擴充方法的應用程式。  
  
 一般來說，您加入至未擁有之類型的擴充方法，會比加入至所控制之類型的擴充方法來得更不安全。  在您未擁有的類別中可能會發生干擾擴充方法的情形。  
  
-   如果存在的可存取執行個體成員都具有與呼叫端陳述式之引數相容的簽章，而沒有從引數到參數所需要的縮小轉換，則擴充方法會偏好使用執行個體方法。  因此，如果將適當的執行個體方法加入至類別，您所依賴的現有擴充成員可能變成無法使用。  
  
-   擴充方法的作者無法避免其他程式設計人員撰寫相衝突的擴充方法，而這些擴充方法的優先順序甚至可能高於原始的擴充方法。  
  
-   您可以將擴充方法放置在自己的命名空間中，即可增進其強度。  您程式庫的消費者接著就能併入或排除命名空間，或者選擇程式庫中其他不同的命名空間。  
  
-   特別在您未擁有介面或類別時，擴充介面可能比擴充類別更不安全。  介面中的變更會影響實作該介面的每個類別。  因此，作者較不希望在介面中加入或變更方法。  不過，如果類別實作兩個介面，而這兩個介面有簽章相同的擴充方法，就看不到任一個擴充方法。  
  
-   擴充最特定的類型。  在類型階層中，如果選取會從中衍生許多其他類型的類型，則可能會引入執行個體方法的各種層面，或者其他可能與您的擴充方法相衝突的擴充方法。  
  
## 擴充方法、執行個體方法和屬性  
 當範圍內的執行個體方法具有與呼叫陳述式之引數相容的簽章時，會先選擇執行個體方法，再選擇任何擴充方法。  即使擴充方法更符合，但執行個體方法會優先適用。  在下列範例中，`ExampleClass` 包含名為 `ExampleMethod` 的執行個體方法，它有一個類型為 `Integer` 的參數。  擴充方法 `ExampleMethod` 則擴充 `ExampleClass`，並有一個類型為 `Long` 的參數。  
  
 [!code-vb[VbVbalrExtensionMethods#4](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/ConsoleApplication1/Class4.vb#4)]  
  
 在下列程式碼中，`ExampleMethod` 的第一個呼叫會呼叫擴充方法，因為 `arg1` 是 `Long`，它只能與擴充方法中的 `Long` 參數相容。  `ExampleMethod` 的第二個呼叫有 `Integer` 引數 `arg2`，因此會呼叫執行個體方法。  
  
 [!code-vb[VbVbalrExtensionMethods#5](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/ConsoleApplication1/Class4.vb#5)]  
  
 現在，將兩個方法中參數的資料類型互換：  
  
 [!code-vb[VbVbalrExtensionMethods#6](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/ConsoleApplication1/Class5.vb#6)]  
  
 這時，`Main` 中的程式碼兩次都會呼叫執行個體方法。  這是因為 `arg1` 和 `arg2` 都可擴展轉換為 `Long`，因此在兩種情況下，執行個體方法都優先於擴充方法。  
  
 [!code-vb[VbVbalrExtensionMethods#7](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/ConsoleApplication1/Class5.vb#7)]  
  
 因此，擴充方法無法取代現有的執行個體方法。  不過，當擴充方法與執行個體方法擁有相同的名稱，但簽章之間沒有衝突，就可存取這兩個方法。  例如，如果類別 `ExampleClass` 包含不接受引數的 `ExampleMethod` 方法，則允許使用具有相同名稱但不同簽章的擴充方法，如下列程式碼所示。  
  
 [!code-vb[VbVbalrExtensionMethods#8](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/ConsoleApplication1/Module3.vb#8)]  
  
 這個程式碼的輸出如下：  
  
 `Extension method`  
  
 `Instance method`  
  
 此情況使用屬性會簡單些：如果擴充方法的名稱與其擴充類別的屬性相同，擴充方法就看不到且無法存取。  
  
## 擴充方法優先順序  
 當具有相同簽章的兩個擴充方法都在範圍內而且可存取時，將會叫用具有較高優先順序的擴充方法。  擴充方法優先順序是根據用來將方法帶入範圍的機制所決定。  下列清單從最高到最低，列出優先順序階層。  
  
1.  在目前的模組內定義的擴充方法。  
  
2.  在目前的命名空間或任何父代之資料類型內定義的擴充方法，其子命名空間的優先順序高於父代命名空間。  
  
3.  在目前檔案之類型匯入內定義的擴充方法。  
  
4.  在目前檔案之命名空間匯入內定義的擴充方法。  
  
5.  在專案層級的類型匯入內定義的擴充方法。  
  
6.  在專案層級的命名空間匯入內定義的擴充方法。  
  
 如果優先順序無法解決模稜兩可 \(Ambiguity\) 的問題，則可以使用完整名稱來指定您正要呼叫的方法。  如果之前範例中的 `Print` 方法是在 `StringExtensions` 這個模組中定義，則完整名稱為 `StringExtensions.Print(example)`，而不是 `example.Print()`。  
  
## 請參閱  
 <xref:System.Runtime.CompilerServices>   
 <xref:System.Runtime.CompilerServices.ExtensionAttribute>   
 [擴充方法](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)   
 [Module Statement](../../../../visual-basic/language-reference/statements/module-statement.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Optional Parameters](../../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)   
 [Parameter Arrays](../../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)   
 [屬性](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)   
 [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)