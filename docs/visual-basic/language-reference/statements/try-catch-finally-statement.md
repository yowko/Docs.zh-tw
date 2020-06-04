---
title: 嘗試 .。。Catch .。。Finally 語句
description: 瞭解如何搭配 Visual Basic Try/Catch/Finally 語句來使用例外狀況處理。
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
ms.openlocfilehash: 22f1611786a3da512632b5b547b7ef141c8f65c6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84391764"
---
# <a name="trycatchfinally-statement-visual-basic"></a>Try...Catch...Finally 陳述式 (Visual Basic)

提供一種方法來處理特定程式碼區塊中可能發生的部分或所有可能錯誤，同時仍執行程式碼。

## <a name="syntax"></a>語法

```vb
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
|`tryStatements`|選擇性。 可能發生錯誤的語句。 可以是複合陳述式。|
|`Catch`|選擇性。 允許多個 `Catch` 區塊。 如果在處理區塊時發生例外狀況 `Try` ， `Catch` 則會以文字順序檢查每個語句，以判斷是否要處理例外狀況，並代表已擲回 `exception` 的例外狀況。|
|`exception`|選擇性。 任何變數名稱。 `exception` 的初始值就是擲回之錯誤的值。 與搭配使用 `Catch` ，以指定攔截到的錯誤。 如果省略，語句會攔截 `Catch` 任何例外狀況。|
|`type`|選擇性。 指定類別篩選的類型。 如果的值 `exception` 是由或衍生型別所指定的型別 `type` ，則識別碼會變成系結至例外狀況物件。|
|`When`|選擇性。 `Catch` `When` 只有當評估為時，含有子句的語句才會攔截例外狀況 `expression` `True` 。 `When`只有在檢查例外狀況的類型之後，才會套用子句，而且 `expression` 可能會參考代表例外狀況的識別碼。|
|`expression`|選擇性。 必須可以隱含地轉換為 `Boolean` 。 描述一般篩選準則的任何運算式。 通常用來依錯誤號碼篩選。 搭配 `When` 關鍵字用來指定發生錯誤的情況。|
|`catchStatements`|選擇性。 用來處理相關聯區塊中所發生之錯誤的語句 `Try` 。 可以是複合陳述式。|
|`Exit Try`|選擇性。 違反結構的關鍵字 `Try...Catch...Finally` 。 執行時，會以緊接在語句之後的程式碼繼續進行 `End Try` 。 `Finally`語句仍會執行。 區塊中不允許使用 `Finally` 。|
|`Finally`|選擇性。 `Finally`當執行離開語句的任何部分時，一律會執行區塊 `Try...Catch` 。|
|`finallyStatements`|選擇性。 發生所有其他錯誤處理之後執行的語句。|
|`End Try`|終止 `Try...Catch...Finally` 結構。|

## <a name="remarks"></a>備註

如果您預期特定的例外狀況可能會在程式碼的特定區段中發生，請將程式碼放在區塊中， `Try` 然後使用 `Catch` 區塊來保留控制項並處理例外狀況（如果發生）。

`Try…Catch`語句是由 `Try` 區塊後面接著一個或多個 `Catch` 子句所組成，其指定各種例外狀況的處理常式。 在區塊中擲回例外 `Try` 狀況時，Visual Basic 會尋找 `Catch` 處理例外狀況的語句。 如果找不到相符的 `Catch` 語句，Visual Basic 會檢查呼叫目前方法的方法，並在呼叫堆疊上開啟。 如果 `Catch` 找不到任何區塊，Visual Basic 會向使用者顯示未處理的例外狀況訊息，並停止執行程式。

您可以在語句中使用一個以上的 `Catch` 語句 `Try…Catch` 。 如果您這樣做，子句的順序 `Catch` 很重要，因為它們會依序進行檢查。 在較不特定的例外狀況之前攔截較特定的例外狀況。

下列 `Catch` 語句條件是最不明確的，而且會攔截所有衍生自類別的例外狀況 <xref:System.Exception> 。 在 `Catch` `Try...Catch...Finally` 捕捉到您預期的所有特定例外狀況之後，通常應該使用這些變化之一做為結構中的最後一個區塊。 控制流程永遠不能觸及 `Catch` 遵循下列其中一種變化的區塊。

- `type`是 `Exception` ，例如：`Catch ex As Exception`

- 語句沒有 `exception` 變數，例如：`Catch`

當 `Try…Catch…Finally` 語句嵌套于另一個 `Try` 區塊時，Visual Basic 會先檢查 `Catch` 最內層區塊中的每個語句 `Try` 。 如果找不到相符 `Catch` 的語句，搜尋會繼續進行 `Catch` 外部區塊的語句 `Try…Catch…Finally` 。

區塊中的本機變數 `Try` 無法在區塊中使用， `Catch` 因為它們是個別的區塊。 如果您想要在多個區塊中使用變數，請在結構外宣告變數 `Try...Catch...Finally` 。

> [!TIP]
> `Try…Catch…Finally`語句是以 IntelliSense 程式碼片段的形式提供。 在 [程式碼片段管理員] 中，展開 [**程式碼模式]-如果每個都嘗試 Catch、Property 等**，然後再進行**錯誤處理（例外狀況）**。 如需詳細資訊，請參閱[程式碼片段](/visualstudio/ide/code-snippets)。

## <a name="finally-block"></a>Finally 區塊

如果您有一或多個必須在結束結構之前執行的語句 `Try` ，請使用 `Finally` 區塊。 控制項在 `Finally` 傳入結構之前就會傳遞至區塊 `Try…Catch` 。 即使在結構內的任何位置發生例外狀況，也是如此 `Try` 。

`Finally`區塊適用于執行任何必須執行的程式碼，即使發生例外狀況也一樣。 不論區塊結束的方式為何，控制項都會傳遞至 `Finally` 區塊 `Try...Catch` 。

`Finally`即使您的程式碼在 `Return` 或區塊中遇到語句，區塊中的程式碼還是會執行 `Try` `Catch` 。 在下列情況下，控制項不會從 `Try` 或 `Catch` 區塊傳遞至對應的 `Finally` 區塊：

- 在或區塊中遇到[End 語句](end-statement.md) `Try` `Catch` 。

- <xref:System.StackOverflowException>或區塊中擲回 `Try` `Catch` 。

將執行明確轉移到區塊中是不正確 `Finally` 。 `Finally`除了例外狀況之外，從區塊傳出執行是不正確。

如果 `Try` 語句未包含至少一個 `Catch` 區塊，它必須包含一個 `Finally` 區塊。

> [!TIP]
> 如果您不需要攔截特定的例外狀況，則 `Using` 語句的行為就像 `Try…Finally` 區塊，並保證資源的處置，不論您如何結束區塊。 即使有未處理的例外狀況，也是如此。 如需詳細資訊，請參閱[Using 語句](using-statement.md)。

## <a name="exception-argument"></a>Exception 引數

`Catch`Block `exception` 引數是類別的實例， <xref:System.Exception> 或衍生自類別的類別 `Exception` 。 `Exception`類別實例會對應到區塊中發生的錯誤 `Try` 。

物件的屬性 `Exception` 有助於找出例外狀況的原因和位置。 例如， <xref:System.Exception.StackTrace%2A> 屬性會列出導致例外狀況的被呼叫方法，協助您找出程式碼中發生錯誤的位置。 <xref:System.Exception.Message%2A>傳回描述例外狀況的訊息。 <xref:System.Exception.HelpLink%2A>傳回關聯之說明檔的連結。 <xref:System.Exception.InnerException%2A>傳回 `Exception` 造成目前例外狀況的物件，如果沒有原始的則傳回 `Nothing` `Exception` 。

## <a name="considerations-when-using-a-trycatch-statement"></a>使用 [嘗試 ...] 時的考慮Catch 語句

僅使用 `Try…Catch` 語句來表示發生異常或意外的程式事件。 其原因包括下列各項：

- 在執行時間攔截例外狀況會產生額外的負荷，而且可能比預先檢查來避免例外狀況的速度慢。

- 如果 `Catch` 未正確處理區塊，則例外狀況可能不會正確地回報給使用者。

- 例外狀況處理會使程式變得更複雜。

您不一定需要 `Try…Catch` 語句來檢查是否有可能發生的狀況。 下列範例會先檢查檔案是否存在，然後再嘗試開啟檔案。 這可減少攔截方法所擲回之例外狀況的需要 <xref:System.IO.File.OpenText%2A> 。

[!code-vb[VbVbalrStatements#94](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#94)]

請確定區塊中的程式碼 `Catch` 可以正確地向使用者報告例外狀況，不論是透過安全線程記錄或適當的訊息。 否則，例外狀況可能會維持不明。

## <a name="async-methods"></a>非同步方法

如果您使用[Async](../modifiers/async.md)修飾詞來標示方法，則可以在方法中使用[Await](../operators/await-operator.md)運算子。 具有運算子的語句會 `Await` 暫停執行方法，直到等候的工作完成為止。 工作代表進行中的工作。 當與運算子相關聯的工作 `Await` 完成時，會在相同的方法中繼續執行。 如需詳細資訊，請參閱[非同步程式中的控制流程](../../programming-guide/concepts/async/control-flow-in-async-programs.md)。

非同步方法傳回的工作可能會以錯誤狀態結束，表示它已因未處理的例外狀況而完成。 工作可能也會以取消的狀態結束，這會導致 `OperationCanceledException` 從 await 運算式擲回。 若要攔截任一類型的例外狀況，請將 `Await` 與工作相關聯的運算式放在區塊中， `Try` 並攔截區塊中的例外狀況 `Catch` 。 本主題稍後會提供範例。

工作可能處於錯誤狀態，因為有多個例外狀況負責其錯誤。 例如，工作可能是對 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> 呼叫的結果。 當您等候這類工作時，攔截到的例外狀況只是其中一個例外狀況，而且您無法預測會攔截到哪個例外狀況。 本主題稍後會提供範例。

`Await`運算式不能在 `Catch` 區塊或區塊內 `Finally` 。

## <a name="iterators"></a>迭代器

反覆運算器函數或存取子會在 `Get` 集合上執行自訂反復專案。 反覆運算器會使用[Yield](yield-statement.md)語句，一次傳回集合中的每個元素。 您可以使用[For Each ... 來呼叫 iterator 函數。下一個語句](for-each-next-statement.md)。

`Yield`語句可以在 `Try` 區塊內。 `Try`包含語句的區塊 `Yield` 可以有 `Catch` 區塊，而且可以有 `Finally` 區塊。 如需範例，請參閱[反覆運算](../../programming-guide/concepts/iterators.md)器的「在 Visual Basic 中嘗試區塊」一節。

`Yield`語句不能在 `Catch` 區塊或 `Finally` 區塊內。

如果 `For Each` 主體（iterator 函式之外）擲回例外狀況， `Catch` 則不會執行 iterator 函式中的區塊，但 `Finally` 會執行 iterator 函式中的區塊。 `Catch`Iterator 函式內的區塊只會攔截反覆運算器函數內所發生的例外狀況。

## <a name="partial-trust-situations"></a>部分信任的情況

在部分信任的情況下，例如在網路共用上裝載的應用程式， `Try...Catch...Finally` 並不會攔截在叫用包含呼叫之方法之前發生的安全性例外狀況。 下列範例中，當您將它放在伺服器共用並從該處執行時，會產生錯誤「SecurityException：要求失敗。」 如需安全性例外狀況的詳細資訊，請參閱 <xref:System.Security.SecurityException> 類別。

[!code-vb[VbVbalrStatements#85](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#85)]

在這種部分信任的情況下，您必須將 `Process.Start` 語句放在不同的 `Sub` 。 的初始呼叫 `Sub` 將會失敗。 這可讓在 `Try...Catch` 啟動包含的之前攔截它 `Sub` `Process.Start` ，並產生安全性例外狀況。

## <a name="examples"></a>範例

### <a name="the-structure-of-trycatchfinally"></a>Try 的結構 .。。Catch .。。一點

下列範例說明語句的結構 `Try...Catch...Finally` 。

[!code-vb[VbVbalrStatements#86](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#86)]  

### <a name="exception-in-a-method-called-from-a-try-block"></a>從 Try 區塊呼叫的方法中發生例外狀況

在下列範例中，方法會擲回 `CreateException` `NullReferenceException` 。 產生例外狀況的程式碼不在區塊中 `Try` 。 因此， `CreateException` 方法不會處理例外狀況。 `RunSample`方法會處理例外狀況，因為方法的呼叫 `CreateException` 是在 `Try` 區塊中。

此範例包含 `Catch` 數個例外狀況類型的語句，從最特定到最常見的順序排序。

[!code-vb[VbVbalrStatements#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#91)]

### <a name="the-catch-when-statement"></a>Catch When 語句

下列範例顯示如何使用 `Catch When` 語句來篩選條件運算式。 如果條件運算式評估為 `True` ，則區塊中的程式碼會 `Catch` 執行。

[!code-vb[VbVbalrStatements#92](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#92)]

### <a name="nested-try-statements"></a>嵌套的 Try 語句

下列範例包含 `Try…Catch` 包含在區塊中的語句 `Try` 。 內部 `Catch` 區塊會擲回例外狀況， `InnerException` 並將其屬性設定為原始例外狀況。 外部 `Catch` 區塊會報告其本身的例外狀況和內部例外狀況。

[!code-vb[VbVbalrStatements#93](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#93)]

### <a name="exception-handling-for-async-methods"></a>非同步方法的例外狀況處理

下列範例說明非同步方法的例外狀況處理。 若要攔截適用于非同步工作的例外狀況， `Await` 運算式會在呼叫端的區塊中， `Try` 而例外狀況會在區塊中攔截 `Catch` 。

取消註解範例中的 `Throw New Exception` 行來示範例外狀況處理。 在區塊中攔截到例外狀況時 `Catch` ，工作的 `IsFaulted` 屬性會設定為 `True` ，而工作的 `Exception.InnerException` 屬性會設定為例外狀況。

取消註解 `Throw New OperationCancelledException` 行來示範取消非同步處理序時會發生的情況。 在區塊中攔截到例外狀況 `Catch` ，而工作的 `IsCanceled` 屬性設定為 `True` 。 不過，在某些不適用此範例的情況下， `IsFaulted` 會設為 `True` ，且 `IsCanceled` 會設定為 `False` 。

[!code-vb[csAsyncExceptions#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncexceptions/vb/class1.vb#1)]

### <a name="handling-multiple-exceptions-in-async-methods"></a>處理非同步方法中的多個例外狀況

下列範例說明多項工作可能會導致多個例外狀況的例外狀況處理。 `Try`區塊具有傳回之 `Await` 工作的運算式 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> 。 當套用的三項工作完成時，工作就會完成 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> 。

這三個工作都會造成例外狀況。 `Catch`區塊會逐一查看例外狀況，這會在傳回的 `Exception.InnerExceptions` 工作的屬性中找到 `Task.WhenAll` 。

[!code-vb[csAsyncExceptions#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncexceptions/vb/class1.vb#3)]

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:System.Exception>
- [Exit 陳述式](exit-statement.md)
- [On Error 陳述式](on-error-statement.md)
- [使用程式碼片段的最佳作法](/visualstudio/ide/best-practices-for-using-code-snippets)
- [例外狀況處理](../../../standard/parallel-programming/exception-handling-task-parallel-library.md)
- [Throw 語句](throw-statement.md)
