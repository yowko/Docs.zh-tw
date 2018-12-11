---
title: Try...Catch...Finally 陳述式 (Visual Basic)
description: 了解如何使用 Visual Basic Try/Catch/Finally 陳述式處理的例外狀況。
ms.date: 12/07/2018
f1_keywords:
- vb.Try...Catch...Finally
- vb.when
- vb.Finally
- vb.Catch
- vb.Try
helpviewer_keywords:
- Try...Catch...Finally statements
- Try statement [Visual Basic]
- try-catch exception handling, Try...Catch...Finally statements
- error handling, while running code
- Try statement [Visual Basic], Try...Catch...Finally
- Finally keyword [Visual Basic], Try...Catch...Finally
- Catch statement [Visual Basic]
- When keyword [Visual Basic]
- Visual Basic code, handling errors while running
- structured exception handling, Try...Catch...Finally statements
ms.assetid: d6488026-ccb3-42b8-a810-0d97b9d6472b
ms.custom: seodec18
ms.openlocfilehash: e7abf094331afc4ba972c0ff4696244900e6eaf1
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53240740"
---
# <a name="trycatchfinally-statement-visual-basic"></a>Try...Catch...Finally 陳述式 (Visual Basic)
提供處理部分或所有可能的錯誤時仍在執行程式碼中指定的程式碼區塊，可能發生的方法。

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
|`tryStatements`|選擇性。 可能發生錯誤的陳述式。 可以是複合陳述式。|  
|`Catch`|選擇性。 多個`Catch`允許的區塊。 如果發生例外狀況處理時`Try`區塊，每個`Catch`陳述式會檢查以判斷是否與處理的例外狀況的文字順序`exception`代表已擲回的例外狀況。|  
|`exception`|選擇性。 任何變數名稱。 `exception` 的初始值就是擲回之錯誤的值。 搭配`Catch`來指定錯誤攔截。 如果省略，`Catch`陳述式攔截任何例外狀況。|  
|`type`|選擇性。 指定的類別篩選器類型。 如果值`exception`所指定型別的`type`或衍生的型別中，識別碼會成為繫結至例外狀況物件。|  
|`When`|選擇性。 A`Catch`陳述式搭配`When`子句會攔截例外狀況時，才`expression`評估為`True`。 A`When`子句會檢查例外狀況的類型之後，才會套用和`expression`可能表示例外狀況的識別項參考。|  
|`expression`|選擇性。 必須是隱含地轉換成`Boolean`。 描述泛型篩選的任何運算式。 通常用來篩選出的錯誤號碼。 搭配`When`關鍵字來指定用以在攔截到錯誤的情況。|  
|`catchStatements`|選擇性。 陳述式來處理發生在相關聯的錯誤`Try`區塊。 可以是複合陳述式。|  
|`Exit Try`|選擇性。 中斷的關鍵字`Try...Catch...Finally`結構。 使用程式碼之後立即繼續執行`End Try`陳述式。 `Finally`仍可執行陳述式。 中不允許`Finally`區塊。|  
|`Finally`|選擇性。 A`Finally`當執行離開的任何部分時，就會永遠執行區塊`Try...Catch`陳述式。|  
|`finallyStatements`|選擇性。 所有其他錯誤處理都發生之後執行的陳述式。|  
|`End Try`|終止`Try...Catch...Finally`結構。|  
  
## <a name="remarks"></a>備註  
 如果您預期特定的例外狀況可能會發生在特定的一段程式碼期間，將程式碼置於`Try`封鎖，並使用`Catch`保留控制項，以及處理例外狀況發生時的區塊。  
  
 A`Try…Catch`陳述式組成`Try`區塊後面接著一或多個`Catch`子句，指定各種不同例外狀況處理常式。 當擲回例外狀況`Try`區塊中，Visual Basic 會尋找`Catch`處理例外狀況的陳述式。 如果比對`Catch`找不到陳述式、 Visual Basic 會檢查呼叫目前的方法，依此類推的呼叫堆疊上的方法。 如果沒有`Catch`找不到區塊、 Visual Basic 向使用者顯示未處理的例外狀況訊息，並停止執行程式。  
  
 您可以使用一個以上`Catch`中的陳述式`Try…Catch`陳述式。 如果您這麼做，順序`Catch`子句很重要，因為它們會依順序檢查。 在較不特定的例外狀況之前攔截較特定的例外狀況。  
  
 下列`Catch`陳述式的條件是最不特定，並會攔截所有例外狀況衍生自<xref:System.Exception>類別。 您通常應該使用其中一個這些變化最後`Catch`中區塊`Try...Catch...Finally`結構之後攔截您預期的所有特定例外狀況。 控制流程可以永遠無法觸達`Catch`遵循其中一個這些變化的區塊。  
  
