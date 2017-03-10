---
title: "泛型委派 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "委派 [C#], 泛型"
  - "泛型 [C#], 委派"
ms.assetid: bdea509c-44c1-4309-aaa9-15c7aee009df
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# 泛型委派 (C# 程式設計手冊)
[delegate](../../../csharp/language-reference/keywords/delegate.md) 能夠定義自己的型別參數。  如下列程式碼範例所示，參考泛型委派 \(Delegate\) 的程式碼可以指定型別引數以建立封閉式建構型別，就像在產生泛型類別或呼叫泛型方法時一樣：  
  
 [!code-cs[csProgGuideGenerics#36](../../../csharp/programming-guide/generics/codesnippet/csharp/generic-delegates_1.cs)]  
  
 C\# 2.0 版有一項適用於具象和泛型委派型別，稱為方法群組轉換的新功能，能夠讓您使用下列簡化的語法撰寫上一行程式碼：  
  
 [!code-cs[csProgGuideGenerics#37](../../../csharp/programming-guide/generics/codesnippet/csharp/generic-delegates_2.cs)]  
  
 在泛型類別中定義的委派可像類別方法一樣，使用泛型類別型別參數。  
  
 [!code-cs[csProgGuideGenerics#38](../../../csharp/programming-guide/generics/codesnippet/csharp/generic-delegates_3.cs)]  
  
 參考委派的程式碼必須指定包含類別的型別引數，如下所示：  
  
 [!code-cs[csProgGuideGenerics#39](../../../csharp/programming-guide/generics/codesnippet/csharp/generic-delegates_4.cs)]  
  
 泛型委派對於根據一般設計模式定義事件特別有用，因為寄件人引數可以是強型別並且不再需要從 <xref:System.Object> 轉換。  
  
 [!code-cs[csProgGuideGenerics#40](../../../csharp/programming-guide/generics/codesnippet/csharp/generic-delegates_5.cs)]  
  
## 請參閱  
 <xref:System.Collections.Generic>   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [泛型簡介](../../../csharp/programming-guide/generics/introduction-to-generics.md)   
 [泛型方法](../../../csharp/programming-guide/generics/generic-methods.md)   
 [泛型類別](../../../csharp/programming-guide/generics/generic-classes.md)   
 [泛型介面](../../../csharp/programming-guide/generics/generic-interfaces.md)   
 [委派](../../../csharp/programming-guide/delegates/index.md)   
 [泛型](../Topic/Generics%20in%20the%20.NET%20Framework.md)