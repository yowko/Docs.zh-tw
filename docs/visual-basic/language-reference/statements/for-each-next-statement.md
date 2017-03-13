---
title: "For Each...Next 陳述式 (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.ForEach"
  - "vb.ForEachNext"
  - "vb.Each"
  - "ForEachNext"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "無限迴圈"
  - "Next 陳述式，For Each...Next"
  - "無窮迴圈"
  - "迴圈結構，For Each...Next"
  - "迴圈，無窮"
  - "Each 關鍵字"
  - "指示，重複"
  - "For Each 陳述式"
  - "集合，指令重複"
  - "迴圈，無限"
  - "For Each...Next 陳述式"
  - "For 關鍵字 [Visual Basic]，Each...Next 陳述式"
  - "Exit 陳述式，For Each...Next 陳述式"
  - "反覆項目"
ms.assetid: ebce3120-95c3-42b1-b70b-fa7da40c75e2
caps.latest.revision: 56
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 56
---
# For Each...Next 陳述式 (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

針對集合中的每個元素，重複一組陳述式。  
  
## 語法  
  
```  
For Each element [ As datatype ] In group  
    [ statements ]  
    [ Continue For ]  
    [ statements ]  
    [ Exit For ]  
    [ statements ]  
Next [ element ]  
```  
  
## 組件  
  
|||  
|-|-|  
|詞彙|定義|  
|`element`|在 `For Each` 陳述式中為必要項。  在 `Next` 陳述式中是選擇項。  變數。  用來逐一查看集合的項目。|  
|`datatype`|必要項，如果 `element` 尚未宣告。  `element` 的資料型別。|  
|`group`|必要項。  與集合型別或物件型別的變數。  請參考要重複 `statements` 的集合。|  
|`statements`|選擇項。  在 `For Each` 和 `Next` 中，有一個或多個陳述式在 `group` 的每個項目上執行。|  
|`Continue For`|選擇項。  將控制轉移至 `For Each` 迴圈的開頭。|  
|`Exit For`|選擇項。  從 `For Each` 迴圈當中傳出控制權。|  
|`Next`|必要項。  結束 `For Each` 迴圈的定義。|  
  
## 簡單的範例  
 當您要重複執行集合或陣列之每個項目的一組陳述式時，請使用 `For Each`...`Next` 迴圈 \(Loop\)。  
  