-   `type`是`Exception`，例如： `Catch ex As Exception`  
  
-   該陳述式沒有`exception`變數，例如： `Catch`  
  
 當`Try…Catch…Finally`陳述式巢狀方式置於另一個`Try`區塊中，Visual Basic 會先檢查每個`Catch`陳述式中最內側`Try`區塊。 如果沒有相符`Catch`找到陳述式中，搜尋會繼續`Catch`陳述式的外部`Try…Catch…Finally`區塊。  
  
 從區域變數`Try`區塊中未提供`Catch`封鎖，因為它們是不同的區塊。 如果您想要使用多個區塊中的變數，將外部變數宣告`Try...Catch...Finally`結構。  
  
> [!TIP]
>  `Try…Catch…Finally`陳述式可從 IntelliSense 程式碼片段。 在程式碼片段管理員 中，依序展開**程式碼模式-If、 For Each、 Try Catch、 屬性等等**，然後**錯誤處理 （例外狀況）**。 如需詳細資訊，請參閱[程式碼片段](/visualstudio/ide/code-snippets)。  
  
## <a name="finally-block"></a>Finally 區塊  
 如果您有一或多個您在結束前必須執行的陳述式`Try`結構，請使用`Finally`區塊。 控制權會傳遞給`Finally`封鎖之前它會傳遞共`Try…Catch`結構。 這是 true，即使在任何一處發生例外狀況`Try`結構。  
  
 A`Finally`區塊在執行任何程式碼必須執行，即使發生例外狀況是很有用。 控制權會傳遞給`Finally`不論區塊`Try...Catch`區塊結束。  
  
 中的程式碼`Finally`封鎖執行，即使您的程式碼遇到`Return`中的陳述式`Try`或`Catch`區塊。 控制項不會從傳遞`Try`或是`Catch`封鎖對應`Finally`封鎖在下列情況：  
  
-   [End 陳述式](../../../visual-basic/language-reference/statements/end-statement.md)中遇到`Try`或`Catch`區塊。  
  
-   A<xref:System.StackOverflowException>中擲回`Try`或`Catch`區塊。  
  
 若要明確地傳輸到執行無效`Finally`區塊。 傳送執行共`Finally`區塊不是有效的除了透過例外狀況。  
  
 如果`Try`陳述式未包含至少一個`Catch`區塊中，它必須包含`Finally`區塊。  
  
> [!TIP]
>  如果您不需要攔截特定的例外狀況`Using`陳述式的行為類似`Try…Finally`區塊，以及保證可供使用的資源，不論您如何結束區塊。 這是即使有未處理的例外狀況，則為 true。 如需詳細資訊，請參閱 [Using 陳述式](../../../visual-basic/language-reference/statements/using-statement.md)。  
  
## <a name="exception-argument"></a>例外狀況的引數  
 `Catch`區塊`exception`引數是的執行個體<xref:System.Exception>類別或衍生自類別`Exception`類別。 `Exception`類別執行個體對應至中發生之錯誤`Try`區塊。  
  
 屬性`Exception`物件協助識別原因和例外狀況的位置。 比方說，<xref:System.Exception.StackTrace%2A>屬性清單導致例外狀況，協助您尋找程式碼中發生錯誤的呼叫的方法。 <xref:System.Exception.Message%2A> 傳回描述例外狀況的訊息。 <xref:System.Exception.HelpLink%2A> 會傳回相關聯的說明檔的連結。 <xref:System.Exception.InnerException%2A> 會傳回`Exception`造成目前例外狀況，或它的物件會傳回`Nothing`如果沒有任何原始`Exception`。  
  
