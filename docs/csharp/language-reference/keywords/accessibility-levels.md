---
title: "存取範圍層級 (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "存取修飾詞 [C#], 存取範圍層次"
  - "存取範圍層次"
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# 存取範圍層級 (C# 參考)
請使用存取修飾詞 \(Modifier\) [public](../../../csharp/language-reference/keywords/public.md)、[protected](../../../csharp/language-reference/keywords/protected.md)、[internal](../../../csharp/language-reference/keywords/internal.md), 或 [private](../../../csharp/language-reference/keywords/private.md)，為成員指定下列其中一個宣告存取範圍層級。  
  
|宣告存取範圍|意義|  
|------------|--------|  
|`public`|存取沒有限制。|  
|`protected`|存取只限於包含的類別或衍生自包含類別的型別。|  
|`internal`|存取只限於目前的組件。|  
|`protected` `internal`|存取只限於目前的組件或衍生自包含類別的型別|  
|`private`|存取只限於包含類別。|  
  
 除了使用 `protected` `internal` 組合的情況，成員或型別都只允許一個存取修飾詞。  
  
 存取修飾詞不能用於命名空間。  因此命名空間沒有存取限制。  
  
 根據發生成員宣告所在的內容，只會允許某些宣告存取範圍。  如果成員宣告裡沒有指定存取修飾詞，使用預設存取範圍。  
  
 最上層型別 \(沒有巢狀於其他型別裡\) 都只能有 `internal` 或 `public` 存取範圍。  這些型別的預設存取範圍是 `internal`。  
  
 巢狀型別，也就是包含在其他型別中的成員，可以有下表所示的宣告存取範圍。  
  
|成員所屬型別|成員預設存取範圍|成員允許的宣告存取範圍|  
|------------|--------------|-----------------|  
|`enum`|`public`|None|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected` `internal`|  
|`interface`|`public`|None|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 巢狀型別的存取範圍是依據其[存取範圍定義域](../../../csharp/language-reference/keywords/accessibility-domain.md)，由成員的宣告存取範圍和立即包含型別的存取範圍定義域來決定。  但是，巢狀型別的存取範圍領域不能超過包含型別 \(Containing Type\) 的存取範圍領域。  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [存取修飾詞](../../../csharp/language-reference/keywords/access-modifiers.md)   
 [存取範圍定義域](../../../csharp/language-reference/keywords/accessibility-domain.md)   
 [使用存取層級的限制](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)   
 [存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)   
 [public](../../../csharp/language-reference/keywords/public.md)   
 [private](../../../csharp/language-reference/keywords/private.md)   
 [protected](../../../csharp/language-reference/keywords/protected.md)   
 [internal](../../../csharp/language-reference/keywords/internal.md)