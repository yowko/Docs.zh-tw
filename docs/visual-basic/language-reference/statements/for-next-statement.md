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
ms.openlocfilehash: 8c54189499b7d5b52cf93b4a0ae6cc47356bf57e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="fornext-statement-visual-basic"></a>For...Next 陳述式 (Visual Basic)
重複指定的次數的陳述式群組。  
  
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
|`counter`|中需要`For`陳述式。 數值變數。 For 迴圈控制變數。 如需詳細資訊，請參閱[計數器引數](#BKMK_Counter)本主題稍後。|  
|`datatype`|選擇性。 資料型別`counter`。 如需詳細資訊，請參閱[計數器引數](#BKMK_Counter)本主題稍後。|  
|`start`|必要。 數值運算式。 `counter` 的初始值。|  
|`end`|必要。 數值運算式。 最終值`counter`。|  
|`step`|選擇性。 數值運算式。 所用的數量`counter`就會遞增每次迴圈。|  
|`statements`|選擇性。 一或多個陳述式之間`For`和`Next`執行指定的次數。|  
|`Continue For`|選擇性。 將控制權傳輸至下一個迴圈反覆項目。|  
|`Exit For`|選擇性。 控制權轉移出`For`迴圈。|  
|`Next`|必要。 結束的定義`For`迴圈。|  
  
> [!NOTE]
>  `To`關鍵字用於此陳述式中指定計數器的範圍。 您也可以使用此關鍵字[選取...陳述式的大小寫](../../../visual-basic/language-reference/statements/select-case-statement.md)和陣列宣告中。 如需陣列宣告的詳細資訊，請參閱[Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)。  
  
## <a name="simple-examples"></a>簡單範例  
 您使用`For`...`Next`結構時您想要一段時間重複一組陳述式。  
  
 在下列範例中，`index`變數開頭的值為 1，並隨著每次反覆運算迴圈，結束之後的值的`index`達到 5。  
  
 [!code-vb[VbVbalrStatements#111](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_1.vb)]  
  
 在下列範例中，`number`變數 2 開始，0.25，在每次反覆運算迴圈結束之後的值，可降低`number`到達 0。 `Step`引數的`-.25`減少 0.25 迴圈的每個反覆運算上的值。  
  
 [!code-vb[VbVbalrStatements#112](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_2.vb)]  
  
> [!TIP]
>  A[時...結束 While 陳述式](../../../visual-basic/language-reference/statements/while-end-while-statement.md)或[執行...迴圈陳述式](../../../visual-basic/language-reference/statements/do-loop-statement.md)就非常適合在不知道事先多少次迴圈中執行陳述式。 不過，當您希望執行迴圈的次數，特定數目`For`...`Next`迴圈是較佳選擇。 當您第一次輸入迴圈時，您可以判斷反覆項目數目。  
  
## <a name="nesting-loops"></a>巢狀迴圈  
 您可以巢狀`For`將放入另一個迴圈內的迴圈。 下列範例會示範巢狀`For`...`Next`具有不同逐步值的結構。 外部迴圈會建立迴圈的每個反覆項目的字串。 內部迴圈遞減迴圈計數器變數的迴圈的每個反覆項目。  
  
 [!code-vb[VbVbalrStatements#113](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_3.vb)]  
  
 當建立巢狀迴圈，每個迴圈必須具有唯一`counter`變數。  
  
 您也可以巢狀內彼此不同種類的控制結構。 如需詳細資訊，請參閱[巢狀控制結構](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)。  
  
## <a name="exit-for-and-continue-for"></a>針對結束後繼續  
 `Exit For`陳述式會立即結束`For`...`Next` 之後的陳述式的迴圈，並傳輸控制項`Next`陳述式。  
  
 `Continue For`陳述式控制將立即轉移到迴圈的下一個反覆項目。 如需詳細資訊，請參閱[Continue 陳述式](../../../visual-basic/language-reference/statements/continue-statement.md)。  
  
 下列範例說明使用`Continue For`和`Exit For`陳述式。  
  
 [!code-vb[VbVbalrStatements#115](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_4.vb)]  
  
 您可以將任意數目的`Exit For`中的陳述式`For`...`Next` 迴圈。 當用在巢狀`For`...`Next` 迴圈，`Exit For`結束最內層的迴圈，並將控制權傳輸至下一個高的層級的巢狀結構。  
  
 `Exit For` 通常是在您評估某些條件後 (例如，在`If`...`Then`...`Else`結構)。 您可能想要使用`Exit For`以下情況：  
  
-   繼續以逐一查看是不必要或不可能。 錯誤的數值或終止要求可能會建立此條件。  
  
-   A `Try`...`Catch`...`Finally`陳述式會攔截例外狀況。 您可能會使用`Exit For`結尾`Finally`區塊。  
  
-   您有無止盡的迴圈，即無法執行大型或甚至無限次數的迴圈。 如果您偵測到這種情況，您可以使用`Exit For`來逸出迴圈。 如需詳細資訊，請參閱[執行...迴圈陳述式](../../../visual-basic/language-reference/statements/do-loop-statement.md)。  
  
## <a name="technical-implementation"></a>技術實作  
 當`For`...`Next`迴圈開始，Visual Basic 會評估`start`， `end`，和`step`。 Visual Basic 會評估這些值只能在這個時間，然後指派`start`至`counter`。 陳述式之前區塊執行時，Visual Basic 比較`counter`至`end`。 如果`counter`已經大於`end`值 (或較小的 if`step`為負)、`For`迴圈結束，並控制傳遞到之後的陳述式`Next`陳述式。 否則，會執行陳述式區塊。  
  
 每次在 Visual Basic 遇到`Next`陳述式，它會`counter`由`step`並傳回給`For`陳述式。 一次，它會比較`counter`至`end`，並再次它執行區塊或結束迴圈，依據的結果。 此程序繼續執行直到`counter`傳遞`end`或`Exit For`遇到陳述式。  
  
 迴圈不會阻止直到`counter`經過`end`。 如果`counter`等於`end`，迴圈會繼續。 這項比較，決定是否要執行區塊會`counter`  <=  `end`如果`step`為正數及`counter`  >=  `end`如果`step`為負數。  
  
 如果您變更的值`counter`迴圈中，內部程式碼可能會更難閱讀及偵錯。 值變更`start`， `end`，或`step`並不會影響之前先進入迴圈時所決定的反覆項目值。  
  
 如果您建立巢狀迴圈，編譯器會發出錯誤信號如果遇到`Next`陳述式的外部的巢狀層級之前`Next`內部層次的陳述式。 不過，編譯器可以偵測此重疊錯誤，只有當您指定`counter`中每個`Next`陳述式。  
  
### <a name="step-argument"></a>步驟引數  
 值`step`可以是正數或負數。 這個參數會決定迴圈處理，根據下表：  
  
|**間距值**|**執行迴圈的條件**|  
|--------------------|--------------------------|  
|正數或零|`counter` <= `end`|  
|負|`counter` >= `end`|  
  
 預設值`step`為 1。  
  
###  <a name="BKMK_Counter"></a> 計數器引數  
 下表指出是否`counter`定義新的本機變數的範圍是整個`For…Next`迴圈。 這項判斷取決於是否`datatype`存在以及是否`counter`已經定義過了。  
  
|是`datatype`存在嗎？|是`counter`已經定義過了嗎？|結果 (是否`counter`定義新的本機變數的範圍是整個`For...Next`迴圈)|  
|----------------------------|-----------------------------------|-------------------------------------------------------------------------------------------------------------|  
|否|[是]|否，因為`counter`已經定義過了。 如果範圍`counter`不是本機程序，就會發生編譯時期警告。|  
|否|否|可以。 資料型別，會從推斷`start`， `end`，和`step`運算式。 類型推斷的相關資訊，請參閱[Option Infer 陳述式](../../../visual-basic/language-reference/statements/option-infer-statement.md)和[區域類型推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。|  
|[是]|[是]|是，但只有當現有`counter`程序之外定義變數。 該變數會維持獨立的。 如果現有的範圍`counter`變數是本機程序，就會發生編譯時期錯誤。|  
|[是]|否|可以。|  
  
 資料型別`counter`決定反覆項目，必須是下列類型的其中一種：  
  
-   A `Byte`， `SByte`， `UShort`， `Short`， `UInteger`， `Integer`， `ULong`， `Long`， `Decimal`， `Single`，或`Double`。  
  
-   您也可以使用宣告的列舉[Enum 陳述式](../../../visual-basic/language-reference/statements/enum-statement.md)。  
  
-   `Object`。  
  
-   型別`T`具有下列的運算子，其中`B`是可用於型別`Boolean`運算式。  
  
     `Public Shared Operator >= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator <= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator - (op1 As T, op2 As T) As T`  
  
     `Public Shared Operator + (op1 As T, op2 As T) As T`  
  
 您可以選擇性地指定`counter`變數中`Next`陳述式。 這個語法改進了您的程式的可讀性，特別是當您擁有巢狀`For`迴圈。 您必須指定此變數會出現在對應`For`陳述式。  
  
 `start`， `end`，和`step`運算式可以評估為任何資料類型可擴展成的型別`counter`。 如果您使用的使用者定義型別`counter`，您可能必須定義`CType`轉換運算子的類型轉換成`start`， `end`，或`step`的型別`counter`。  
  
## <a name="example"></a>範例  
 下列範例會移除所有項目，自泛型清單。 而不是[每個...下一個陳述式](../../../visual-basic/language-reference/statements/for-each-next-statement.md)，此範例將示範`For`...`Next`以遞減順序反覆運算的陳述式。 此範例會使用這項技術，因為`removeAt`方法會有較低的索引值的已移除項目之後的項目。  
  
 [!code-vb[VbVbalrStatements#114](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_5.vb)]  
  
## <a name="example"></a>範例  
 下列範例會逐一列舉宣告可透過[Enum 陳述式](../../../visual-basic/language-reference/statements/enum-statement.md)。  
  
 [!code-vb[VbVbalrStatements#116](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_6.vb)]  
  
## <a name="example"></a>範例  
 在下列範例中，陳述式參數使用運算子多載類別`+`， `-`， `>=`，和`<=`運算子。  
  
 [!code-vb[VbVbalrStatements#117](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_7.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Collections.Generic.List%601>  
 [迴圈結構](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [While...End While 陳述式](../../../visual-basic/language-reference/statements/while-end-while-statement.md)  
 [Do...Loop 陳述式](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [巢狀控制結構](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [Exit 陳述式](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [集合](../../programming-guide/concepts/collections.md)
