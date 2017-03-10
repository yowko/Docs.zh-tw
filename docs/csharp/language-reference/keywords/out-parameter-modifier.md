---
title: "out 參數修飾詞 (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "out 參數 [C#]"
  - "參數 [C#], out"
ms.assetid: 3fce0dc5-03f4-4faa-bd61-36c41bc6baf1
caps.latest.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 9
---
# out 參數修飾詞 (C# 參考)
`out` 關鍵字會導致以傳址 \(By Reference\) 方式傳遞引數。  這點與 [ref](../../../csharp/language-reference/keywords/ref.md) 關鍵字相似，除了 `ref` 需要在傳遞參數之前先初始化變數以外。  若要使用 `out` 參數，方法定義和呼叫方法都必須明確使用 `out` 關鍵字。  例如：  
  
 [!code-cs[csrefKeywordsMethodParams#1](../../../csharp/language-reference/keywords/codesnippet/csharp/out-parameter-modifier_1.cs)]  
  
 雖然當做 `out` 引數傳遞的變數不需要在傳遞之前先初始化，但需要在方法傳回之前呼叫方法以指派值。  
  
 雖然 `ref` 與 `out` 關鍵字會產生不同的執行階段行為，但是在編譯期間它們並不被視為方法簽章的一部分。  因此，如果唯一的差別在於其中一個方法使用 `ref` 引數，而另一個方法使用 `out` 引數，則不能多載方法。  例如，下列程式碼將無法編譯：  
  
 [!code-cs[csrefKeywordsMethodParams#2](../../../csharp/language-reference/keywords/codesnippet/csharp/out-parameter-modifier_2.cs)]  
  
 然而，若其中一個方法使用 `ref` 或 `out` 引數，另一個方法不使用任何引數，就可以完成多載，如下所示：  
  
 [!code-cs[csrefKeywordsMethodParams#3](../../../csharp/language-reference/keywords/codesnippet/csharp/out-parameter-modifier_3.cs)]  
  
 屬性並非變數，所以不能當做 `out` 參數傳遞。  
  
 如需傳遞陣列的詳細資訊，請參閱[使用 ref 和 out 傳遞陣列](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)。  
  
 您無法使用下列幾種方法使用 `ref` 和 `out` 關鍵字:  
  
-   用於初始化方法，或是使用 [非同步](../../../csharp/language-reference/keywords/async.md) 修飾詞，請定義。  
  
-   Iterator方法，其中包括一 [的yield return](../../../csharp/language-reference/keywords/yield.md) 或 `yield break` 陳述式。  
  
## 範例  
 當您想讓一個方法傳回多個值時，宣告 `out` 方法十分有用。  下列範例使用 `out` 以單一呼叫方法傳回三個變數。  請注意，第三個引數是指派為 null。  這樣可讓方法能夠選擇性地傳回值。  
  
 [!code-cs[csrefKeywordsMethodParams#4](../../../csharp/language-reference/keywords/codesnippet/csharp/out-parameter-modifier_4.cs)]  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [方法參數](../../../csharp/language-reference/keywords/method-parameters.md)