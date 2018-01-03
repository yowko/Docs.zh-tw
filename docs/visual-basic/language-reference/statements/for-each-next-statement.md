---
title: "For Each...Next 陳述式 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ForEach
- vb.ForEachNext
- vb.Each
- ForEachNext
helpviewer_keywords:
- infinite loops
- Next statement [Visual Basic], For Each...Next
- endless loops
- loop structures [Visual Basic], For Each...Next
- loops, endless
- Each keyword [Visual Basic]
- instructions, repeating
- For Each statement [Visual Basic]
- collections, instruction repetition
- loops, infinite
- For Each...Next statements
- For keyword [Visual Basic], For Each...Next statements
- Exit statement [Visual Basic], For Each...Next statements
- iteration
ms.assetid: ebce3120-95c3-42b1-b70b-fa7da40c75e2
caps.latest.revision: "56"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 11601eb1caad1c6cc6d9898f590436a977a78fa1
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="for-eachnext-statement-visual-basic"></a>For Each...Next 陳述式 (Visual Basic)
每個項目集合中重複陳述式的群組。  
  
## <a name="syntax"></a>語法  
  
```  
For Each element [ As datatype ] In group  
    [ statements ]  
    [ Continue For ]  
    [ statements ]  
    [ Exit For ]  
    [ statements ]  
Next [ element ]  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`element`|中需要`For Each`陳述式。 選擇性在`Next`陳述式。 變數。 用來逐一查看集合的元素。|  
|`datatype`|若`element`不已宣告。 資料型別`element`。|  
|`group`|必要。 集合型別或物件類型的變數。 參考的集合`statements`會重複執行。|  
|`statements`|選擇性。 一或多個陳述式之間`For Each`和`Next`中每個項目上執行的`group`。|  
|`Continue For`|選擇性。 將控制權傳輸至開頭`For Each`迴圈。|  
|`Exit For`|選擇性。 控制權轉移出`For Each`迴圈。|  
|`Next`|必要。 結束的定義`For Each`迴圈。|  
  
## <a name="simple-example"></a>簡單的範例  
 使用`For Each`...`Next`循環播放，當您想要針對集合或陣列的每個項目重複一組陳述式。  
  
> [!TIP]
>  A [For...下一個陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)就非常適合時您可以將迴圈的每個反覆項目與控制變數產生關聯，並決定該變數的初始和最終值。 不過，當您處理集合，初始和最終的值的概念沒有意義，而且您不一定了解集合的項目數目。 在這種情況下， `For Each`...`Next`迴圈通常是較佳選擇。  
  
 在下列範例中， `For Each`...`Next` 陳述式逐一查看清單集合中的所有項目。  
  
 [!code-vb[VbVbalrStatements#121](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_1.vb)]  
  
 如需其他範例，請參閱[集合](../../../standard/collections/index.md)和[陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)。  
  
## <a name="nested-loops"></a>巢狀的迴圈  
 您可以巢狀`For Each`將放入另一個迴圈內的迴圈。  
  
 下列範例會示範巢狀`For Each`...`Next` 結構。  
  
 [!code-vb[VbVbalrStatements#122](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_2.vb)]  
  
 當您建立巢狀迴圈時，每個迴圈必須具有唯一`element`變數。  
  
 您也可以巢狀不同類型的其他控制結構。 如需詳細資訊，請參閱[巢狀控制結構](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)。  
  
## <a name="exit-for-and-continue-for"></a>針對結束後繼續  
 [Exit For](../../../visual-basic/language-reference/statements/exit-statement.md)陳述式會結束執行`For`...`Next` 之後的陳述式的迴圈，並傳輸控制項`Next`陳述式。  
  
 `Continue For`陳述式控制將立即轉移到迴圈的下一個反覆項目。 如需詳細資訊，請參閱[Continue 陳述式](../../../visual-basic/language-reference/statements/continue-statement.md)。  
  
 下列範例示範如何使用`Continue For`和`Exit For`陳述式。  
  
 [!code-vb[VbVbalrStatements#123](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_3.vb)]  
  
 您可以將任意數目的`Exit For`中的陳述式`For Each`迴圈。 使用時內巢狀`For Each`迴圈`Exit For`導致執行動作的巢狀下一個較高的層級來結束最內層的迴圈和傳輸控制項。  
  
 `Exit For`通常是某項條件的評估期過後，例如在`If`...`Then`...`Else`結構。 您可能想要使用`Exit For`以下情況：  
  
-   繼續以逐一查看是不必要或不可能。 這可能被造成錯誤的數值或終止要求。  
  
-   在攔截到例外狀況`Try`...`Catch`...`Finally`.您可能會使用`Exit For`結尾`Finally`區塊。  
  
-   那里無止盡的迴圈，即無法執行大型或甚至無限次數的迴圈。 如果您偵測到這種情況，您可以使用`Exit For`來逸出迴圈。 如需詳細資訊，請參閱[執行...迴圈陳述式](../../../visual-basic/language-reference/statements/do-loop-statement.md)。  
  
## <a name="iterators"></a>迭代器  
 您使用*迭代器*若要在集合上執行自訂反覆項目。 迭代器可以是函式或`Get`存取子。 它會使用`Yield`陳述式來傳回一次一個集合的每個項目。  
  
 您可以使用呼叫迭代器`For Each...Next`陳述式。 `For Each` 迴圈的每個反覆項目都會呼叫迭代器。 當`Yield`陳述式中的迭代器中的運算式，已達`Yield`陳述式會傳回，而且保留在程式碼中的目前位置。 下一次呼叫迭代器時，便會從這個位置重新開始執行。  
  
 下列範例會使用 iterator 函式。 迭代器函式有`Yield`陳述式內[For...下一步](../../../visual-basic/language-reference/statements/for-next-statement.md)迴圈。 在`ListEvenNumbers`方法中，每個反覆項目`For Each`陳述式主體建立 iterator 函式，繼續進行下一個呼叫`Yield`陳述式。  
  
 [!code-vb[VbVbalrStatements#127](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_4.vb)]  
  
 如需詳細資訊，請參閱[迭代器](../../programming-guide/concepts/iterators.md)， [Yield 陳述式](../../../visual-basic/language-reference/statements/yield-statement.md)，和[迭代器](../../../visual-basic/language-reference/modifiers/iterator.md)。  
  
## <a name="technical-implementation"></a>技術實作  
 當`For Each`...`Next` 陳述式執行時，Visual Basic 會評估集合只有一個迴圈開始前的時間。 如果陳述式區塊變更`element`或`group`，這些變更不會影響在迴圈的反覆項目。  
  
 當集合中的所有項目已連續將指派給`element`、`For Each`迴圈停駐點，並控制傳遞到之後的陳述式`Next`陳述式。  
  
 如果`element`尚未宣告此迴圈外，您必須將其宣告中`For Each`陳述式。 您可以宣告的型別`element`明確地使用`As`陳述式，或者您可以依賴類型推斷，來指派類型。 在任一情況下，範圍`element`是迴圈的主體。 不過，您無法宣告`element`外部和內部迴圈。  
  
 您可以選擇性地指定`element`中`Next`陳述式。 這有助於改善您程式的可讀性，特別是當您擁有巢狀`For Each`迴圈。 您必須指定相同的變數會出現在對應的一個`For Each`陳述式。  
  
 您可能想要避免變更的值`element`在迴圈內。 如此一來，可讓更難閱讀及偵錯程式碼。 值變更`group`不會影響集合或其項目之前先進入迴圈時所決定。  
  
 當您在巢狀迴圈，如果`Next`外部的巢狀層級的陳述式就碰到`Next`內部的層級，編譯器會發出錯誤信號。 不過，編譯器可以偵測此重疊錯誤，只有當您指定`element`中每個`Next`陳述式。  
  
 如果您的程式碼相依於周遊到集合中特定的順序， `For Each`...`Next`迴圈不是最佳選擇，除非您知道特性列舉值物件的集合會公開。 周遊的順序不由 Visual Basic 中，而<xref:System.Collections.IEnumerator.MoveNext%2A>列舉值物件的方法。 因此，您可能無法預測集合中的哪個項目是要在傳回第一個`element`，或這是要傳回給定的項目之後的下一步。 您可能會達到更可靠的結果，使用不同的迴圈結構，例如`For`...`Next`或`Do`...`Loop`.  
  
 資料型別`element`使的資料類型的項目必須是`group`可以轉換成它。  
  
 資料型別`group`必須是參考類型，這指的是集合或陣列可以列舉。 這通常表示`group`實作的物件是指<xref:System.Collections.IEnumerable>介面`System.Collections`命名空間或<xref:System.Collections.Generic.IEnumerable%601>介面`System.Collections.Generic`命名空間。 `System.Collections.IEnumerable`定義<xref:System.Collections.IEnumerable.GetEnumerator%2A>方法，這個方法會傳回集合的列舉值物件。 列舉值物件實作`System.Collections.IEnumerator`介面`System.Collections`命名空間，並公開<xref:System.Collections.IEnumerator.Current%2A>屬性和<xref:System.Collections.IEnumerator.Reset%2A>和<xref:System.Collections.IEnumerator.MoveNext%2A>方法。 Visual Basic 會使用這些來周遊集合。  
  
### <a name="narrowing-conversions"></a>縮小轉換  
 當`Option Strict`設`On`，縮小轉換通常會造成編譯器錯誤。 在`For Each`陳述式，不過，轉換中的項目`group`至`element`評估和執行階段，並歸併的縮小轉換造成編譯器錯誤。  
  
 在下列範例中，指派`m`做為初始值`n`不會進行編譯時`Option Strict`會因為轉換`Long`至`Integer`是縮小轉換。 在`For Each`陳述式，不過，任何編譯器錯誤會報告，即使指派給`number`需要從相同的轉換`Long`至`Integer`。 在`For Each`包含大量的陳述式，則執行階段會發生錯誤時<xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A>套用到太多。  
  
 [!code-vb[VbVbalrStatements#89](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_5.vb)]  
  
### <a name="ienumerator-calls"></a>IEnumerator 呼叫  
 當執行`For Each`...`Next`迴圈開始、 Visual Basic 確認`group`指的是有效的集合物件。 如果沒有，就會擲回例外狀況。 否則，它會呼叫<xref:System.Collections.IEnumerator.MoveNext%2A>方法和<xref:System.Collections.IEnumerator.Current%2A>来傳回的第一個元素的列舉值物件的屬性。 如果`MoveNext`表示沒有下一個項目，也就是，如果集合是空的`For Each`迴圈停駐點，並控制傳遞到之後的陳述式`Next`陳述式。 否則，Visual Basic 會將`element`對第一個項目及執行陳述式區塊。  
  
 每次在 Visual Basic 遇到`Next`陳述式，它會返回`For Each`陳述式。 它會呼叫一次`MoveNext`和`Current`傳回下一個項目，再執行區塊或停止迴圈依據的結果。 此程序繼續執行直到`MoveNext`表示沒有下一個項目或`Exit For`遇到陳述式。  
  
 **修改集合。** 所傳回的列舉值物件<xref:System.Collections.IEnumerable.GetEnumerator%2A>通常不會讓您新增、 刪除、 取代或重新排列任何項目來變更集合。 如果您將集合變更後已起始`For Each`...`Next`迴圈 」 列舉值物件就會變成無效，以及下一步 嘗試存取的項目; 因此導致<xref:System.InvalidOperationException>例外狀況。  
  
 然而，修改這個封鎖不由決定[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]，而是由實作<xref:System.Collections.IEnumerable>介面。 它也可以實作`IEnumerable`反覆項目期間，修改允許的方式。 如果您考慮執行這類動態修改，請確定您了解的特性`IEnumerable`您使用的集合上實作。  
  
 **修改集合項目。** <xref:System.Collections.IEnumerator.Current%2A>列舉值物件的屬性是[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)，並傳回每個集合項目的本機複本。 這表示您無法修改項目本身中`For Each`...`Next`迴圈。 您進行任何修改會影響的本機複本從`Current`並不會反應回基礎集合。 不過，如果項目是參考類型，您可以修改它所指向的執行個體的成員。 下列範例會修改`BackColor`成員隸屬每個`thisControl`項目。 但是，您不能修改`thisControl`本身。  
  
```vb  
Sub lightBlueBackground(ByVal thisForm As System.Windows.Forms.Form)  
    For Each thisControl As System.Windows.Forms.Control In thisForm.Controls  
        thisControl.BackColor = System.Drawing.Color.LightBlue  
    Next thisControl  
