---
title: "new 運算子 (C# 參考) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "new 運算子關鍵字 [C#]"
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
caps.latest.revision: 22
caps.handback.revision: 22
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# new 運算子 (C# 參考)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

用來建立物件並叫用 \(Invoke\) 建構函式。  例如：  
  
```  
Class1 obj  = new Class1();  
```  
  
 它也可以用來建立匿名型別的執行個體 \(Instance\)：  
  
```  
var query = from cust in customers  
            select new {Name = cust.Name, Address = cust.PrimaryAddress};  
```  
  
 `new` 運算子也可用來叫用實值型別 \(Value Type\) 的預設建構函式。  例如：  
  
```  
int i = new int();  
```  
  
 在前面的陳述式中，`i` 會被初始化為 `0`，這是 `int` 型別的預設值。  此陳述式的效果等同於：  
  
```  
int i = 0;  
```  
  
 如需預設值的完整清單，請參閱[預設值表](../../../csharp/language-reference/keywords/default-values-table.md)。  
  
 請記住，為 [struct](../../../csharp/language-reference/keywords/struct.md) 宣告預設建構函式會發生錯誤，因為每一個實值型別都有隱含的公用預設建構函式。  可以在結構型別上宣告參數化的建構函式以設定其初始值，但只有在需要預設值以外的其他值時，才必須這麼做。  
  
 像結構這樣的實值型別物件是建立於堆疊上，而像類別這樣的參考型別則是建立在堆積上。  兩種物件型別都會自動終結，但是依據實值型別的物件會在超出範圍時終結，而依據參考型別的物件則會在移除最後一個參考之後終結。  對於消耗固定資源 \(例如，大量記憶體、檔案控制代碼或網路連線\) 的參考型別，有時最好採用決定性的最終化，以確保儘速終結物件。  如需詳細資訊，請參閱 [Using 陳述式](../../../csharp/language-reference/keywords/using-statement.md)。  
  
 `new` 運算子無法多載。  
  
 如果 `new` 運算子無法配置記憶體，就會擲出例外狀況 <xref:System.OutOfMemoryException>。  
  
## 範例  
 在下列範例中，`struct` 物件與類別物件都是使用 `new` 運算子來建立與初始化，並隨後指派值。  預設值與指派的值都會顯示出來。  
  
 [!code-cs[csrefKeywordsOperator#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-operator_1.cs)]  
  
 請注意範例裡字串的預設值為 `null`。  因此，並未顯示此值。  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 請參閱  
 [C\# 參考](../../../visual-basic/reference/command-line-compiler/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [運算子關鍵字](../../../csharp/language-reference/keywords/operator-keywords.md)   
 [new](../../../csharp/language-reference/keywords/new.md)   
 [匿名類型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)