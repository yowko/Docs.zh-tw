---
title: Option Strict 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Strict
- vb.OptionStrict
helpviewer_keywords:
- Strict keyword [Visual Basic]
- Option Strict statement [Visual Basic]
- conversions [Visual Basic], implicit
- late binding [Visual Basic]
- implicit conversions [Visual Basic]
ms.assetid: 5883e0c1-a920-4274-8e46-b0ff047eaee5
ms.openlocfilehash: ac8f6fa2ebd2f8d846c3662184c83a83477e2311
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43805282"
---
# <a name="option-strict-statement"></a>Long
會限制僅限於擴展轉換的隱含資料類型轉換，不允許晚期繫結，不允許隱含型別，會導致`Object`型別。  
  
## <a name="syntax"></a>語法  
  
```  
Option Strict { On | Off }  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`On`|選擇性。 可讓`Option Strict`檢查。|  
|`Off`|選擇性。 停用`Option Strict`檢查。|  
  
## <a name="remarks"></a>備註  
 當`Option Strict On`或`Option Strict`會出現在檔案中，在下列情況會造成編譯時期錯誤：  
  
-   隱含縮小轉換  
  
-   晚期繫結  
  
-   導致 `Object` 類型的隱含類型化  
  
> [!NOTE]
>  您可以設定的警告組態[編譯的 Page，Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)，有三個設定對應至三個條件會造成編譯時期錯誤。 如需有關如何使用這些設定的資訊，請參閱[在 IDE 中設定警告組態](../../../visual-basic/language-reference/statements/option-strict-statement.md#conditions)本主題稍後的。  
  
 `Option Strict Off`陳述式會關閉錯誤和警告檢查所有的三個條件，即使指定了相關聯的 IDE 設定，例如： 若要開啟這些錯誤或警告。 `Option Strict On`陳述式會開啟錯誤和警告檢查所有的三個條件，即使指定了相關聯的 IDE 設定，例如： 若要關閉這些錯誤或警告。  
  
 如果使用，`Option Strict`陳述式必須出現在檔案中任何其他程式碼陳述式之前。  
  
 當您設定`Option Strict`至`On`，Visual Basic 會檢查所有的程式設計項目指定的資料類型。 資料類型可以明確地指定，或使用區域類型推斷來指定。 指定資料類型的所有程式設計項目建議，原因如下：  
  
-   它可讓您的變數和參數的 IntelliSense 支援。 這可讓您查看其屬性與其他成員，當您輸入程式碼。  
  
-   它可讓編譯器執行類型檢查。 類型檢查可協助您找出可以在執行階段失敗，因為型別轉換錯誤的陳述式。 它也會識別不支援這些方法的物件上的方法呼叫。  
  
-   它會加快執行的程式碼。 其原因之一是，如果您未指定資料類型的程式設計項目，則 Visual Basic 編譯器將其指派`Object`型別。 已編譯程式碼可能必須將之間來回轉換`Object`及其他資料類型，會降低效能。  
  
## <a name="implicit-narrowing-conversion-errors"></a>隱含的縮小轉換錯誤  
 隱含資料類型轉換是縮小轉換時，會發生隱含縮小轉換錯誤。  
  
 Visual Basic 可以將許多資料類型轉換成其他資料類型。 一種資料類型的值轉換為具有較少有效位數或容量較小的資料類型時，就可能發生資料遺失。 如果縮小轉換失敗，就會發生執行階段錯誤。 `Option Strict` 可確保這些縮小轉換的編譯時期通知，好讓您可以避免它們。 如需詳細資訊，請參閱 <<c0> [ 隱含和明確轉換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)並[Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。  
  
 可能會導致錯誤的轉換會在運算式中包含所發生的隱含轉換。 如需詳細資訊，請參閱下列主題：  
  
-   [+ 運算子](../../../visual-basic/language-reference/operators/addition-operator.md)  
  
-   [+= 運算子](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
  
-   [\ 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
  
-   [/ = 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
  
-   [Char 資料類型](../../../visual-basic/language-reference/data-types/char-data-type.md)  
  
 當您使用，會在串連字串時[& 運算子](../../../visual-basic/language-reference/operators/concatenation-operator.md)，所有轉換成字串會被都視為擴展。 因此這些轉換不會產生隱含的縮小轉換錯誤，即使`Option Strict`上。  
  
 如果縮小轉換，當您呼叫具有不同的對應參數的資料類型的引數的方法時，會造成編譯時期錯誤`Option Strict`上。 您可以使用擴展轉換或明確的轉換，以避免產生編譯時期錯誤。  
  
 隱含的縮小轉換錯誤會在編譯時期轉換中的項目隱藏`For Each…Next`迴圈控制變數的集合。 發生這種情況即使`Option Strict`上。 如需詳細資訊，請參閱 「 縮小轉換 」 一節[每個...下一個陳述式](../../../visual-basic/language-reference/statements/for-each-next-statement.md)。  
  
## <a name="late-binding-errors"></a>晚期繫結錯誤  
 當物件指派給宣告為 `Object` 類型之變數的屬性或方法時，該物件即為「晚期繫結」。 如需詳細資訊，請參閱 <<c0> [ 早期和晚期繫結](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)。  
  
## <a name="implicit-object-type-errors"></a>隱含物件類型錯誤  
 無法推斷宣告變數的適當類型時，會發生隱含物件類型錯誤，因此推斷類型為 `Object`。 這主要是發生在您使用 `Dim` 陳述式宣告變數而未使用 `As` 子句，並且 `Option Infer` 已設為關閉的時候。 如需詳細資訊，請參閱 < [Option Infer 陳述式](../../../visual-basic/language-reference/statements/option-infer-statement.md)並[Visual Basic 語言規格](../../../visual-basic/reference/language-specification/index.md)。  
  
 方法參數`As`是選擇性的子句如果`Option Strict`已關閉。 不過，如果任何一個參數使用`As`子句，它們全都必須使用它。 如果`Option Strict`已開啟，`As`子句是必要的每個參數定義。  
  
 如果您宣告變數時不用`As`子句並將它設定為`Nothing`，該變數具有一種`Object`。 沒有編譯時期錯誤，就會發生這種情況下當`Option Strict`位於和`Option Infer`上。 這個範例是`Dim something = Nothing`。  
  
### <a name="default-data-types-and-values"></a>預設資料類型和值  
 下表描述的指定資料型別和初始設定式中的各種組合結果[Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)。  
  
|指定了資料類型？|指定了初始設定式？|範例|結果|  
|---|---|---|---|  
|否|否|`Dim qty`|如果 `Option Strict` 已關閉 (預設值)，此變數會設定為 `Nothing`。<br /><br /> 如果 `Option Strict` 已開啟，就會發生編譯時期錯誤。|  
|否|是|`Dim qty = 5`|如果 `Option Infer` 已開啟 (預設值)，此變數會採用初始設定式的資料類型。 請參閱[區域型別推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。<br /><br /> 如果 `Option Infer` 已關閉，且 `Option Strict` 也已關閉，此變數會採用 `Object` 的資料類型。<br /><br /> 如果 `Option Infer` 已關閉，但是 `Option Strict` 已開啟，就會發生編譯時期錯誤。|  
|是|否|`Dim qty As Integer`|變數會初始化為資料類型的預設值。 如需詳細資訊，請參閱 < [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)。|  
|是|是|`Dim qty  As Integer = 5`|如果初始設定式的資料類型無法轉換成指定的資料類型，就會發生編譯時間錯誤。|  
  
## <a name="when-an-option-strict-statement-is-not-present"></a>Option Strict 陳述式時不存在  
 如果原始程式碼不包含`Option Strict`陳述式中， **Option strict**上設定[編譯的 Page，Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)用。 **編譯頁面**都有提供產生錯誤條件的額外控制的設定。  
  
 如果您使用命令列編譯器，您可以使用[/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)編譯器選項以指定的設定`Option Strict`。  
  
### <a name="to-set-option-strict-in-the-ide"></a>若要設定在 IDE 中的 Option Strict  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
1.  在方案總管中選取專案。 在 [專案] 功能表上，按一下 [屬性]。  
  
2.  在 [**編譯**索引標籤上，在設定的值**Option Strict** ] 方塊中。  
  
###  <a name="conditions"></a> 在 IDE 中設定警告組態  
 當您使用[編譯的 Page，Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)而不是`Option Strict`陳述式中，您可以額外控制產生錯誤的條件。 **警告組態**一節**編譯的頁面**已對應至三個條件會造成編譯時期錯誤設定時`Option Strict`上。 以下是這些設定：  
  
-   **隱含轉換**  
  
-   **晚期繫結，執行階段時呼叫可能失敗**  
  
-   **隱含類型，假設是 Object**  
  
 當您將 [Option Strict] 設定為 [On] 時，這三個警告組態設定都會設定為 [錯誤]。 當您將 [Option Strict] 設定為 [Off] 時，所有三個設定都會設定為 [無]。  
  
 您可以將每個警告組態個別變更為 [無]、[警告] 或 [錯誤]。 如果三個警告組態設定皆設為 [錯誤]，`On` 會出現在 `Option strict` 方塊中。 如果這三個都設定為 [無]，`Off` 會出現在此方塊中。 若為這些設定的其他任何組合，則會出現 [(自訂)]。  
  
### <a name="to-set-the-option-strict-default-setting-for-new-projects"></a>若要設定新專案的 Option Strict 預設設定  
 當您建立專案時， **Option Strict**上設定**編譯**索引標籤設定為**Option Strict**中設定**選項** 對話方塊。  
  
 若要設定`Option Strict`在這個對話方塊中，在**工具**功能表上，按一下**選項**。 在 [選項] 對話方塊中，展開 [專案和方案]，然後按一下 [VB 預設值]。 中的初始預設設定**VB 預設值**是`Off`。  
  
### <a name="to-set-option-strict-on-the-command-line"></a>若要設定 命令列上的 Option Strict  
 包含[/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)中的編譯器選項**vbc**命令。  
  
## <a name="example"></a>範例  
 下列範例示範隱含類型轉換縮小轉換，所造成的編譯時期錯誤。 這類錯誤對應到**隱含轉換**條件**編譯的頁面**。  
  
 [!code-vb[VbVbalrStatements#161](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_1.vb)]  
  
## <a name="example"></a>範例  
 下列範例會示範透過晚期繫結所造成的編譯時期錯誤。 這類錯誤對應到**Late 繫結，在執行階段無法呼叫**條件**編譯的頁面**。  
  
 [!code-vb[VbVbalrStatements#162](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_2.vb)]  
  
## <a name="example"></a>範例  
 下列範例示範宣告的隱含類型變數所造成的錯誤`Object`。 這類錯誤對應到**隱含型別，假設是 object**條件**編譯的頁面**。  
  
 [!code-vb[VbVbalrStatements#163](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_3.vb)]  
  
 [!code-vb[VbVbalrStatements#164](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_4.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [擴展和縮小轉換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [隱含和明確轉換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [專案設計工具、編譯頁面 (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)  
 [Option Explicit 陳述式](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [如何：存取物件的成員](../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)  
 [XML 中內嵌的運算式](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)  
 [寬鬆委派轉換](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)  
 [Office 方案中的晚期繫結](https://msdn.microsoft.com/library/3xxe951d)  
 [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [選項對話方塊、專案、Visual Basic 預設值](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
