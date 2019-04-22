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
ms.openlocfilehash: 5d47d57b75005d5c13dbf8633981dfb2d57d3e90
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58826323"
---
# <a name="fornext-statement-visual-basic"></a>For...Next 陳述式 (Visual Basic)
一組陳述式會重複指定的次數。  
  
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
|`counter`|需要`For`陳述式。 數值變數。 For 迴圈控制變數。 如需詳細資訊，請參閱 < [Counter 引數](#BKMK_Counter)本主題稍後的。|  
|`datatype`|選擇性。 資料類型的`counter`。 如需詳細資訊，請參閱 < [Counter 引數](#BKMK_Counter)本主題稍後的。|  
|`start`|必要項。 數值運算式。 `counter` 的初始值。|  
|`end`|必要項。 數值運算式。 最終值`counter`。|  
|`step`|選擇性。 數值運算式。 所用的數量`counter`會遞增每次執行迴圈。|  
|`statements`|選擇性。 一或多個陳述式之間`For`和`Next`執行指定重試次數。|  
|`Continue For`|選擇性。 將控制權傳輸至下一個迴圈反覆項目。|  
|`Exit For`|選擇性。 控制權轉移共`For`迴圈。|  
|`Next`|必要項。 結束的定義`For`迴圈。|  
  
> [!NOTE]
>  `To`關鍵字用以在此陳述式中指定計數器的範圍。 您也可以使用這個關鍵字在[選取...Case 陳述式](../../../visual-basic/language-reference/statements/select-case-statement.md)和陣列宣告中。 如需陣列宣告的詳細資訊，請參閱[Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)。  
  
## <a name="simple-examples"></a>簡單的範例  
 您使用`For`...`Next`結構，當您想要重複執行陳述式的一組固定數目的時間。  
  
 在下列範例中，`index`變數的值為 1 以開頭，且會隨著每次反覆運算迴圈時，結束之後的值`index`達到 5。  
  
 [!code-vb[VbVbalrStatements#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#111)]  
  
 在下列範例中，`number`變數開始 2，並在每次反覆運算迴圈時，結束之後的值 0.25 可降低`number`到達 0。 `Step`引數`-.25`減少 0.25 迴圈的每個反覆運算上的值。  
  
 [!code-vb[VbVbalrStatements#112](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#112)]  
  
> [!TIP]
>  A[時...While 陳述式結束](../../../visual-basic/language-reference/statements/while-end-while-statement.md)或[執行...迴圈陳述式](../../../visual-basic/language-reference/statements/do-loop-statement.md)非常適合在不知道事先多少次，在迴圈中執行的陳述式。 不過，當您預期要執行迴圈以特定次數， `For`...`Next`迴圈是較好的選擇。 當您第一次輸入迴圈時，您可以判斷反覆項目的數目。  
  
## <a name="nesting-loops"></a>巢狀迴圈  
 您可以巢狀`For`放在另一個迴圈的迴圈。 下列範例會示範巢狀`For`...`Next`具有不同步驟值的結構。 外部迴圈會建立迴圈的每個反覆項目的字串。 「 內部迴圈遞減迴圈計數器變數的迴圈的每個反覆項目。  
  
 [!code-vb[VbVbalrStatements#113](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#113)]  
  
 當建立巢狀迴圈，每個迴圈必須具有唯一`counter`變數。  
  
 您也可以巢狀內彼此不同種類的控制結構。 如需詳細資訊，請參閱 <<c0> [ 巢狀控制結構](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)。  
  
## <a name="exit-for-and-continue-for"></a>針對結束後繼續  
 `Exit For`陳述式會立即結束`For`...`Next` 後面的陳述式的迴圈和傳輸控制項`Next`陳述式。  
  
 `Continue For`陳述式控制將立即轉移到迴圈的下一個反覆項目。 如需詳細資訊，請參閱 < [Continue 陳述式](../../../visual-basic/language-reference/statements/continue-statement.md)。  
  
 下列範例示範如何將`Continue For`和`Exit For`陳述式。  
  
 [!code-vb[VbVbalrStatements#115](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#115)]  
  
 您可以將任意數目的放`Exit For`中的陳述式`For`...`Next` 迴圈。 當用在巢狀`For`...`Next` 迴圈、`Exit For`結束最內層的迴圈，並將控制權傳輸至下一個較高的層級，巢狀。  
  
 `Exit For` 通常用在您評估某些條件後 (例如，在`If`...`Then`...`Else`結構)。 您可能想要使用`Exit For`下列條件：  
  
-   繼續向逐一查看是不必要或不可能。 錯誤的數值或終止要求可能會建立這種情況。  
  
-   A `Try`...`Catch`...`Finally`陳述式攔截到例外狀況。 您可以使用`Exit For`結尾的`Finally`區塊。  
  
-   您有無止盡的迴圈，也就是無法執行大型或甚至是無限次數的迴圈。 如果您偵測到這種情況，您可以使用`Exit For`來逸出迴圈。 如需詳細資訊，請參閱[執行...迴圈陳述式](../../../visual-basic/language-reference/statements/do-loop-statement.md)。  
  
## <a name="technical-implementation"></a>技術實作  
 當`For`...`Next`迴圈開始，Visual Basic 會評估`start`， `end`，和`step`。 Visual Basic 會評估這些值只能在此時間，然後指派`start`至`counter`。 之前的陳述式區塊會執行，Visual Basic 比較`counter`至`end`。 如果`counter`已經是大於`end`值 (或較小的 if`step`為負數)，則`For`迴圈結束，並控制傳遞到後面的陳述式`Next`陳述式。 否則，會執行陳述式區塊。  
  
 每次 Visual Basic 遇到`Next`陳述式，就會自動遞增`counter`由`step`，並返回`For`陳述式。 再次比較`counter`至`end`，和一次它執行的區塊或結束迴圈時，根據結果。 此程序一直`counter`通過`end`或`Exit For`遇到陳述式。  
  
 迴圈不停止直到`counter`已經過`end`。 如果`counter`等於`end`，迴圈會繼續。 比較，決定是否要執行區塊會`counter`  <=  `end`如果`step`正並`counter`  >=  `end`如果`step`為負數。  
  
 如果您變更的值`counter`在迴圈中，內您的程式碼可能會更難閱讀及偵錯。 變更的值`start`， `end`，或`step`並不會影響所決定時初次進入迴圈的反覆項目值。  
  
 如果您使用巢狀迴圈，編譯器會發出錯誤信號如果遇到`Next`陳述式的外部的巢狀層級之前`Next`內部層級的陳述式。 不過，編譯器可以偵測此重疊錯誤，只有當您指定`counter`在每個`Next`陳述式。  
  
### <a name="step-argument"></a>步驟引數  
 值`step`可以是正數或負數。 這個參數會決定迴圈處理，根據下表：  
  
|**間距值**|**執行迴圈的條件**|  
|--------------------|--------------------------|  
|正數或零|`counter` <= `end`|  
|負|`counter` >= `end`|  
  
 預設值`step`為 1。  
  
### <a name="BKMK_Counter"></a> Counter 引數  
 下表會指出是否`counter`定義新的本機變數的範圍是整個`For…Next`迴圈。 這個決定取決於是否`datatype`存在以及是否`counter`已經定義。  
  
|是`datatype`存在？|是`counter`已經定義嗎？|結果 (是否`counter`定義新的本機變數的範圍是整個`For...Next`迴圈)|  
|----------------------------|-----------------------------------|-------------------------------------------------------------------------------------------------------------|  
|否|是|否，因為`counter`已經定義。 如果範圍`counter`不是本機程序，就會發生編譯時期警告。|  
|否|否|可以。 資料類型從推斷`start`， `end`，和`step`運算式。 型別推斷的相關資訊，請參閱[Option Infer 陳述式](../../../visual-basic/language-reference/statements/option-infer-statement.md)並[區域型別推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。|  
|是|是|可以，但只有當現有`counter`變數定義在程序之外。 該變數會維持獨立的。 如果現有的範圍`counter`變數是本機程序，就會發生編譯時期錯誤。|  
|是|否|可以。|  
  
 資料類型`counter`決定反覆項目，必須是下列類型的其中一種：  
  
-   A `Byte`， `SByte`， `UShort`， `Short`， `UInteger`， `Integer`， `ULong`， `Long`， `Decimal`， `Single`，或`Double`。  
  
-   您使用宣告列舉[Enum 陳述式](../../../visual-basic/language-reference/statements/enum-statement.md)。  
  
-   `Object`。  
  
-   型別`T`具有下列的運算子，其中`B`是類型，可用於`Boolean`運算式。  
  
     `Public Shared Operator >= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator <= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator - (op1 As T, op2 As T) As T`  
  
     `Public Shared Operator + (op1 As T, op2 As T) As T`  
  
 您可以選擇性地指定`counter`變數中`Next`陳述式。 此語法可改善可讀性的程式碼，尤其是如果您有巢狀`For`迴圈。 您必須指定此變數會出現在對應`For`陳述式。  
  
 `start`， `end`，並`step`運算式可以評估為任何資料類型可擴展成的型別`counter`。 如果您使用的使用者定義類型`counter`，您可能必須定義`CType`轉換運算子的類型轉換成`start`， `end`，或`step`的型別`counter`。  
  
## <a name="example"></a>範例  
 下列範例會移除的泛型清單中的所有項目。 而不是[每個...下一個陳述式](../../../visual-basic/language-reference/statements/for-each-next-statement.md)，此範例將示範`For`...`Next`以遞減順序反覆運算的陳述式。 此範例會使用這項技術，因為`removeAt`方法導致項目後面移除的項目具有較低的索引值。  
  
 [!code-vb[VbVbalrStatements#114](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#114)]  
  
## <a name="example"></a>範例  
 下列範例會逐一宣告可透過列舉[Enum 陳述式](../../../visual-basic/language-reference/statements/enum-statement.md)。  
  
 [!code-vb[VbVbalrStatements#116](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#116)]  
  
## <a name="example"></a>範例  
 在下列範例中，陳述式參數使用類別，具有的運算子多載`+`， `-`， `>=`，和`<=`運算子。  
  
 [!code-vb[VbVbalrStatements#117](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#117)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Collections.Generic.List%601>
- [迴圈結構](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [While...End While 陳述式](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Do...Loop 陳述式](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [巢狀控制結構](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit 陳述式](../../../visual-basic/language-reference/statements/exit-statement.md)
- [集合](../../programming-guide/concepts/collections.md)
