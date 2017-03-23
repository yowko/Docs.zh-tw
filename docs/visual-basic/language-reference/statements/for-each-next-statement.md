---
title: "每個...下一個陳述式 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ForEach
- vb.ForEachNext
- vb.Each
- ForEachNext
dev_langs:
- VB
helpviewer_keywords:
- infinite loops
- Next statement, For Each...Next
- endless loops
- loop structures, For Each...Next
- loops, endless
- Each keyword
- instructions, repeating
- For Each statement
- collections, instruction repetition
- loops, infinite
- For Each...Next statements
- For keyword [Visual Basic], For Each...Next statements
- Exit statement, For Each...Next statements
- iteration
ms.assetid: ebce3120-95c3-42b1-b70b-fa7da40c75e2
caps.latest.revision: 56
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e0173877fa4a57da76fd774d70ce63d2beda23ad
ms.lasthandoff: 03/13/2017

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
|`element`|在需要`For Each`陳述式。 選擇性在`Next`陳述式。 變數。 用來逐一查看集合的項目。|  
|`datatype`|只有在`element`不已經宣告。 資料型別`element`。|  
|`group`|必要項。 集合型別或物件類型的變數。 若超過此集合是指`statements`會重複。|  
|`statements`|選擇項。 一或多個陳述式之間`For Each`和`Next`中每個項目上執行的`group`。|  
|`Continue For`|選擇項。 將控制權傳輸至開頭`For Each`迴圈。|  
|`Exit For`|選擇項。 控制權轉移超出`For Each`迴圈。|  
|`Next`|必要項。 結束的定義`For Each`迴圈。|  
  
## <a name="simple-example"></a>簡單的範例  
 Use a `For Each`...`Next`循環播放，當您想要針對集合或陣列的每個項目重複一組陳述式。  
  
