---
title: For Each...Next 陳述式 (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 5081f80ad0da738ebb950bcd649af7a593582356
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638073"
---
# <a name="for-eachnext-statement-visual-basic"></a>For Each...Next 陳述式 (Visual Basic)
每個項目集合中，會重複一組陳述式。  
  
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
|`element`|需要`For Each`陳述式。 選擇性在`Next`陳述式。 變數。 用來逐一查看集合的元素。|  
|`datatype`|需要`element`不已宣告。 資料類型的`element`。|  
|`group`|必要項。 是集合型別或物件類型的變數。 哪些是指集合`statements`會重複執行。|  
|`statements`|選擇性。 一或多個陳述式之間`For Each`並`Next`中的每個項目上執行`group`。|  
|`Continue For`|選擇性。 將控制權傳輸至開頭`For Each`迴圈。|  
|`Exit For`|選擇性。 控制權轉移共`For Each`迴圈。|  
|`Next`|必要項。 結束的定義`For Each`迴圈。|  
  
## <a name="simple-example"></a>簡單的範例  
 使用`For Each`...`Next`循環播放，當您想要針對集合或陣列的每個項目重複一組陳述式。  
  
> [!TIP]
>  A [For...下一個陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)運作良好時，您便可以控制變數相關聯的迴圈的每個反覆項目上，並判斷該變數的初始和最終值。 不過，當您處理集合時，初始和最終值的概念沒有意義，而且您不一定要知道集合的項目數目。 在這種情況下， `For Each`...`Next`迴圈通常是較好的選擇。  
  
 在下列範例中， `For Each`...`Next` 陳述式逐一查看清單集合中的所有項目。  
  
 [!code-vb[VbVbalrStatements#121](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#121)]  
  
 如需其他範例，請參閱 <<c0> [ 集合](../../../standard/collections/index.md)並[陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)。  
  
## <a name="nested-loops"></a>巢狀的迴圈  
 您可以巢狀`For Each`放在另一個迴圈的迴圈。  
  
 下列範例會示範巢狀`For Each`...`Next` 結構。  
  
 [!code-vb[VbVbalrStatements#122](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#122)]  
  
 當您使用巢狀迴圈時，每個迴圈必須具有唯一`element`變數。  
  
 您也可以巢狀不同種類的控制結構彼此。 如需詳細資訊，請參閱 <<c0> [ 巢狀控制結構](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)。  
  
## <a name="exit-for-and-continue-for"></a>針對結束後繼續  
 [Exit For](../../../visual-basic/language-reference/statements/exit-statement.md)陳述式會結束執行`For`...`Next` 後面的陳述式的迴圈和傳輸控制項`Next`陳述式。  
  
 `Continue For`陳述式控制將立即轉移到迴圈的下一個反覆項目。 如需詳細資訊，請參閱 < [Continue 陳述式](../../../visual-basic/language-reference/statements/continue-statement.md)。  
  
 下列範例示範如何使用`Continue For`和`Exit For`陳述式。  
  
 [!code-vb[VbVbalrStatements#123](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#123)]  
  
 您可以將任意數目的放`Exit For`中的陳述式`For Each`迴圈。 使用時內巢狀`For Each`迴圈，`Exit For`導致執行動作的巢狀下一個較高的等級結束最內層的迴圈和傳輸控制項。  
  
 `Exit For` 在某些狀況中，評估後通常用在`If`...`Then`...`Else`結構。 您可能想要使用`Exit For`下列條件：  
  
- 繼續向逐一查看是不必要或不可能。 這可能被造成錯誤的數值或終止要求。  
  
- 在攔截到例外狀況`Try`...`Catch`...`Finally`.您可以使用`Exit For`結尾的`Finally`區塊。  
  
- 該處永無止盡的迴圈，也就是無法執行大型或甚至是無限次數的迴圈。 如果您偵測到這種情況，您可以使用`Exit For`來逸出迴圈。 如需詳細資訊，請參閱[執行...迴圈陳述式](../../../visual-basic/language-reference/statements/do-loop-statement.md)。  
  
## <a name="iterators"></a>迭代器  
 您使用*迭代器*若要在集合上執行自訂反覆項目。 迭代器可以是函式或`Get`存取子。 它會使用`Yield`陳述式來傳回一次一個集合的每個項目。  
  
 您可以使用呼叫迭代器`For Each...Next`陳述式。 `For Each` 迴圈的每個反覆項目都會呼叫迭代器。 當`Yield`到達陳述式時的迭代器，在運算式中`Yield`陳述式會傳回，而且會保留在程式碼中的目前位置。 下一次呼叫迭代器時，便會從這個位置重新開始執行。  
  
 下列範例會使用迭代器函式。 迭代器函式具有`Yield`內的陳述式[For...下一步](../../../visual-basic/language-reference/statements/for-next-statement.md)迴圈。 在 `ListEvenNumbers`方法中，每次反覆運算`For Each`陳述式主體會建立迭代器，才能繼續進行下一個呼叫`Yield`陳述式。  
  
 [!code-vb[VbVbalrStatements#127](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#127)]  
  
 如需詳細資訊，請參閱 <<c0> [ 迭代器](../../programming-guide/concepts/iterators.md)， [Yield 陳述式](../../../visual-basic/language-reference/statements/yield-statement.md)，並[迭代器](../../../visual-basic/language-reference/modifiers/iterator.md)。  
  
## <a name="technical-implementation"></a>技術實作  
 當`For Each`...`Next` 陳述式執行時，Visual Basic 會評估集合只有一個之前在迴圈開始的時間。 如果陳述式區塊變更`element`或`group`，這些變更不會影響在迴圈的反覆項目。  
  
 當集合中的所有項目連續指派給`element`，則`For Each`迴圈停駐點，並控制傳遞到之後的陳述式`Next`陳述式。  
  
 如果`element`尚未已外宣告此迴圈中，您必須將其宣告中`For Each`陳述式。 您可以宣告的型別`element`明確地使用`As`陳述式，或者您可以依賴指派類型的型別推斷。 在任一情況下，範圍`element`是迴圈的主體。 不過，您不能宣告`element`同時內部和外部迴圈。  
  
 您可以選擇性地指定`element`在`Next`陳述式。 這有助於改善您的程式的可讀性，尤其是如果您有巢狀`For Each`迴圈。 您必須指定相同的變數會出現在對應的`For Each`陳述式。  
  
 您可能想要避免變更的值`element`迴圈內。 如此一來，可以讓更難閱讀及偵錯您的程式碼。 值變更`group`不會影響集合或其項目迴圈的第一次輸入時所決定。  
  
 當您要建立巢狀迴圈，如果`Next`外部的巢狀層級的陳述式之前就遇到`Next`內部層級，編譯器會發出錯誤信號。 不過，編譯器可以偵測此重疊錯誤，只有當您指定`element`在每個`Next`陳述式。  
  
 如果您的程式碼相依於周遊集合中特定的順序， `For Each`...`Next`迴圈不是最好的選擇，除非您知道的特性，列舉值物件的集合會公開。 周遊順序不取決於 Visual Basic 中，但取決<xref:System.Collections.IEnumerator.MoveNext%2A>列舉值物件的方法。 因此，您可能會無法預測哪些項目集合中傳回的第一個`element`，或這是要傳回在指定的項目之後的下一步。 您可能會達到更可靠的結果，使用不同的迴圈結構，例如`For`...`Next`或`Do`...`Loop`.  
  
 資料類型`element`使的資料類型的項目必須是`group`可以轉換成它。  
  
 資料類型`group`必須是指的是集合或陣列，是可列舉的參考型別。 通常這表示`group`實作的物件是指<xref:System.Collections.IEnumerable>介面`System.Collections`命名空間或<xref:System.Collections.Generic.IEnumerable%601>介面`System.Collections.Generic`命名空間。 `System.Collections.IEnumerable` 定義<xref:System.Collections.IEnumerable.GetEnumerator%2A>方法，以傳回集合的列舉值物件。 列舉值物件會實作`System.Collections.IEnumerator`介面`System.Collections`命名空間，並公開<xref:System.Collections.IEnumerator.Current%2A>屬性並<xref:System.Collections.IEnumerator.Reset%2A>和<xref:System.Collections.IEnumerator.MoveNext%2A>方法。 Visual Basic 會使用這些來周遊集合。  
  
### <a name="narrowing-conversions"></a>縮小轉換  
 當`Option Strict`設為`On`，縮小轉換通常會導致編譯器錯誤。 在`For Each`陳述式，不過中的項目從不`group`到`element`評估和執行在執行階段，而造成的縮小轉換的編譯器錯誤受到抑制。  
  
 在下列範例中，指派`m`做為初始的值`n`不會進行編譯時`Option Strict`是上，因為轉換`Long`到`Integer`是縮小轉換。 在`For Each`陳述式，不過，沒有編譯器錯誤會報告，即使指派給`number`需要從相同的轉換`Long`至`Integer`。 在 `For Each`包含大量的陳述式，執行階段錯誤發生時<xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A>套用大的數字。  
  
 [!code-vb[VbVbalrStatements#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class3.vb#89)]  
  
### <a name="ienumerator-calls"></a>IEnumerator 呼叫  
 當執行`For Each`...`Next`迴圈開始，Visual Basic 會確認`group`指的是有效的集合物件。 如果沒有，就會擲回例外狀況。 否則，它會呼叫<xref:System.Collections.IEnumerator.MoveNext%2A>方法和<xref:System.Collections.IEnumerator.Current%2A>要傳回的第一個元素的列舉值物件的屬性。 如果`MoveNext`指出，沒有下一個項目，也就是這個集合是空的如果`For Each`迴圈停駐點，並控制傳遞到之後的陳述式`Next`陳述式。 否則，Visual Basic 會將設定`element`第一個項目並執行陳述式區塊。  
  
 每次 Visual Basic 遇到`Next`陳述式，它會返回`For Each`陳述式。 它會呼叫一次`MoveNext`和`Current`傳回下一個項目，再執行此區塊或根據結果迴圈就會停止。 此程序一直`MoveNext`表示沒有下一個項目或`Exit For`遇到陳述式。  
  
 **修改集合。** 所傳回的列舉值物件<xref:System.Collections.IEnumerable.GetEnumerator%2A>通常不會讓您新增、 刪除、 取代或重新排列任何項目來變更集合。 如果您已起始之後，變更集合`For Each`...`Next`迴圈 」 列舉值物件就會變成無效，和下一步 嘗試存取的項目，會造成<xref:System.InvalidOperationException>例外狀況。  
  
 不過，修改這個封鎖不取決於 Visual basic，而是只要實作<xref:System.Collections.IEnumerable>介面。 它是可以實作`IEnumerable`反覆項目期間，修改允許的方式。 如果您正在考慮進行這類動態修改，請確定您了解特性`IEnumerable`對您使用的集合物件的實作。  
  
 **修改集合的項目。** <xref:System.Collections.IEnumerator.Current%2A>列舉值物件的屬性是[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)，並傳回每個集合項目的本機副本。 這表示您無法修改項目本身中`For Each`...`Next`迴圈。 您進行任何修改會影響本機複本從`Current`而不反映回基礎的集合。 不過，如果項目是參考型別，您可以修改它所指向的執行個體的成員。 下列範例會修改`BackColor`的每個成員`thisControl`項目。 不過，您不能修改`thisControl`本身。  
  
```vb  
Sub lightBlueBackground(ByVal thisForm As System.Windows.Forms.Form)  
    For Each thisControl As System.Windows.Forms.Control In thisForm.Controls  
        thisControl.BackColor = System.Drawing.Color.LightBlue  
    Next thisControl  
End Sub  
```  
  
 前一個範例可以修改`BackColor`的每個成員`thisControl`項目，雖然它不能修改`thisControl`本身。  
  
 **周遊的陣列。** 因為<xref:System.Array>類別會實作<xref:System.Collections.IEnumerable>介面，所有陣列都公開<xref:System.Array.GetEnumerator%2A>方法。 這表示，您可以逐一查看陣列`For Each`...`Next`迴圈。 不過，您可以只讀取陣列項目。 您無法變更它們。  
  
## <a name="example"></a>範例  
 下列範例會列出在 C:\ 目錄中的所有資料夾使用<xref:System.IO.DirectoryInfo>類別。  
  
 [!code-vb[VbVbalrStatements#124](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#124)]  
  
## <a name="example"></a>範例  
 下列範例說明排序集合的程序。 此範例排序的執行個體`Car`類別，會儲存在<xref:System.Collections.Generic.List%601>。 `Car` 類別實作 <xref:System.IComparable%601> 介面，而這個介面要求實作 <xref:System.IComparable%601.CompareTo%2A> 方法。  
  
 每次呼叫<xref:System.IComparable%601.CompareTo%2A>方法可用於排序的單一比較。 當目前物件和另一個物件比較時，在 `CompareTo` 方法中的使用者撰寫程式碼會傳回值。 如果目前物件比另一個物件小則傳回的值小於零，如果目前物件比另一個物件大則傳回的值大於零，如果它們相等則傳回零。 這可讓您以程式碼定義大於、小於、等於的準則。  
  
 在 `ListCars` 方法中，`cars.Sort()` 陳述式會排序清單。 對 <xref:System.Collections.Generic.List%601> 之 <xref:System.Collections.Generic.List%601.Sort%2A> 方法的這個呼叫，會導致 `CompareTo` 方法對 `List` 的 `Car` 物件自動呼叫。  
  
 [!code-vb[VbVbalrStatements#125](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#125)]  
  
## <a name="see-also"></a>另請參閱

- [集合](../../../standard/collections/index.md)
- [For...Next 陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [迴圈結構](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [While...End While 陳述式](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Do...Loop 陳述式](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [擴展和縮小轉換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [物件初始設定式：具名和匿名類型](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [集合初始設定式](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)
