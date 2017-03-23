---
title: "for (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "for"
  - "for_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "for 關鍵字 [C#]"
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
caps.latest.revision: 39
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 39
---
# for (C# 參考)
使用 `for` 迴圈中，您可以重複執行陳述式或陳述式區塊，直到指定的運算式評估為 `false`。  這個迴圈是用來逐一查看陣列以及您事先知道的其他應用程式多少次要迴圈會逐一查看。  
  
## 範例  
 在下列範例中， `i` 的值寫入主控台 \(Console\) 和方法會將此屬性加入在每次反覆運算時。  
  
 [!code-cs[csrefKeywordsIteration#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_1.cs)]  
  
 在上述範例中的 `for` 陳述式會執行下列動作。  
  
1.  首先，變數 `i` 的初始值建立。  這個步驟中只出現一次，不論次數重複迴圈。  您可以將這個初始化為發生的外部迴圈的流程。  
  
2.  要評估這個情況 \(`i <= 5`\)， `i` 的值與的 . 比較。  
  
    -   如果 `i` 小於或等於引數，這個條件評估為 `true`，此外，也會發生下列動作。  
  
        1.  在迴圈主體的 `Console.WriteLine` 陳述式顯示 `i`的值。  
  
        2.  `i` 的值長達 . 加入。  
  
        3.  迴圈回到開始 2D 步驟重新評估條件。  
  
    -   如果 `i` 比五大，條件評估為， `false`，而且您結束迴圈。  
  
 請注意，則為，否則 `i` 的初始值比五大，迴圈的主體甚至一次不會執行。  
  
 每 `for` 陳述式定義初始設定式、條件和 Iterator 部分。  這些部分通常會判斷有多少個迴圈會逐一查看。  
  
```c#  
for (initializer; condition; iterator)  
    body  
```  
  
 下列章節提供用途。  
  
-   初始設定式部分設定初始條件。  在只執行一次的這個部分的陳述式，，在進入迴圈之前。  這個章節只可以包含下列兩個選項。  
  
    -   本機路徑環境變數的宣告和初始化，做為第一個範例顯示 \(`int i = 1`\)。  變數是在本機迴圈，無法從迴圈外存取。  
  
    -   請從下列清單中的零個或多個陳述式 expressons，以逗號分隔。  
  
        -   [指派](../../../csharp/language-reference/operators/assignment-operator.md) 陳述式  
  
        -   方法的引動過程  
  
        -   重新命名或後置 [加入](../../../csharp/language-reference/operators/increment-operator.md) 運算式前置字元，例如 `++i` 或 `i++`  
  
        -   重新命名或後置 [遞減](../../../csharp/language-reference/operators/decrement-operator.md) 運算式前置字元，例如 `--i` 或 `i--`  
  
        -   物件的建立使用 [新](../../../csharp/language-reference/keywords/new-operator.md)的  
  
        -   表示[等候](../../../csharp/language-reference/keywords/await.md)  
  
-   條件部分包含評估判斷的一個布林運算式迴圈是否應該結束或應該再次執行。  
  
-   Iterator 部分定義要在迴圈主體的每次反覆運算後發生。  Iterator 部分包含零或多個下列陳述式表示，以逗號分隔:  
  
    -   [指派](../../../csharp/language-reference/operators/assignment-operator.md) 陳述式  
  
    -   方法的引動過程  
  
    -   重新命名或後置 [加入](../../../csharp/language-reference/operators/increment-operator.md) 運算式前置字元，例如 `++i` 或 `i++`  
  
    -   重新命名或後置 [遞減](../../../csharp/language-reference/operators/decrement-operator.md) 運算式前置字元，例如 `--i` 或 `i--`  
  
    -   物件的建立使用 [新](../../../csharp/language-reference/keywords/new-operator.md)的  
  
    -   表示[等候](../../../csharp/language-reference/keywords/await.md)  
  
-   迴圈的主體包含陳述式，則會傳回空的陳述式或陳述式區塊，可以放在括號的零或多個陳述式建立。  
  
     使用 [中斷](../../../csharp/language-reference/keywords/break.md) 關鍵字，您可以產生 `for` 迴圈，使用 [繼續](../../../csharp/language-reference/keywords/continue.md) 關鍵字，或者您可以逐步執行至下一個反覆運算。  使用 [定位](../../../csharp/language-reference/keywords/goto.md)、或 [擲回。](../../../csharp/language-reference/keywords/throw.md)[return](../../../csharp/language-reference/keywords/return.md)陳述式，您也可以關閉所有迴圈。  
  
 本主題中的第一個範例顯示最常見的 `for` 迴圈，做出部分的下列選項。  
  
-   初始設定式宣告並初始化本機路徑環境變數， `i`，維護迴圈的反覆項目計數。  
  
-   狀態檢查迴圈變數的值對已知的最終值，如同 . 的。  
  
-   Iterator 部分使用後置遞增陳述式， `i++`相符，迴圈的每個反覆項目。  
  
 下列範例說明數個較不常見的選項:指派值給初始設定式部分的外部迴圈變數，叫用初始設定式和 Iterator 部分的 `Console.WriteLine` 方法和變更兩個變數的值在 Iterator 的部分。  
  
 [!code-cs[csrefKeywordsIteration#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_2.cs)]  
  
 定義 `for` 陳述式的所有運算式都是選擇性的。  例如，下列陳述式建立無限迴圈。  
  
 [!code-cs[csrefKeywordsIteration#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_3.cs)]  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [foreach、in](../../../csharp/language-reference/keywords/foreach-in.md)   
 [for 陳述式 \(C\+\+\)](/visual-cpp/cpp/for-statement-cpp)   
 [反覆運算陳述式](../../../csharp/language-reference/keywords/iteration-statements.md)