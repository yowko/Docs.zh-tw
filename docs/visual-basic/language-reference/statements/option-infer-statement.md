---
title: Option Infer 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.OptionInfer
- vb.Infer
helpviewer_keywords:
- variables [Visual Basic], declaring
- Option Infer statement [Visual Basic]
- Infer keyword [Visual Basic]
- declaring variables [Visual Basic], inferred
- inferred variable declaration
ms.assetid: 4ad3e6e9-8f5b-4209-a248-de22ef6e4652
ms.openlocfilehash: 59766999c5b03aac7aec13b293feaa8c17f2ced0
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59338562"
---
# <a name="option-infer-statement"></a>Option Infer 陳述式
可讓您在宣告變數時使用區域類型推斷。  
  
## <a name="syntax"></a>語法  
  
```  
Option Infer { On | Off }  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`On`|選擇性。 啟用區域類型推斷。|  
|`Off`|選擇性。 停用區域類型推斷。|  
  
## <a name="remarks"></a>備註  
 若要在檔案中設定 `Option Infer`，請在檔案頂端的任何其他原始程式碼之前輸入 `Option Infer On` 或 `Option Infer Off`。 如果在檔案中設定給 `Option Infer` 的值與 IDE 或命令列中設定的值衝突，檔案中的值具有優先權。  
  
 當您將 `Option Infer` 設定為 `On` 時，可以宣告區域變數而不用明確陳述資料類型。 編譯器會從其初始化運算式的類型推斷變數的資料類型。  
  
 在下圖中，`Option Infer` 已開啟。 宣告 `Dim someVar = 2` 中的變數依類型推斷宣告為整數。

 Option Infer 開啟時，下列螢幕擷取畫面會顯示 IntelliSense: 
  
 ![Option Infer 開啟時顯示 IntelliSense 檢視的螢幕擷取畫面。](./media/option-infer-statement/option-infer-as-integer-on.png)  
  
 在下圖中，`Option Infer` 已關閉。 宣告 `Dim someVar = 2` 中的變數依類型推斷宣告為 `Object`。 在此範例中， **Option Strict**設定設為**Off**上[編譯的 Page，Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)。  
  
 Option Infer 關閉時，下列螢幕擷取畫面會顯示 IntelliSense:
 
 ![Option Infer 關閉時，顯示 IntelliSense 檢視的螢幕擷取畫面。](./media/option-infer-statement/option-infer-as-object-off.png)  
  
> [!NOTE]
>  當變數被宣告為 `Object` 時，執行階段類型可以在程式執行時變更。 Visual Basic 執行呼叫的作業*boxing*並*unboxing*之間進行轉換`Object`和實值類型，可讓執行速度變慢。 如需 boxing 和 unboxing 的詳細資訊，請參閱[Visual Basic 語言規格](~/_vblang/spec/conversions.md#value-type-conversions)。
  
 類型推斷會套用在程序層級，不會套用在類別、結構、模組或介面中的程序之外。  
  
 如需詳細資訊，請參閱[區域型別推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。  
  
## <a name="when-an-option-infer-statement-is-not-present"></a>Option Infer 陳述式不存在時  
 如果原始程式碼不包含`Option Infer`陳述式中， **Option Infer**上設定[編譯的 Page，Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)用。 如果使用命令列編譯器，則[/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)編譯器選項使用。  
  
#### <a name="to-set-option-infer-in-the-ide"></a>在 IDE 中設定 Option Infer  
  
1. 在方案總管中選取專案。 在 [專案] 功能表上，按一下 [屬性]。  
  
2. 按一下 [編譯] 索引標籤。  
  
3. 在設定的值**Option infer**  方塊中。  
  
 當您建立新的專案中， **Option Infer**上設定**編譯**索引標籤設定為**Option Infer**中設定**VB 預設值** 對話方塊。 若要存取**VB 預設值**對話方塊的 **工具**功能表上，按一下 **選項**。 在 [選項] 對話方塊中，展開 [專案和方案]，然後按一下 [VB 預設值]。 中的初始預設設定**VB 預設值**是`On`。  
  
#### <a name="to-set-option-infer-on-the-command-line"></a>在命令列上設定 Option Infer  
  
-   包含[/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)中的編譯器選項**vbc**命令。  
  
## <a name="default-data-types-and-values"></a>預設資料類型和值  
 下表說明在 `Dim` 陳述式中指定資料類型和初始設定式的各種組合結果。  
  
|指定了資料類型？|指定了初始設定式？|範例|結果|  
|---|---|---|---|  
|否|否|`Dim qty`|如果 `Option Strict` 已關閉 (預設值)，此變數會設定為 `Nothing`。<br /><br /> 如果 `Option Strict` 已開啟，就會發生編譯時間錯誤。|  
|否|是|`Dim qty = 5`|如果 `Option Infer` 已開啟 (預設值)，此變數會採用初始設定式的資料類型。 請參閱[區域型別推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。<br /><br /> 如果 `Option Infer` 已關閉，且 `Option Strict` 也已關閉，此變數會採用 `Object` 的資料類型。<br /><br /> 如果 `Option Infer` 已關閉，但是 `Option Strict` 已開啟，就會發生編譯時間錯誤。|  
|是|否|`Dim qty As Integer`|變數會初始化為資料類型的預設值。 如需詳細資訊，請參閱 < [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)。|  
|是|是|`Dim qty  As Integer = 5`|如果初始設定式的資料類型無法轉換成指定的資料類型，就會發生編譯時期錯誤。|  
  
## <a name="example"></a>範例  
 下列範例示範 `Option Infer` 陳述式如何啟用區域類型推斷。  
  
 [!code-vb[VbVbalrTypeInference#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#6)]  
  
## <a name="example"></a>範例  
 下列範例示範當變數被視為 `Object` 時，執行階段類型可能會不同。  
  
 [!code-vb[VbVbalrTypeInference#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#11)]  
  
## <a name="see-also"></a>另請參閱

- [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)
- [區域類型推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Compare 陳述式](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [Option Explicit 陳述式](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Long](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [選項對話方塊、專案、Visual Basic 預設值](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [Boxing 和 Unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
