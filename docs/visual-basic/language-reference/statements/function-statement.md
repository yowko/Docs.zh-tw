---
title: "Function 陳述式 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Function
helpviewer_keywords:
- procedures [Visual Basic], creating
- Function procedures [Visual Basic], Function statement syntax
- functions [Visual Basic], function procedures
- ParamArray keyword [Visual Basic], Function statements
- Private keyword [Visual Basic], Function statements
- declarations [Visual Basic], procedures
- procedures [Visual Basic], declaration
- Public keyword [Visual Basic], in Function statement
- ByVal keyword [Visual Basic], Function statements
- procedures [Visual Basic], recursive
- Implements keyword [Visual Basic], Function statements
- procedures [Visual Basic], returning values
- Exit statement [Visual Basic], in Function procedures
- recursive procedures
- As keyword [Visual Basic], in Function statement
- Optional keyword [Visual Basic], Function statements
- Function statement [Visual Basic]
- Visual Basic code, Function procedures
- procedures [Visual Basic], function
- ByRef keyword [Visual Basic], Function statements
- Friend keyword [Visual Basic], Function statements
- End keyword [Visual Basic], Function statements
- Handles keyword [Visual Basic], Function statements
ms.assetid: a4497077-0f46-4ede-a27f-9e8670df52b9
caps.latest.revision: "62"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 52e9210f9e715b6055e6ed199ef1aa4b919c6dd6
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="function-statement-visual-basic"></a>Function 陳述式 (Visual Basic)
名稱、 參數和定義的程式碼會宣告`Function`程序。  
  
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
  
     選擇性。 請參閱[屬性清單](attribute-list.md)。  
  
