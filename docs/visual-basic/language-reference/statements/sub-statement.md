---
title: Sub 陳述式 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Sub
helpviewer_keywords:
- Public keyword [Visual Basic], Sub statements
- procedures [Visual Basic], creating
- declaring procedures [Visual Basic], Sub statement
- arguments [Visual Basic], Sub procedures
- As keyword [Visual Basic], Sub statements
- Optional keyword [Visual Basic], Sub statements
- declarations [Visual Basic], procedures
- Sub keyword [Visual Basic]
- Handles keyword [Visual Basic], Sub statements
- Protected Friend keyword [Visual Basic]
- ParamArray keyword [Visual Basic], Sub statements
- Implements keyword [Visual Basic], Sub statements
- Sub statement [Visual Basic]
- subroutines
- ByRef keyword [Visual Basic], Sub statements
- Sub procedures [Visual Basic], Sub statement
- recursive procedures
- Private keyword [Visual Basic], Sub statements
- Friend keyword [Visual Basic], Sub statements
- Exit statement [Visual Basic], Sub statements
- procedures [Visual Basic], Sub
- End keyword [Visual Basic], Sub statements
- ByVal keyword [Visual Basic], Sub statements
- Visual Basic code, Sub procedures
ms.assetid: e347d700-d06c-405b-b302-e9b1edb57dfc
caps.latest.revision: 52
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0a2d0d5ffdca857a3a5ca58cd38b0930f254526f
ms.sourcegitcommit: 8ed4ebc15b5ef89d06a7507dc9d5e306e30accf7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2017
---
# <a name="sub-statement-visual-basic"></a>Sub 陳述式 (Visual Basic)
名稱、 參數和定義的程式碼會宣告`Sub`程序。  
  
## <a name="syntax"></a>語法  
  
```  
[ <attributelist> ] [ Partial ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async ]  
Sub name [ (Of typeparamlist) ] [ (parameterlist) ] [ Implements implementslist | Handles eventlist ]  
    [ statements ]  
    [ Exit Sub ]  
    [ statements ]  
End Sub  
```  
  
## <a name="parts"></a>組件  
  
-   `attributelist`  
  
     選擇項。 請參閱[屬性清單](attribute-list.md)。  
  
-   `Partial`  
  
     選擇項。 表示定義部分方法。 請參閱[部分方法](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)。  
  
