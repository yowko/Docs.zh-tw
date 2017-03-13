---
title: "泛型程式碼中的預設關鍵字 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "default 關鍵字 [C#], 泛型程式設計"
  - "泛型 [C#], 預設 關鍵字"
ms.assetid: b9daf449-4e64-496e-8592-6ed2c8875a98
caps.latest.revision: 22
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 22
---
# 泛型程式碼中的預設關鍵字 (C# 程式設計手冊)
在泛型類別和方法中會發生一個問題，也就是當您無法預先知道下列資訊時，如何將預設值指派給參數化型別 T：  
  
-   T 是參考型別或實值型別  
  
-   如果 T 是實值型別，則會是數字值或結構  
  
 當指定參數化型別 T 的變數 t 時，只有在 T 是參考型別時，陳述式 t \= null 才有效，並且 t \= 0 只有對數值型別 \(而不是結構\) 有效。  解決方法是使用 `default` 關鍵字，對參考型別傳回 null 而對數值型別傳回零。  這種方法會根據結構是實值或參考型別，為結構傳回初始化成零或 null 的每個結構成員。  對於可為 Null 的實質型別，預設值會傳回 <xref:System.Nullable%601?displayProperty=fullName>，該值會與任一結構一樣經過初始化。  
  
 下列 `GenericList<T>` 類別的程式碼範例示範如何使用 `default` 關鍵字。  如需詳細資訊，請參閱[泛型概觀](../../../csharp/programming-guide/generics/introduction-to-generics.md)。  
  
 [!code-cs[csProgGuideGenerics#41](../../../csharp/programming-guide/generics/codesnippet/CSharp/default-keyword-in-generic-code_1.cs)]  
  
## 請參閱  
 <xref:System.Collections.Generic>   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [泛型](../../../csharp/programming-guide/generics/index.md)   
 [泛型方法](../../../csharp/programming-guide/generics/generic-methods.md)   
 [泛型](../Topic/Generics%20in%20the%20.NET%20Framework.md)