-   `accessmodifier`  
  
     選擇性。 可以是下列其中一項：  
  
    -   [Public](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   `Protected Friend`  
  
     請參閱[存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
-   `proceduremodifiers`  
  
     選擇性。 可以是下列其中一項：  
  
    -   [多載](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
    -   [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)  
  
    -   [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)  
  
    -   [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
  
    -   [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     選擇性。 請參閱[共用](../../../visual-basic/language-reference/modifiers/shared.md)。  
  
-   `Shadows`  
  
     選擇性。 請參閱[陰影](../../../visual-basic/language-reference/modifiers/shadows.md)。  
  
-   `Async`  
  
     選擇性。 請參閱[非同步](../../../visual-basic/language-reference/modifiers/async.md)。  
  
-   `Iterator`  
  
     選擇性。 請參閱[迭代器](../../../visual-basic/language-reference/modifiers/iterator.md)。  
  
-   `name`  
  
     必要。 程序的名稱。 請參閱[宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。  
  
-   `typeparamlist`  
  
     選擇性。 泛型程序中的型別參數的清單。 請參閱[輸入清單](type-list.md)。  
  
-   `parameterlist`  
  
     選擇性。 本機變數的名稱，表示此程序的參數清單。 請參閱[參數清單](parameter-list.md)。  
  
-   `returntype`  
  
     若`Option Strict`是`On`。 這個程序所傳回之值的資料類型。  
  
-   `Implements`  
  
     選擇性。 表示此程序會實作一或多個`Function`程序，每一個定義中包含這個程序的類別或結構所實作的介面。 請參閱[實作陳述式](implements-statement.md)。  
  
-   `implementslist`  
  
     如果使用 `Implements`，則為必要項。 實作之 `Function` 程序的清單。  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     每個 `implementedprocedure` 都具有下列語法和組件：  
  
     `interface.definedname`  
  
    |組件|描述|  
    |---|---|  
    |`interface`|必要。 這個程序所實作的介面名稱所含的類別或結構。|  
    |`definedname`|必要。 名稱，據以在 `interface` 中定義程序。|  
  
-   `Handles`  
  
     選擇性。 指出此程序可以處理一或多個特定事件。 請參閱[處理](handles-clause.md)。  
  
-   `eventlist`  
  
     如果使用 `Handles`，則為必要項。 此程序處理的事件清單。  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     每個 `eventspecifier` 都具有下列語法和組件：  
  
     `eventvariable.event`  
  
    |組件|描述|  
    |---|---|  
    |`eventvariable`|必要。 宣告的類別或結構，會引發事件的資料類型的物件變數。|  
    |`event`|必要。 此程序處理事件的名稱。|  
  
-   `statements`  
  
     選擇性。 要執行此程序內的陳述式區塊。  
  
-   `End Function`  
  
     結束此程序的定義。  
  
## <a name="remarks"></a>備註  
 所有可執行程式碼必須是程序內。 每個程序中，依次是類別、 結構、 或包含的類別、 結構或模組指模組內宣告。  
  
 若要將值傳回給呼叫程式碼，使用`Function`程序; 否則，請使用`Sub`程序。  
  
## <a name="defining-a-function"></a>定義函式  
 您可以定義`Function`程序只能在模組層級。 因此，函式的宣告內容必須是類別、 結構、 模組或介面，而且不能在原始程式檔、 命名空間、 程序或區塊。 如需詳細資訊，請參閱[宣告內容和預設存取層級](declaration-contexts-and-default-access-levels.md)。  
  
 `Function`程序預設為公用存取。 您可以調整其存取層級，使用存取修飾詞。  
  
 A`Function`程序可以宣告此程序傳回值的資料類型。 您可以指定任何資料類型或列舉、 結構、 類別或介面的名稱。 如果您未指定`returntype`參數，此程序傳回`Object`。  
  
 如果此程序使用`Implements`關鍵字、 包含的類別或結構也必須`Implements`緊接在後面的陳述式其`Class`或`Structure`陳述式。 `Implements`陳述式必須包含每個介面中指定`implementslist`。 不過，用介面會定義的名稱`Function`(在`definedname`) 不需要符合此程序的名稱 (在`name`)。  
  
> [!NOTE]
>  您可以使用 lambda 運算式來定義函式運算式內嵌。 如需詳細資訊，請參閱[函式運算式](../../../visual-basic/language-reference/operators/function-expression.md)和[Lambda 運算式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。  
  
## <a name="returning-from-a-function"></a>傳回從函式  
 當`Function`程序傳回呼叫程式碼，執行會繼續進行之後呼叫程序的陳述式的陳述式。  
  
 若要從函式傳回值，您可以將值指派給函式名稱，或將它併入`Return`陳述式。  
  
 `Return`陳述式同時指派傳回值，並結束函式，如下列範例所示。  
  
 [!code-vb[VbVbalrStatements#24](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_1.vb)]  
  
 下列範例將傳回的值指派給函式名稱`myFunction`，然後使用`Exit Function`陳述式來傳回。  
  
 [!code-vb[VbVbalrStatements#23](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_2.vb)]  
  
 `Exit Function`和`Return`陳述式會導致立即結束`Function`程序。 任何數目的`Exit Function`和`Return`陳述式可以出現在任何地方程序，且您可以混合`Exit Function`和`Return`陳述式。  
  
 如果您使用`Exit Function`而不指派值給`name`，程序會傳回中所指定的資料類型的預設值`returntype`。 如果`returntype`未指定，此程序傳回`Nothing`，這是預設值`Object`。  
  
## <a name="calling-a-function"></a>呼叫函式  
 您呼叫`Function`使用程序名稱，後面接著以括號，在運算式中的引數清單的程序。 只有當您未提供任何引數，您可以省略括號。 不過，您的程式碼的可讀性您加上括號。  
  
 您呼叫`Function`程序相同的方式，您呼叫任何程式庫函式例如`Sqrt`， `Cos`，或`ChrW`。  
  
 您也可以呼叫函式使用`Call`關鍵字。 在此情況下，會忽略傳回值。 使用`Call`關鍵字時，不建議在大部分情況下。 如需詳細資訊，請參閱[Call 陳述式](call-statement.md)。  
  
 Visual Basic 有時會重新排列算術運算式，以提高內部的效率。 因此，您不應該使用`Function`函式相同的運算式中的變數值變更時的算術運算式中的程序。  
  
## <a name="async-functions"></a>非同步函式  
 *非同步*功能可讓您叫用的非同步函式，而不使用明確回呼或手動將您的程式碼分散到多個函式或 lambda 運算式。  
  
 如果您將標記的函式[非同步](../../../visual-basic/language-reference/modifiers/async.md)修飾詞，您可以使用[Await](../../../visual-basic/language-reference/operators/await-operator.md)函式中的運算子。 當控制項到達`Await`中的運算式`Async`函式，控制權回到呼叫端，和函式中的進度會暫停，直到等候的工作完成。 當工作完成時，可以繼續執行，函式中。  
  
> [!NOTE]
>  `Async`程序會傳回給呼叫者，可能會在遇到尚未完成，第一個等候的物件或是到達結尾`Async`程序中，何者先發生。  
  
 `Async`函式可以有傳回類型為<xref:System.Threading.Tasks.Task%601>或<xref:System.Threading.Tasks.Task>。 舉例來說，`Async`函式的傳回型別<xref:System.Threading.Tasks.Task%601>底下提供。  
  
 `Async`函式不可以宣告任何[ByRef](../../../visual-basic/language-reference/modifiers/byref.md)參數。  
  
 A [Sub 陳述式](sub-statement.md)也可以使用標記`Async`修飾詞。 這主要用於事件處理常式，不會傳回的值。 `Async``Sub`無法等候程序，和呼叫端的`Async``Sub`程序無法攔截所擲回的例外狀況`Sub`程序。  
  
 如需有關`Async`函式，請參閱[使用 Async 和 Await 進行非同步程式設計](../../../visual-basic/programming-guide/concepts/async/index.md)，[非同步程式中的控制流程](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)，和[非同步傳回型別](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="iterator-functions"></a>Iterator 函式  
 *迭代器*函式集合，例如清單或陣列上執行自訂反覆項目。 Iterator 函式會使用[產生](yield-statement.md)陳述式來一次傳回一個項目。 當[產生](yield-statement.md)到達陳述式時，會記住在程式碼中的目前位置。 下次呼叫迭代器函式時，便會從這個位置重新開始執行。  
  
 從用戶端程式碼呼叫迭代器使用[每個...下一步](for-each-next-statement.md)陳述式。  
  
 Iterator 函式的傳回型別可以是<xref:System.Collections.IEnumerable>， <xref:System.Collections.Generic.IEnumerable%601>， <xref:System.Collections.IEnumerator>，或<xref:System.Collections.Generic.IEnumerator%601>。  
  
 如需詳細資訊，請參閱[迭代器](../../programming-guide/concepts/iterators.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用`Function`陳述式來宣告名稱、 參數和形成主體的程式碼`Function`程序。 `ParamArray`修飾詞會啟用要接受可變數目的引數的函式。  
  
 [!code-vb[VbVbalrStatements#25](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_3.vb)]  
  
## <a name="example"></a>範例  
 下列範例會叫用前一個範例中宣告的函式。  
  
 [!code-vb[VbVbalrStatements#26](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_4.vb)]  
  
## <a name="example"></a>範例  
 在下列範例中，`DelayAsync`是`Async``Function`具有傳回類型為<xref:System.Threading.Tasks.Task%601>。 `DelayAsync` 具有傳回整數的 `Return` 陳述式。 因此函式宣告的`DelayAsync`必須有傳回類型為`Task(Of Integer)`。 因為傳回類型為`Task(Of Integer)`，評估`Await`中的運算式`DoSomethingAsync`會產生整數。 這示範於這個陳述式： `Dim result As Integer = Await delayTask`。  
  
 `startButton_Click`程序是範例`Async Sub`程序。 因為`DoSomethingAsync`是`Async`函式，呼叫工作`DoSomethingAsync`必須等候，如下列陳述式所示範： `Await DoSomethingAsync()`。 `startButton_Click``Sub`程序都必須定義`Async`修飾詞因為它有`Await`運算式。  
  
 [!code-vb[csAsyncMethod#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/function-statement_5.vb)]  
  
## <a name="see-also"></a>請參閱  
 [Sub 陳述式](sub-statement.md)  
 [函式程序](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)  
 [參數清單](parameter-list.md)  
 [Dim 陳述式](dim-statement.md)  
 [Call 陳述式](call-statement.md)  
 [Of](of-clause.md)  
 [參數陣列](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)  
 [如何：使用泛型類別](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [程序的疑難排解](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)  
 [Lambda 運算式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [函式運算式](../../../visual-basic/language-reference/operators/function-expression.md)
