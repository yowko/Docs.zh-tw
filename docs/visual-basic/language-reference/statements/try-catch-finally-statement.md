---
title: "Try...Catch...Finally Statement (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Try...Catch...Finally"
  - "vb.when"
  - "vb.Finally"
  - "vb.Catch"
  - "vb.Try"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Try...Catch...Finally statements"
  - "Try statement"
  - "try-catch exception handling, Try...Catch...Finally statements"
  - "error handling, while running code"
  - "Try statement, Try...Catch...Finally"
  - "Finally keyword [Visual Basic], Try...Catch...Finally"
  - "Catch statement"
  - "When keyword"
  - "Visual Basic code, handling errors while running"
  - "structured exception handling, Try...Catch...Finally statements"
ms.assetid: d6488026-ccb3-42b8-a810-0d97b9d6472b
caps.latest.revision: 69
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 69
---
# Try...Catch...Finally Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

提供在給定的程式碼區塊 \(仍在執行中的程式碼\) 發生的部分或所有可能錯誤的處理方式。  
  
## 語法  
  
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
  
## 組件  
  
|||  
|-|-|  
|詞彙|定義|  
|`tryStatements`|選擇項。  發生錯誤的陳述式。  可以是複合陳述式。|  
|`Catch`|選擇項。  允許多個 `Catch` 區塊。  在處理 `Try` 區塊時，如果發生例外狀況 \(Exception\)，則會按文字順序檢查每一個 `Catch` 陳述式，以判斷它是否會利用代表已擲回之例外狀況的 `exception` 來處理例外狀況。|  
|`exception`|選擇項。  任何變數名稱。  `exception` 的初始值就是擲回的錯誤值。  與 `Catch` 搭配使用以指定攔截的錯誤。  如果省略，則 `Catch` 陳述式會攔截所有例外狀況。|  
|`type`|選擇項。  指定類別篩選條件類型。  如果 `exception` 的值為 `type` 所指定的型別或衍生型別 \(Derived Type\)，則識別項會繫結到例外狀況物件。|  
|`When`|選擇項。  只有在 `expression` 評估為 `True` 時，具有 `When` 子句的 `Catch` 陳述式才會攔截例外狀況。  只有在檢查例外狀況的型別之後，才會套用 `When` 子句，而且 `expression` 可能會參考代表例外狀況的識別項。|  
|`expression`|選擇項。  必須能夠隱含轉換為 `Boolean`。  描述一般篩選條件的任何運算式。  通常，用於按錯誤代碼篩選。  和 `When` 關鍵字一起使用來指定何種環境下會攔截錯誤。|  
|`catchStatements`|選擇項。  處理在關聯的 `Try` 區塊中所發生之錯誤的陳述式。  可以是複合陳述式。|  
|`Exit Try`|選擇項。  從 `Try...Catch...Finally` 結構中斷的關鍵字。  執行會利用緊跟在 `End Try` 陳述式後面的程式碼繼續進行。  仍將執行 `Finally` 陳述式。  不可用於 `Finally` 區塊中。|  
|`Finally`|選擇項。  當執行離開 `Try...Catch` 陳述式的任一部分時，一律會執行 `Finally` 區塊。|  
|`finallyStatements`|選擇項。  在所有其他錯誤處理發生之後執行的陳述式。|  
|`End Try`|結束 `Try...Catch...Finally` 結構。|  
  
## 備註  
 如果您預期在特定的程式碼區段的執行期間會發生特定的例外狀況，則請在 `Try` 區塊中放置程式碼，並使用 `Catch` 區塊來持續控制和處理發生的例外狀況。  
  
 `Try…Catch` 陳述式是由其後跟隨一個或多個指定各種例外狀況處理常式之 `Catch` 子句的 `Try` 區塊組成。  當 `Try` 區塊中擲回例外狀況時，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會尋找處理此例外狀況的 `Catch` 陳述式。  如果找到對應的 `Catch` 陳述式，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會檢查呼叫目前方法的方法，一直向上檢查至呼叫堆疊。  如果找不到 `Catch` 區塊，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 就會顯示未處理的例外狀況訊息以告知使用者，並停止執行程式。  
  
 您可以在 `Try…Catch` 陳述式中，使用一個以上的 `Catch` 陳述式。  如果這樣做，由於 `Catch` 子句是依照順序進行檢查，因此子句的順序就非常重要。  在較不特定的例外狀況之前攔截較特定的例外狀況。  
  
 下列 `Catch` 陳述式條件是最通用的，將會攔截所有衍生自 <xref:System.Exception> 類別的例外狀況。  在攔截您預期的所有特定例外狀況之後，您通常會使用這其中一個變化形式做為 `Try...Catch...Finally` 結構中的最後一個 `Catch` 區塊。  控制流程可能永遠不會達到下列任一變化隨後的 `Catch` 區塊。  
  
