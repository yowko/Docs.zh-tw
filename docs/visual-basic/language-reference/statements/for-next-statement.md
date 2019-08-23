---
title: For...Next 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Step
- vb.Next
- vb.To
- vb.for
helpviewer_keywords:
- infinite loops
- Next keyword [Visual Basic], For...Next statements
- For keyword [Visual Basic], For...Next statements
- Step keyword [Visual Basic], For...Next statements
- operator overloading, For...Next statement
- To keyword [Visual Basic], For...Next statements
- endless loops
- loops, endless
- instructions, repeating
- Next statement [Visual Basic], For...Next
- For...Next statements
- loop structures [Visual Basic], For...Next
- loops, infinite
- Exit statement [Visual Basic], For...Next statements
- For statement [Visual Basic]
ms.assetid: f5fc0d51-67ce-4c36-9f09-31c9a91c94e9
ms.openlocfilehash: 9a9aed51f6d7bf3233e6e89116b8209b22f3d15d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912409"
---
# <a name="fornext-statement-visual-basic"></a>For...Next 陳述式 (Visual Basic)
重複指定次數的語句群組。  
  
## <a name="syntax"></a>語法  
  
```  
For counter [ As datatype ] = start To end [ Step step ]  
    [ statements ]  
    [ Continue For ]  
    [ statements ]  
    [ Exit For ]  
    [ statements ]  
Next [ counter ]  
```  
  
## <a name="parts"></a>組件  
  
