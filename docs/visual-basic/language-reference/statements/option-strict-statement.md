---
title: "Option Strict 陳述式 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Strict
- vb.OptionStrict
dev_langs:
- VB
helpviewer_keywords:
- Strict keyword
- Option Strict statement
- conversions, implicit
- late binding
- implicit conversions
ms.assetid: 5883e0c1-a920-4274-8e46-b0ff047eaee5
caps.latest.revision: 49
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3bf0d4939f24c38392d7ca4764c41d12366067b5
ms.lasthandoff: 03/13/2017

---
# <a name="option-strict-statement"></a>Long
隱含資料型別將轉換限制為只有擴展轉換不允許晚期繫結，不允許隱含型別，而產生的`Object`型別。  
  
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
 當`Option Strict On`或`Option Strict`會出現在檔案中，在下列情況會造成編譯時期錯誤︰  
  
-   隱含的縮小轉換  
  
-   晚期繫結  
  
-   隱含型別，而產生的`Object`類型  
  
> [!NOTE]
>  您可以設定的警告組態中[編譯的頁面上，專案設計工具 (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic)，有三種設定對應至三個條件會造成編譯時期錯誤。 如需如何使用這些設定資訊，請參閱[在 IDE 中設定警告組態](../../../visual-basic/language-reference/statements/option-strict-statement.md#conditions)稍後在本主題中。  
  
 `Option Strict Off`陳述式關閉 錯誤和警告檢查所有的三個條件，即使相關聯的 IDE 設定指定要開啟這些錯誤或警告。 `Option Strict On`陳述式會開啟錯誤和警告檢查所有的三個條件，即使相關聯的 IDE 設定指定要關閉這些錯誤或警告。  
  
 如果使用`Option Strict`陳述式必須出現在檔案中任何其他程式碼陳述式之前。  
  
 當您設定`Option Strict`至`On`，Visual Basic 會檢查資料型別會指定針對所有的程式設計項目。 資料類型可以明確地指定，或使用區域型別推斷來指定。 指定的所有程式設計項目資料型別建議，原因如下︰  
  
-   它可讓您的變數和參數的 IntelliSense 支援。 這可讓您查看其屬性和其他成員，當您輸入程式碼。  
  
-   它可讓編譯器執行類型檢查。 型別檢查，可協助您找出可以在執行階段失敗，因為型別轉換錯誤的陳述式。 它也會識別不支援這些方法的物件上方法的呼叫。  
  
-   它能加速程式碼的執行。 一個理由是，如果您未指定資料類型的程式設計項目，則 Visual Basic 編譯器將其指派`Object`型別。 可能需要編譯的程式碼之間來回轉換`Object`和其他資料類型，這會降低效能。  
  
## <a name="implicit-narrowing-conversion-errors"></a>隱含的縮小轉換錯誤  
 縮小轉換的隱含資料類型轉換時，就會發生隱含的縮小轉換錯誤。  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]可以將許多資料型別轉換成其他資料型別。 一種資料類型的值轉換為具有較少的有效位數或容量較小的資料類型時，可能發生資料遺失。 如果縮小轉換失敗，就會發生執行階段錯誤。 `Option Strict`可確保這些縮小轉換的編譯時期通知，好讓您可以避免它們。 如需詳細資訊，請參閱[隱含和明確轉換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)和[擴大和縮小轉換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。  
  
 可能會導致錯誤的轉換會在運算式中包含所發生的隱含轉換。 如需詳細資訊，請參閱下列主題：  
  
-   [+ 運算子](../../../visual-basic/language-reference/operators/addition-operator.md)  
  
-   [+= 運算子](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
  
-   [\ 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
  
-   [/ = 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
  
-   [Char 資料類型](../../../visual-basic/language-reference/data-types/char-data-type.md)  
  
 當您使用串連字串[i 運算子](../../../visual-basic/language-reference/operators/concatenation-operator.md)，所有轉換成字串會被都視為擴展。 因此這些轉換不會產生隱含的縮小轉換錯誤，即使`Option Strict`上。  
  
 如果縮小轉換，當您呼叫具有對應的參數與不同的資料類型的引數的方法時，會導致編譯時期錯誤`Option Strict`上。 您可以使用擴展轉換或明確的轉換，以避免產生編譯時期錯誤。  
  
 隱含的縮小轉換錯誤會隱藏在編譯階段進行中的項目轉換`For Each…Next`迴圈控制變數的集合。 發生這種情況即使`Option Strict`上。 如需詳細資訊，請參閱 「 縮小轉換 」 一節[每個...下一個陳述式](../../../visual-basic/language-reference/statements/for-each-next-statement.md)。  
  
## <a name="late-binding-errors"></a>晚期繫結錯誤  
 物件晚期繫結指派至屬性或方法的宣告類型的變數時`Object`。 如需詳細資訊，請參閱[早期和晚期繫結](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)。  
  
## <a name="implicit-object-type-errors"></a>隱含的物件類型的錯誤  
 隱含的物件類型的錯誤發生時適當的型別無法推斷為宣告的變數，因此一種`Object`會推斷而來。 這主要是發生在您使用`Dim`陳述式來宣告變數，而不需使用`As`子句和`Option Infer`已關閉。 如需詳細資訊，請參閱[Option Infer 陳述式](../../../visual-basic/language-reference/statements/option-infer-statement.md)和[Visual Basic 語言規格](../../../visual-basic/reference/language-specification.md)。  
  
 方法參數`As`子句是選擇性的如果`Option Strict`已關閉。 不過，如果任何一個參數使用`As`子句，它們都必須使用它。 如果`Option Strict`，`As`子句是針對每個參數定義必要的。  
  
 如果您宣告變數，而不需使用`As`子句，將它設定為`Nothing`，變數有一種`Object`。 在此情況下發生編譯時期錯誤時`Option Strict`上和`Option Infer`上。 這個範例是`Dim something = Nothing`。  
  
### <a name="default-data-types-and-values"></a>預設資料類型和值  
 下表描述的指定資料類型和初始設定式中的各種組合結果[Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)。  
  
|指定了資料類型？|指定了初始設定式？|範例|結果|  
|---|---|---|---|  
|否|否|`Dim qty`|如果 `Option Strict` 已關閉 (預設值)，此變數會設定為 `Nothing`。<br /><br /> 如果 `Option Strict` 已開啟，就會發生編譯時期錯誤。|  
|否|是|`Dim qty = 5`|如果 `Option Infer` 已開啟 (預設值)，此變數會採用初始設定式的資料類型。 請參閱[區域型別推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。<br /><br /> 如果 `Option Infer` 已關閉，且 `Option Strict` 也已關閉，此變數會採用 `Object` 的資料類型。<br /><br /> 如果 `Option Infer` 已關閉，但是 `Option Strict` 已開啟，就會發生編譯時期錯誤。|  
|是|否|`Dim qty As Integer`|變數會初始化為資料類型的預設值。 如需詳細資訊，請參閱[Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)。|  
|是|是|`Dim qty  As Integer = 5`|如果初始設定式的資料類型無法轉換成指定的資料類型，就會發生編譯時間錯誤。|  
  
## <a name="when-an-option-strict-statement-is-not-present"></a>當 Option Strict 陳述式不存在  
 如果原始程式碼不包含`Option Strict`陳述式， **Option strict**上設定[編譯的頁面上，專案設計工具 (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic)用。 **編譯頁面**有提供產生錯誤之條件的額外控制的設定。  
  
 如果您使用命令列編譯器，您可以使用[/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)編譯器選項以指定的設定`Option Strict`。  
  
### <a name="to-set-option-strict-in-the-ide"></a>若要在 IDE 中設定 Option Strict  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
1.  在**方案總管 中**，選取專案。 在**專案**] 功能表上，按一下 [**屬性**。 如需詳細資訊，請參閱[專案設計工具簡介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)。  
  
2.  在**編譯**索引標籤上，在設定的值**Option Strict**方塊。  
  
###  <a name="conditions"></a>在 IDE 中設定警告組態  
 當您使用[編譯的頁面上，專案設計工具 (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic)而不是`Option Strict`陳述式中，您有其他控制項，會產生錯誤的狀況。 **警告組態**區段**編譯頁面**已設定會對應到三個條件會造成編譯時期錯誤時`Option Strict`上。 以下是這些設定︰  
  
-   **隱含轉換**  
  
-   **晚期繫結。呼叫可能會在執行階段失敗**  
  
-   **隱含型別。假設是物件**  
  
 當您設定**Option Strict**至**上**，這三個以上的警告組態設定會設定為**錯誤**。 當您設定**Option Strict**至**關閉**，所有三項設定會設定為**無**。  
  
 您可以個別變更每個警告組態設定**無**，**警告**，或**錯誤**。 如果所有三個警告組態設定會設定為**錯誤**，`On`會出現在`Option strict`方塊。 如果這三個設為**無**，`Off`出現在此方塊。 這些設定的任何其他組合**（自訂）**隨即出現。  
  
### <a name="to-set-the-option-strict-default-setting-for-new-projects"></a>若要設定新專案的 Option Strict 預設設定  
 當您建立專案， **Option Strict**上設定**編譯** 索引標籤設為**Option Strict**中設定**選項**對話方塊。  
  
 若要設定`Option Strict`在這個對話方塊中，在**工具** 功能表上，按一下**選項**。 在**選項**對話方塊方塊中，展開**專案和方案**，然後按一下  **VB 預設值**。 中的初始預設設定**VB 預設值**是`Off`。  
  
### <a name="to-set-option-strict-on-the-command-line"></a>若要命令列上設定 Option Strict  
 包含[/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)編譯器選項，在**vbc**命令。  
  
## <a name="example"></a>範例  
 下列範例將示範會縮小轉換的隱含型別轉換所造成的編譯時期錯誤。 這類錯誤對應於**隱含轉換**條件**編譯頁面**。  
  
 [!code-vb[VbVbalrStatements #&161;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_1.vb)]  
  
## <a name="example"></a>範例  
 下列範例將示範造成晚期繫結的編譯時期錯誤。 這類錯誤對應於**05 繫結; 呼叫無法在執行階段失敗**條件**編譯頁面**。  
  
 [!code-vb[VbVbalrStatements #&162;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_2.vb)]  
  
## <a name="example"></a>範例  
 下列範例示範的隱含型別宣告的變數所造成的錯誤`Object`。 這類錯誤對應於**隱含型別，假設是物件**條件**編譯頁面**。  
  
 [!code-vb[VbVbalrStatements #&163;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_3.vb)]  
  
 [!code-vb[VbVbalrStatements #&164;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_4.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [擴展和縮小轉換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [隱含和明確轉換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [專案設計工具、編譯頁 (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic)   
 [Option Explicit 陳述式](../../../visual-basic/language-reference/statements/option-explicit-statement.md)   
 [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [如何︰ 存取物件的成員](../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)   
 [XML 中內嵌的運算式](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)   
 [寬鬆的委派轉換](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)   
 [在 Office 方案中的晚期繫結](https://msdn.microsoft.com/library/3xxe951d)   
 [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)   
 [選項對話方塊、專案、Visual Basic 預設值](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