## <a name="considerations-when-using-a-trycatch-statement"></a>使用 Try 時的考量...Catch 陳述式  
 使用`Try…Catch`只表示發生異常或非預期的程式事件的陳述式。 這樣做的原因包括：  
  
-   在執行階段攔截例外狀況會建立額外的負荷，並可能會低於預先檢查，以避免發生例外狀況。  
  
-   如果`Catch`無法正確處理區塊、 例外狀況可能不會報告正確的使用者。  
  
-   例外狀況處理可讓程式更複雜。  
  
 您不一定需要`Try…Catch`陳述式來檢查是否有可能發生的狀況。 下列範例會檢查檔案是否存在然後再嘗試開啟它。 這可減少需要攔截所擲回的例外狀況<xref:System.IO.File.OpenText%2A>方法。  
  
 [!code-vb[VbVbalrStatements#94](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_1.vb)]  
  
 請確定該程式碼中的`Catch`區塊可以正確地報告給使用者，例外狀況，不論是透過安全執行緒記錄或適當的訊息。 否則，您可能會維持未知例外狀況。  
  
## <a name="async-methods"></a>非同步方法  
 如果您將標記的方法[非同步](../../../visual-basic/language-reference/modifiers/async.md)修飾詞，您可以使用[Await](../../../visual-basic/language-reference/operators/await-operator.md)方法中的運算子。 陳述式加上`Await`運算子會暫停執行方法，直到等候的工作完成。 工作代表進行中的工作。 當相關聯的工作`Await`運算子完成時，執行會繼續在相同的方法。 如需詳細資訊，請參閱 <<c0> [ 非同步程式中的控制流程](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)。  
  
 非同步方法所傳回的工作可能會處於錯誤狀態，指出它完成因為發生未處理的例外狀況。 工作可能也會結束取消的狀態，導致`OperationCanceledException`擲出 await 運算式。 若要攔截的例外狀況的其中一個類型，請將`Await`運算式中的工作與相關聯`Try`區塊中，並攔截例外狀況中的`Catch`區塊。 本主題稍後提供的範例。  
  
 工作可能處於錯誤狀態，因為多個例外狀況會負責其錯誤。 例如，工作可能是對 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> 呼叫的結果。 當您等候這類工作時，攔截的例外狀況只是其中一個例外狀況，而且您無法預測會攔截到例外狀況。 本主題稍後提供的範例。  
  
 `Await`運算式不能是內`Catch`區塊或`Finally`區塊。  
  
## <a name="iterators"></a>迭代器  
 迭代器函式或`Get`存取子會對集合執行自訂反覆項目。 迭代器會使用[產生](../../../visual-basic/language-reference/statements/yield-statement.md)陳述式來傳回一次一個集合的每個項目。 您可以使用呼叫 iterator 函式[每個...下一個陳述式](../../../visual-basic/language-reference/statements/for-each-next-statement.md)。  
  
 A`Yield`陳述式可以位於`Try`區塊。 A`Try`包含區塊`Yield`陳述式可以有`Catch`區塊中使用，而且可以有`Finally`區塊。 請參閱 「 嘗試區塊在 Visual Basic 」 一節[迭代器](../../programming-guide/concepts/iterators.md)的範例。  
  
 A`Yield`陳述式不能內`Catch`區塊或`Finally`區塊。  
  
 如果`For Each`主體 （之外的迭代器函式） 會擲回的例外狀況，`Catch`迭代器函式中的區塊不會執行，但`Finally`執行迭代器函式中的區塊。 A`Catch`迭代器函式內的區塊會攔截在迭代器函式內所發生的例外狀況。  
  
## <a name="partial-trust-situations"></a>部分信任情況下  
 在部分信任情況下，應用程式裝載在網路共用，例如`Try...Catch...Finally`不會攔截之前叫用包含呼叫方法時，發生安全性例外狀況。 下列範例中，當您將它放在伺服器共用，並從該處執行會產生錯誤 「 System.Security.SecurityException:要求失敗。 」 如需安全性例外狀況的詳細資訊，請參閱<xref:System.Security.SecurityException>類別。  
  
 [!code-vb[VbVbalrStatements#85](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_2.vb)]  
  
 在這類的部分信任情況下，您必須將放`Process.Start`在個別的陳述式`Sub`。 若要在初次呼叫`Sub`將會失敗。 這可讓`Try...Catch`攔截之前`Sub`包含`Process.Start`已啟動，並產生安全性例外狀況。  
  
## <a name="examples"></a>範例

### <a name="the-structure-of-trycatchfinally"></a>請嘗試結構...Catch...最後

下列範例說明結構`Try...Catch...Finally`陳述式。  
  
 [!code-vb[VbVbalrStatements#86](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_3.vb)]  
  
### <a name="exception-in-a-method-called-from-a-try-block"></a>從 Try 區塊中呼叫的方法中的例外狀況

 在下列範例中，`CreateException`方法會擲回`NullReferenceException`。 不會產生例外狀況的程式碼是`Try`區塊。 因此，`CreateException`方法不會處理例外狀況。 `RunSample`方法未處理例外狀況，因為呼叫`CreateException`方法是在`Try`區塊。  
  
 此範例也包含`Catch`陳述式中的數種類型的例外狀況，排序從最特定到最普遍。  
  
 [!code-vb[VbVbalrStatements#91](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_4.vb)]  
  
### <a name="the-catch-when-statement"></a>當 Catch 陳述式

 下列範例示範如何使用`Catch When`篩選條件運算式的陳述式。 如果條件運算式評估為`True`中的程式碼`Catch`封鎖執行。  
  
 [!code-vb[VbVbalrStatements#92](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_5.vb)]  
  
### <a name="nested-try-statements"></a>巢狀的 Try 陳述式

 下列範例具有`Try…Catch`陳述式中包含`Try`區塊。 內部`Catch`區塊擲回例外狀況有其`InnerException`屬性設為原始的例外狀況。 外部`Catch`區塊會報告它自己的例外狀況以及內部例外狀況。  
  
 [!code-vb[VbVbalrStatements#93](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_6.vb)]  
  
### <a name="exception-handling-for-async-methods"></a>非同步方法的例外狀況處理

 下列範例說明非同步方法的例外狀況處理。 若要擷取套用至一項非同步工作，例外狀況`Await`運算式是在`Try`的呼叫端和例外狀況區塊會攔截在`Catch`區塊。  
  
 取消註解範例中的 `Throw New Exception` 行來示範例外狀況處理。 中攔截例外狀況`Catch`封鎖工作的`IsFaulted`屬性設定為`True`，以及使用 「 工作`Exception.InnerException`屬性設定為例外狀況。  
  
 取消註解 `Throw New OperationCancelledException` 行來示範取消非同步處理序時會發生的情況。 在攔截例外狀況`Catch`區塊，以及工作`IsCanceled`屬性設定為`True`。 不過，在未套用至這個範例中，某些情況下`IsFaulted`設定為`True`並`IsCanceled`設定為`False`。  
  
 [!code-vb[csAsyncExceptions#1](../../../csharp/language-reference/keywords/codesnippet/VisualBasic/try-catch-finally-statement_7.vb)]  
  
### <a name="handling-multiple-exceptions-in-async-methods"></a>在非同步方法中的多個例外狀況處理

 下列範例說明多項工作可能會導致多個例外狀況的例外狀況處理。 `Try`區塊`Await`工作的運算式，<xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>傳回。 工作已完成的三個工作的<xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>套用都已完成。  
  
 這三個工作都會造成例外狀況。 `Catch`區塊會逐一查看的例外狀況中找到`Exception.InnerExceptions`工作的屬性，`Task.WhenAll`傳回。  
  
 [!code-vb[csAsyncExceptions#3](../../../csharp/language-reference/keywords/codesnippet/VisualBasic/try-catch-finally-statement_8.vb)]  
  
## <a name="see-also"></a>另請參閱  

- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:System.Exception>
- [Exit 陳述式](../../../visual-basic/language-reference/statements/exit-statement.md)
- [On Error 陳述式](../../../visual-basic/language-reference/statements/on-error-statement.md)
- [使用程式碼片段的最佳作法](/visualstudio/ide/best-practices-for-using-code-snippets)
- [例外狀況處理](../../../standard/parallel-programming/exception-handling-task-parallel-library.md)
- [Throw 陳述式](../../../visual-basic/language-reference/statements/throw-statement.md)