|組件|描述|  
|----------|-----------------|  
|`counter`|語句中的`For`必要項。 數值變數。 迴圈的控制變數。 如需詳細資訊, 請參閱本主題稍後的[計數器引數](#BKMK_Counter)。|  
|`datatype`|選擇性。 的`counter`資料類型。 如需詳細資訊, 請參閱本主題稍後的[計數器引數](#BKMK_Counter)。|  
|`start`|必要項。 數值運算式。 `counter` 的初始值。|  
|`end`|必要項。 數值運算式。 的最終值`counter`。|  
|`step`|選擇性。 數值運算式。 每次透過迴圈`counter`遞增的數量。|  
|`statements`|選擇性。 在和`For` `Next`之間執行指定次數的一或多個語句。|  
|`Continue For`|選擇性。 將控制權轉移至下一個迴圈反復專案。|  
|`Exit For`|選擇性。 將`For`控制權轉移給迴圈。|  
|`Next`|必要項。 終止`For`迴圈的定義。|  
  
> [!NOTE]
> 此語句中會使用關鍵字來指定計數器的範圍。`To` 您也可以在 [選取 ...] 中使用此關鍵字[Case 語句](../../../visual-basic/language-reference/statements/select-case-statement.md)和陣列宣告。 如需陣列宣告的詳細資訊, 請參閱[Dim 語句](../../../visual-basic/language-reference/statements/dim-statement.md)。  
  
## <a name="simple-examples"></a>簡單範例  
 您可以使用`For`。`Next`當您想要以設定的次數重複一組語句時的結構。  
  
 在下列範例中, `index`變數會以1的值開頭, 並隨著迴圈的每個反復專案而遞增, 並在的`index`值到達5之後結束。  
  
 [!code-vb[VbVbalrStatements#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#111)]  
  
 在下列範例中, `number`變數會從2開始, 並在迴圈的每次反覆運算時減少 0.25, 並在的`number`值到達0之後結束。 的`Step` 引數會在迴圈的每個反復專案上,將`-.25`值減少0.25。  
  
 [!code-vb[VbVbalrStatements#112](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#112)]  
  
> [!TIP]
>  A [While 。End While 語句](../../../visual-basic/language-reference/statements/while-end-while-statement.md)或[Do 。](../../../visual-basic/language-reference/statements/do-loop-statement.md)當您事先不知道要在迴圈中執行語句的次數時, Loop 語句的運作效果很好。 不過, 當您預期執行迴圈的特定次數時, `For`。`Next` 「迴圈」是較佳的選擇。 您會在第一次進入迴圈時判斷反覆運算次數。  
  
## <a name="nesting-loops"></a>嵌套迴圈  
 您可以藉`For`由在另一個迴圈中放入迴圈來加以嵌套。 下列範例示範 nested `For`。`Next`具有不同步驟值的結構。 外部迴圈會為迴圈的每個反覆運算建立一個字串。 內部迴圈會針對迴圈的每個反覆運算遞減迴圈計數器變數。  
  
 [!code-vb[VbVbalrStatements#113](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#113)]  
  
 當嵌套迴圈時, 每個迴圈都必須`counter`有唯一的變數。  
  
 您也可以將不同類型的控制結構分別放在其中。 如需詳細資訊, 請參閱[嵌套控制項結構](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)。  
  
## <a name="exit-for-and-continue-for"></a>結束並繼續進行  
 語句會立即`For`結束... `Exit For``Next` 迴圈, 並將控制權轉移至`Next`語句後面的語句。  
  
 `Continue For`語句會立即將控制權轉移到迴圈的下一個反復專案。 如需詳細資訊, 請參閱[Continue 語句](../../../visual-basic/language-reference/statements/continue-statement.md)。  
  
 下列範例說明如何使用`Continue For`和`Exit For`語句。  
  
 [!code-vb[VbVbalrStatements#115](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#115)]  
  
 您可以將任意數目的`Exit For`語句放`For`在 。`Next` 進入. 在 nested `For`中使用時 。`Next` 迴圈, `Exit For`結束最內層的迴圈, 並將控制權轉移至下一個較高層級的嵌套。  
  
 `Exit For`通常是在評估某個條件之後使用 (例如, 在`If`。`Then`...`Else`結構)。 在下列情況下, `Exit For`您可能會想要使用:  
  
- 繼續進行反覆運算是不必要或不可能的。 錯誤值或終止要求可能會建立此條件。  
  
- 答`Try`:`Catch`...`Finally`語句會攔截例外狀況。 您可以在`Exit For` `Finally`區塊結尾使用。  
  
- 您有一個無止盡的迴圈, 這是一種迴圈, 可能會執行很長或甚至無限次數。 如果您偵測到這種情況, 您可以`Exit For`使用來將迴圈轉義。 如需詳細資訊, 請參閱[Do 。Loop 語句](../../../visual-basic/language-reference/statements/do-loop-statement.md)。  
  
## <a name="technical-implementation"></a>技術實作  
 `For`當 。迴圈啟動, Visual Basic 評估`start`、 `end`和`step`。 `Next` Visual Basic 只會在此時評估這些值, 然後將`start`指派`counter`給。 在執行語句區塊之前, Visual Basic 會`counter`與`end`進行比較。 如果`counter`已經大於`end`值 (如果`step`是負數, 則為較小), `For` `Next`迴圈就會結束, 並將控制權傳遞至語句後面的語句。 否則, 會執行語句區塊。  
  
 每`Next`次 Visual Basic 遇到語句時, 它會`counter` `step`遞增並返回`For`語句。 同樣地, `counter`它`end`會與進行比較, 並再次執行區塊或結束迴圈, 視結果而定。 此程式會繼續`counter`進行`end` , 直到`Exit For`遇到 pass 或語句為止。  
  
 迴圈不會停止, `counter`直到通過`end`為止。 `counter` 如果`end`等於, 迴圈就會繼續。 判斷是否要執行區塊的比較是正向`counter` , `step`而且如果`end` `counter`  >=   <=  `end` 是負值`step` , 則為。  
  
 如果您在迴圈內變更`counter`的值, 則您的程式碼可能會更容易讀取和 debug。 變更`start`、 `end`或`step`的值, 並不會影響第一次進入迴圈時所決定的反復專案值。  
  
 如果您嵌套迴圈, 編譯器在內部層級的`Next` `Next`語句之前遇到外部嵌套層級的語句時, 會發出錯誤信號。 不過, 只有當您在每個`counter` `Next`語句中指定時, 編譯器才會偵測到這個重迭的錯誤。  
  
### <a name="step-argument"></a>Step 引數  
 的值`step`可以是正數或負數。 這個參數會根據下表來決定迴圈處理:  
  
|**步驟值**|**迴圈執行 (如果**|  
|--------------------|--------------------------|  
|正數或零|`counter` <= `end`|  
|負|`counter` >= `end`|  
  
 的預設值`step`為1。  
  
### <a name="BKMK_Counter"></a>Counter 引數  
 下表指出是否`counter`定義範圍為整個`For…Next`迴圈的新本機變數。 這項決定取決於`datatype`是否存在, 以及`counter`是否已定義。  
  
|`datatype`存在嗎？|已經`counter`定義了嗎？|Result (是否`counter`定義範圍設定為整個`For...Next`迴圈的新區域變數)|  
|----------------------------|-----------------------------------|-------------------------------------------------------------------------------------------------------------|  
|否|是|否, 因為`counter`已經定義過。 如果的範圍`counter`不是程式的本機, 就會發生編譯時期警告。|  
|否|否|是的。 資料類型是從`start`、 `end`和`step`運算式推斷而來。 如需型別推斷的詳細資訊, 請參閱[Option 推斷語句](../../../visual-basic/language-reference/statements/option-infer-statement.md)和[區欄位型別推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。|  
|是|是|是, 但只有在程式之外`counter`定義了現有的變數時。 該變數會保持不變。 如果現有`counter`變數的範圍是程式的本機, 就會發生編譯時期錯誤。|  
|是|否|是的。|  
  
 的資料類型`counter`決定反復專案的類型, 必須是下列其中一種類型:  
  
- `Byte`、 `SByte`、 、、`Integer`、、、、、或。`Double` `UShort` `Short` `UInteger` `ULong` `Long` `Decimal` `Single`  
  
- 使用[Enum 語句](../../../visual-basic/language-reference/statements/enum-statement.md)宣告的列舉。  
  
- `Object`。  
  
- 具有下列`T`運算子的類型, 其中`B`是`Boolean`可以在運算式中使用的類型。  
  
     `Public Shared Operator >= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator <= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator - (op1 As T, op2 As T) As T`  
  
     `Public Shared Operator + (op1 As T, op2 As T) As T`  
  
 您可以選擇性地指定`counter` `Next`語句中的變數。 此語法可改善程式的可讀性, 特別是當您有嵌套`For`的迴圈時。 您必須指定出現在對應`For`語句中的變數。  
  
 、和運算式可以評估為任何擴大至類型的`counter`資料類型。 `step` `end` `start` 如果您使用`counter`的使用者定義型別, 您可能必須`CType`定義轉換運算子`start`, 以將、 `end`或`step`的類型轉換成的類型`counter`。  
  
## <a name="example"></a>範例  
 下列範例會從泛型清單中移除所有元素。 而不是[針對每個 。下一個語句](../../../visual-basic/language-reference/statements/for-each-next-statement.md), 此範例會`For`顯示 。`Next`以遞減順序逐一查看的語句。 此範例會使用這項技術`removeAt` , 因為方法會使已移除專案之後的元素具有較低的索引值。  
  
 [!code-vb[VbVbalrStatements#114](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#114)]  
  
## <a name="example"></a>範例  
 下列範例會逐一查看使用[Enum 語句](../../../visual-basic/language-reference/statements/enum-statement.md)宣告的列舉。  
  
 [!code-vb[VbVbalrStatements#116](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#116)]  
  
## <a name="example"></a>範例  
 在下列範例中, 語句參數會使用`+`具有、 `-`、 `>=`和`<=`運算子之運算子多載的類別。  
  
 [!code-vb[VbVbalrStatements#117](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#117)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Collections.Generic.List%601>
- [迴圈結構](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [While...End While 陳述式](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Do...Loop 陳述式](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [巢狀控制結構](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit 陳述式](../../../visual-basic/language-reference/statements/exit-statement.md)
- [集合](../../programming-guide/concepts/collections.md)