-   `accessmodifier`  
  
     選擇項。 可以是下列其中一項：  
  
    -   [Public](../modifiers/public.md)  
  
    -   [Protected](../modifiers/protected.md)  
  
    -   [Friend](../modifiers/friend.md)  
  
    -   [Private](../modifiers/private.md)  
  
    -   `Protected Friend`  
  
     請參閱[存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
-   `proceduremodifiers`  
  
     選擇項。 可以是下列其中一項：  
  
    -   [多載](../modifiers/overloads.md)  
  
    -   [Overrides](../modifiers/overrides.md)  
  
    -   [Overridable](../modifiers/overridable.md)  
  
    -   [NotOverridable](../modifiers/notoverridable.md)  
  
    -   [MustOverride](../modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     選擇項。 請參閱[共用](../modifiers/shared.md)。  
  
-   `Shadows`  
  
     選擇項。 請參閱[陰影](../modifiers/shadows.md)。  
  
-   `Async`  
  
     選擇項。 請參閱[非同步](../modifiers/async.md)。  
  
-   `name`  
  
     必要項。 程序的名稱。 請參閱[宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。 若要建立之類別的建構函式程序，將名稱設定`Sub`程序`New`關鍵字。 如需詳細資訊，請參閱[物件存留期： 物件的建立和終結](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)。  
  
-   `typeparamlist`  
  
     選擇項。 泛型程序中的型別參數的清單。 請參閱[輸入清單](type-list.md)。  
  
-   `parameterlist`  
  
     選擇項。 本機變數的名稱，表示此程序的參數清單。 請參閱[參數清單](parameter-list.md)。  
  
-   `Implements`  
  
     選擇項。 表示此程序會實作一或多個`Sub`程序，每一個定義中包含這個程序的類別或結構所實作的介面。 請參閱[實作陳述式](implements-statement.md)。  
  
-   `implementslist`  
  
     如果使用 `Implements`，則為必要項。 實作之 `Sub` 程序的清單。  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     每個 `implementedprocedure` 都具有下列語法和組件：  
  
     `interface.definedname`  
  
    |組件|說明|  
    |---|---|  
    |`interface`|必要項。 這個程序所實作的介面名稱所含的類別或結構。|  
    |`definedname`|必要項。 名稱，據以在 `interface` 中定義程序。|  
  
-   `Handles`  
  
     選擇項。 指出此程序可以處理一或多個特定事件。 請參閱[處理](handles-clause.md)。  
  
-   `eventlist`  
  
     如果使用 `Handles`，則為必要項。 此程序處理的事件清單。  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     每個 `eventspecifier` 都具有下列語法和組件：  
  
     `eventvariable.event`  
  
    |組件|說明|  
    |---|---|  
    |`eventvariable`|必要項。 宣告的類別或結構，會引發事件的資料類型的物件變數。|  
    |`event`|必要項。 此程序處理事件的名稱。|  
  
-   `statements`  
  
     選擇項。 若要執行此程序內的陳述式區塊。  
  
-   `End Sub`  
  
     結束此程序的定義。  
  
## <a name="remarks"></a>備註  
 所有可執行程式碼必須是程序內。 使用`Sub`程序時您不想要將值傳回給呼叫程式碼。 使用`Function`程序，當您想要傳回的值。  
  
## <a name="defining-a-sub-procedure"></a>定義 Sub 程序  
 您可以定義`Sub`程序只能在模組層級。 Sub 程序的宣告內容，因此，必須在類別、 結構、 模組或介面，且不能在原始程式檔、 命名空間、 程序或區塊。 如需詳細資訊，請參閱[宣告內容和預設存取層級](declaration-contexts-and-default-access-levels.md)。  
  
 `Sub`程序預設為公用存取。 您可以使用存取修飾詞來調整其存取層級。  
  
 如果程序使用`Implements`關鍵字、 包含的類別或結構必須`Implements`緊接在後面的陳述式其`Class`或`Structure`陳述式。 `Implements`陳述式必須包含每個介面中指定`implementslist`。 不過，用介面會定義的名稱`Sub`(在`definedname`) 沒有符合此程序的名稱 (在`name`)。  
  
## <a name="returning-from-a-sub-procedure"></a>從 Sub 程序傳回  
 當`Sub`程序傳回呼叫程式碼，呼叫它的陳述式之後的陳述式繼續執行。  
  
 下列範例示範從傳回`Sub`程序。  
  
```vb  
Sub mySub(ByVal q As String)  
    Return  
End Sub   
```  
  
 `Exit Sub`和`Return`陳述式會導致立即結束`Sub`程序。 任何數目的`Exit Sub`和`Return`陳述式可以出現在任何地方程序，且您可以混合`Exit Sub`和`Return`陳述式。  
  
## <a name="calling-a-sub-procedure"></a>呼叫 Sub 程序  
 您呼叫`Sub`陳述式中使用的程序名稱，然後遵循與它的引數清單括號括住該名稱的程序。 只有當您並未提供任何引數，您可以省略括號。 不過，您的程式碼的可讀性您加上括號。  
  
 A`Sub`程序和`Function`程序可以有參數，並且執行一系列的陳述式。 不過，`Function`程序傳回的值，以及`Sub`程序不會。 因此，您無法使用`Sub`在運算式中的程序。  
  
 您可以使用`Call`關鍵字，當您呼叫`Sub`程序，但該關鍵字時，不建議用於大部分用途。 如需詳細資訊，請參閱[Call 陳述式](call-statement.md)。  
  
 Visual Basic 有時會重新排列算術運算式，以提高內部的效率。 基於這個原因，如果引數清單包含運算式呼叫其他程序，您不應該假設這些運算式，會以特定順序呼叫。  
  
## <a name="async-sub-procedures"></a>Async Sub 程序  
 使用 Async 功能，您可以不使用明確回呼或手動將您的程式碼分散到多個函式或 lambda 運算式呼叫的非同步函式。  
  
 如果您將標記的程序有[非同步](../modifiers/async.md)修飾詞，您可以使用[Await](../../../visual-basic/language-reference/operators/await-operator.md)程序中的運算子。 當控制項到達`Await`中的運算式`Async`程序中，控制項會傳回給呼叫者，並在程序的進度會暫停，直到等候的工作完成。 工作完成時，可以在程序繼續執行。  
  
> [!NOTE]
>  `Async`程序傳回給呼叫端時遇到的其中一個第一次的等候的物件尚未完成或結束`Async`達到程序時，何者先發生。  
  
 您也可以將標記[Function 陳述式](function-statement.md)與`Async`修飾詞。 `Async`函式可以有傳回類型為<xref:System.Threading.Tasks.Task%601>或<xref:System.Threading.Tasks.Task>。 範例稍後在本主題說明`Async`函式的傳回型別<xref:System.Threading.Tasks.Task%601>。  
  
 `Async``Sub`程序主要用於事件處理常式，不會傳回的值。 `Async``Sub`無法等候程序，和呼叫端的`Async``Sub`程序無法攔截例外狀況，`Sub`程序會擲回。  
  
 `Async`程序不可以宣告任何[ByRef](../modifiers/byref.md)參數。  
  
 如需有關`Async`程序，請參閱[使用 Async 和 Await 進行非同步程式設計](../../../visual-basic/programming-guide/concepts/async/index.md)，[非同步程式中的控制流程](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)，和[非同步傳回型別](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="example"></a>範例  
 下列範例會使用`Sub`陳述式來定義名稱、 參數和形成主體的程式碼`Sub`程序。  
  
 [!code-vb[VbVbalrStatements#58](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/sub-statement_1.vb)]  
  
## <a name="example"></a>範例  
 在下列範例中，`DelayAsync`是`Async``Function`具有傳回類型為<xref:System.Threading.Tasks.Task%601>。 `DelayAsync` 具有傳回整數的 `Return` 陳述式。 因此，函式宣告的`DelayAsync`必須具有傳回類型為`Task(Of Integer)`。 因為傳回類型為`Task(Of Integer)`，評估`Await`中的運算式`DoSomethingAsync`產生整數，如下列陳述式所示： `Dim result As Integer = Await delayTask`。  
  
 `startButton_Click`程序是範例`Async Sub`程序。 因為`DoSomethingAsync`是`Async`函式，呼叫工作`DoSomethingAsync`必須等候，如下列陳述式所示： `Await DoSomethingAsync()`。 `startButton_Click``Sub`程序都必須定義`Async`修飾詞因為它有`Await`運算式。  
  
 [!code-vb[csAsyncMethod#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/sub-statement_2.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [Implements 陳述式](implements-statement.md)  
 [Function 陳述式](function-statement.md)  
 [參數清單](parameter-list.md)  
 [Dim 陳述式](dim-statement.md)  
 [Call 陳述式](call-statement.md)  
 [Of](of-clause.md)  
 [參數陣列](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)  
 [如何：使用泛型類別](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [程序的疑難排解](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)  
 [部分方法](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