> [!TIP]
>  A [For...下一個陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)很適合當您可以在此迴圈的每個反覆項目關聯的控制項變數並決定該變數的初始和最終值。 不過，當您處理集合時，初始和最終的值的概念並不具意義，而且您不一定要知道集合中有多少項目。 在這種情況下， `For Each`...`Next`迴圈通常是較好的選擇。  
  
 在下列範例中， `For Each`...`Next` 陳述式逐一查看清單集合的所有項目。  
  
 [!code-vb[VbVbalrStatements #&121;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_1.vb)]  
  
 如需詳細資訊，請參閱[集合](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)和[陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)。  
  
## <a name="nested-loops"></a>巢狀的迴圈  
 您可以巢狀`For Each`放在另一個迴圈的迴圈。  
  
 下列範例會示範巢狀`For Each`...`Next` 結構。  
  
 [!code-vb[VbVbalrStatements #&122;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_2.vb)]  
  
 當您建立巢狀迴圈時，每個迴圈必須具有唯一`element`變數。  
  
 您也可以不同種類的控制結構內互相巢狀。 如需詳細資訊，請參閱[巢狀控制結構](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)。  
  
## <a name="exit-for-and-continue-for"></a>針對結束後繼續  
 [Exit For](../../../visual-basic/language-reference/statements/exit-statement.md)陳述式會執行結束`For`...`Next` 之後的陳述式的迴圈，並傳輸控制項`Next`陳述式。  
  
 `Continue For`陳述式將控制項傳送立即的迴圈的下一個反覆項目。 如需詳細資訊，請參閱[繼續陳述式](../../../visual-basic/language-reference/statements/continue-statement.md)。  
  
 下列範例示範如何使用`Continue For`和`Exit For`陳述式。  
  
 [!code-vb[VbVbalrStatements #&123;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_3.vb)]  
  
 您可以將任何數目的`Exit For`中的陳述式`For Each`迴圈。 使用時內巢狀`For Each`迴圈，`Exit For`會執行到下一個較高等級的巢狀結束最內層的迴圈和傳輸控制項。  
  
 `Exit For`通常是某項條件，評估後，例如`If`...`Then`...`Else`結構。 您可能想要使用`Exit For`下列條件︰  
  
-   繼續在逐一查看是不必要或不可能。 這可能被因錯誤的數值或終止要求。  
  
-   在攔截到例外狀況`Try`...`Catch`...`Finally`. 您可以使用`Exit For`結尾`Finally`區塊。  
  
-   那里無止盡的迴圈，而無法執行大型或甚至無限次數的迴圈。 若您偵測到這種情況，您可以使用`Exit For`來逸出迴圈。 如需詳細資訊，請參閱[執行...迴圈陳述式](../../../visual-basic/language-reference/statements/do-loop-statement.md)。  
  
## <a name="iterators"></a>Iterator  
 您使用*迭代器*集合上執行自訂的反覆項目。 迭代器可以是函式或`Get`存取子。 它會使用`Yield`陳述式來傳回每個項目一次一個的集合。  
  
 您可以使用呼叫迭代器`For Each...Next`陳述式。 每個反覆項目`For Each`迴圈就會呼叫迭代器。 當`Yield`陳述式為止迭代器，在運算式中`Yield`陳述式會傳回，而且保留在程式碼中目前的位置。 下一次呼叫迭代器時，便會從這個位置重新開始執行。  
  
 下列範例會使用 iterator 函式。 迭代器函式具有`Yield`陳述式內[For...下一步](../../../visual-basic/language-reference/statements/for-next-statement.md)迴圈。 在`ListEvenNumbers`方法中，每個反覆項目`For Each`陳述式主體會建立呼叫 iterator 函式，繼續進行下一個`Yield`陳述式。  
  
 [!code-vb[VbVbalrStatements #&127;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_4.vb)]  
  
 如需詳細資訊，請參閱[迭代器](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)， [Yield 陳述式](../../../visual-basic/language-reference/statements/yield-statement.md)，和[迭代器](../../../visual-basic/language-reference/modifiers/iterator.md)。  
  
## <a name="technical-implementation"></a>技術實作  
 當`For Each`...`Next` 陳述式執行時，Visual Basic 會評估集合只有一個迴圈開始前的時間。 如果陳述式區塊變更`element`或`group`，這些變更不會影響迴圈的反覆項目。  
  
 當集合中的所有項目接著指派給`element`、`For Each`停駐點，並將控制項傳遞給之後的陳述式`Next`陳述式。  
  
 如果`element`尚未被外宣告此迴圈中，您必須將它宣告中`For Each`陳述式。 您可以宣告的型別`element`明確地使用`As`陳述式，或者您可以依賴型別推斷來指派類型。 在任一情況下，範圍`element`是迴圈的主體。 不過，您無法宣告`element`外部和內部迴圈。  
  
 您可以選擇性地指定`element`中`Next`陳述式。 這有助於改善您程式的可讀性，特別是如果您有巢狀`For Each`迴圈。 您必須指定相同的變數會出現在對應的`For Each`陳述式。  
  
 您可能想要避免變更值的`element`在迴圈內。 如此一來，可以讓更難閱讀及偵錯程式碼。 變更值的`group`不會影響集合或其項目初次進入迴圈時所決定。  
  
 當您在巢狀迴圈，如果`Next`外部的巢狀層級的陳述式之前便遇到`Next`內部的層級，編譯器會發出錯誤信號。 不過，編譯器可以偵測此重疊錯誤，只有當您指定`element`中每個`Next`陳述式。  
  
 如果您的程式碼相依於周遊集合以特定順序`For Each`...`Next`迴圈並不是最佳的選擇，除非您知道的特性，列舉值物件的集合會公開。 周遊的順序不由 Visual Basic 中，但由<xref:System.Collections.IEnumerator.MoveNext%2A>列舉值物件的方法。</xref:System.Collections.IEnumerator.MoveNext%2A> 因此，您可能無法預測集合中的哪個項目是要在傳回第一個`element`，或指定的項目後傳回下一步。 使用不同的迴圈結構，例如更可靠的結果可能會比較`For`...`Next` or `Do`...`Loop`.  
  
 資料型別`element`，這類的資料類型的項目必須是`group`可以轉換成它。  
  
 資料型別`group`必須是指的是集合或陣列，是可列舉的參考型別。 通常這表示，`group`參考該物件會實作<xref:System.Collections.IEnumerable>介面`System.Collections`命名空間或<xref:System.Collections.Generic.IEnumerable%601>介面`System.Collections.Generic`命名空間。</xref:System.Collections.Generic.IEnumerable%601> </xref:System.Collections.IEnumerable> `System.Collections.IEnumerable`定義<xref:System.Collections.IEnumerable.GetEnumerator%2A>方法，傳回集合的列舉值物件。</xref:System.Collections.IEnumerable.GetEnumerator%2A> 列舉值物件實作`System.Collections.IEnumerator`介面`System.Collections`命名空間，並公開<xref:System.Collections.IEnumerator.Current%2A>屬性和<xref:System.Collections.IEnumerator.Reset%2A>和<xref:System.Collections.IEnumerator.MoveNext%2A>方法。</xref:System.Collections.IEnumerator.MoveNext%2A> </xref:System.Collections.IEnumerator.Reset%2A> </xref:System.Collections.IEnumerator.Current%2A> Visual Basic 會使用這些來周遊集合。  
  
### <a name="narrowing-conversions"></a>縮小轉換  
 當`Option Strict`設為`On`，縮小轉換通常會導致編譯器錯誤。 在`For Each`陳述式，不過，轉換中的項目`group`至`element`評估和執行階段，且會抑制因縮小轉換的編譯器錯誤。  
  
 在下列範例中，指派`m`做為初始值`n`不會進行編譯時`Option Strict`上是因為轉換`Long`至`Integer`是縮小轉換。 在`For Each`陳述式，不過，錯誤會報告，即使指派給`number`需要從相同的轉換`Long`到`Integer`。 在`For Each`包含大量的陳述式，執行階段錯誤發生時<xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A>套用至數量龐大。</xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A>  
  
 [!code-vb[VbVbalrStatements #&89;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_5.vb)]  
  
### <a name="ienumerator-calls"></a>IEnumerator 呼叫  
 當執行`For Each`...`Next`迴圈啟動時，Visual Basic 會確認`group`指的是有效的集合物件。 如果沒有，則會擲回例外狀況。 否則，它會呼叫<xref:System.Collections.IEnumerator.MoveNext%2A>方法和<xref:System.Collections.IEnumerator.Current%2A>傳回的第一個項目列舉值物件的屬性。</xref:System.Collections.IEnumerator.Current%2A> </xref:System.Collections.IEnumerator.MoveNext%2A> 如果`MoveNext`表示有下一個項目，亦即，如果集合是空的`For Each`停駐點，並將控制項傳遞給之後的陳述式`Next`陳述式。 否則，Visual Basic 會將設定`element`到第一個項目以及執行陳述式區塊。  
  
 每次在 Visual Basic 遇到`Next`陳述式，它會傳回`For Each`陳述式。 它會呼叫一次`MoveNext`和`Current`傳回下一個項目，再執行區塊或根據結果迴圈就會停止。 此程序會繼續進行到`MoveNext`表示沒有下一個項目或`Exit For`遇到陳述式。  
  
 **修改集合。** 所傳回的列舉值物件<xref:System.Collections.IEnumerable.GetEnumerator%2A>通常不會讓您新增、 刪除、 取代或重新排列任何項目來變更集合。</xref:System.Collections.IEnumerable.GetEnumerator%2A> 如果您初始化之後，變更集合`For Each`...`Next`迴圈中，列舉程式物件失效，且後續嘗試存取的項目會導致<xref:System.InvalidOperationException>例外狀況。</xref:System.InvalidOperationException>  
  
 不過，修改這個封鎖不由[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]，而是由實作<xref:System.Collections.IEnumerable>介面。</xref:System.Collections.IEnumerable> 它就能實作`IEnumerable`反覆項目期間，修改允許的方式。 如果您考慮要進行這類動態修改，請確定您了解特性`IEnumerable`集合上的實作。  
  
 **修改集合項目。** <xref:System.Collections.IEnumerator.Current%2A>列舉值物件的屬性是[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)，並傳回每個集合項目的本機複本。</xref:System.Collections.IEnumerator.Current%2A> 這表示您無法修改項目本身中`For Each`...`Next` loop. 您進行任何修改會影響本機複本從`Current`並不會反應到基礎集合。 不過，如果項目是參考型別，您可以修改它所指向的執行個體的成員。 下列範例會修改`BackColor`的每個成員`thisControl`項目。 不過，您不能修改`thisControl`本身。  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 可以修改上述範例`BackColor`的每個成員`thisControl`項目，雖然它不能修改`thisControl`本身。  
  
 **周遊陣列。** 因為<xref:System.Array>類別會實作<xref:System.Collections.IEnumerable>介面，所有陣列都公開<xref:System.Array.GetEnumerator%2A>方法。</xref:System.Array.GetEnumerator%2A> </xref:System.Collections.IEnumerable> </xref:System.Array> 這表示，您可以逐一查看陣列`For Each`...`Next` loop. 不過，您可以只讀取陣列元素。 您無法變更。  
  
## <a name="example"></a>範例  
 下列範例會列出在 C:\ 目錄中的所有資料夾使用<xref:System.IO.DirectoryInfo>類別。</xref:System.IO.DirectoryInfo>  
  
 [!code-vb[VbVbalrStatements #&124;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_6.vb)]  
  
## <a name="example"></a>範例  
 下列範例說明排序集合的程序。 此範例來排序的執行個體`Car` <xref:System.Collections.Generic.List%601>.</xref:System.Collections.Generic.List%601>中儲存的類別 `Car`類別會實作<xref:System.IComparable%601>介面，需要<xref:System.IComparable%601.CompareTo%2A>實作方法。</xref:System.IComparable%601.CompareTo%2A> </xref:System.IComparable%601>  
  
 每次呼叫<xref:System.IComparable%601.CompareTo%2A>方法會讓您用來排序的單一比較。</xref:System.IComparable%601.CompareTo%2A> 使用者撰寫的程式碼`CompareTo`方法會傳回目前物件與另一個物件的每個比較的值。 如果目前物件比另一個物件小則傳回的值小於零，如果目前物件比另一個物件大則傳回的值大於零，如果它們相等則傳回零。 這可讓您以程式碼定義大於、小於、等於的準則。  
  
 在`ListCars`方法，`cars.Sort()`陳述式會將清單排序。 這個呼叫<xref:System.Collections.Generic.List%601.Sort%2A>方法<xref:System.Collections.Generic.List%601>造成`CompareTo`自動呼叫的方法`Car`物件`List`。</xref:System.Collections.Generic.List%601> </xref:System.Collections.Generic.List%601.Sort%2A>  
  
 [!code-vb[VbVbalrStatements #&125;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_7.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [集合](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)   
 [For...下一個陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [迴圈結構](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [While...結束 While 陳述式](../../../visual-basic/language-reference/statements/while-end-while-statement.md)   
 [執行動作...迴圈陳述式](../../../visual-basic/language-reference/statements/do-loop-statement.md)   
 [擴展和縮小轉換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [物件初始設定式︰ 具名和匿名類型](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)   
 [集合初始設定式](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)   
 [陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)
