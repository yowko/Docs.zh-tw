---
title: Long
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "49"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 238f64001b097b86306e0ed9630bd5df2e6a189f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="option-strict-statement"></a>Long
不允許晚期繫結，且允許隱含型別，結果中，會限制為只有擴展轉換的隱含資料類型轉換`Object`型別。  
  
## <a name="syntax"></a>語法  
  
```  
Option Strict { On | Off }  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`On`|選擇項。 可讓`Option Strict`檢查。|  
|`Off`|選擇項。 停用`Option Strict`檢查。|  
  
## <a name="remarks"></a>備註  
 當`Option Strict On`或`Option Strict`會出現在檔案中，在下列情況會導致編譯時間錯誤：  
  
-   隱含的縮小轉換  
  
-   晚期繫結  
  
-   隱含類型導致`Object`類型  
  
> [!NOTE]
>  您可以設定的警告組態[編譯的頁面上，專案設計工具 (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)，有三個設定對應至三個條件會造成編譯時期錯誤。 如需如何使用這些設定的資訊，請參閱[在 IDE 中設定警告組態](../../../visual-basic/language-reference/statements/option-strict-statement.md#conditions)本主題稍後。  
  
 `Option Strict Off`陳述式，則會關閉錯誤和警告檢查所有的三個條件，即使開啟這些錯誤或警告，指定相關聯的 IDE 設定。 `Option Strict On`陳述式會開啟錯誤和警告檢查所有的三個條件，即使相關聯的 IDE 設定指定要關閉這些錯誤或警告。  
  
 如果單獨使用，`Option Strict`陳述式必須出現在檔案中任何其他程式碼陳述式之前。  
  
 當您將`Option Strict`至`On`，Visual Basic 會檢查所有的程式設計項目會指定資料類型。 資料類型可以明確地指定，或使用區域類型推斷來指定。 指定資料類型的所有程式設計項目建議使用，原因如下：  
  
-   它可讓您的變數和參數的 IntelliSense 支援。 這可讓您查看其屬性和其他成員，當您輸入程式碼。  
  
-   它可讓編譯器執行類型檢查。 類型檢查可協助您尋找可以在執行階段失敗，因為型別轉換錯誤的陳述式。 它也可以識別不支援這些方法的物件上方法的呼叫。  
  
-   它能加速程式碼執行。 其中一個原因是，如果您未指定資料類型的程式設計項目，Visual Basic 編譯器將其指派`Object`型別。 可能需要編譯的程式碼之間來回轉換`Object`和其他資料類型，這會降低效能。  
  
## <a name="implicit-narrowing-conversion-errors"></a>隱含的縮小轉換錯誤  
 是縮小轉換的隱含資料類型轉換時，就會發生隱含的縮小轉換錯誤。  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]可以將許多資料類型轉換成其他資料型別。 一種資料類型的值轉換為具有較少的有效位數或容量較小的資料類型時，就可能發生資料遺失。 如果這類縮小轉換會失敗，就會發生執行階段錯誤。 `Option Strict`可確保這些縮小轉換的編譯時期通知，以便加以避免。 如需詳細資訊，請參閱[隱含和明確轉換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)和[擴大和縮小轉換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。  
  
 可能會導致錯誤的轉換會在運算式中包含所發生的隱含轉換。 如需詳細資訊，請參閱下列主題：  
  
-   [+ 運算子](../../../visual-basic/language-reference/operators/addition-operator.md)  
  
-   [+= 運算子](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
  
-   [\ 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
  
-   [/ = 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
  
-   [Char 資料類型](../../../visual-basic/language-reference/data-types/char-data-type.md)  
  
 當您使用串連字串[& 運算子](../../../visual-basic/language-reference/operators/concatenation-operator.md)，所有轉換的字串會被都視為擴展。 讓這些轉換不會產生隱含縮小轉換錯誤，即使`Option Strict`上。  
  
 如果有縮小轉換，當您呼叫具有對應的參數不同的資料類型的引數的方法時，導致編譯時間錯誤`Option Strict`上。 您可以使用擴展轉換或明確轉換，以避免產生編譯時期錯誤。  
  
 隱含的縮小轉換錯誤會在編譯時期轉換中的項目隱藏`For Each…Next`迴圈控制變數的集合。 發生這種情況即使`Option Strict`上。 如需詳細資訊，請參閱 「 縮小轉換 」 一節[每個...下一個陳述式](../../../visual-basic/language-reference/statements/for-each-next-statement.md)。  
  
## <a name="late-binding-errors"></a>晚期繫結錯誤  
 物件晚期繫結指派至屬性或方法宣告為類型的變數時`Object`。 如需詳細資訊，請參閱[早期和晚期繫結](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)。  
  
## <a name="implicit-object-type-errors"></a>隱含的物件類型錯誤  
 隱含的物件類型錯誤發生時適當的類型不能是推斷為宣告的變數，因此一種`Object`會推斷而來。 這主要是當您使用時發生`Dim`陳述式來宣告變數，而不使用`As`子句，和`Option Infer`已關閉。 如需詳細資訊，請參閱[Option Infer 陳述式](../../../visual-basic/language-reference/statements/option-infer-statement.md)和[Visual Basic 語言規格](../../../visual-basic/reference/language-specification/index.md)。  
  
 方法參數`As`子句是選擇性的如果`Option Strict`已關閉。 不過，如果任何一個參數使用`As`子句，它們都必須使用它。 如果`Option Strict`已開啟，`As`子句是必要的每個參數定義。  
  
 如果您宣告變數，而不使用`As`子句並將它設定為`Nothing`，變數會有一種`Object`。 任何編譯時間錯誤，就會發生這種情況下時`Option Strict`上和`Option Infer`上。 舉例來說，這是`Dim something = Nothing`。  
  
### <a name="default-data-types-and-values"></a>預設資料類型和值  
 下表描述的指定資料類型和初始設定式中的各種組合結果[Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)。  
  
|指定了資料類型？|指定了初始設定式？|範例|結果|  
|---|---|---|---|  
|否|否|`Dim qty`|如果 `Option Strict` 已關閉 (預設值)，此變數會設定為 `Nothing`。<br /><br /> 如果 `Option Strict` 已開啟，就會發生編譯時期錯誤。|  
|否|是|`Dim qty = 5`|如果 `Option Infer` 已開啟 (預設值)，此變數會採用初始設定式的資料類型。 請參閱[區域類型推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。<br /><br /> 如果 `Option Infer` 已關閉，且 `Option Strict` 也已關閉，此變數會採用 `Object` 的資料類型。<br /><br /> 如果 `Option Infer` 已關閉，但是 `Option Strict` 已開啟，就會發生編譯時期錯誤。|  
|是|否|`Dim qty As Integer`|變數會初始化為資料類型的預設值。 如需詳細資訊，請參閱[Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)。|  
|是|是|`Dim qty  As Integer = 5`|如果初始設定式的資料類型無法轉換成指定的資料類型，就會發生編譯時間錯誤。|  
  
## <a name="when-an-option-strict-statement-is-not-present"></a>Option Strict 陳述式時不存在  
 如果不包含原始碼`Option Strict`陳述式，**選項嚴格**上設定[編譯的頁面上，專案設計工具 (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)用。 **編譯網頁**已設定，可提供其他控制產生錯誤的狀況。  
  
 如果您使用命令列編譯器時，您可以使用[/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)編譯器選項以指定的設定`Option Strict`。  
  
### <a name="to-set-option-strict-in-the-ide"></a>若要在 IDE 中設定 Option Strict  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
1.  在方案總管中選取專案。 在 [專案] 功能表上，按一下 [屬性]。 如需詳細資訊，請參閱[專案設計工具簡介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)。  
  
2.  在**編譯**索引標籤上，設定中的值**Option Strict**方塊。  
  
###  <a name="conditions"></a>若要在 IDE 中設定警告組態  
 當您使用[編譯的頁面上，專案設計工具 (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)而不是`Option Strict`陳述式中，您有其他控制產生錯誤的狀況。 **警告組態**區段**編譯網頁**的設定會對應至三個條件會造成編譯時間錯誤時`Option Strict`上。 以下是這些設定：  
  
-   **隱含轉換**  
  
-   **晚期繫結，執行階段時呼叫可能失敗**  
  
-   **隱含類型。假設是 object**  
  
 當您將**Option Strict**至**上**，這三個這些警告的組態設定會設定為**錯誤**。 當您將**Option Strict**至**關閉**，所有三項設定會設定為**無**。  
  
 您可以個別變更每個警告的組態設定為**無**，**警告**，或**錯誤**。 如果所有三個警告的組態設定會設定為**錯誤**，`On`會出現在`Option strict`方塊。 如果這三個設定為**無**，`Off`出現在此方塊。 這些設定，任何其他組合**（自訂）**隨即出現。  
  
### <a name="to-set-the-option-strict-default-setting-for-new-projects"></a>若要設定 Option Strict 預設設定為新專案  
 當您建立專案， **Option Strict**上設定**編譯** 索引標籤設為**Option Strict**中設定**選項**對話方塊。  
  
 若要設定`Option Strict`在此對話方塊，請在**工具**功能表上，按一下**選項**。 在**選項**對話方塊方塊中，展開 **專案和方案**，然後按一下  **VB 預設值**。 中的初始預設設定**VB 預設值**是`Off`。  
  
### <a name="to-set-option-strict-on-the-command-line"></a>若要在命令列上設定 Option Strict  
 包含[/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)編譯器選項在**vbc**命令。  
  
## <a name="example"></a>範例  
 下列範例示範隱含類型轉換縮小轉換，所造成的編譯時間錯誤。 這類錯誤對應於**隱含轉換**條件上**編譯網頁**。  
  
 [!code-vb[VbVbalrStatements#161](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_1.vb)]  
  
## <a name="example"></a>範例  
 下列範例會示範晚期繫結所造成的編譯時間錯誤。 這類錯誤對應於**最遲繫結，在執行階段無法呼叫**條件上**編譯網頁**。  
  
 [!code-vb[VbVbalrStatements#162](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_2.vb)]  
  
## <a name="example"></a>範例  
 下列範例示範具有隱含的類型宣告的變數所造成的錯誤`Object`。 這類錯誤對應於**隱含的類型; 假設是 object**條件上**編譯網頁**。  
  
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