End Sub  
```  
  
 可以修改上述範例`BackColor`成員隸屬每個`thisControl`項目，雖然它不能修改`thisControl`本身。  
  
 **周遊陣列。** 因為<xref:System.Array>類別會實作<xref:System.Collections.IEnumerable>介面，所有陣列都公開<xref:System.Array.GetEnumerator%2A>方法。 這表示您可以逐一查看陣列以進行`For Each`...`Next`迴圈。 不過，您可以只讀取陣列項目。 您無法變更它們。  
  
## <a name="example"></a>範例  
 下列範例會列出在 C:\ 目錄中的所有資料夾使用<xref:System.IO.DirectoryInfo>類別。  
  
 [!code-vb[VbVbalrStatements#124](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_6.vb)]  
  
## <a name="example"></a>範例  
 下列範例說明排序集合的程序。 此範例排序的執行個體`Car`類別會儲存在<xref:System.Collections.Generic.List%601>。 `Car` 類別實作 <xref:System.IComparable%601> 介面，而這個介面要求實作 <xref:System.IComparable%601.CompareTo%2A> 方法。  
  
 每次呼叫<xref:System.IComparable%601.CompareTo%2A>方法可用於排序的單一比較。 當目前物件和另一個物件比較時，在 `CompareTo` 方法中的使用者撰寫程式碼會傳回值。 如果目前物件比另一個物件小則傳回的值小於零，如果目前物件比另一個物件大則傳回的值大於零，如果它們相等則傳回零。 這可讓您以程式碼定義大於、小於、等於的準則。  
  
 在 `ListCars` 方法中，`cars.Sort()` 陳述式會排序清單。 對 <xref:System.Collections.Generic.List%601> 之 <xref:System.Collections.Generic.List%601.Sort%2A> 方法的這個呼叫，會導致 `CompareTo` 方法對 `List` 的 `Car` 物件自動呼叫。  
  
 [!code-vb[VbVbalrStatements#125](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_7.vb)]  
  
## <a name="see-also"></a>請參閱  
 [集合](../../../standard/collections/index.md)  
 [For...Next 陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [迴圈結構](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [While...End While 陳述式](../../../visual-basic/language-reference/statements/while-end-while-statement.md)  
 [Do...Loop 陳述式](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [擴展和縮小轉換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [物件初始設定式：具名和匿名類型](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [集合初始設定式](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)  
 [陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)
