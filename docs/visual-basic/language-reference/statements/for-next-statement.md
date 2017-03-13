---
title: "For...Next 陳述式 (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Step"
  - "vb.Next"
  - "vb.To"
  - "vb.for"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "無限迴圈"
  - "Next 關鍵字，For...Next 陳述式"
  - "For 關鍵字 [Visual Basic]，For...Next 陳述式"
  - "Step 關鍵字，For...Next 陳述式"
  - "運算子多載，For...Next 陳述式"
  - "To 關鍵字，For...Next 陳述式"
  - "無窮迴圈"
  - "迴圈，無窮"
  - "指示，重複"
  - "Next 陳述式，For...Next"
  - "For...Next 陳述式"
  - "迴圈結構，For...Next"
  - "迴圈，無限"
  - "Exit 陳述式，For...Next 陳述式"
  - "For 陳述式"
ms.assetid: f5fc0d51-67ce-4c36-9f09-31c9a91c94e9
caps.latest.revision: 64
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 64
---
# For...Next 陳述式 (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

按指定次數重複一組陳述式  
  
## 語法  
  
```  
For counter [ As datatype ] = start To end [ Step step ]  
    [ statements ]  
    [ Continue For ]  
    [ statements ]  
    [ Exit For ]  
    [ statements ]  
Next [ counter ]  
```  
  
## 組件  
  
