---
title: "陳述式 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# 語言, 陳述式"
  - "陳述式 [C#], 關於陳述式"
ms.assetid: 901bcde7-87de-4e15-833c-f9cfd40c8ce3
caps.latest.revision: 28
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 28
---
# 陳述式 (C# 程式設計手冊)
程式中採用的動作以「陳述式」\(Statement\) 表示。  一般動作包括宣告變數、指派值、呼叫方法、在集合中執行迴圈，以及分支前往一個或另一個程式碼區塊 \(視給定的條件而定\)。  程式中陳述式的執行順序稱為「控制流程」\(Flow Of Control\) 或「執行流程」\(Flow Of Execution\)。  依據程式對其在執行階段收到之輸入的回應而定，每次程式執行時的控制流程可能都不一樣。  
  
 陳述式可以包含結尾為分號的單行程式碼，也可以包含內含一組單行陳述式的區塊。  陳述式區塊以 {} 括弧括住，而且可以包含巢狀區塊。  下列程式碼顯示兩個範例，一個是單行陳述式，一個是單行陳述式區塊：  
  
 [!code-cs[csProgGuideStatements#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_1.cs)]  
  
## 陳述式類別  
 下表列出 C\# 各種陳述式類型及其關聯的關鍵字，以及提供更多資訊的主題連結：  
  
|分類|C\# 關鍵字\/附註|  
|--------|-----------------|  
|宣告陳述式|宣告陳述式 \(Declaration Statement\) 可引進一個新變數或常數。  變數宣告可以選擇要或不要指派值給變數。  常數宣告則一定要進行指派。<br /><br /> [!code-cs[csProgGuideStatements#23](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_2.cs)]|  
|運算陳述式|用於計算值的運算陳述式 \(Expression Statement\)，必須將值儲存在變數中。<br /><br /> [!code-cs[csProgGuideStatements#24](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_3.cs)]|  
|[選擇陳述式](../../../csharp/language-reference/keywords/selection-statements.md)|選擇陳述式 \(Selection Statement\) 可讓您根據一個或多個指定條件，分支前往不同的程式碼區段。  如需詳細資訊，請參閱下列主題：<br /><br /> [if](../../../csharp/language-reference/keywords/if-else.md)、[else](../../../csharp/language-reference/keywords/if-else.md)、[switch](../../../csharp/language-reference/keywords/switch.md)、[case](../../../csharp/language-reference/keywords/switch.md)|  
|[反覆運算陳述式](../../../csharp/language-reference/keywords/iteration-statements.md)|反覆運算陳述式可讓您在集合 \(例如陣列\) 中執行迴圈，或重複執行相同的一組陳述式，直到符合指定的條件為止。  如需詳細資訊，請參閱下列主題：<br /><br /> [do](../../../csharp/language-reference/keywords/do.md)、[for](../../../csharp/language-reference/keywords/for.md)、[foreach](../../../csharp/language-reference/keywords/foreach-in.md)、[in](../../../csharp/language-reference/keywords/foreach-in.md)、[while](../../../csharp/language-reference/keywords/while.md)|  
|[跳躍陳述式](../../../csharp/language-reference/keywords/jump-statements.md)|跳躍陳述式 \(Jump Statement\) 可將控制轉移到另一個程式碼區段。  如需詳細資訊，請參閱下列主題：<br /><br /> [break](../../../csharp/language-reference/keywords/break.md)、[continue](../../../csharp/language-reference/keywords/continue.md)、[default](../../../csharp/language-reference/keywords/switch.md)、[goto](../../../csharp/language-reference/keywords/goto.md)、[return](../../../csharp/language-reference/keywords/return.md)、[yield](../../../csharp/language-reference/keywords/yield.md)|  
|[例外狀況處理陳述式](../../../csharp/language-reference/keywords/exception-handling-statements.md)|例外狀況處理 \(Exception Handling\) 陳述式可讓您順利地從執行階段發生的例外情況復原。  如需詳細資訊，請參閱下列主題：<br /><br /> [throw](../../../csharp/language-reference/keywords/throw.md)、[try\-catch](../../../csharp/language-reference/keywords/try-catch.md)、[try\-finally](../../../csharp/language-reference/keywords/try-finally.md)、[try\-catch\-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)|  
|[Checked 和 Unchecked](../../../csharp/language-reference/keywords/checked-and-unchecked.md)|Checked 和 Unchecked 陳述式可讓您指定當數值運算用來儲存結果的變數因為太小而無法保存結果值時，是否允許數值運算溢位。  如需詳細資訊，請參閱 [checked \(C\# 參考\)](../../../csharp/language-reference/keywords/checked.md) 和 [unchecked \(C\# 參考\)](../../../csharp/language-reference/keywords/unchecked.md)。|  
|`await` 陳述式|如果您將標記為已與 [非同步](../../../csharp/language-reference/keywords/async.md) 修飾詞的方法，您可以使用方法在 [等候](../../../csharp/language-reference/keywords/await.md) 運算子。  當控制項到達非同步方法的一個 `await` 表示，控制項傳回至呼叫端，因此，在方法的進度暫止，直到等候的工作完成。  當工作完成時，則會從方法可以復原。<br /><br /> 如需簡單範例，請參閱 [方法](../../../csharp/programming-guide/classes-and-structs/methods.md)「Async 方法\>一節。  如需詳細資訊，請參閱[使用 Async 和 Await 設計非同步程式](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md)。|  
|`yield return` 陳述式|Iterator 對集合的自訂反覆運算，例如清單或陣列。  Iterator 使用 [yield return](../../../csharp/language-reference/keywords/yield.md) 陳述式傳回每個項目一次一個。  當 `yield return` 陳述式到達，目前位置在程式碼中的事項。  當 Iterator，下次呼叫時，執行與該位置重新開始。<br /><br /> 如需詳細資訊，請參閱[迭代器](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md)。|  
|`fixed` 陳述式|fixed 陳述式可讓記憶體回收行程避免重新配置可移動的變數。  如需詳細資訊，請參閱 [fixed 陳述式 \(C\# 參考\)](../../../csharp/language-reference/keywords/fixed-statement.md)。|  
|`lock` 陳述式|lock 陳述式可讓您將程式碼區塊的存取限制為一次僅限一個執行緒。  如需詳細資訊，請參閱 [lock 陳述式 \(C\# 參考\)](../../../csharp/language-reference/keywords/lock-statement.md)。|  
|標記陳述式|您可以提供標記給陳述式，然後使用 [goto \(C\# 參考\)](../../../csharp/language-reference/keywords/goto.md) 關鍵字跳至標記陳述式 \(Label Statement\)   \(請參閱下一列的範例\)。|  
|空白陳述式|空白陳述式只包含一個分號，  不會執行任何動作，可以用在需有陳述式但不需要執行動作的地方。  下列範例顯示空白陳述式的兩種用法：<br /><br /> [!code-cs[csProgGuideStatements#25](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_4.cs)]|  
  
## 內嵌陳述式  
 有些陳述式 \(包括 [do](../../../csharp/language-reference/keywords/do.md)、[while](../../../csharp/language-reference/keywords/while.md)、[for](../../../csharp/language-reference/keywords/for.md) 和 [foreach](../../../csharp/language-reference/keywords/foreach-in.md)\) 其後總會跟著內嵌陳述式。  這種內嵌陳述式可以是單一陳述式，也可以是以 {} 括弧括住內含多行陳述式的陳述式區塊。  單行內嵌陳述式也可以用 {} 括弧括住，如下列範例所示：  
  
 [!code-cs[csProgGuideStatements#26](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_5.cs)]  
  
 未以 {} 括弧括住的內嵌陳述式不能為宣告或標記陳述式。  這會在下列範例中示範：  
  
 [!code-cs[csProgGuideStatements#27](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_6.cs)]  
  
 將內嵌陳述式置入區塊，修正錯誤：  
  
 [!code-cs[csProgGuideStatements#28](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_7.cs)]  
  
## 巢狀陳述式區塊  
 陳述式區塊也可以形成巢狀，如下列程式碼所示：  
  
 [!code-cs[csProgGuideStatements#29](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_8.cs)]  
  
## 不可能執行到的陳述式  
 如果編譯器 \(Compiler\) 判斷控制流程在任何情況下都不可能執行到某個特定陳述式，就會產生警告 CS0162，如下列範例所示：  
  
 [!code-cs[csProgGuideStatements#22](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_9.cs)]  
  
## 相關章節  
  
-   [陳述式關鍵字](../../../csharp/language-reference/keywords/statement-keywords.md)  
  
-   [運算式](../../../csharp/programming-guide/statements-expressions-operators/expressions.md)  
  
-   [運算子](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)