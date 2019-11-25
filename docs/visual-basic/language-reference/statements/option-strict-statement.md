---
title: Option Strict Statement
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
ms.openlocfilehash: a002526a107fdc6e8e02890d11db94a3d224c94b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353756"
---
# <a name="option-strict-statement"></a>Option Strict Statement
Restricts implicit data type conversions to only widening conversions, disallows late binding, and disallows implicit typing that results in an `Object` type.  
  
## <a name="syntax"></a>語法  
  
```vb  
Option Strict { On | Off }  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`On`|選擇項。 Enables `Option Strict` checking.|  
|`Off`|選擇項。 Disables `Option Strict` checking.|  
  
## <a name="remarks"></a>備註  
 When `Option Strict On` or `Option Strict` appears in a file, the following conditions cause a compile-time error:  
  
- 隱含縮小轉換  
  
- 晚期繫結  
  
- 導致 `Object` 類型的隱含類型化  
  
> [!NOTE]
> In the warning configurations that you can set on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), there are three settings that correspond to the three conditions that cause a compile-time error. For information about how to use these settings, see [To set warning configurations in the IDE](../../../visual-basic/language-reference/statements/option-strict-statement.md#conditions) later in this topic.  
  
 The `Option Strict Off` statement turns off error and warning checking for all three conditions, even if the associated IDE settings specify to turn on these errors or warnings. The `Option Strict On` statement turns on error and warning checking for all three conditions, even if the associated IDE settings specify to turn off these errors or warnings.  
  
 If used, the `Option Strict` statement must appear before any other code statements in a file.  
  
 When you set `Option Strict` to `On`, Visual Basic checks that data types are specified for all programming elements. Data types can be specified explicitly, or specified by using local type inference. Specifying data types for all your programming elements is recommended, for the following reasons:  
  
- It enables IntelliSense support for your variables and parameters. This enables you to see their properties and other members as you type code.  
  
- It enables the compiler to perform type checking. Type checking helps you find statements that can fail at run time because of type conversion errors. It also identifies calls to methods on objects that do not support those methods.  
  
- It speeds up the execution of code. One reason for this is that if you do not specify a data type for a programming element, the Visual Basic compiler assigns it the `Object` type. Compiled code might have to convert back and forth between `Object` and other data types, which reduces performance.  
  
## <a name="implicit-narrowing-conversion-errors"></a>Implicit Narrowing Conversion Errors  
 隱含資料類型轉換是縮小轉換時，會發生隱含縮小轉換錯誤。  
  
 Visual Basic can convert many data types to other data types. Data loss can occur when the value of one data type is converted to a data type that has less precision or a smaller capacity. A run-time error occurs if such a narrowing conversion fails. `Option Strict` ensures compile-time notification of these narrowing conversions so that you can avoid them. For more information, see [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) and [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
 Conversions that can cause errors include implicit conversions that occur in expressions. 如需詳細資訊，請參閱下列主題：  
  
- [+ 運算子](../../../visual-basic/language-reference/operators/addition-operator.md)  
  
- [+= 運算子](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
  
- [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
  
- [/= Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
  
- [Char 資料類型](../../../visual-basic/language-reference/data-types/char-data-type.md)  
  
 When you concatenate strings by using the [& Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md), all conversions to the strings are considered to be widening. So these conversions do not generate an implicit narrowing conversion error, even if `Option Strict` is on.  
  
 When you call a method that has an argument that has a data type different from the corresponding parameter, a narrowing conversion causes a compile-time error if `Option Strict` is on. You can avoid the compile-time error by using a widening conversion or an explicit conversion.  
  
 Implicit narrowing conversion errors are suppressed at compile-time for conversions from the elements in a `For Each…Next` collection to the loop control variable. This occurs even if `Option Strict` is on. For more information, see the "Narrowing Conversions" section in [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
## <a name="late-binding-errors"></a>Late Binding Errors  
 當物件指派給宣告為 `Object` 類型之變數的屬性或方法時，該物件即為「晚期繫結」。 For more information, see [Early and Late Binding](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md).  
  
## <a name="implicit-object-type-errors"></a>Implicit Object Type Errors  
 無法推斷宣告變數的適當類型時，會發生隱含物件類型錯誤，因此推斷類型為 `Object`。 這主要是發生在您使用 `Dim` 陳述式宣告變數而未使用 `As` 子句，並且 `Option Infer` 已設為關閉的時候。 For more information, see [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) and the [Visual Basic Language Specification](../../../visual-basic/reference/language-specification/index.md).  
  
 For method parameters, the `As` clause is optional if `Option Strict` is off. However, if any one parameter uses an `As` clause, they all must use it. If `Option Strict` is on, the `As` clause is required for every parameter definition.  
  
 If you declare a variable without using an `As` clause and set it to `Nothing`, the variable has a type of `Object`. No compile-time error occurs in this case when `Option Strict` is on and `Option Infer` is on. An example of this is `Dim something = Nothing`.  
  
### <a name="default-data-types-and-values"></a>預設資料類型和值  
 The following table describes the results of various combinations of specifying the data type and initializer in a [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
|指定了資料類型？|指定了初始設定式？|範例|結果|  
|---|---|---|---|  
|否|否|`Dim qty`|如果 `Option Strict` 已關閉 (預設值)，此變數會設定為 `Nothing`。<br /><br /> 如果 `Option Strict` 已開啟，就會發生編譯時間錯誤。|  
|否|[是]|`Dim qty = 5`|如果 `Option Infer` 已開啟 (預設值)，此變數會採用初始設定式的資料類型。 See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).<br /><br /> 如果 `Option Infer` 已關閉，且 `Option Strict` 也已關閉，此變數會採用 `Object` 的資料類型。<br /><br /> 如果 `Option Infer` 已關閉，但是 `Option Strict` 已開啟，就會發生編譯時間錯誤。|  
|[是]|否|`Dim qty As Integer`|變數會初始化為資料類型的預設值。 For more information, see [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).|  
|[是]|[是]|`Dim qty  As Integer = 5`|如果初始設定式的資料類型無法轉換成指定的資料類型，就會發生編譯時期錯誤。|  
  
## <a name="when-an-option-strict-statement-is-not-present"></a>When an Option Strict Statement Is Not Present  
 If the source code does not contain an `Option Strict` statement, the **Option strict** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used. The **Compile Page** has settings that provide additional control over the conditions that generate an error.  
  
 If you are using the command-line compiler, you can use the [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) compiler option to specify a setting for `Option Strict`.  
  
### <a name="to-set-option-strict-in-the-ide"></a>To set Option Strict in the IDE  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
1. 在方案總管中選取專案。 在 [專案] 功能表上，按一下 [屬性]。  
  
2. On the **Compile** tab, set the value in the **Option Strict** box.  
  
### <a name="conditions"></a> To set warning configurations in the IDE  
 When you use the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) instead of an `Option Strict` statement, you have additional control over the conditions that generate errors. The **Warning configurations** section of the **Compile Page** has settings that correspond to the three conditions that cause a compile-time error when `Option Strict` is on. 以下是這些設定：  
  
- **隱含轉換**  
  
- **晚期繫結，執行階段時呼叫可能失敗**  
  
- **隱含類型，假設是 Object**  
  
 當您將 [Option Strict] 設定為 [On] 時，這三個警告組態設定都會設定為 [錯誤]。 當您將 [Option Strict] 設定為 [Off] 時，所有三個設定都會設定為 [無]。  
  
 您可以將每個警告組態個別變更為 [無]、[警告] 或 [錯誤]。 如果三個警告組態設定皆設為 [錯誤]，`On` 會出現在 `Option strict` 方塊中。 如果這三個都設定為 [無]，`Off` 會出現在此方塊中。 若為這些設定的其他任何組合，則會出現 [(自訂)]。  
  
### <a name="to-set-the-option-strict-default-setting-for-new-projects"></a>To set the Option Strict default setting for new projects  
 When you create a project, the **Option Strict** setting on the **Compile** tab is set to the **Option Strict** setting in the **Options** dialog box.  
  
 To set `Option Strict` in this dialog box, on the **Tools** menu, click **Options**. 在 [選項] 對話方塊中，展開 [專案和方案]，然後按一下 [VB 預設值]。 The initial default setting in **VB Defaults** is `Off`.  
  
### <a name="to-set-option-strict-on-the-command-line"></a>To set Option Strict on the command line  
 Include the [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) compiler option in the **vbc** command.  
  
## <a name="example"></a>範例  
 The following examples demonstrate compile-time errors caused by implicit type conversions that are narrowing conversions. This category of errors corresponds to the **Implicit conversion** condition on the **Compile Page**.  
  
 [!code-vb[VbVbalrStatements#161](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#161)]  
  
## <a name="example"></a>範例  
 The following example demonstrates a compile-time error caused by late binding. This category of errors corresponds to the **Late binding; call could fail at run time** condition on the **Compile Page**.  
  
 [!code-vb[VbVbalrStatements#162](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#162)]  
  
## <a name="example"></a>範例  
 The following examples demonstrate errors caused by variables that are declared with an implicit type of `Object`. This category of errors corresponds to the **Implicit type; object assumed** condition on the **Compile Page**.  
  
 [!code-vb[VbVbalrStatements#163](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#163)]  
  
 [!code-vb[VbVbalrStatements#164](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#164)]  
  
## <a name="see-also"></a>請參閱

- [擴展和縮小轉換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [隱含和明確轉換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [專案設計工具、編譯頁面 (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [Option Explicit 陳述式](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [如何：存取物件的成員](../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)
- [XML 中內嵌的運算式](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [寬鬆委派轉換](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [Office 方案中的晚期繫結](/visualstudio/vsto/late-binding-in-office-solutions)
- [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [選項對話方塊、專案、Visual Basic 預設值](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