|組件|描述|  
|--------|--------|  
|`counter`|在 `For` 陳述式中為必要項。  數值變數。  迴圈 \(Loop\) 的控制項變數。  如需詳細資訊，請參閱本主題中稍後的[計數器引數](#BKMK_Counter)。|  
|`datatype`|選擇項。  `counter` 的資料型別。  如需詳細資訊，請參閱本主題中稍後的[計數器引數](#BKMK_Counter)。|  
|`start`|必要項。  數值運算式。  `counter` 的初始值。|  
|`end`|必要項。  數值運算式。  `counter` 的最終值。|  
|`step`|選擇項。  數值運算式。  在迴圈中 `counter` 每次增加的數量。|  
|`statements`|選擇項。  在 `For` 和 `Next` 之間執行指定次數的一或多個陳述式。|  
|`Continue For`|選擇項。  將控制權轉移到下一個迴圈反覆運算。|  
|`Exit For`|選擇項。  從 `For` 迴圈當中傳出控制權。|  
|`Next`|必要項。  結束 `For` 迴圈的定義。|  
  
> [!NOTE]
>  `To` 關鍵字可在此陳述式為計數器指定範圍。  您可以在 [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md) 和陣列宣告也可以使用這個關鍵字。  如需陣列宣告的詳細資訊，請參閱 [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)。  
  
## 簡單的範例  
 例如，當您想要重複一組陳述式數次時，您可以使用 `For``Next` …結構。  
  
 在下列範例中， `index` 變數是以值 1 並加入具有每次反覆運算迴圈，結束，在 `index` 到達 5. 之後的值。  
  
 [!code-vb[VbVbalrStatements#111](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_1.vb)]  
  
 在下列範例中， `number` 變數從 2 開始減少 0.25 在每次反覆運算迴圈，結束，在 `number` 到達 0 後的值。  `-.25` 的 `Step` 引數減少值的 0.25 在每次反覆運算迴圈。  
  
 [!code-vb[VbVbalrStatements#112](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_2.vb)]  
  
> [!TIP]
>  [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md) 或 [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md) 很適合使用，當您事先不知道次數執行迴圈中的陳述式。  不過，若預期會執行特定次數的迴圈，則最好選用 `For`...`Next` 迴圈。  初次進入迴圈時，判斷反覆運算的次數。  
  
## 巢狀迴圈  
 您可以將一個迴圈置於另一個迴圈內，使 `For` 迴圈套疊成巢狀。  下列範例示範具有不同間距值的巢狀 `For`...`Next` 結構。  外部迴圈會在迴圈的每次反覆運算中建立字串。  內部迴圈會在迴圈的每次反覆運算中遞減迴圈計數器變數。  
  
 [!code-vb[VbVbalrStatements#113](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_3.vb)]  
  
 當巢狀迴圈，每個迴圈必須具備唯一的 `counter` 變數。  
  
 您可以將不同類型的控制結構相互套疊成巢狀。  如需詳細資訊，請參閱[Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)。  
  
## 關閉並繼續。  
 `Exit For` 陳述式會立即關閉 `For``Next` …迴圈和將控制權傳輸至接在 `Next` 陳述式的陳述式。  
  
 `Continue For` 陳述式會立即將控制權轉移至迴圈的下一個反覆運算。  如需詳細資訊，請參閱[Continue Statement](../../../visual-basic/language-reference/statements/continue-statement.md)。  
  
 下列範例說明 `Continue For` 和 `Exit For` 陳述式的用法。  
  
 [!code-vb[VbVbalrStatements#115](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_4.vb)]  
  
 您可以將任意數目的 `Exit For` 陳述式放在 `For`…`Next` 迴圈中。  用於巢狀的 `For`…`Next` 迴圈內時，`Exit For` 會退出最內層的迴圈，並將控制權轉移到下一個較高的巢狀層次。  
  
 `Exit For` ，通常會在評估某些條件之後 \(例如，在 `If`…`Then`…`Else` 結構\)。  在下列情況中，您可能會想要使用 `Exit For`：  
  
-   繼續逐一查看則沒有必要或是不可行。  錯誤值或終止要求可能會產生這個條件。  
  
-   `Try` `Catch` `Finally` ……陳述式攔截例外狀況。  您可能在 `Finally` 區塊的結尾處使用 `Exit For`。  
  
-   您有一個無限迴圈，迴圈就是會執行大或甚至無限次數。  如果您偵測到這類狀況，可以使用 `Exit For` 逸出此迴圈。  如需詳細資訊，請參閱[Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md)。  
  
## 技術實作  
 當 `For`...`Next` 迴圈開始時，Visual Basic 會評估 `start`、`end` 和 `step`。  Visual Basic 此時只評估這些值並將 `start` 設為 `counter`。  在陳述式區塊執行之前， Visual Basic 與 `end`比較的 `counter` 。  如果 `counter` 大於 `end` 值 \(或小，如果 `step` 是負值\)， `For` 迴圈結束和控制項傳遞至已在 `Next` 之後的陳述式之後的陳述式。  否則，陳述式區塊執行。  
  
 Visual Basic 每次遇到 `Next` 陳述式時，便會依 `step` 遞增 `counter`，並回到 `For` 陳述式。  接著再比較 `counter` 和 `end`，然後根據結果重新執行區塊或結束迴圈。  這個處理序會一直繼續，直到 `counter` 超過 `end` 或遇到 `Exit For` 陳述式為止。  
  
 迴圈不會停止，直到 `counter` 傳遞 `end`。  如果 `counter` 等於 `end`，則迴圈會繼續執行。  如果 `step` 是正值，則判斷是否執行區塊的比較為 `counter` \<\= `end`，如果 `step` 是負值則為 `counter` \>\= `end`。  
  
 如果您變更 `counter` 的值，在迴圈內時，您的程式碼可能更難閱讀及偵錯。  變更 `start`的值為 `end`，或者 `step` 不會影響已決定的反覆項目值，當初次進入迴圈。  
  
 如果巢狀迴圈，編譯器會發出錯誤信號，如果它在內部層級的 `Next` 陳述式之前遇到外層巢狀層次的 `Next` 陳述式。  但是，只有當您在每個 `Next` 陳述式中指定 `counter` 時，編譯器才會偵測到這個重疊錯誤。  
  
### 步驟引數  
 `step` 值可為正值或負值。  這個參數決定處理根據下表的迴圈:  
  
|**Step 值**|**執行迴圈的條件**|  
|----------------|-----------------|  
|正值或零|`counter` \<\= `end`|  
|負|`counter` \>\= `end`|  
  
 `step` 的預設值為 1。  
  
###  <a name="BKMK_Counter"></a> 計數器引數  
 下表指出 `counter` 是否定義範圍是整個 `For…Next` 迴圈的新的區域變數。  這個解析 `datatype` 決定是否存在，而且 `counter` 是否已定義。  
  
|`datatype` 上是否有?|`counter` 已經定義?|結果 \( `counter` 是否定義範圍是整個 `For...Next` 迴圈\) 的新的區域變數|  
|----------------------|---------------------|---------------------------------------------------------|  
|否|是|否，，因為 `counter` 已經定義。  如果 `counter` 範圍不是在程序中，編譯時期警告出現。|  
|否|否|是。  資料型別是 `start`、 `end`和 `step` 運算式推斷。  如需型別推斷的詳細資訊，請參閱 [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) 和 [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。|  
|是|是|是，，不過，只有在現有 `counter` 變數在程序外定義。  該變數維持不同。  如果現有的 `counter` 變數的範圍是在程序中，編譯時期發生錯誤。|  
|是|否|是。|  
  
 `counter` 的資料型別決定反覆項目類型，必須是下列其中一種型別:  
  
-   `Byte`、`SByte`、`UShort`、`Short`、`UInteger`、`Integer`、`ULong`、`Long`、`Decimal`、`Single` 或 `Double`。  
  
-   您使用 [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md)宣告的列舉。  
  
-   `Object`。  
  
-   具有下列運算子的型別 `T`，其中 `B` 是可在 `Boolean` 運算式中使用的型別。  
  
     `Public Shared Operator >= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator <= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator - (op1 As T, op2 As T) As T`  
  
     `Public Shared Operator + (op1 As T, op2 As T) As T`  
  
 您可以在 `Next` 陳述式可以選擇性地指定 `counter` 變數。  尤其是在您具有巢狀 `For` 迴圈，這個語法能提高程式的可讀性。  您必須指定出現在對應的 `For` 陳述式的變數。  
  
 `start`、`end` 和 `step` 運算式可以評估擴展至 `counter` 型別的任何資料型別。  如果您使用 `counter`的使用者定義型別，您可能必須定義 `CType` 轉換運算子 `start`、 `end`或 `step` 的型別為 `counter`的型別。  
  
## 範例  
 下列範例會移除泛型清單中的所有項目。  而不是 [For Each...Next 陳述式](../../../visual-basic/language-reference/statements/for-each-next-statement.md)，這個範例會示範以遞減順序逐一查看的 `For`…`Next` 陳述式。  因為 `removeAt` 方法所移除的項目之後建立項目具有較低的索引值，這個範例會使用這個技術。  
  
 [!code-vb[VbVbalrStatements#114](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_5.vb)]  
  
## 範例  
 下列範例會使用 [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md)，宣告的逐一查看列舉型別。  
  
 [!code-vb[VbVbalrStatements#116](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_6.vb)]  
  
## 範例  
 在下列範例中，陳述式參數會使用具有 `+`、`-`、`>=` 和 `<=` 運算子多載運算子的類別。  
  
 [!code-vb[VbVbalrStatements#117](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_7.vb)]  
  
## 請參閱  
 <xref:System.Collections.Generic.List%601>   
 [Loop Structures](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md)   
 [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md)   
 [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)   
 [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)   
 [集合](../Topic/Collections%20\(C%23%20and%20Visual%20Basic\).md)