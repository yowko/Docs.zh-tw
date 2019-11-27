---
title: For...Next 陳述式
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
ms.openlocfilehash: 3cae44abb8e790542f11e6c5a5f1e317675ff988
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351190"
---
# <a name="fornext-statement-visual-basic"></a>For...Next 陳述式 (Visual Basic)

重複指定次數的語句群組。

## <a name="syntax"></a>語法

```vb
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
|`counter`|在 `For` 語句中是必要的。 數值變數。 迴圈的控制變數。 如需詳細資訊，請參閱本主題稍後的[計數器引數](#BKMK_Counter)。|
|`datatype`|選擇性。 `counter`的資料類型。 如需詳細資訊，請參閱本主題稍後的[計數器引數](#BKMK_Counter)。|
|`start`|必要。 數值運算式。 `counter` 的初始值。|
|`end`|必要。 數值運算式。 `counter`的最終值。|
|`step`|選擇性。 數值運算式。 每次執行迴圈時，`counter` 的遞增量。|
|`statements`|選擇性。 `For` 和 `Next` 之間的一個或多個語句執行指定的次數。|
|`Continue For`|選擇性。 將控制權轉移至下一個迴圈反復專案。|
|`Exit For`|選擇性。 將控制權轉移 `For` 迴圈。|
|`Next`|必要。 結束 `For` 迴圈的定義。|

> [!NOTE]
> 這個語句中會使用 `To` 關鍵字來指定計數器的範圍。 您也可以在 [選取 ...] 中使用此關鍵字[Case 語句](../../../visual-basic/language-reference/statements/select-case-statement.md)和陣列宣告。 如需陣列宣告的詳細資訊，請參閱[Dim 語句](../../../visual-basic/language-reference/statements/dim-statement.md)。

## <a name="simple-examples"></a>簡單範例

當您想要以設定的次數重複一組語句時，您可以使用 `For`...`Next` 結構。

在下列範例中，`index` 變數的開頭為1的值，而且會隨著迴圈的每個反復專案而遞增，並在 `index` 的值到達5之後結束。

[!code-vb[VbVbalrStatements#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#111)]

在下列範例中，`number` 變數會從2開始，並在迴圈的每次反覆運算時減少0.25，並在 `number` 的值到達0之後結束。 `-.25` 的 `Step` 引數會在迴圈的每個反覆運算上減少0.25 的值。

[!code-vb[VbVbalrStatements#112](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#112)]

> [!TIP]
> A [While .。。End While 語句](../../../visual-basic/language-reference/statements/while-end-while-statement.md)或[Do .。。](../../../visual-basic/language-reference/statements/do-loop-statement.md)當您事先不知道要在迴圈中執行語句的次數時，Loop 語句的運作效果很好。 不過，當您預期會執行特定次數的迴圈時，`For`...`Next` 迴圈是較佳的選擇。 您會在第一次進入迴圈時判斷反覆運算次數。

## <a name="nesting-loops"></a>嵌套迴圈

您可以藉由將一個迴圈放在另一個迴圈中，來將 `For` 迴圈。 下列範例示範具有不同步驟值的 nested `For`...`Next` 結構。 外部迴圈會為迴圈的每個反覆運算建立一個字串。 內部迴圈會針對迴圈的每個反覆運算遞減迴圈計數器變數。

[!code-vb[VbVbalrStatements#113](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#113)]

當嵌套迴圈時，每個迴圈都必須有唯一的 `counter` 變數。

您也可以將不同類型的控制結構分別放在其中。 如需詳細資訊，請參閱[嵌套控制項結構](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)。

## <a name="exit-for-and-continue-for"></a>結束並繼續進行

`Exit For` 語句會立即離開 `For`...`Next` 迴圈，並將控制權轉移至 `Next` 語句後面的語句。

`Continue For` 語句會立即將控制權轉移到迴圈的下一個反復專案。 如需詳細資訊，請參閱[Continue 語句](../../../visual-basic/language-reference/statements/continue-statement.md)。

下列範例說明如何使用 `Continue For` 和 `Exit For` 語句。

[!code-vb[VbVbalrStatements#115](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#115)]

您可以將任意數目的 `Exit For` 語句放在 `For`...`Next` loop： 在 nested `For`中使用時 ...`Next` 迴圈，`Exit For` 會結束最內層的迴圈，並將控制權轉移至下一個較高層級的嵌套。

在您評估某個條件（例如，在 `If`...`Then`...`Else` 結構）之後，通常會使用 `Exit For`。 在下列情況中，您可能會想要使用 `Exit For`：

- 繼續進行反覆運算是不必要或不可能的。 錯誤值或終止要求可能會建立此條件。

- `Try`...`Catch`...`Finally` 語句會攔截例外狀況。 您可以使用 `Finally` 區塊結尾處的 `Exit For`。

- 您有一個無止盡的迴圈，這是一種迴圈，可能會執行很長或甚至無限次數。 如果您偵測到這種情況，您可以使用 `Exit For` 來對迴圈進行 escape。 如需詳細資訊，請參閱[Do .。。Loop 語句](../../../visual-basic/language-reference/statements/do-loop-statement.md)。

## <a name="technical-implementation"></a>技術實作

當 `For`...`Next` 迴圈啟動時，Visual Basic 會評估 `start`、`end`和 `step`。 Visual Basic 只會在這段時間評估這些值，然後將 `start` 指派給 `counter`。 在執行語句區塊之前，Visual Basic 會比較 `counter` 與 `end`。 如果 `counter` 已經大於 `end` 值（如果 `step` 是負數，則較小），`For` 迴圈就會結束，並將控制權傳遞至緊接在 `Next` 語句之後的語句。 否則，會執行語句區塊。

每次 Visual Basic 遇到 `Next` 語句時，它會以 `step` 遞增 `counter`，並返回 `For` 語句。 同樣地，它會比較 `counter` 與 `end`，然後根據結果，執行區塊或結束迴圈。 此程式會繼續進行，直到 `counter` 通過 `end` 或遇到 `Exit For` 語句為止。

直到 `counter` 傳遞 `end`後，迴圈才會停止。 如果 `counter` 等於 `end`，迴圈就會繼續進行。 如果 `step` 為正數，則決定是否要執行區塊的比較 `counter` <= `end` 如果 `counter`為負數，則  >= `end` `step`。

如果您在迴圈內變更 `counter` 的值，您的程式碼可能會更容易讀取和 debug。 變更 `start`、`end`或 `step` 的值，並不會影響第一次進入迴圈時所決定的反復專案值。

如果您嵌套迴圈，編譯器在內部層級的 `Next` 語句之前遇到外部嵌套層級的 `Next` 語句時，會發出錯誤信號。 不過，只有當您在每個 `Next` 語句中指定 `counter` 時，編譯器才能夠偵測到這個重迭的錯誤。

### <a name="step-argument"></a>Step 引數

`step` 的值可以是正數或負數。 這個參數會根據下表來決定迴圈處理：

|**步驟值**|**迴圈執行（如果**|
|--------------------|--------------------------|
|正數或零|`counter` <= `end`|
|負|`counter` >= `end`|

`step` 的預設值為1。

### <a name="BKMK_Counter"></a>Counter 引數

下表指出 `counter` 是否定義範圍設定為整個 `For…Next` 迴圈的新區域變數。 這項決定取決於是否存在 `datatype`，以及 `counter` 是否已定義。

|`datatype` 存在嗎？|`counter` 已經定義了嗎？|Result （`counter` 是否定義範圍設定為整個 `For...Next` 迴圈的新區域變數）|
|----------------------------|-----------------------------------|-------------------------------------------------------------------------------------------------------------|
|否|[是]|否，因為已定義 `counter`。 如果 `counter` 的範圍不是程式的本機，就會發生編譯時期警告。|
|否|否|可以。 資料類型是從 [`start`]、[`end`] 和 [`step`] 運算式推斷而來。 如需型別推斷的詳細資訊，請參閱[Option 推斷語句](../../../visual-basic/language-reference/statements/option-infer-statement.md)和[區欄位型別推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。|
|[是]|[是]|是，但只有在程式之外定義了現有的 `counter` 變數時。 該變數會保持不變。 如果現有 `counter` 變數的範圍是程式的本機，就會發生編譯時期錯誤。|
|[是]|否|可以。|

`counter` 的資料類型會決定反復專案的類型，必須是下列其中一種類型：

- `Byte`、`SByte`、`UShort`、`Short`、`UInteger`、`Integer`、`ULong`、`Long`、`Decimal`、`Single`或 `Double`。

- 使用[Enum 語句](../../../visual-basic/language-reference/statements/enum-statement.md)宣告的列舉。

- `Object`。

- 具有下列運算子的類型 `T`，其中 `B` 是可用於 `Boolean` 運算式的類型。

  `Public Shared Operator >= (op1 As T, op2 As T) As B`

  `Public Shared Operator <= (op1 As T, op2 As T) As B`

  `Public Shared Operator - (op1 As T, op2 As T) As T`

  `Public Shared Operator + (op1 As T, op2 As T) As T`

您可以選擇性地在 `Next` 語句中指定 `counter` 變數。 此語法可改善程式的可讀性，特別是如果您有嵌套的 `For` 迴圈。 您必須指定出現在對應的 `For` 語句中的變數。

`start`、`end`和 `step` 運算式可以評估為任何擴大至 `counter`類型的資料類型。 如果您使用 `counter`的使用者定義型別，您可能必須定義 `CType` 轉換運算子，以將 `start`、`end`或 `step` 的類型轉換成 `counter`的類型。

## <a name="example"></a>範例

下列範例會從泛型清單中移除所有元素。 而不是[針對每個 .。。下一個語句](../../../visual-basic/language-reference/statements/for-each-next-statement.md)，此範例會顯示以遞減順序逐一查看的 `For`...`Next` 語句。 此範例會使用這項技術，因為 `removeAt` 方法會使已移除專案之後的元素具有較低的索引值。

[!code-vb[VbVbalrStatements#114](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#114)]

## <a name="example"></a>範例

下列範例會逐一查看使用[Enum 語句](../../../visual-basic/language-reference/statements/enum-statement.md)宣告的列舉。

[!code-vb[VbVbalrStatements#116](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#116)]

## <a name="example"></a>範例

在下列範例中，語句參數使用的類別具有 `+`、`-`、`>=`和 `<=` 運算子的運算子多載。

[!code-vb[VbVbalrStatements#117](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#117)]

## <a name="see-also"></a>請參閱

- <xref:System.Collections.Generic.List%601>
- [迴圈結構](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [While...End While 陳述式](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Do...Loop 陳述式](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [巢狀控制結構](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit 陳述式](../../../visual-basic/language-reference/statements/exit-statement.md)
- [集合](../../programming-guide/concepts/collections.md)
