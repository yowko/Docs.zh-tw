---
title: "Function 陳述式 (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Function"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "程序建立"
  - "Function 程序、 函式陳述式語法"
  - "函式 [Visual Basic] function 程序"
  - "ParamArray 關鍵字，函式陳述式"
  - "Private 關鍵字，函式陳述式"
  - "宣告程序"
  - "程序宣告"
  - "Public 關鍵字，在 Function 陳述式"
  - "ByVal 關鍵字，函式陳述式"
  - "遞迴程序"
  - "Implements 關鍵字，函式陳述式"
  - "程序，傳回值"
  - "Exit 陳述式，在 Function 程序"
  - "遞迴程序"
  - "As 關鍵字，在 Function 陳述式"
  - "選擇性的關鍵字，函式陳述式"
  - "Function 陳述式"
  - "Visual Basic 程式碼，函式程序"
  - "程序、 函式"
  - "ByRef 關鍵字，函式陳述式"
  - "Friend 關鍵字，函式陳述式"
  - "End 關鍵字 Function 陳述式"
  - "Handles 關鍵字，函式陳述式"
ms.assetid: a4497077-0f46-4ede-a27f-9e8670df52b9
caps.latest.revision: 62
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 62
---
# Function 陳述式 (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

名稱、 參數和定義的程式碼會宣告 `Function` 程序。  
  
## <a name="syntax"></a>語法  
  
```  
[ <attributelist> ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async | Iterator ]  
Function name [ (Of typeparamlist) ] [ (parameterlist) ] [ As returntype ] [ Implements implementslist | Handles eventlist ]  
    [ statements ]  
    [ Exit Function ]  
    [ statements ]  
End Function  
```  
  
## <a name="parts"></a>組件  
  
-   `attributelist`  
  
     選擇項。 請參閱 [屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)。  
  