-   `type` 為 `Exception`，例如：`Catch ex As Exception`  
  
-   陳述式沒有 `exception` 變數，例如：`Catch`  
  
 當 `Try…Catch…Finally` 陳述式巢狀套疊於另一個 `Try` 區塊內時，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會首先檢查最內部 `Try` 區塊中的 `Catch` 陳述式。  如果找到相符的 `Catch` 陳述式，則會繼續搜尋外部 `Try…Catch…Finally` 區塊的 `Catch` 陳述式。  
  
 來自 `Try` 區塊的區域變數是個別的區塊，所以無法在 `Catch` 區塊中使用。  如果想在多個區塊中共用一個變數，請在 `Try...Catch...Finally` 結構外宣告該變數。  
  
> [!TIP]
>  `Try…Catch…Finally` 陳述式可用來做為 IntelliSense 程式碼片段。  在 \[程式碼片段管理員\] 中，依序展開 \[**程式碼模式 \- If、For Each、Try Catch、Property 等**\] 和 \[**錯誤處理 \(例外狀況\)**\]。  如需詳細資訊，請參閱 [程式碼片段](/visual-studio/ide/code-snippets)。  
  
## Finally 區塊  
 如果必須先執行一或多個陳述式再結束 `Try` 結構，請使用 `Finally` 區塊。  控制項會先傳遞至 `Finally` 區塊，再從 `Try…Catch` 結構傳出。  即使 `Try` 結構內部的任何位置發生例外狀況 \(Exception\)，也會執行這個動作。  
  
 `Finally` 區塊可用於執行即使發生例外狀況都必須執行的任何程式碼。  不論 `Try...Catch` 區塊如何結束，程式執行都會轉移到 `Finally` 區塊。  
  
 即使您的程式碼在 `Try` 或 `Catch` 區塊中遇到 `Return` 陳述式，`Finally` 區塊中的程式碼仍會執行。  在下列情況下，不會將控制項從 `Try` 或 `Catch` 區塊傳遞至對應的 `Finally` 區塊：  
  
-   [End Statement](../../../visual-basic/language-reference/statements/end-statement.md) 是在 `Try` 或 `Catch` 區塊中發生的。  
  
-   <xref:System.StackOverflowException> 是在 `Try` 或 `Catch` 區塊中擲回的。  
  
 您不能明確執行傳輸到 `Finally` 區塊。  在 `Finally` 區塊以外的傳送之執行無效，除了透過例外狀況。  
  
 如果 `Try` 陳述式未包含至少一個 `Catch` 區塊，它必須包含一個 `Finally` 區塊。  
  
> [!TIP]
>  如果不需要攔截特定例外狀況，則 `Using` 陳述式的行為會像 `Try…Finally` 區塊，而且不論是以何種方式結束該區塊，都保證會處置 \(Dispose\) 資源。  即使在未處理例外狀況的情況下也一樣。  如需詳細資訊，請參閱 [Using Statement](../../../visual-basic/language-reference/statements/using-statement.md)。  
  
## 例外狀況引數  
 `Catch` 區塊的 `exception` 引數是 <xref:System.Exception> 類別的執行個體或衍生自 `Exception` 類別的類別。  `Exception` 類別執行個體會對應至在 `Try` 區塊中發生的錯誤。  
  
 `Exception` 物件的屬性有助於識別例外狀況的原因和位置。  例如，<xref:System.Exception.StackTrace%2A> 屬性會列出呼叫過、且導致例外狀況發生的方法，幫助您在程式碼中找出錯誤發生之處。  <xref:System.Exception.Message%2A> 會傳回描述例外狀況的訊息。  <xref:System.Exception.HelpLink%2A> 會傳回相關說明檔的連結。  <xref:System.Exception.InnerException%2A> 會傳回造成目前例外狀況的 `Exception` 物件，如果沒有原始 `Exception`，則傳回 `Nothing`。  
  
