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
ms.openlocfilehash: 6896c6cfb4ec5d6207011e56b72639c459120e53
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404637"
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

|部分|描述|
|----------|-----------------|
|`counter`|語句中的必要項 `For` 。 數值變數。 迴圈的控制變數。 如需詳細資訊，請參閱本主題稍後的[計數器引數](#BKMK_Counter)。|
|`datatype`|選擇性。 的資料類型 `counter` 。 如需詳細資訊，請參閱本主題稍後的[計數器引數](#BKMK_Counter)。|
|`start`|必要。 數值運算式。 `counter` 的初始值。|
|`end`|必要。 數值運算式。 的最終值 `counter` 。|
|`step`|選擇性。 數值運算式。 `counter`每次透過迴圈遞增的數量。|
|`statements`|選擇性。 `For`在和之間 `Next` 執行指定次數的一或多個語句。|
|`Continue For`|選擇性。 將控制權轉移至下一個迴圈反復專案。|
|`Exit For`|選擇性。 將控制權轉移給 `For` 迴圈。|
|`Next`|必要。 終止迴圈的定義 `For` 。|

> [!NOTE]
> `To`此語句中會使用關鍵字來指定計數器的範圍。 您也可以在 [選取 ...] 中使用此關鍵字[Case 語句](select-case-statement.md)和陣列宣告。 如需陣列宣告的詳細資訊，請參閱[Dim 語句](dim-statement.md)。

## <a name="simple-examples"></a> 簡單範例

`For` `Next` 當您想要以設定的次數重複一組語句時，可以使用 ... 結構。

在下列範例中， `index` 變數會以1的值開頭，並隨著迴圈的每個反復專案而遞增，並在的值 `index` 到達5之後結束。

[!code-vb[VbVbalrStatements#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#111)]

在下列範例中， `number` 變數會從2開始，並在迴圈的每次反覆運算時減少0.25，並在的值 `number` 到達0之後結束。 的 `Step` 引數會 `-.25` 在迴圈的每個反復專案上，將值減少0.25。

[!code-vb[VbVbalrStatements#112](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#112)]

> [!TIP]
> A [While .。。End While 語句](while-end-while-statement.md)或[Do .。。](do-loop-statement.md)當您事先不知道要在迴圈中執行語句的次數時，Loop 語句的運作效果很好。 不過，如果您預期會執行迴圈特定次數，則 `For` ... `Next` 迴圈是較佳的選擇。 您會在第一次進入迴圈時判斷反覆運算次數。

## <a name="nesting-loops"></a>嵌套迴圈

您可以藉 `For` 由在另一個迴圈中放入迴圈來加以嵌套。 下列範例示範 `For` `Next` 具有不同步驟值的 nested 結構。 外部迴圈會為迴圈的每個反覆運算建立一個字串。 內部迴圈會針對迴圈的每個反覆運算遞減迴圈計數器變數。

[!code-vb[VbVbalrStatements#113](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#113)]

當嵌套迴圈時，每個迴圈都必須有唯一的 `counter` 變數。

您也可以將不同類型的控制結構分別放在其中。 如需詳細資訊，請參閱[嵌套控制項結構](../../programming-guide/language-features/control-flow/nested-control-structures.md)。

## <a name="exit-for-and-continue-for"></a>結束並繼續進行

`Exit For`語句會立即結束 `For` .。。`Next` 迴圈，並將控制權轉移至語句後面的語句 `Next` 。

`Continue For`語句會立即將控制權轉移到迴圈的下一個反復專案。 如需詳細資訊，請參閱[Continue 語句](continue-statement.md)。

下列範例說明如何使用 `Continue For` 和 `Exit For` 語句。

[!code-vb[VbVbalrStatements#115](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#115)]

您可以將任意數目的 `Exit For` 語句放在 `For` .。。`Next` loop： 在 nested 中使用 `For` 時 .。。`Next` 迴圈，結束 `Exit For` 最內層的迴圈，並將控制權轉移至下一個較高層級的嵌套。

`Exit For`通常是在評估某個條件之後使用（例如，在 `If` ... `Then`...`Else`結構）。 在下列情況下，您可能會想要使用 `Exit For` ：

- 繼續進行反覆運算是不必要或不可能的。 錯誤值或終止要求可能會建立此條件。

- 答 `Try` `Catch` ：...`Finally`語句會攔截例外狀況。 您可以 `Exit For` 在區塊結尾使用 `Finally` 。

- 您有一個無止盡的迴圈，這是一種迴圈，可能會執行很長或甚至無限次數。 如果您偵測到這種情況，您可以使用 `Exit For` 來將迴圈轉義。 如需詳細資訊，請參閱[Do .。。Loop 語句](do-loop-statement.md)。

## <a name="technical-implementation"></a>技術實作

當 `For` ... `Next` 迴圈啟動時，Visual Basic 會評估 `start` 、 `end` 和 `step` 。 Visual Basic 只會在此時評估這些值，然後將指派 `start` 給 `counter` 。 在執行語句區塊之前，Visual Basic 會 `counter` 與進行比較 `end` 。 如果 `counter` 已經大於 `end` 值（如果是負數，則為較小 `step` ），迴圈就會 `For` 結束，並將控制權傳遞至語句後面 `Next` 的語句。 否則，會執行語句區塊。

每次 Visual Basic 遇到 `Next` 語句時，它會 `counter` 遞增 `step` 並返回 `For` 語句。 同樣地，它會與進行比較 `counter` `end` ，並再次執行區塊或結束迴圈，視結果而定。 此程式會繼續 `counter` 進行，直到 `end` 遇到 pass 或語句為止 `Exit For` 。

迴圈不會停止，直到 `counter` 通過為止 `end` 。 如果 `counter` 等於 `end` ，迴圈就會繼續。 判斷是否要執行區塊的比較是正向 `counter`  <=  `end` `step` ，而且 `counter`  >=  `end` 如果 `step` 是負值，則為。

如果您在迴圈內變更的值 `counter` ，則您的程式碼可能會更容易讀取和 debug。 變更 `start` 、或的值， `end` `step` 並不會影響第一次進入迴圈時所決定的反復專案值。

如果您嵌套迴圈，編譯器在 `Next` 內部層級的語句之前遇到外部嵌套層級的語句時，會發出錯誤信號 `Next` 。 不過，只有當您 `counter` 在每個語句中指定時，編譯器才會偵測到這個重迭的錯誤 `Next` 。

### <a name="step-argument"></a>Step 引數

的值 `step` 可以是正數或負數。 這個參數會根據下表來決定迴圈處理：

|**步驟值**|**迴圈執行（如果**|
|--------------------|--------------------------|
|正數或零|`counter` <= `end`|
|Neutral|`counter` >= `end`|

`step` 的預設值為 1。

### <a name="counter-argument"></a><a name="BKMK_Counter"></a>Counter 引數

下表指出是否 `counter` 定義範圍為整個迴圈的新本機變數 `For…Next` 。 這項決定取決於是否 `datatype` 存在，以及是否 `counter` 已定義。

|`datatype`存在嗎？|`counter`已經定義了嗎？|Result （是否 `counter` 定義範圍設定為整個迴圈的新區域變數 `For...Next` ）|
|----------------------------|-----------------------------------|-------------------------------------------------------------------------------------------------------------|
|否|是|否，因為 `counter` 已經定義過。 如果的範圍 `counter` 不是程式的本機，就會發生編譯時期警告。|
|No|否|是。 資料類型是從 `start` 、 `end` 和運算式推斷而來 `step` 。 如需型別推斷的詳細資訊，請參閱[Option 推斷語句](option-infer-statement.md)和[區欄位型別推斷](../../programming-guide/language-features/variables/local-type-inference.md)。|
|Yes|Yes|是，但只有在 `counter` 程式之外定義了現有的變數時。 該變數會保持不變。 如果現有變數的範圍 `counter` 是程式的本機，就會發生編譯時期錯誤。|
|是|否|是。|

的資料類型 `counter` 決定反復專案的類型，必須是下列其中一種類型：

- 、、、、、、、、、 `Byte` `SByte` `UShort` `Short` `UInteger` `Integer` `ULong` `Long` `Decimal` `Single` 或 `Double` 。

- 使用[Enum 語句](enum-statement.md)宣告的列舉。

- `Object`。

- `T`具有下列運算子的類型，其中 `B` 是可以在運算式中使用的類型 `Boolean` 。

  `Public Shared Operator >= (op1 As T, op2 As T) As B`

  `Public Shared Operator <= (op1 As T, op2 As T) As B`

  `Public Shared Operator - (op1 As T, op2 As T) As T`

  `Public Shared Operator + (op1 As T, op2 As T) As T`

您可以選擇性地指定 `counter` 語句中的變數 `Next` 。 此語法可改善程式的可讀性，特別是當您有嵌套的 `For` 迴圈時。 您必須指定出現在對應語句中的變數 `For` 。

`start`、 `end` 和 `step` 運算式可以評估為任何擴大至類型的資料類型 `counter` 。 如果您使用的使用者定義型別 `counter` ，您可能必須定義 `CType` 轉換運算子，以將、或的類型轉換成的 `start` `end` `step` 類型 `counter` 。

## <a name="example"></a>範例

下列範例會從泛型清單中移除所有元素。 而不是[針對每個 .。。下一個語句](for-each-next-statement.md)，此範例會顯示逐一查看 `For` `Next` 遞減順序的 ... 語句。 此範例會使用這項技術，因為 `removeAt` 方法會使已移除專案之後的元素具有較低的索引值。

[!code-vb[VbVbalrStatements#114](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#114)]

## <a name="example"></a>範例

下列範例會逐一查看使用[Enum 語句](enum-statement.md)宣告的列舉。

[!code-vb[VbVbalrStatements#116](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#116)]

## <a name="example"></a>範例

在下列範例中，語句參數會使用具有 `+` 、 `-` 、 `>=` 和運算子之運算子多載的類別 `<=` 。

[!code-vb[VbVbalrStatements#117](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#117)]

## <a name="see-also"></a>另請參閱

- <xref:System.Collections.Generic.List%601>
- [迴圈結構](../../programming-guide/language-features/control-flow/loop-structures.md)
- [While...End While 陳述式](while-end-while-statement.md)
- [Do...Loop 陳述式](do-loop-statement.md)
- [巢狀控制結構](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit 陳述式](exit-statement.md)
- [集合](../../programming-guide/concepts/collections.md)
