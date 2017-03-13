---
title: "存取範圍定義域 (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "存取範圍定義域 [C#]"
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
caps.latest.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 17
---
# 存取範圍定義域 (C# 參考)
成員的存取範圍定義域會指定可參考成員的程式區段。  如果成員在其他型別內成巢狀，其存取範圍定義域是由成員的[存取範圍層級](../../../csharp/language-reference/keywords/accessibility-levels.md)和立即包含型別的存取範圍定義域來決定。  
  
 最上層型別的存取範圍定義域至少包含其宣告之專案的程式內容。  也就是網域包含這個專案所有的原始程式檔。  巢狀型別的存取範圍定義域至少包含其宣告之型別的程式內容。  也就是說，定義域是型別主體，其中包括所有的巢狀型別。  巢狀型別的存取範圍定義域不會超過包含型別的存取範圍定義域。  這些概念會在下列範例裡示範。  
  
## 範例  
 這個範例包含最上層型別，`T1`，和兩個巢狀類別，`M1` 和 `M2`。  這些類別包含具有不同宣告存取範圍的欄位。  `Main` 方法裡，每一個陳述式後會有註解指出每一個成員的存取範圍定義域。  請注意，嘗試參考無法存取之成員的陳述式都會標記為註解。  如果您要查看由參考無法存取之成員所造成的編譯器錯誤，請一次移除一個註解。  
  
 [!code-cs[csrefKeywordsModifiers#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/accessibility-domain_1.cs)]  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [存取修飾詞](../../../csharp/language-reference/keywords/access-modifiers.md)   
 [存取層級](../../../csharp/language-reference/keywords/accessibility-levels.md)   
 [使用存取層級的限制](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)   
 [存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)   
 [public](../../../csharp/language-reference/keywords/public.md)   
 [private](../../../csharp/language-reference/keywords/private.md)   
 [protected](../../../csharp/language-reference/keywords/protected.md)   
 [internal](../../../csharp/language-reference/keywords/internal.md)