-   `accessmodifier`  
  
     選擇項。 可以是下列其中一項：  
  
    -   [公用](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [受保護](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [私用](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   `Protected Friend`  
  
     請參閱 [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
-   `proceduremodifiers`  
  
     選擇項。 可以是下列其中一項：  
  
    -   [多載](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
    -   [覆寫](../../../visual-basic/language-reference/modifiers/overrides.md)  
  
    -   [可覆寫](../../../visual-basic/language-reference/modifiers/overridable.md)  
  
    -   [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
  
    -   [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     選擇項。 請參閱 [共用](../../../visual-basic/language-reference/modifiers/shared.md)。  
  
-   `Shadows`  
  
     選擇項。 請參閱 [陰影](../../../visual-basic/language-reference/modifiers/shadows.md)。  
  
-   `Async`  
  
     選擇項。 請參閱 [非同步](../../../visual-basic/language-reference/modifiers/async.md)。  
  
-   `Iterator`  
  
     選擇項。 請參閱 [迭代器](../../../visual-basic/language-reference/modifiers/iterator.md)。  
  
-   `name`  
  
     必要項。 程序的名稱。 請參閱 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。  
  
-   `typeparamlist`  
  
     選擇項。 泛型程序的類型參數的清單。 請參閱 [輸入清單](../../../visual-basic/language-reference/statements/type-list.md)。  
  
-   `parameterlist`  
  
     選擇項。 代表此程序參數的本機變數名稱的清單。 請參閱 [參數清單](../../../visual-basic/language-reference/statements/parameter-list.md)。  
  
-   `returntype`  
  
     只有在 `Option Strict` 是 `On`。 這個程序所傳回之值的資料型別。  
  
-   `Implements`  
  
     選擇項。 表示此程序會實作一個或多個 `Function` 程序，每一個定義在此程序包含類別或結構所實作的介面。 請參閱 [實作陳述式](../../../visual-basic/language-reference/statements/implements-statement.md)。  
  
-   `implementslist`  
  
     如果使用 `Implements`，則為必要項。 實作之 `Function` 程序的清單。  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     每個 `implementedprocedure` 都具有下列語法和組件：  
  
     `interface.definedname`  
  
    |||  
    |-|-|  
    |組件|說明|  
    |`interface`|必要項。 這個程序所實作的介面名稱的包含類別或結構。|  
    |`definedname`|必要項。 名稱，據以在 `interface` 中定義程序。|  
  
-   `Handles`  
  
     選擇項。 表示此程序可以處理一或多個特定的事件。 請參閱 [處理](../../../visual-basic/language-reference/statements/handles-clause.md)。  
  
-   `eventlist`  
  
     如果使用 `Handles`，則為必要項。 此程序處理的事件清單。  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     每個 `eventspecifier` 都具有下列語法和組件：  
  
     `eventvariable.event`  
  
    |||  
    |-|-|  
    |組件|說明|  
    |`eventvariable`|必要項。 宣告的類別或結構，會引發事件的資料類型的物件變數。|  
    |`event`|必要項。 此程序處理事件的名稱。|  
  
-   `statements`  
  
     選擇項。 要執行此程序內的陳述式區塊。  
  
-   `End Function`  
  
     結束這個程序的定義。  
  
## <a name="remarks"></a>備註  
 所有的可執行程式碼必須在程序。 每個程序，接著，在宣告類別、 結構或就是包含類別、 結構或模組的模組。  
  
 若要將值傳回給呼叫程式碼，使用 `Function` 程序; 否則，請使用 `Sub` 程序。  
  
## <a name="defining-a-function"></a>定義函式  
 您可以定義 `Function` 只能在模組層級的程序。 因此，函式宣告內容必須是類別、 結構、 模組或介面，且不能是原始程式檔、 命名空間、 程序或區塊。 如需詳細資訊，請參閱 [宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。  
  
 `Function` 程序預設為公用存取。 您可以調整存取層級的存取修飾詞。  
  
 A `Function` 程序可以宣告此程序傳回值的資料型別。 您可以指定任何資料型別或列舉、 結構、 類別或介面的名稱。 如果您未指定 `returntype` 參數，此程序傳回 `Object`。  
  
 如果此程序使用 `Implements` 關鍵字、 包含類別或結構也必須 `Implements` 緊接在後面的陳述式其 `Class` 或 `Structure` 陳述式。  `Implements` 陳述式必須包含在指定的每個介面 `implementslist`。 不過，名稱的介面會定義 `Function` (在 `definedname`) 不需要符合此程序的名稱 (在 `name`)。  
  
> [!NOTE]
>  您可以使用 lambda 運算式來定義函式運算式內嵌。 如需詳細資訊，請參閱 [函式運算式](../../../visual-basic/language-reference/operators/function-expression.md) 和 [Lambda 運算式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。  
  
## <a name="returning-from-a-function"></a>傳回從函式  
 當 `Function` 程序會傳回呼叫程式碼，呼叫程序的陳述式後面的陳述式繼續執行。  
  
 若要從函式傳回值，您可以將值指派給函式名稱，或將它併入 `Return` 陳述式。  
  
  `Return` 陳述式同時指派傳回值，並結束函式，如下列範例所示。  
  
 [!code-vb[VbVbalrStatements#24](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_1.vb)]  
  
 下列範例將傳回值指派給函式名稱 `myFunction` ，然後使用 `Exit Function` 陳述式來傳回。  
  
 [!code-vb[VbVbalrStatements#23](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_2.vb)]  
  
  `Exit Function` 和 `Return` 陳述式會造成立即結束 `Function` 程序。 任何數目的 `Exit Function` 和 `Return` 陳述式可以出現在任何地方程序，且您可以混合 `Exit Function` 和 `Return` 陳述式。  
  
 如果您使用 `Exit Function` 而不指派值給 `name`, ，程序會傳回在指定的資料類型的預設值 `returntype`。 如果 `returntype` 未指定，此程序傳回 `Nothing`, ，這是預設值為 `Object`。  
  
## <a name="calling-a-function"></a>呼叫函式  
 您呼叫 `Function` 程序所使用的程序名稱，後面接著在運算式中括號括住的引數清單。 只有當您不提供任何引數，您可以省略括號。 不過，您的程式碼的可讀性您加上括號。  
  
 您呼叫 `Function` 程序相同的方式，您呼叫任何程式庫函式如 `Sqrt`, ，`Cos`, ，或 `ChrW`。  
  
 您也可以呼叫函式使用 `Call` 關鍵字。 在此情況下，會忽略傳回值。 使用 `Call` 關鍵字時，不建議在大部分情況下。 如需詳細資訊，請參閱 [Call 陳述式](../../../visual-basic/language-reference/statements/call-statement.md)。  
  
 Visual Basic 有時會重新排列提高內部效率的算術運算式。 基於這個理由，您不應該使用 `Function` 函式相同的運算式中的變數值變更時的算術運算式中的程序。  
  
## <a name="async-functions"></a>非同步函式  
  *非同步* 功能可讓您叫用的非同步函式，而使用明確的回呼或手動將您的程式碼分散到多個函式或 lambda 運算式。  
  
 如果您將標示的函式 [非同步](../../../visual-basic/language-reference/modifiers/async.md) 修飾詞，您可以使用 [Await](../../../visual-basic/language-reference/operators/await-operator.md) 函式中的運算子。 當控制到達 `Await` 中的運算式 `Async` 函式，控制權會回到呼叫端，並且函式中的進度會暫停，直到等候的工作完成。 當工作完成時，可以繼續執行，函式中。  
  
> [!NOTE]
>   `Async` 程序會傳回給呼叫者，可能會在遇到尚未完成，第一個等候的物件或是到達結尾 `Async` 程序中，何者先發生。  
  
  `Async` 函式的傳回類型可以是 <xref:System.Threading.Tasks.Task%601> 或 <xref:System.Threading.Tasks.Task>。 舉例來說， `Async` 函式的傳回類型為 <xref:System.Threading.Tasks.Task%601> 底下提供。  
  
  `Async` 函式不可以宣告任何 [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) 參數。  
  
 A [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md) 也可以使用標記 `Async` 修飾詞。 這主要用於事件處理常式，無法傳回值的位置。  `Async``Sub` 無法等候程序，和呼叫端的 `Async``Sub` 程序無法攔截例外狀況擲回的 `Sub` 程序。  
  
 如需詳細資訊 `Async` 函式，請參閱 [使用 Async 和 Await 進行非同步程式設計](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md), ，[非同步程式中的控制流程](../Topic/Control%20Flow%20in%20Async%20Programs%20\(C%23%20and%20Visual%20Basic\).md), ，和 [非同步傳回型別](../Topic/Async%20Return%20Types%20\(C%23%20and%20Visual%20Basic\).md)。  
  
## <a name="iterator-functions"></a>迭代器函式  
  *迭代器* 函式集合，例如清單或陣列上執行自訂的反覆項目。 Iterator 函式會使用 [產生](../../../visual-basic/language-reference/statements/yield-statement.md) 陳述式來傳回一個元素一次。 當 [產生](../../../visual-basic/language-reference/statements/yield-statement.md) 陳述式為止，程式碼中的目前位置會記住。 已重新開始執行從該位置下一次呼叫 iterator 函式。  
  
 從用戶端程式碼呼叫迭代器使用 [每個...下一步](../../../visual-basic/language-reference/statements/for-each-next-statement.md) 陳述式。  
  
 Iterator 函式的傳回型別可以是 <xref:System.Collections.IEnumerable>, ，<xref:System.Collections.Generic.IEnumerable%601>, ，<xref:System.Collections.IEnumerator>, ，或 <xref:System.Collections.Generic.IEnumerator%601>。  
  
 如需詳細資訊，請參閱 [Iterator](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md)。  
  
## <a name="example"></a>範例  
 下列範例會使用 `Function` 陳述式來宣告名稱、 參數和程式碼，構成的主體 `Function` 程序。  `ParamArray` 修飾詞會啟用要接受可變數目的引數的函式。  
  
 [!code-vb[VbVbalrStatements#25](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_3.vb)]  
  
## <a name="example"></a>範例  
 下列範例會叫用前面範例中宣告的函式。  
  
 [!code-vb[VbVbalrStatements#26](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_4.vb)]  
  
## <a name="example"></a>範例  
 在下列範例中， `DelayAsync` 是 `Async``Function` 具有傳回類型為 <xref:System.Threading.Tasks.Task%601>。 `DelayAsync` 具有傳回整數的 `Return` 陳述式。 因此函式宣告的 `DelayAsync` 必須要有的傳回型別 `Task(Of Integer)`。 因為傳回型別是 `Task(Of Integer)`, ，評估 `Await` 中的運算式 `DoSomethingAsync` 會產生一個整數。 此陳述式所示︰ `Dim result As Integer = Await delayTask`。  
  
  `startButton_Click` 程序是範例 `Async Sub` 程序。 因為 `DoSomethingAsync` 是 `Async` 函式，呼叫工作 `DoSomethingAsync` 必須等候，如下列陳述式所示︰ `Await DoSomethingAsync()`。  `startButton_Click``Sub` 程序都必須定義 `Async` 修飾詞因為它有 `Await` 運算式。  
  
 [!code-vb[csAsyncMethod#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/function-statement_5.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Function 程序](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [參數清單](../../../visual-basic/language-reference/statements/parameter-list.md)   
 [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)   
 [Call 陳述式](../../../visual-basic/language-reference/statements/call-statement.md)   
 [的](../../../visual-basic/language-reference/statements/of-clause.md)   
 [參數陣列](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)   
 [如何︰ 使用泛型類別](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)   
 [疑難排解程序](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)   
 [Lambda 運算式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)   
 [函式運算式](../../../visual-basic/language-reference/operators/function-expression.md)