> [!TIP]
>  當您可以使迴圈的每個反覆運算與控制項變數產生關聯，並判斷變數的初始值和最終值時，[For...Next 陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md) 就能順利工作。  不過，也就是說，當您處理集合時，初始值和最終值的概念沒有意義，，您並不需要知道多少個項目集合的。  在這種情況下， `For Each``Next` …迴圈通常是較佳的選擇。  
  
 在下列範例中， `For Each`…`Next` 陳述式將清單集合的所有項目的。  
  
 [!code-vb[VbVbalrStatements#121](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_1.vb)]  
  
 如需更多範例，請參閱[集合](../Topic/Collections%20\(C%23%20and%20Visual%20Basic\).md) 和[陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)。  
  
## 巢狀迴圈  
 您可以將一個迴圈置於另一個迴圈內，使 `For Each` 迴圈套疊成巢狀。  
  
 下列範例示範巢狀的 `For Each`…`Next` 結構。  
  
 [!code-vb[VbVbalrStatements#122](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_2.vb)]  
  
 當您巢狀迴圈時，每個迴圈必須具備唯一的 `element` 變數。  
  
 您可以將不同類型的控制結構相互套疊成巢狀。  如需詳細資訊，請參閱[Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)。  
  
## 關閉並繼續。  
 結束 `For``Next` …迴圈和傳輸控制權的 [結束。](../../../visual-basic/language-reference/statements/exit-statement.md) 陳述式會讓執行對 `Next` 之後的陳述式之後的陳述式。  
  
 `Continue For` 陳述式會立即將控制權轉移至迴圈的下一個反覆運算。  如需詳細資訊，請參閱[Continue Statement](../../../visual-basic/language-reference/statements/continue-statement.md)。  
  
 下列範例示範如何使用 `Continue For` 和 `Exit For` 陳述式。  
  
 [!code-vb[VbVbalrStatements#123](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_3.vb)]  
  
 您可以將任意數目的 `Exit For` 陳述式放在 `For Each` 迴圈中。  用於巢狀的 `For Each` 迴圈內時，`Exit For` 會使程式執行退出最內層的迴圈，並將控制權轉移到下一個較高的巢狀層次。  
  
 `Exit For` 通常會在評估一些條件之後使用，例如 `If`...`Then`...`Else` 結構。  在下列情況中，您可能會想要使用 `Exit For`：  
  
-   繼續逐一查看則沒有必要或是不可行。  這可能是因為錯誤值或終止要求所造成。  
  
-   在 `Try`...`Catch`...`Finally` 中攔截到例外狀況。  您可能在 `Finally` 區塊的結尾處使用 `Exit For`。  
  
-   發生無止盡迴圈，這是可以執行龐大甚或無限次數的迴圈。  如果您偵測到這類狀況，可以使用 `Exit For` 逸出此迴圈。  如需詳細資訊，請參閱[Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md)。  
  
## Iterators  
 您可以使用 *Iterator* 對集合的自訂反覆項目。  Iterator 可以是函式或 `Get` 存取子。  它會使用 `Yield` 陳述式會傳回集合中的每個項目一次一個。  
  
 使用 `For Each...Next` 陳述式，則呼叫 Iterator。  `For Each` 迴圈反覆運算時呼叫 Iterator。  執行 `Yield` 陳述式在 Iterator 時為止，而在 `Yield` 陳述式中的運算式傳回，因此，目前位置在程式碼中保留。  下一次呼叫此 Iterator 時，便會從這個位置重新開始執行。  
  
 下列範例會使用 Iterator 函式。  Iterator 函式具有 [對於 Each…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) 迴圈中的 `Yield` 陳述式。  在 `ListEvenNumbers` 方法， `For Each` 陳述式主體的每個反覆項目建立呼叫 Iterator 函式，執行下一個 `Yield` 陳述式。  
  
 [!code-vb[VbVbalrStatements#127](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_4.vb)]  
  
 如需詳細資訊，請參閱 [迭代器](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md)、[Yield 陳述式](../../../visual-basic/language-reference/statements/yield-statement.md)和[Iterator](../../../visual-basic/language-reference/modifiers/iterator.md)。  
  
## 技術實作  
 當 `For Each`…`Next` 陳述式時， Visual Basic 評估集合只有一次，，在迴圈開始之前。  如果陳述式區塊變更 `element` 或 `group`，這些變更不會影響迴圈的反覆項目。  
  
 當集合中所有的項目都已連續指派給 `element` 時，`For Each` 迴圈會停用，並且控制權會傳遞至 `Next` 陳述式隨後的陳述式。  
  
 如果 `element` 不在這個迴圈外宣告，您必須將它宣告在 `For Each` 陳述式。  您可以使用 `As` 陳述式明確宣告 `element` 的型別，或者依據型別推斷指派型別。  不論哪個情況，`element` 的範圍即是迴圈的主體。  但不能在迴圈內外宣告 `element`。  
  
 您可以在 `Next` 陳述式中選擇性地指定 `element`。  這能提高程式的可讀性，尤其是在您具有巢狀 `For Each` 迴圈時。  所指定的變數必須和相對應之 `For Each` 陳述式中出現的變數相同。  
  
 您可能想要避免在迴圈內變更 `element` 的值。  這樣做可能會讓程式碼更難以閱讀和偵錯。  變更 `group` 的值不會影響集合或其項目，來決定的，當初次進入迴圈。  
  
 當您為巢狀迴圈，則為，如果外部巢狀層次的 `Next` 遇到陳述式，在內部層級的 `Next` ，編譯器會發出錯誤信號之前。  但是，只有當您在每個 `Next` 陳述式中指定 `element` 時，編譯器才會偵測到這個重疊錯誤。  
  
 如果程式碼依賴周遊集合以特殊的順序， `For Each``Next` …迴圈不是最佳選擇，，除非您知道集合公開列舉值物件的特性。  周遊命令不會由 Visual Basic，，而是列舉值物件的 <xref:System.Collections.IEnumerator.MoveNext%2A> 方法。  因此您可能無法預測哪一個集合項目會在 `element` 中第一個傳回，或者哪一個項目會接在指定之項目後傳回。  使用不同的迴圈結構 \(例如，`For`...`Next` 或 `Do`...`Loop`\)，可以獲得更可靠的結果.  
  
 `element` 的資料型別必須是可將 `group` 的項目轉換成它的資料型別。  
  
 `group` 資料型別必須是參考集合或陣列是可列舉的參考型別。  這通常表示該 `group` 參考至實作 `System.Collections` 命名空間之 <xref:System.Collections.IEnumerable> 介面或 `System.Collections.Generic` 命名空間之 <xref:System.Collections.Generic.IEnumerable%601> 介面的物件。  `System.Collections.IEnumerable` 定義 <xref:System.Collections.IEnumerable.GetEnumerator%2A> 方法，該方法會傳回集合的列舉值物件。  列舉值物件會實作 `System.Collections` 命名空間的 `System.Collections.IEnumerator` 介面，並公開 \(Expose\) <xref:System.Collections.IEnumerator.Current%2A> 屬性和 <xref:System.Collections.IEnumerator.Reset%2A> 與 <xref:System.Collections.IEnumerator.MoveNext%2A> 方法。  Visual Basic 使用這些屬性和方法來周遊集合。  
  
### 縮小轉換  
 當 `Option Strict` 設定為 `On`，縮小轉換通常會造成編譯器錯誤。  不過，在 `For Each` 陳述式中，由 `group` 中項目變成 `element` 的轉換作業會在執行階段評估與執行，並隱藏縮小轉換造成的編譯器錯誤。  
  
 在下列範例中， `m` 的指派做為 `n` 的原始值無法編譯 `Option Strict` 時開啟，因為 `Long` 轉換為 `Integer` 是縮小轉換。  但是在 `For Each` 陳述式中，即使需要進行從 `Long` 到 `Integer` 的相同轉換才能指派 `number`，也不會報告任何編譯器錯誤。  在數字很大的 `For Each` 陳述式中，將 <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A> 套用至該數字時會發生執行階段錯誤。  
  
 [!code-vb[VbVbalrStatements#89](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_5.vb)]  
  
### IEnumerator 呼叫  
 開始執行 `For Each`...`Next` 迴圈時，Visual Basic 會驗證 `group` 是否參考有效的集合物件。  如果沒有，會擲回例外狀況。  否則，會呼叫 <xref:System.Collections.IEnumerator.MoveNext%2A> 方法和列舉值物件的 <xref:System.Collections.IEnumerator.Current%2A> 屬性，傳回第一個項目。  如果 `MoveNext` 指出沒有下一個項目，也就是說，集合是空的，則 `For Each` 迴圈會停止，且控制權會傳遞至 `Next` 陳述式隨後的陳述式。  否則，Visual Basic 會將 `element` 設為第一個項目，並執行陳述式區塊。  
  
 Visual Basic 每次遇到 `Next` 陳述式時，就會回到 `For Each` 陳述式。  接著再次呼叫 `MoveNext` 和 `Current` 傳回下一個項目，並根據結果重新執行區塊或停止迴圈。  此處理序會繼續執行，直到 `MoveNext` 指出沒有下一個項目，或是遇到 `Exit For` 陳述式為止。  
  
 **修改集合** <xref:System.Collections.IEnumerable.GetEnumerator%2A> 所傳回的列舉值物件通常不允許您將，刪除，取代或重新排列任何項目變更集合。  如果您在初始 `For Each`...`Next` 迴圈後變更集合，列舉程式物件會變成無效，而且在下次嘗試存取項目時會引發 <xref:System.InvalidOperationException> 例外狀況。  
  
 不過，修改這個封鎖未由 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)]，，而是 <xref:System.Collections.IEnumerable> 介面的實作。  您也可以實作 `IEnumerable`，允許在反覆運算時進行修改。  如果您考慮要進行這類動態修改，對於您所使用的集合，請務必了解 `IEnumerable` 實作的特性。  
  
 **修改集合項目**列舉程式物件的 <xref:System.Collections.IEnumerator.Current%2A> 屬性是 [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)，而且它會傳回每一個集合項目的本機複本。  這表示您無法在 `For Each`...`Next` 迴圈中修改項目本身。  所有修改 `Current` 所做的變更只會影響本機複本並不會反映回基礎集合。  然而，如果項目是參考型別，您可以修改它所指向的執行個體成員。  下列範例修改每個 `thisControl` 項目的 `BackColor` 成員。  您不能，然而，修改 `thisControl` 。  
  
```vb#  
Sub lightBlueBackground(ByVal thisForm As System.Windows.Forms.Form)  
    For Each thisControl As System.Windows.Forms.Control In thisForm.Controls  
        thisControl.BackColor = System.Drawing.Color.LightBlue  
    Next thisControl  
End Sub  
```  
  
 上述範例可以修改每個 `thisControl` 項目的 `BackColor` 成員，不過它無法修改 `thisControl` 本身。  
  
 **走訪陣列**因為 <xref:System.Array> 類別會實作 <xref:System.Collections.IEnumerable> 介面，因此全部的陣列都會公開 <xref:System.Array.GetEnumerator%2A> 方法。  這表示您可以使用 `For Each`...`Next` 逐一查看陣列。  不過，您只能讀取陣列元素。  您無法加以變更。  
  
## 範例  
 下列範例會使用 <xref:System.IO.DirectoryInfo> 類別列出 C:\\ 目錄中的所有資料夾。  
  
 [!code-vb[VbVbalrStatements#124](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_6.vb)]  
  
## 範例  
 下列範例說明如何排序集合的方法。  儲存於 <xref:System.Collections.Generic.List%601>中 `Car` 的範例排序執行個體分類。  `Car` 類別實作 <xref:System.IComparable%601> 介面，要求實作<xref:System.IComparable%601.CompareTo%2A> 方法。  
  
 對 <xref:System.IComparable%601.CompareTo%2A> 方法的每一個呼叫將會使用的唯一比較。  在 `CompareTo` 方法的使用者撰寫的程式碼會傳回目前物件的每個和另一個物件的比較的值。  如果目前物件比另一個物件小則傳回的值小於零，如果目前物件比另一個物件大則傳回的值大於零，如果它們相等則回傳零。  這可讓您定義字碼大於，小於，等於的準。  
  
 在 `ListCars` 方法， `cars.Sort()` 陳述式排序清單。  為 <xref:System.Collections.Generic.List%601> 的 <xref:System.Collections.Generic.List%601.Sort%2A> 方法的呼叫會導致 `CompareTo` 方法對 `List`的 `Car` 物件自動呼叫。  
  
 [!code-vb[VbVbalrStatements#125](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_7.vb)]  
  
## 請參閱  
 [集合](../Topic/Collections%20\(C%23%20and%20Visual%20Basic\).md)   
 [For...Next 陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [Loop Structures](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md)   
 [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md)   
 [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)   
 [Collection Initializers](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)   
 [陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)