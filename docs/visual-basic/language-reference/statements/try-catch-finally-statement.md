---
title: "請嘗試...Catch...Finally 陳述式 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Try...Catch...Finally
- vb.when
- vb.Finally
- vb.Catch
- vb.Try
dev_langs:
- VB
helpviewer_keywords:
- Try...Catch...Finally statements
- Try statement
- try-catch exception handling, Try...Catch...Finally statements
- error handling, while running code
- Try statement, Try...Catch...Finally
- Finally keyword [Visual Basic], Try...Catch...Finally
- Catch statement
- When keyword
- Visual Basic code, handling errors while running
- structured exception handling, Try...Catch...Finally statements
ms.assetid: d6488026-ccb3-42b8-a810-0d97b9d6472b
caps.latest.revision: 69
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 379359e3a338746ccd440dbe1ad58c483e562dbe
ms.lasthandoff: 03/13/2017

---
# <a name="trycatchfinally-statement-visual-basic"></a>Try...Catch...Finally 陳述式 (Visual Basic)
提供處理部分或所有可能的錯誤時繼續執行程式碼時可能發生給定的程式碼區塊的方式。  
  
## <a name="syntax"></a>語法  
  
```  
Try  
    [ tryStatements ]  
    [ Exit Try ]  
[ Catch [ exception [ As type ] ] [ When expression ]  
    [ catchStatements ]  
    [ Exit Try ] ]  
[ Catch ... ]  
[ Finally  
    [ finallyStatements ] ]  
End Try  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`tryStatements`|選擇項。 可能發生錯誤的陳述式。 可以是複合陳述式。|  
|`Catch`|選擇項。 多個`Catch`允許的區塊。 如果發生例外狀況處理時`Try`區塊，每個`Catch`陳述式會檢查以判斷是否與處理的例外狀況的文字順序`exception`代表已擲回的例外狀況。|  
|`exception`|選擇項。 任何變數名稱。 `exception` 的初始值就是擲回之錯誤的值。 搭配使用`Catch`來指定錯誤攔截。 如果省略，`Catch`陳述式會攔截任何例外狀況。|  
|`type`|選擇項。 指定的類別篩選器類型。 如果值`exception`所指定型別的`type`或衍生型別，識別項會變成繫結至例外狀況物件。|  
|`When`|選擇項。 A`Catch`陳述式搭配`When`子句會攔截例外狀況時，才`expression`評估為`True`。 A`When`子句會先例外狀況類型、 套用和`expression`可能會參考表示例外狀況的識別項。|  
|`expression`|選擇項。 必須能夠隱含轉換為`Boolean`。 描述一般篩選器的任何運算式。 通常用來篩選錯誤號碼。 搭配`When`關鍵字來指定的情況下會攔截錯誤。|  
|`catchStatements`|選擇項。 處理發生在相關聯的錯誤的陳述式`Try`區塊。 可以是複合陳述式。|  
|`Exit Try`|選擇項。 中斷的關鍵字`Try...Catch...Finally`結構。 後面的程式碼繼續執行`End Try`陳述式。 `Finally`仍可執行陳述式。 中不允許`Finally`區塊。|  
|`Finally`|選擇項。 A`Finally`執行離開的任何部分時，就會永遠執行區塊`Try...Catch`陳述式。|  
|`finallyStatements`|選擇項。 所有其他錯誤處理都發生之後執行的陳述式。|  
|`End Try`|終止`Try...Catch...Finally`結構。|  
  
## <a name="remarks"></a>備註  
 如果您希望特定的例外狀況可能會發生在特定一段程式碼時，請將程式碼放`Try`區塊和使用`Catch`保留控制項，並處理例外狀況發生時的區塊。  
  
 A`Try…Catch`陳述式的組成`Try`區塊後面接著一個或多個`Catch`子句，指定的各種例外狀況處理常式。 當擲回例外狀況`Try`區塊，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]求取`Catch`處理例外狀況的陳述式。 如果比對`Catch`找不到陳述式，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]會檢查呼叫目前方法的呼叫堆疊上，依此類推的方法。 如果沒有`Catch`找不到區塊，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]向使用者顯示未處理的例外狀況訊息，並停止執行程式。  
  
 您可以使用多個`Catch`陳述式中的`Try…Catch`陳述式。 如果您這樣做，請順序`Catch`子句非常重要，因為順序進行檢查。 在較不特定的例外狀況之前攔截較特定的例外狀況。  
  
 下列`Catch`陳述式是最不特定 and 會攔截所有例外狀況衍生自<xref:System.Exception>類別。</xref:System.Exception> 您通常應該使用其中一個這些變化最後`Catch`區塊放在`Try...Catch...Finally`後攔截您預期的所有特定例外狀況的結構。 控制流程永遠達不到可以`Catch`遵循其中一個這些變化的區塊。  
  
-   `type`是`Exception`，例如︰`Catch ex As Exception`  
  
-   陳述式沒有`exception`變數，例如︰`Catch`  
  
 當`Try…Catch…Finally`陳述式巢狀方式置於另一個`Try`區塊，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]先檢查每個`Catch`陳述式中最內側`Try`區塊。 如果沒有相符的`Catch`找不到陳述式，搜尋會繼續`Catch`陳述式的外部`Try…Catch…Finally`區塊。  
  
 從本機變數`Try`區塊中沒有`Catch`封鎖，因為它們是不同的區塊。 如果您想要使用多個區塊中的變數，將外部變數宣告`Try...Catch...Finally`結構。  
  
> [!TIP]
>  `Try…Catch…Finally`陳述式會以提供 IntelliSense 程式碼片段。 在程式碼片段管理員中，展開**程式碼模式-如果，針對每個，Try Catch 屬性等**，然後**錯誤處理 （例外狀況）**。 如需詳細資訊，請參閱[程式碼片段](https://docs.microsoft.com/visualstudio/ide/code-snippets)。  
  
## <a name="finally-block"></a>Finally 區塊  
 如果您有一或多個陳述式結束之前，必須執行`Try`結構時，請使用`Finally`區塊。 控制權會傳遞給`Finally`封鎖之前就不會傳遞`Try…Catch`結構。 即使在任意處發生例外狀況是，則為 true`Try`結構。  
  
 A`Finally`區塊執行任何程式碼必須執行，即使發生例外狀況時非常有用。 控制權會傳遞給`Finally`不論區塊`Try...Catch`區塊結束。  
  
 中的程式碼`Finally`區塊執行，即使程式碼遇到`Return`陳述式中的`Try`或`Catch`區塊。 控制項不會從傳遞`Try`或`Catch`封鎖對應`Finally`封鎖在下列情況︰  
  
-   [End 陳述式](../../../visual-basic/language-reference/statements/end-statement.md)發生`Try`或`Catch`區塊。  
  
-   A<xref:System.StackOverflowException>中擲回`Try`或`Catch`區塊。</xref:System.StackOverflowException>  
  
 明確地傳送到執行無效`Finally`區塊。 傳輸郵件執行`Finally`區塊不正確的除了透過例外狀況。  
  
 如果`Try`陳述式未包含至少一個`Catch`區塊時，它必須包含`Finally`區塊。  
  
> [!TIP]
>  如果您不需要攔截特定例外狀況，`Using`陳述式的行為類似`Try…Finally`區塊，以及保證可供使用的資源，不論結束區塊的方式。 這是即使有未處理的例外狀況，則為 true。 如需詳細資訊，請參閱[Using 陳述式](../../../visual-basic/language-reference/statements/using-statement.md)。  
  
## <a name="exception-argument"></a>例外狀況引數  
 `Catch`區塊`exception`引數是執行個體<xref:System.Exception>類別或衍生自類別`Exception`類別</xref:System.Exception> `Exception`類別執行個體對應至錯誤的發生`Try`區塊。  
  
 屬性的`Exception`物件有助於識別原因和例外狀況的位置。 例如，<xref:System.Exception.StackTrace%2A>屬性清單導致例外狀況，協助您找出程式碼中發生錯誤的呼叫的方法。</xref:System.Exception.StackTrace%2A> <xref:System.Exception.Message%2A>傳回描述例外狀況的訊息。</xref:System.Exception.Message%2A> <xref:System.Exception.HelpLink%2A>傳回相關聯的說明檔的連結。</xref:System.Exception.HelpLink%2A> <xref:System.Exception.InnerException%2A>傳回`Exception`造成目前例外狀況，或它的物件會傳回`Nothing`如果沒有任何原始`Exception`。</xref:System.Exception.InnerException%2A>  
  
## <a name="considerations-when-using-a-trycatch-statement"></a>使用 Try 時的考量...Catch 陳述式  
 使用`Try…Catch`陳述式只能用來表示不尋常或非預期的程式事件的發生。 這麼做的原因包括︰  
  
-   攔截例外狀況在執行階段會建立額外的負荷，並可能會低於預先檢查，以避免例外狀況。  
  
-   如果`Catch`無法正確處理區塊、 例外狀況可能不會正確地報告給使用者。  
  
-   例外狀況處理可讓程式更複雜。  
  
 您不一定需要`Try…Catch`陳述式來檢查是否有可能發生的狀況。 下列範例會檢查檔案是否存在然後再嘗試開啟它。 這樣可以減少需要擲回的例外狀況攔截<xref:System.IO.File.OpenText%2A>方法。</xref:System.IO.File.OpenText%2A>  
  
 [!code-vb[VbVbalrStatements #&94;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_1.vb)]  
  
 請確定該程式碼中的`Catch`區塊可以正確地報告例外狀況給使用者，透過安全執行緒的記錄或適當的訊息。 否則，您可能仍未知例外狀況。  
  
## <a name="async-methods"></a>非同步方法  
 如果您將標示的方法與[非同步](../../../visual-basic/language-reference/modifiers/async.md)修飾詞，您可以使用[Await](../../../visual-basic/language-reference/operators/await-operator.md)方法中的運算子。 陳述式加上`Await`運算子暫止方法的執行，直到等候的工作完成為止。 工作代表進行中的工作。 當相關聯的工作`Await`運算子完成後，繼續執行相同的方法。 如需詳細資訊，請參閱[非同步程式中的控制流程](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)。  
  
 非同步方法所傳回的工作可能會結束錯誤的狀態，指出它已完成，因為未處理例外狀況。 工作可能也會取消的狀態，導致結束`OperationCanceledException`await 運算式不擲回。 若要攔截任一類型的例外狀況，請將`Await`中的工作相關聯的運算式`Try`區塊，並攔截的例外狀況中`Catch`區塊。 本主題稍後提供的範例。  
  
 工作可以處於錯誤狀態，因為多個例外狀況是負責其判定為失敗。 例如，工作可能是<xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>。</xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>呼叫的結果 當您等候這類工作時，攔截的例外狀況是其中一個例外狀況，並會攔截的例外狀況，您無法預測。 本主題稍後提供的範例。  
  
 `Await`運算式不能在`Catch`區塊或`Finally`區塊。  
  
## <a name="iterators"></a>Iterator  
 Iterator 函式或`Get`存取子集合上執行自訂的反覆項目。 迭代器會使用[產生](../../../visual-basic/language-reference/statements/yield-statement.md)陳述式來傳回每個項目一次一個的集合。 您可以使用呼叫 iterator 函式[每個...下一個陳述式](../../../visual-basic/language-reference/statements/for-each-next-statement.md)。  
  
 A`Yield`陳述式可以是內`Try`區塊。 A`Try`包含區塊`Yield`陳述式可以有`Catch`區塊，而且可以有`Finally`區塊。 請參閱 「 嘗試區塊在 Visual Basic 」 一節[迭代器](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)範例。  
  
 A`Yield`陳述式不能在`Catch`區塊或`Finally`區塊。  
  
 如果`For Each`（之外 iterator 函式） 的主體擲回例外狀況， `Catch` iterator 函式中的區塊不會執行，但`Finally`就會執行 iterator 函式中的區塊。 A `Catch` iterator 函式區塊攔截函式迭代器內發生的例外狀況。  
  
## <a name="partial-trust-situations"></a>部分信任的情況下  
 在部分信任情況下，應用程式裝載在網路共用，例如`Try...Catch...Finally`不會攔截之前叫用包含呼叫方法時，發生安全性例外狀況。 下列範例中，當您將它放在伺服器共用，然後執行之後，會產生錯誤 「 System.Security.SecurityException︰ 要求失敗。 」 如需安全性例外狀況的詳細資訊，請參閱<xref:System.Security.SecurityException>類別。</xref:System.Security.SecurityException>  
  
 [!code-vb[VbVbalrStatements #&85;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_2.vb)]  
  
 這類的部分信任情況下，您必須將`Process.Start`在個別的陳述式`Sub`。 若要在初次呼叫`Sub`將會失敗。 這可讓`Try...Catch`攔截它之前`Sub`，其中包含`Process.Start`已啟動，並產生安全性例外狀況。  
  
## <a name="example"></a>範例  
 下列範例說明結構`Try...Catch...Finally`陳述式。  
  
 [!code-vb[VbVbalrStatements # x86](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_3.vb)]  
  
## <a name="example"></a>範例  
 在下列範例中，`CreateException`方法會擲回`NullReferenceException`。 不會產生例外狀況的程式碼是`Try`區塊。 因此，`CreateException`方法不會處理例外狀況。 `RunSample`方法並處理例外狀況，因為呼叫`CreateException`方法位於`Try`區塊。  
  
 此範例也包含`Catch`數種類型的例外狀況的陳述式的順序來排列最特定到最普遍。  
  
 [!code-vb[VbVbalrStatements #&91;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_4.vb)]  
  
## <a name="example"></a>範例  
 下列範例示範如何使用`Catch When`篩選條件運算式的陳述式。 如果條件運算式評估為`True`中的程式碼`Catch`封鎖執行。  
  
 [!code-vb[VbVbalrStatements #&92;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_5.vb)]  
  
## <a name="example"></a>範例  
 下列範例具有`Try…Catch`陳述式中包含的`Try`區塊。 內部`Catch`區塊擲回例外狀況有其`InnerException`屬性設定為原始的例外狀況。 外部`Catch`區塊報告它自己的例外狀況，以及內部例外狀況。  
  
 [!code-vb[VbVbalrStatements #&93;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_6.vb)]  
  
## <a name="example"></a>範例  
 下列範例說明非同步方法的例外狀況處理。 若要攔截的例外狀況，適用於一項非同步工作，`Await`運算式是`Try`的呼叫端和例外狀況區塊會陷入`Catch`區塊。  
  
 取消註解範例中的 `Throw New Exception` 行來示範例外狀況處理。 在攔截例外狀況`Catch`封鎖工作的`IsFaulted`屬性設定為`True`，和工作的`Exception.InnerException`屬性設定為例外狀況。  
  
 取消註解`Throw New OperationCancelledException`列，以示範當您取消非同步處理序中發生的情況。 在攔截例外狀況`Catch`區塊，以及工作的`IsCanceled`屬性設定為`True`。 不過，在不適用於此範例中，某些情況下`IsFaulted`設為`True`和`IsCanceled`設為`False`。  
  
 [!code-vb[csAsyncExceptions&#1;](../../../csharp/language-reference/keywords/codesnippet/VisualBasic/try-catch-finally-statement_7.vb)]  
  
## <a name="example"></a>範例  
 下列範例說明多項工作可能會導致多個例外狀況的例外狀況處理。 `Try`區塊`Await`工作的運算式，<xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>傳回。</xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> 工作已完成的三個工作的<xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>套用已完成。</xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>  
  
 這三個工作都會造成例外狀況。 `Catch`區塊逐一查看的例外狀況中找到`Exception.InnerExceptions`工作的屬性，`Task.WhenAll`傳回。  
  
 [!code-vb[csAsyncExceptions&#3;](../../../csharp/language-reference/keywords/codesnippet/VisualBasic/try-catch-finally-statement_8.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.Information.Err%2A></xref:Microsoft.VisualBasic.Information.Err%2A>   
 <xref:System.Exception></xref:System.Exception>   
 [Exit 陳述式](../../../visual-basic/language-reference/statements/exit-statement.md)   
 [On Error 陳述式](../../../visual-basic/language-reference/statements/on-error-statement.md)   
 [使用程式碼片段的最佳作法](https://docs.microsoft.com/visualstudio/ide/best-practices-for-using-code-snippets)   
 [例外狀況處理](https://msdn.microsoft.com/library/dd997415)   
 [Throw 陳述式](../../../visual-basic/language-reference/statements/throw-statement.md)