## 使用 Try…Catch 陳述式時的注意事項  
 使用 `Try…Catch` 陳述式只是要表示發生不尋常或意外的程式事件。  發生這種情況的原因如下：  
  
-   在執行階段快取例外狀況會產生額外負荷，而且可能會比預先檢查避免例外狀況來得慢。  
  
-   如果未正確處理 `Catch` 區塊，可能就無法向使用者正確報告例外狀況。  
  
-   例外狀況處理使得程式更加複雜。  
  
 您不一定需要使用 `Try…Catch` 陳述式來檢查很可能發生的條件。  下列範例會在嘗試開啟檔案之前檢查檔案是否存在。  這會減少對 <xref:System.IO.File.OpenText%2A> 方法所擲回例外狀況進行快取的需要。  
  
 [!code-vb[VbVbalrStatements#94](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/try-catch-finally-statem_1.vb)]  
  
 確保 `Catch` 區塊中的程式碼可以將例外狀況正確報告給使用者，不論是透過安全執行緒記錄還是透過適當的訊息。  否則，例外狀況可能仍是未知。  
  
## 用於方法  
 如果您將標記為與 [用於初始化](../../../visual-basic/language-reference/modifiers/async.md) 修飾詞的方法，在方法中使用 [等候](../../../visual-basic/language-reference/operators/await-operator.md) 運算子。  使用 `Await` 運算子的陳述式暫停方法的執行，直到等候工作完成。  表示工作持續進行的工作。  當控制項與 `Await` 運算子時的工作之後，執行在相同方法復原。  如需詳細資訊，請參閱 [非同步程式中的控制流程](../Topic/Control%20Flow%20in%20Async%20Programs%20\(C%23%20and%20Visual%20Basic\).md)。  
  
 用於方法傳回的工作在錯誤狀態可能會結束，指示其已完成因為未處理的例外狀況。  工作已取消的狀態可能也會結束，導致擲回等候運算式之外的 `OperationCanceledException` 。  若要攔截例外狀況的其中一種，可將與 `Try` 封鎖的工作的 `Await` 運算式並攔截例外狀況在 `Catch` 區塊。  範例會在本主題稍後會提供。  
  
 因為多個例外狀況指派給它，並查看管理工作可以在錯誤狀態。  例如，工作可能為呼叫的結果指派給 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>。  當您正在等候這些工作時，會攔截的例外狀況只能有一個例外狀況，因此，您無法預測哪個例外狀況會攔截它。  範例會在本主題稍後會提供。  
  
 `Await` 運算式不可以在 `Catch` 區塊或 `Finally` 區塊內。  
  
## Iterator  
 Iterator 函式或 `Get` 存取子對集合的自訂反覆項目。  Iterator 使用 [yield](../../../visual-basic/language-reference/statements/yield-statement.md) 陳述式會傳回集合中的每個項目一次。  您可以使用 [For Each...Next 陳述式](../../../visual-basic/language-reference/statements/for-each-next-statement.md)Iterator，請呼叫函式。  
  
 `Yield` 陳述式可以是 `Try` 區塊內。  包含 `Yield` 陳述式的 `Try` 區塊有 `Catch` 區塊，而且 `Finally` 區塊。  如需範例 [迭代器](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md) 「請參閱 Visual Basic 的 try 區塊\>一節。  
  
 `Yield` 陳述式不可以在 `Catch` 區塊或 `Finally` 區塊內。  
  
 如果 `For Each` 主體 \(在 Iterator 函式之外\) 擲回例外狀況，在函式的 `Catch` Iterator 區塊，並不會執行，但在 Iterator 函式的 `Finally` 區塊執行。  在 Iterator 的函式中 `Catch` 區塊攔截發生在 Iterator 函式內的例外狀況。  
  
## 部分信任情況  
 在部分信任的情況下，例如裝載在網路共用的應用程式，`Try...Catch...Finally` 不會攔截在叫用包含呼叫的方法前所發生的安全性例外狀況。  當置於伺服器共用並予以執行時，下列範例會產生錯誤："System.Security.SecurityException: Request Failed"。如需安全性例外狀況的詳細資訊，請參閱 <xref:System.Security.SecurityException> 類別。  
  
 [!code-vb[VbVbalrStatements#85](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/try-catch-finally-statem_2.vb)]  
  
 在此種部分信任的情況下，您必須將 `Process.Start` 陳述式放在個別的 `Sub` 中。  對 `Sub` 進行的初始呼叫將會失敗。  這會使得包含 `Process.Start` 的 `Sub` 開始之前，且在產生安全性例外狀況之前，讓 `Try...Catch` 攔截到這項錯誤。  
  
## 範例  
 下列範例說明 `Try...Catch...Finally` 陳述式的結構。  
  
 [!code-vb[VbVbalrStatements#86](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/try-catch-finally-statem_3.vb)]  
  
## 範例  
 在下列範例中，`CreateException` 方法會擲回 `NullReferenceException`。  產生例外狀況的程式碼不在 `Try` 區塊中。  因此 `CreateException` 方法不會處理例外狀況。  由於對 `CreateException` 方法的呼叫是在 `Try` 區塊中進行的，因此`RunSample` 方法不會處理例外狀況。  
  
 範例包含許多例外狀況類型的 `Catch` 陳述式，這些例外狀況依序從最特殊的類型排列到最常見的類型。  
  
 [!code-vb[VbVbalrStatements#91](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/try-catch-finally-statem_4.vb)]  
  
## 範例  
 下列範例示範如何使用 `Catch When` 陳述式來篩選條件運算式。  如果條件運算式評估為 `True`，`Catch` 區塊中的程式碼就會執行。  
  
 [!code-vb[VbVbalrStatements#92](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/try-catch-finally-statem_5.vb)]  
  
## 範例  
 下列範例含有包含在 `Try` 區塊中的 `Try…Catch` 陳述式。  內部 `Catch` 區塊會擲回 `InnerException` 屬性設為原始例外狀況的例外狀況。  外部 `Catch` 區塊會報告本身的例外狀況及內部的例外狀況。  
  
 [!code-vb[VbVbalrStatements#93](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/try-catch-finally-statem_6.vb)]  
  
## 範例  
 下列範例說明例外狀況處理非同步方法的。  若要攔截適用於非同步工作所擲回的例外狀況， `Await` 運算式在呼叫端的 `Try` 區塊，，而且已在 `Catch` 區塊會攔截。  
  
 取消註解說明例外狀況處理的範例中的 `Throw New Exception` 線條。  例外狀況會在 `Catch` 區塊攔截，工作的 `IsFaulted` 屬性設定為， `True`，工作的 `Exception.InnerException` 屬性設為例外狀況。  
  
 取消註解中時會發生何種 `Throw New OperationCancelledException` 線條，當您取消非同步處理序。  例外狀況會在 `Catch` 區塊攔截，，和 `IsCanceled` 屬性設定為 `True`。  在某些情況下，不過這並不適用這個範例， `IsFaulted` 設為 `True` ，並 `IsCanceled` 設為 `False`。  
  
 [!code-vb[csAsyncExceptions#1](../../../csharp/language-reference/keywords/codesnippet/visualbasic/try-catch-finally-statem_7.vb)]  
  
## 範例  
 下列範例說明例外狀況處理多項工作可能會導致多個例外狀況的位置。  `Try` 區塊有 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> 傳回的工作 `Await` 運算式。  工作完成時， <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> 套用時的三項工作已完成。  
  
 三個工作原因中每一個例外狀況。  `Catch` 區塊傳遞例外狀況，逐一查看工作中的 `Exception.InnerExceptions` 屬性中 `Task.WhenAll` 傳回。  
  
 [!code-vb[csAsyncExceptions#3](../../../csharp/language-reference/keywords/codesnippet/visualbasic/try-catch-finally-statem_8.vb)]  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.Information.Err%2A>   
 <xref:System.Exception>   
 [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)   
 [On Error Statement](../../../visual-basic/language-reference/statements/on-error-statement.md)   
 [使用程式碼片段的最佳作法](/visual-studio/ide/best-practices-for-using-code-snippets)   
 [例外狀況處理](../Topic/Exception%20Handling%20\(Task%20Parallel%20Library\).md)   
 [Throw Statement](../../../visual-basic/language-reference/statements/throw-statement.md)