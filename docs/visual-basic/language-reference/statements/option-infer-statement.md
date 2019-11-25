---
title: Option Infer 陳述式
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
ms.openlocfilehash: 53bc9d41f28f63061db2012395480aa6be7515dd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346501"
---
# <a name="option-infer-statement"></a>Option Infer 陳述式

可讓您在宣告變數時使用區域類型推斷。

## <a name="syntax"></a>語法

```vb
Option Infer { On | Off }
```

## <a name="parts"></a>組件

|詞彙|定義|
|---|---|
|`On`|選擇項。 啟用區域類型推斷。|
|`Off`|選擇項。 停用區域類型推斷。|

## <a name="remarks"></a>備註

若要在檔案中設定 `Option Infer`，請在檔案頂端的任何其他原始程式碼之前輸入 `Option Infer On` 或 `Option Infer Off`。 如果在檔案中設定給 `Option Infer` 的值與 IDE 或命令列中設定的值衝突，檔案中的值具有優先權。

當您將 `Option Infer` 設定為 `On` 時，可以宣告區域變數而不用明確陳述資料類型。 編譯器會從其初始化運算式的類型推斷變數的資料類型。

在下圖中，`Option Infer` 已開啟。 宣告 `Dim someVar = 2` 中的變數依類型推斷宣告為整數。

The following screenshot shows IntelliSense when Option Infer is on:

![Screenshot showing IntelliSense view when Option Infer is on.](./media/option-infer-statement/option-infer-as-integer-on.png)

在下圖中，`Option Infer` 已關閉。 宣告 `Dim someVar = 2` 中的變數依類型推斷宣告為 `Object`。 In this example, the **Option Strict** setting is set to **Off** on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).

The following screenshot shows IntelliSense when Option Infer is off:

![Screenshot showing IntelliSense view when Option Infer is off.](./media/option-infer-statement/option-infer-as-object-off.png)

> [!NOTE]
> 當變數被宣告為 `Object` 時，執行階段類型可以在程式執行時變更。 Visual Basic performs operations called *boxing* and *unboxing* to convert between an `Object` and a value type, which makes execution slower. For information about boxing and unboxing, see the [Visual Basic Language Specification](~/_vblang/spec/conversions.md#value-type-conversions).

類型推斷會套用在程序層級，不會套用在類別、結構、模組或介面中的程序之外。

For additional information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).

## <a name="when-an-option-infer-statement-is-not-present"></a>Option Infer 陳述式不存在時

If the source code does not contain an `Option Infer` statement, the **Option Infer** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used. If the command-line compiler is used, the [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option is used.

#### <a name="to-set-option-infer-in-the-ide"></a>在 IDE 中設定 Option Infer

1. 在方案總管中選取專案。 在 [專案] 功能表上，按一下 [屬性]。

2. 按一下 [編譯] 索引標籤。

3. Set the value in the **Option infer** box.

When you create a new project, the **Option Infer** setting on the **Compile** tab is set to the **Option Infer** setting in the **VB Defaults** dialog box. To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**. 在 [選項] 對話方塊中，展開 [專案和方案]，然後按一下 [VB 預設值]。 The initial default setting in **VB Defaults** is `On`.

#### <a name="to-set-option-infer-on-the-command-line"></a>在命令列上設定 Option Infer

Include the [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option in the **vbc** command.

## <a name="default-data-types-and-values"></a>預設資料類型和值

下表說明在 `Dim` 陳述式中指定資料類型和初始設定式的各種組合結果。

|指定了資料類型？|指定了初始設定式？|範例|結果|
|---|---|---|---|
|否|否|`Dim qty`|如果 `Option Strict` 已關閉 (預設值)，此變數會設定為 `Nothing`。<br /><br /> 如果 `Option Strict` 已開啟，就會發生編譯時間錯誤。|
|否|[是]|`Dim qty = 5`|如果 `Option Infer` 已開啟 (預設值)，此變數會採用初始設定式的資料類型。 See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).<br /><br /> 如果 `Option Infer` 已關閉，且 `Option Strict` 也已關閉，此變數會採用 `Object` 的資料類型。<br /><br /> 如果 `Option Infer` 已關閉，但是 `Option Strict` 已開啟，就會發生編譯時間錯誤。|
|[是]|否|`Dim qty As Integer`|變數會初始化為資料類型的預設值。 For more information, see [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).|
|[是]|[是]|`Dim qty  As Integer = 5`|如果初始設定式的資料類型無法轉換成指定的資料類型，就會發生編譯時期錯誤。|

## <a name="example"></a>範例

下列範例示範 `Option Infer` 陳述式如何啟用區域類型推斷。

[!code-vb[VbVbalrTypeInference#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#6)]

## <a name="example"></a>範例

下列範例示範當變數被視為 `Object` 時，執行階段類型可能會不同。

[!code-vb[VbVbalrTypeInference#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#11)]

## <a name="see-also"></a>請參閱

- [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)
- [區域類型推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Compare 陳述式](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [Option Explicit 陳述式](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [選項對話方塊、專案、Visual Basic 預設值](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [Boxing 和 Unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
