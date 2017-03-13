---
title: "switch (C# 參考) | Microsoft Docs"
ms.date: "2017-03-07"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "switch_CSharpKeyword"
  - "switch"
  - "case"
  - "case_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "switch 陳述式 [C#]"
  - "switch 關鍵字 [C#]"
  - "case 陳述式 [C#]"
  - "default 關鍵字 [C#]"
ms.assetid: 44bae8b8-8841-4d85-826b-8a94277daecb
caps.latest.revision: 47
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 47
---
# switch (C# 參考)
`switch` 陳述式是控制項陳述式，該陳述式會從候選項清單中選取要執行的「*參數區段*」\(Switch Section\)。  
  
 `switch` 陳述式包含一個或多個參數區段。  每個參數區段都包含一個或多個「*case 標籤*」\(Case Label\)，後面接著一個或多個陳述式。  下列範例將示範擁有三個參數區段的簡單 `switch` 陳述式。  每個參數區段擁有一個 case 標籤，例如 `case 1`，以及兩個陳述式。  
  
 [!code-cs[csrefKeywordsSelection#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/switch_1.cs)]  
  
## 備註  
 每個 case 標籤都會指定一個常數值。  Switch 陳述式會將控制項傳輸至 case 標籤符合「*switch 運算式*」\(Switch Expression\) 之值的參數區段 \(範例中為 `caseSwitch`\)。  如果沒有任何 case 標籤包含相符的值，則控制項會傳輸至 `default` 區段 \(如果有的話\)。  如果沒有 `default` 區段，則不會採取任何動作，而且控制項會在 `switch` 陳述式之外傳輸。  在上面的範例中，因為 `case 1` 符合 `caseSwitch` 的值，所以第一個參數區段中的陳述式會執行。  
  
 `switch` 陳述式可包含任意數目的參數區段，而每個區段都可以擁有一個或多個 case 標籤 \(如下面的字串 case 標籤範例中所示\)。  但是，不可以有兩個 case 標籤包含相同的常數值。  
  
 在選取的參數區段中，陳述式清單是從第一個陳述式開始執行，然後繼續進行整份陳述式清單，通常會進行直到跳躍陳述式為止，例如到達 `break`、`goto case`、`return` 或 `throw`。  到達該點時，控制項會在 `switch` 陳述式之外傳輸，或傳輸至另一個 case 標籤。  
  
 與 C\+\+ 不同的是，C\# 不允許從某個參數區段繼續執行至另一個參數區段。  下列程式碼會產生錯誤。  
  
```c#  
switch (caseSwitch)  
{  
    // The following switch section causes an error.  
    case 1:  
        Console.WriteLine("Case 1...");  
        // Add a break or other jump statement here.  
    case 2:  
        Console.WriteLine("... and/or Case 2");  
        break;  
}  
```  
  
 C\# 需要有無法到達的參數區段結尾，包括最後一個。也就是說，與部分其他語言不同的是，您的程式碼無法繼續到下一個參數區段。雖然這項需求通常可使用 `break` 陳述式達成，但是後續 case 仍有效，因為它可確保無法到達陳述式清單的結尾。  
  
```c#  
case 4:  
    while (true)  
        Console.WriteLine("Endless looping. . . .");  
```  
  
## 範例  
 下列範例將說明 `switch` 陳述式的需求和功能。  
  
 [!code-cs[csrefKeywordsSelection#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/switch_2.cs)]  
  
## 範例  
 在最後一個範例中，字串變數、`str` 及字串 case 標籤負責控制執行流程。  
  
 [!code-cs[csrefKeywordsSelection#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/switch_3.cs)]  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [switch 陳述式 \(C\+\+\)](/visual-cpp/cpp/switch-statement-cpp)   
 [if\-else](../../../csharp/language-reference/keywords/if-else.md)