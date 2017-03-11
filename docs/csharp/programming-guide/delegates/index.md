---
title: "委派 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# 語言, 委派"
  - "委派 [C#]"
ms.assetid: 97de039b-c76b-4b9c-a27d-8c1e1c8d93da
caps.latest.revision: 30
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 30
---
# 委派 (C# 程式設計手冊)
[委派](../../../csharp/language-reference/keywords/delegate.md)是一種類型，代表具有特定參數清單和傳回類型的方法參考。  當您具現化委派時，可以將其執行個體與任何具有相容簽章和傳回類型的方法產生關聯。  您可以透過委派執行個體叫用 \(或呼叫\) 方法。  
  
 委派可以用來將方法當做引數傳遞給其他方法。  事件處理常式就是透過委派叫用的方法。  建立自訂方法後，像是 Windows 控制項這樣的類別就會在特定事件發生時呼叫您的方法。  下列範例將示範委派宣告：  
  
 [!code-cs[csProgGuideDelegates#20](../../../csharp/programming-guide/delegates/codesnippet/csharp/csrefDelegates/Delegates.cs#20)]  
  
 來自符合委派類型之任何可存取類別或結構的任何方法都可以指派給委派。  方法可以是靜態或執行個體方法。  如此即可用程式設計的方式變更方法呼叫，也可將新的程式碼插入現有的類別中。  
  
> [!NOTE]
>  在方法多載的內容中，方法的簽章並不包括傳回值。  不過在委派的內容中，簽章卻包含傳回值。  換句話說，方法必須與委派擁有相同的傳回類型。  
  
 由於委派能夠將方法當做參數來參考，因此很適合用來定義回呼方法。  例如，可以將比較兩個物件的方法參考當成引數傳遞至排序演算法。  因為比較程式碼是在獨立的程序中，因此排序演算法可以用較普通的方式撰寫。  
  
## 委派概觀  
 委派包含下列屬性：  
  
-   委派與 C\+\+ 函式指標類似，但為類型安全。  
  
-   委派允許將方法當做參數傳遞。  
  
-   委派可用於定義回呼方法。  
  
-   您可將委派鏈結在一起，例如，可在單一事件上呼叫多個方法。  
  
-   方法不需要完全符合委派類型。  如需詳細資訊，請參閱[在委派中使用變異數](../Topic/Using%20Variance%20in%20Delegates%20\(C%23%20and%20Visual%20Basic\).md)。  
  
-   C\# 2.0 版引進了[匿名方法](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)的概念，能夠將程式碼區塊當做參數傳遞，以取代個別定義的方法。  C\# 3.0 引進了 Lambda 運算式，做為更簡潔的內嵌 \(Inline\) 程式碼區塊撰寫方式。  匿名方法與 Lambda 運算式 \(在特定內容中\) 都會編譯為委派類型。  現在，這些功能合稱為「匿名函式」\(Anonymous Function\)。  如需 Lambda 運算式的詳細資訊，請參閱 [匿名函式](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)。  
  
## 本章節內容  
  
-   [使用委派](../../../csharp/programming-guide/delegates/using-delegates.md)  
  
-   [When to Use Delegates Instead of Interfaces \(C\# Programming Guide\)](http://msdn.microsoft.com/zh-tw/2e759bdf-7ca4-4005-8597-af92edf6d8f0)  
  
-   [使用具名和匿名方法委派的比較](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)  
  
-   [匿名方法](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
  
-   [在委派中使用變異數](../Topic/Using%20Variance%20in%20Delegates%20\(C%23%20and%20Visual%20Basic\).md)  
  
-   [如何：組合委派 \(多點傳送委派\)](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)  
  
-   [如何：宣告、產生和使用委派](../../../csharp/programming-guide/delegates/how-to-declare-instantiate-and-use-a-delegate.md)  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 精選書籍章節  
 [C\# 3.0 Cookbook, Third Edition: More than 250 solutions for C\# 3.0 programmers](http://go.microsoft.com/fwlink/?LinkId=195369) 中的[Delegates, Events, and Lambda Expressions](http://go.microsoft.com/fwlink/?LinkId=195395)  
  
 [Learning C\# 3.0: Master the fundamentals of C\# 3.0](http://go.microsoft.com/fwlink/?LinkId=195412) 中的[Delegates and Events](http://go.microsoft.com/fwlink/?LinkId=195418)  
  
## 請參閱  
 <xref:System.Delegate>   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [事件](../../../csharp/programming-guide/events/index.md)