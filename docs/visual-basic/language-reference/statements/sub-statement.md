---
title: Sub 陳述式 (Visual Basic)
ms.date: 05/12/2018
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
ms.openlocfilehash: e7015474a0617b76ca537d2e84e8d7bfc72b6e12
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54737659"
---
# <a name="sub-statement-visual-basic"></a>Sub 陳述式 (Visual Basic)
宣告名稱、 參數和定義的程式碼`Sub`程序。  
  
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
  
     選擇性。 請參閱[屬性清單](attribute-list.md)。  
  
-   `Partial`  
  
     選擇性。 表示定義部分方法。 請參閱[部分方法](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)。  
  
-   `accessmodifier`  
  
     選擇性。 可以是下列其中一項：  
  
    -   [Public](../modifiers/public.md)  
  
    -   [Protected](../modifiers/protected.md)  
  
    -   [Friend](../modifiers/friend.md)  
  
    -   [Private](../modifiers/private.md)  
  
    - [Protected Friend](../../language-reference/modifiers/protected-friend.md)

    - [Private Protected](../../language-reference/modifiers/private-protected.md)
  
     請參閱 [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
-   `proceduremodifiers`  
  
     選擇性。 可以是下列其中一項：  
  
    -   [多載](../modifiers/overloads.md)  
  
    -   [Overrides](../modifiers/overrides.md)  
  
    -   [Overridable](../modifiers/overridable.md)  
  
    -   [NotOverridable](../modifiers/notoverridable.md)  
  
    -   [MustOverride](../modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     選擇性。 請參閱[共用](../modifiers/shared.md)。  
  
-   `Shadows`  
  
     選擇性。 請參閱[Shadows](../modifiers/shadows.md)。  
  
-   `Async`  
  
     選擇性。 請參閱[非同步](../modifiers/async.md)。  
  
-   `name`  
  
     必要項。 程序的名稱。 請參閱 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。 若要建立類別的建構函式程序，將名稱設定`Sub`程序`New`關鍵字。 如需詳細資訊，請參閱[物件存留期：如何建立和終結物件](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)。  
  
-   `typeparamlist`  
  
     選擇性。 泛型程序中的型別參數的清單。 請參閱[輸入清單](type-list.md)。  
  
-   `parameterlist`  
  
     選擇性。 本機變數的名稱，表示此程序的參數清單。 請參閱[參數清單](parameter-list.md)。  
  
-   `Implements`  
  
     選擇性。 表示此程序會實作一或多個`Sub`程序，每一個都在此程序包含類別或結構所實作的介面中定義。 請參閱[實作陳述式](implements-statement.md)。  
  
-   `implementslist`  
  
     如果使用 `Implements`，則為必要項。 實作之 `Sub` 程序的清單。  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     每個 `implementedprocedure` 都具有下列語法和組件：  
  
     `interface.definedname`  
  
    |組件|描述|  
    |---|---|  
    |`interface`|必要項。 這個程序所實作的介面名稱的包含類別或結構。|  
    |`definedname`|必要項。 名稱，據以在 `interface` 中定義程序。|  
  
-   `Handles`  
  
     選擇性。 表示此程序可以處理一或多個特定的事件。 請參閱[處理](handles-clause.md)。  
  
-   `eventlist`  
  
     如果使用 `Handles`，則為必要項。 此程序處理的事件清單。  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     每個 `eventspecifier` 都具有下列語法和組件：  
  
     `eventvariable.event`  
  
    |組件|描述|  
    |---|---|  
    |`eventvariable`|必要項。 宣告的類別或結構，會引發事件的資料類型的物件變數。|  
    |`event`|必要項。 此程序處理事件的名稱。|  
  
-   `statements`  
  
     選擇性。 若要執行此程序內的陳述式區塊。  
  
-   `End Sub`  
  
     結束這個程序的定義。  
  
## <a name="remarks"></a>備註  
 所有的可執行程式碼必須在程序。 使用`Sub`程序，當您不想要將值傳回給呼叫程式碼。 使用`Function`程序，當您想要傳回的值。  
  
## <a name="defining-a-sub-procedure"></a>定義 Sub 程序  
 您可以定義`Sub`只能在模組層級的程序。 Sub 程序的宣告內容，因此，必須類別、 結構、 模組或介面，且不能是原始程式檔、 命名空間、 程序或區塊。 如需詳細資訊，請參閱[宣告內容和預設存取層級](declaration-contexts-and-default-access-levels.md)。  
  
 `Sub` 程序預設為公用存取。 您可以使用存取修飾詞，以調整其存取層級。  
  
 如果程序會使用`Implements`關鍵字、 包含類別或結構必須`Implements`緊接在後面的陳述式及其`Class`或`Structure`陳述式。 `Implements`陳述式必須包含在指定的每個介面`implementslist`。 不過，由此介面定義的名稱`Sub`(在`definedname`) 不需符合此程序名稱 (在`name`)。  
  
## <a name="returning-from-a-sub-procedure"></a>傳回從 Sub 程序  
 當`Sub`程序傳回給呼叫程式碼，執行會繼續進行呼叫它的陳述式之後的陳述式。  
  
 下列範例顯示傳回`Sub`程序。  
  
```vb  
Sub mySub(ByVal q As String)  
    Return  
End Sub   
```  
  
 `Exit Sub`並`Return`陳述式會導致立即結束`Sub`程序。 任意數目的`Exit Sub`並`Return`陳述式可以出現在任何位置的程序中，您可以混合`Exit Sub`和`Return`陳述式。  
  
## <a name="calling-a-sub-procedure"></a>呼叫子函數程序  
 您呼叫`Sub`陳述式中使用的程序名稱，並接著遵循和它的引數清單括號括住該名稱的程序。 只有當您未提供任何引數，您可以省略括號。 不過，您的程式碼是如果您加上括號的更容易閱讀。  
  
 A`Sub`程序和`Function`程序可以有參數，並且執行一系列的陳述式。 不過，`Function`程序傳回的值，以及`Sub`程序不會。 因此，您無法使用`Sub`在運算式中的程序。  
  
 您可以使用`Call`關鍵字，當您呼叫`Sub`程序，但該關鍵字，不建議用於大部分用途。 如需詳細資訊，請參閱 < [Call 陳述式](call-statement.md)。  
  
 Visual Basic 中有時重新排列算術運算式，以提高內部的效率。 基於這個理由，如果您的引數清單包含運算式呼叫其他程序，您不應假設特定的順序，將會呼叫這些運算式。  
  
## <a name="async-sub-procedures"></a>Async Sub 程序  
 使用非同步功能，可以叫用非同步的函數，而不使用明確回呼或手動將您的程式碼分散到多個函式或 lambda 運算式。  
  
 如果您將標記的程序[非同步](../modifiers/async.md)修飾詞，您可以使用[Await](../../../visual-basic/language-reference/operators/await-operator.md)程序中的運算子。 當控制項到達`Await`中的運算式`Async`程序中，控制項會傳回給呼叫者，並在程序的進度會暫停，直到等候的工作完成。 工作完成時，可以在程序繼續執行。  
  
> [!NOTE]
>  `Async`程序傳回給呼叫端在遇到可能是第一次的等候的物件尚未完成時或結尾`Async`達到程序時，何者先發生。  
  
 您也可以將標記[Function 陳述式](function-statement.md)使用`Async`修飾詞。 `Async`函式可以有傳回型別<xref:System.Threading.Tasks.Task%601>或<xref:System.Threading.Tasks.Task>。 範例稍後在本主題說明`Async`函式具有傳回型別<xref:System.Threading.Tasks.Task%601>。  
  
 `Async` `Sub` 程序主要用於事件處理常式，不會傳回的值。 `Async` `Sub`無法等候程序，和呼叫端`Async``Sub`程序無法攔截例外狀況，`Sub`程序會擲回。  
  
 `Async`程序不可以宣告任何[ByRef](../modifiers/byref.md)參數。  
  
 如需詳細資訊`Async`程序，請參閱[使用 Async 和 Await 進行非同步程式設計](../../../visual-basic/programming-guide/concepts/async/index.md)，[非同步程式中的控制流程](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)，和[非同步傳回型別](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="example"></a>範例  
 下列範例會使用`Sub`陳述式來定義名稱、 參數和構成的主體的程式碼`Sub`程序。  
  
 [!code-vb[VbVbalrStatements#58](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/sub-statement_1.vb)]  
  
## <a name="example"></a>範例  
 在下列範例中，`DelayAsync`已`Async``Function`具有傳回型別<xref:System.Threading.Tasks.Task%601>。 `DelayAsync` 具有傳回整數的 `Return` 陳述式。 因此，函式的宣告`DelayAsync`必須具有傳回型別`Task(Of Integer)`。 因為傳回類型是`Task(Of Integer)`，評估`Await`中的運算式`DoSomethingAsync`會產生整數，下列陳述式所示： `Dim result As Integer = Await delayTask`。  
  
 `startButton_Click`程序是範例`Async Sub`程序。 因為`DoSomethingAsync`已`Async`函式，呼叫工作`DoSomethingAsync`必須等候，下列陳述式所示： `Await DoSomethingAsync()`。 `startButton_Click` `Sub`程序都必須定義`Async`修飾詞因為它有`Await`運算式。  
  
 [!code-vb[csAsyncMethod#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/sub-statement_2.vb)]  
  
## <a name="see-also"></a>另請參閱
- [Implements 陳述式](implements-statement.md)
- [Function 陳述式](function-statement.md)
- [參數清單](parameter-list.md)
- [Dim 陳述式](dim-statement.md)
- [Call 陳述式](call-statement.md)
- [Of](of-clause.md)
- [參數陣列](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
- [如何：使用泛型類別](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [程序的疑難排解](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [部分方法](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
