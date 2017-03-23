---
title: "泛型和屬性 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "屬性 [C#], 使用泛型"
  - "泛型 [C#], 屬性"
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
caps.latest.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 13
---
# 泛型和屬性 (C# 程式設計手冊)
將屬性套用到泛型型別的方式，就跟非泛型型別一樣。  如需套用屬性的詳細資訊，請參閱[屬性](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)。  
  
 自訂屬性只能參考開放泛型型別 \(即不提供型別引數的泛型型別\)，以及封閉建構的泛型型別 \(即提供引數給所有型別參數的泛型型別\)。  
  
 下列範例使用了這個自訂屬性：  
  
 [!code-cs[csProgGuideGenerics#48](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_1.cs)]  
  
 屬性可參考開放泛型型別：  
  
 [!code-cs[csProgGuideGenerics#49](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_2.cs)]  
  
 使用適當數目的逗號指定多個型別參數。  在此範例中，`GenericClass2` 具有兩個型別參數：  
  
 [!code-cs[csProgGuideGenerics#50](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_3.cs)]  
  
 屬性可參考封閉建構的泛型型別：  
  
 [!code-cs[csProgGuideGenerics#51](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_4.cs)]  
  
 參考泛型型別參數的屬性會造成編譯時期錯誤：  
  
 [!code-cs[csProgGuideGenerics#52](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_5.cs)]  
  
 泛型型別無法繼承自 <xref:System.Attribute>：  
  
 [!code-cs[csProgGuideGenerics#53](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_6.cs)]  
  
 若要取得執行階段的泛型型別或型別參數的詳細資訊，您可以使用 <xref:System.Reflection> 方法。  如需詳細資訊，請參閱[泛型和反映](../../../csharp/programming-guide/generics/generics-and-reflection.md)。  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [泛型](../../../csharp/programming-guide/generics/index.md)   
 [屬性](../Topic/Extending%20Metadata%20Using%20Attributes.md)