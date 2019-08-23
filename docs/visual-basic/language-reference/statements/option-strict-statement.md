---
title: Option Strict 語句 (Visual Basic)
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
ms.openlocfilehash: a8466cb0672ccf26717d012bdebb7363f31ebb08
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912274"
---
# <a name="option-strict-statement"></a>Long
將隱含資料類型轉換限制為僅限擴輾轉換、不允許晚期繫結, 而且不`Object`允許產生類型的隱含類型。  
  
## <a name="syntax"></a>語法  
  
```  
Option Strict { On | Off }  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`On`|選擇性。 啟用`Option Strict`檢查。|  
|`Off`|選擇性。 停`Option Strict`用檢查。|  
  
## <a name="remarks"></a>備註  
 當`Option Strict On`檔案`Option Strict`中出現或時, 下列情況會導致編譯時期錯誤:  
  
- 隱含縮小轉換  
  
- 晚期繫結  
  
- 導致 `Object` 類型的隱含類型化  
  
> [!NOTE]
> 在 [[編譯] 頁面上, [專案設計](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)工具] ([Visual Basic]) 可設定的警告設定中, 有三個設定會對應到造成編譯時期錯誤的三個條件。 如需有關如何使用這些設定的詳細資訊, 請參閱本主題稍後[的在 IDE 中設定警告設定](../../../visual-basic/language-reference/statements/option-strict-statement.md#conditions)。  
  
 `Option Strict Off`語句會關閉所有三個條件的錯誤和警告檢查, 即使相關聯的 IDE 設定指定要開啟這些錯誤或警告。 `Option Strict On`語句會針對這三個條件開啟錯誤和警告檢查, 即使相關聯的 IDE 設定指定要關閉這些錯誤或警告。  
  
 如果使用的話, `Option Strict`語句必須出現在檔案中的任何其他程式碼語句之前。  
  
 當您將`Option Strict`設定`On`為時, Visual Basic 會檢查是否已針對所有程式設計項目指定資料類型。 您可以明確指定資料類型, 或使用區欄位型別推斷來指定。 建議您為所有的程式設計項目指定資料類型, 原因如下:  
  
- 它會針對您的變數和參數啟用 IntelliSense 支援。 這可讓您在輸入程式碼時看到其屬性和其他成員。  
  
- 它可讓編譯器執行類型檢查。 類型檢查可協助您尋找在執行時間因類型轉換錯誤而失敗的語句。 它也會識別不支援這些方法之物件上方法的呼叫。  
  
- 它會加速程式碼的執行。 其中一個原因是, 如果您沒有指定程式設計項目的資料類型, Visual Basic 編譯器會為它`Object`指派類型。 已編譯的程式碼可能必須在和其他`Object`資料類型之間來回轉換, 以降低效能。  
  
## <a name="implicit-narrowing-conversion-errors"></a>隱含縮小轉換錯誤  
 隱含資料類型轉換是縮小轉換時，會發生隱含縮小轉換錯誤。  
  
 Visual Basic 可以將許多資料類型轉換成其他資料類型。 當某個資料類型的值轉換成具有較少精確度或較小容量的資料類型時, 可能會發生資料遺失。 如果這類縮小轉換失敗, 就會發生執行階段錯誤。 `Option Strict`確保這些縮小轉換的編譯時間通知, 讓您可以避免它們。 如需詳細資訊, 請參閱[隱含和明確轉換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)和[擴展和縮小轉換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。  
  
 可能造成錯誤的轉換包括運算式中發生的隱含轉換。 如需詳細資訊，請參閱下列主題：  
  
- [+ 運算子](../../../visual-basic/language-reference/operators/addition-operator.md)  
  
- [+= 運算子](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
  
- [\ 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
  
- [/= 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
  
- [Char 資料類型](../../../visual-basic/language-reference/data-types/char-data-type.md)  
  
 當您使用[& 運算子](../../../visual-basic/language-reference/operators/concatenation-operator.md)來串連字號串時, 會將字串的所有轉換視為擴展。 因此, 即使`Option Strict`是 on, 這些轉換也不會產生隱含的縮小轉換錯誤。  
  
 當您呼叫的方法具有與對應參數不同的資料類型引數時, 如果`Option Strict`為 on, 則縮小轉換會導致編譯時期錯誤。 您可以使用擴輾轉換或明確轉換來避免編譯時期錯誤。  
  
 在編譯時間會抑制隱含縮小轉換錯誤, 以從`For Each…Next`集合中的元素轉換為迴圈控制變數。 即使`Option Strict`是 on, 也會發生這種情況。 如需詳細資訊, 請參閱[For Each ... 中的「縮小轉換」一節。下一個語句](../../../visual-basic/language-reference/statements/for-each-next-statement.md)。  
  
## <a name="late-binding-errors"></a>晚期繫結錯誤  
 當物件指派給宣告為 `Object` 類型之變數的屬性或方法時，該物件即為「晚期繫結」。 如需詳細資訊, 請參閱[早期和晚期繫結](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)。  
  
## <a name="implicit-object-type-errors"></a>隱含物件類型錯誤  
 無法推斷宣告變數的適當類型時，會發生隱含物件類型錯誤，因此推斷類型為 `Object`。 這主要是發生在您使用 `Dim` 陳述式宣告變數而未使用 `As` 子句，並且 `Option Infer` 已設為關閉的時候。 如需詳細資訊, 請參閱[Option 推斷語句](../../../visual-basic/language-reference/statements/option-infer-statement.md)和[Visual Basic 語言規格](../../../visual-basic/reference/language-specification/index.md)。  
  
 針對方法參數, 如果`As` `Option Strict`為 off, 子句是選擇性的。 不過, 如果有任何一個參數使用`As`子句, 則它們都必須使用它。 如果`Option Strict`為 on `As` , 則每個參數定義都需要子句。  
  
 如果您在不使用`As`子句的情況下宣告變數, 並將它設定為`Nothing`, 則`Object`變數的類型為。 當是 on, 且為 on 時`Option Strict` , `Option Infer`在此情況下不會發生編譯時期錯誤。 其中一個範例是`Dim something = Nothing`。  
  
### <a name="default-data-types-and-values"></a>預設資料類型和值  
 下表描述在[Dim 語句](../../../visual-basic/language-reference/statements/dim-statement.md)中指定資料類型和初始化運算式的各種組合結果。  
  
|指定了資料類型？|指定了初始設定式？|範例|結果|  
|---|---|---|---|  
|否|否|`Dim qty`|如果 `Option Strict` 已關閉 (預設值)，此變數會設定為 `Nothing`。<br /><br /> 如果 `Option Strict` 已開啟，就會發生編譯時間錯誤。|  
|否|是|`Dim qty = 5`|如果 `Option Infer` 已開啟 (預設值)，此變數會採用初始設定式的資料類型。 請參閱[區欄位型別推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。<br /><br /> 如果 `Option Infer` 已關閉，且 `Option Strict` 也已關閉，此變數會採用 `Object` 的資料類型。<br /><br /> 如果 `Option Infer` 已關閉，但是 `Option Strict` 已開啟，就會發生編譯時間錯誤。|  
|是|否|`Dim qty As Integer`|變數會初始化為資料類型的預設值。 如需詳細資訊, 請參閱[Dim 語句](../../../visual-basic/language-reference/statements/dim-statement.md)。|  
|是|是|`Dim qty  As Integer = 5`|如果初始設定式的資料類型無法轉換成指定的資料類型，就會發生編譯時期錯誤。|  
  
## <a name="when-an-option-strict-statement-is-not-present"></a>當 Option Strict 語句不存在時  
 如果原始程式碼不包含`Option Strict`語句, 則會使用 [編譯] 頁面上的 [ **Option strict** ] 設定 ([專案設計工具] [(Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) 。 [**編譯] 頁面**有一些設定, 可對產生錯誤的條件提供額外的控制。  
  
 如果您使用命令列編譯器, 您可以使用[/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)編譯器選項來指定的設定`Option Strict`。  
  
### <a name="to-set-option-strict-in-the-ide"></a>若要在 IDE 中設定 Option Strict  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
1. 在方案總管中選取專案。 在 [專案] 功能表上，按一下 [屬性]。  
  
2. 在 [**編譯**] 索引標籤上, 于 [**選項 Strict** ] 方塊中設定值。  
  
### <a name="conditions"></a>若要在 IDE 中設定警告設定  
 當您使用 [[編譯] 頁面時, [專案設計工具] (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) , 而不`Option Strict`是語句, 您可以進一步控制產生錯誤的條件。 [**編譯] 頁面**的 [ `Option Strict` **警告**設定] 區段中, 具有對應于當為 on 時造成編譯時期錯誤的三個條件。 以下是這些設定：  
  
- **隱含轉換**  
  
- **晚期繫結，執行階段時呼叫可能失敗**  
  
- **隱含類型，假設是 Object**  
  
 當您將 [Option Strict] 設定為 [On] 時，這三個警告組態設定都會設定為 [錯誤]。 當您將 [Option Strict] 設定為 [Off] 時，所有三個設定都會設定為 [無]。  
  
 您可以將每個警告組態個別變更為 [無]、[警告] 或 [錯誤]。 如果三個警告組態設定皆設為 [錯誤]，`On` 會出現在 `Option strict` 方塊中。 如果這三個都設定為 [無]，`Off` 會出現在此方塊中。 若為這些設定的其他任何組合，則會出現 [(自訂)]。  
  
### <a name="to-set-the-option-strict-default-setting-for-new-projects"></a>設定新專案的 Option Strict 預設設定  
 當您建立專案時, [**編譯**] 索引標籤上的 [ **option strict** ] 設定會設定為 [**選項**] 對話方塊中的 [ **option strict** ] 設定。  
  
 若要`Option Strict`在此對話方塊中設定, 請在 [**工具**] 功能表上, 按一下 [**選項**]。 在 [選項] 對話方塊中，展開 [專案和方案]，然後按一下 [VB 預設值]。 **VB 預設值**中的初始預設設定`Off`為。  
  
### <a name="to-set-option-strict-on-the-command-line"></a>若要在命令列上設定 Option Strict  
 在**vbc**命令中包含[/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)編譯器選項。  
  
## <a name="example"></a>範例  
 下列範例示範以縮小轉換的隱含類型轉換所造成的編譯時期錯誤。 這個錯誤類別會對應至 [**編譯] 頁面**上的**隱含轉換**條件。  
  
 [!code-vb[VbVbalrStatements#161](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#161)]  
  
## <a name="example"></a>範例  
 下列範例示範晚期繫結所造成的編譯時期錯誤。 這個錯誤類別會對應至晚期繫結; 在 [**編譯] 頁面**上, [**呼叫可能會在執行時間失敗**] 條件。  
  
 [!code-vb[VbVbalrStatements#162](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#162)]  
  
## <a name="example"></a>範例  
 下列範例示範以隱含類型宣告的`Object`變數所造成的錯誤。 這個類別的錯誤對應于**隱含類型;** 在 [**編譯] 頁面**上的 [物件假設] 條件。  
  
 [!code-vb[VbVbalrStatements#163](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#163)]  
  
 [!code-vb[VbVbalrStatements#164](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#164)]  
  
## <a name="see-also"></a>另請參閱

- [擴展和縮小轉換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [隱含和明確轉換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [專案設計工具、編譯頁面 (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [Option Explicit 陳述式](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [如何：存取物件的成員](../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)
- [XML 中內嵌的運算式](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [寬鬆委派轉換](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [Office 方案中的晚期繫結](/visualstudio/vsto/late-binding-in-office-solutions)
- [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [選項對話方塊、專案、Visual Basic 預設值](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
