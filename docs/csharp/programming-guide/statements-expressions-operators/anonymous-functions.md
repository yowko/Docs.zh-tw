---
title: "匿名函式 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "匿名函式 [C#]"
  - "匿名方法 [C#]"
  - "Lambda 運算式 [C#], 當做匿名函式"
ms.assetid: 6ce3f04d-0c71-4728-9127-634c7e9a8365
caps.latest.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 14
---
# 匿名函式 (C# 程式設計手冊)
匿名函式是指可以在任何需要委派型別 \(Delegate Type\) 的位置上使用的「內嵌」\(Inline\) 陳述式 \(Statement\) 或運算式。  您可以用這種函式來初始化具名的委派，或是用它取代具名委派型別來傳遞做為方法參數。  
  
 匿名函式可分為兩種，我們將在下列主題中個別加以討論：  
  
-   [Lambda 運算式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
-   [匿名方法](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
  
    > [!NOTE]
    >  Lambda 運算式可以繫結至運算式樹狀架構，也可以繫結至委派。  
  
## C\# 中的委派演進  
 過去在 C\# 1.0 中，建立委派之執行個體的步驟，是使用已定義於程式碼內其他位置的方法來明確初始化該委派。  到了 C\# 2.0，則引進以匿名方法來撰寫未命名內嵌陳述式區塊的概念，當時，該類區塊會透過委派引動過程來執行。  C\# 3.0 引進了 Lambda 運算式，這種運算式與匿名方法的概念相似，但其表示功能更為強大，而且也更簡潔。  這兩種功能合稱為「*匿名函式*」\(Anonymous Function\)。  一般而言，以 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 3.5 版 \(含\) 以後版本做為目標的應用程式，都應該使用 Lambda 運算式。  
  
 下列範例會示範從 C\# 1.0 到 C\# 3.0 的委派建立演進過程：  
  
 [!code-cs[csProgGuideLINQ#65](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csRef30LangFeatures_2.cs#65)]  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [陳述式、運算式和運算子](../../../csharp/programming-guide/statements-expressions-operators/index.md)   
 [Lambda 運算式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)   
 [委派](../../../csharp/programming-guide/delegates/index.md)   
 [運算式樹狀架構](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md)