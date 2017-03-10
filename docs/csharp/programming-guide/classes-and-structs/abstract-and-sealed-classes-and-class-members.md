---
title: "抽象和密封類別以及類別成員 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "抽象類別 [C#]"
  - "密封類別 [C#]"
  - "C# 語言，抽象類別"
  - "C# 語言，密封"
ms.assetid: 99aa52f7-b435-43f9-936e-2470af734c4e
caps.latest.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 14
---
# 抽象和密封類別以及類別成員 (C# 程式設計手冊)
[abstract](../../../csharp/language-reference/keywords/abstract.md) 關鍵字可讓您建立類別和[類別](../../../csharp/language-reference/keywords/class.md)成員，這些類別和成員並不完整，因此必須在衍生類別中實作。  
  
 [sealed](../../../csharp/language-reference/keywords/sealed.md) 關鍵字可讓您避免繼承類別，或是先前標記為 [virtual](../../../csharp/language-reference/keywords/virtual.md) 的特定類別成員。  
  
## 抽象類別和類別成員  
 在類別定義前面加入 `abstract` 關鍵字，就可以將類別宣告為抽象。  例如：  
  
 [!code-cs[csProgGuideInheritance#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/abstract-and-sealed-clas_1.cs)]  
  
 抽象類別無法具現化。  抽象類別的用途是提供基底類別的通用定義，可供多個衍生類別共用。  例如，類別庫會定義做為其多個函式的參數使用的抽象類別，並且要求使用該類別庫的程式設計人員建立衍生類別來提供自己的類別實作。  
  
 抽象類別也可以定義抽象方法。  只要在方法的傳回類型前面加上關鍵字 `abstract`，就可以達到這個目的。  例如：  
  
 [!code-cs[csProgGuideInheritance#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/abstract-and-sealed-clas_2.cs)]  
  
 抽象方法沒有任何實作，因此方法定義後面會接著一個分號，而不是一般方法區塊。  抽象類別的衍生類別必須實作所有抽象方法。  當抽象類別從基底類別繼承虛擬方法時，抽象類別可以使用抽象方法覆寫虛擬方法。  例如：  
  
 [!code-cs[csProgGuideInheritance#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/abstract-and-sealed-clas_3.cs)]  
  
 如果 `virtual` 方法宣告為 `abstract`，則該方法對於繼承自抽象類別的任何類別來說仍為虛擬。  繼承抽象方法的類別無法存取方法的原始實作，在前面的範例中，F 類別上的 `DoWork` 無法呼叫 D 類別上的 `DoWork`。  如此一來，抽象類別就能強制衍生類別為虛擬方法提供新的方法實作。  
  
## 密封類別和類別成員  
 在類別定義前面加入 `sealed` 關鍵字，就可以將類別宣告為 [sealed](../../../csharp/language-reference/keywords/sealed.md)。  例如：  
  
 [!code-cs[csProgGuideInheritance#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/abstract-and-sealed-clas_4.cs)]  
  
 密封類別不能當做基底類別使用。  基於這個理由，該類別也不能是抽象類別。  密封類別可以避免衍生。  由於密封類別永遠不能當做基底類別使用，因此某些執行階段最佳化呼叫密封類別成員的速度就能夠稍為加快。  
  
 若方法、索引子、屬性或事件位於覆寫基底類別之虛擬成員的衍生類別上，就可以將該成員宣告為密封。  這樣一來，後續任何衍生類別的成員都不再擁有虛擬部分。  只要在類別成員宣告中的 [override](../../../csharp/language-reference/keywords/override.md) 關鍵字前面放置 `sealed` 關鍵字，就可以達到這個目的。  例如：  
  
 [!code-cs[csProgGuideInheritance#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/abstract-and-sealed-clas_5.cs)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [類別和結構](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [繼承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)   
 [方法](../../../csharp/programming-guide/classes-and-structs/methods.md)   
 [欄位](../../../csharp/programming-guide/classes-and-structs/fields.md)   
 [如何：定義抽象屬性](../../../csharp/programming-guide/classes-and-structs/how-to-define-abstract-properties.md)