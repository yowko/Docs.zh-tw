---
title: "泛型介面 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# 語言, 泛型介面"
  - "泛型 [C#], 介面"
ms.assetid: a8fa49a1-6e78-4a09-87e5-84a0b9f5ffbe
caps.latest.revision: 28
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 28
---
# 泛型介面 (C# 程式設計手冊)
通常為泛型集合類別或代表集合中項目的泛型類別定義介面是很有用的。  泛型類別最好是使用泛型介面，例如 <xref:System.IComparable%601>，而非 <xref:System.IComparable>，如此才能避免實值型別 \(Value Type\) 的 boxing 和 unboxing 作業。  .NET Framework 類別庫 \(Class Library\) 定義了幾種泛型介面，以便搭配 <xref:System.Collections.Generic> 命名空間 \(Namespace\) 中的集合類別使用。  
  
 當介面指定當做型別參數上的條件約束時，就只能使用實作介面的型別。  下列程式碼範例示範衍生自 `GenericList<T>` 類別的 `SortedList<T>` 類別。  如需詳細資訊，請參閱 [泛型簡介](../../../csharp/programming-guide/generics/introduction-to-generics.md)。  `SortedList<T>` 會加入條件約束 `where T : IComparable<T>`。  如此可讓 `SortedList<T>` 中的 `BubbleSort` 方法使用清單項目上的泛型 <xref:System.IComparable%601.CompareTo%2A> 方法。  在這個程式碼範例中，清單項目是實作 `IComparable<Person>` 的簡單類別 `Person`。  
  
 [!code-cs[csProgGuideGenerics#29](../../../csharp/programming-guide/generics/codesnippet/csharp/generic-interfaces_1.cs)]  
  
 在單一型別上可以指定多個介面當做條件約束，如下所示：  
  
 [!code-cs[csProgGuideGenerics#30](../../../csharp/programming-guide/generics/codesnippet/csharp/generic-interfaces_2.cs)]  
  
 一個介面可以定義一個以上的型別參數，如下所示：  
  
 [!code-cs[csProgGuideGenerics#31](../../../csharp/programming-guide/generics/codesnippet/csharp/generic-interfaces_3.cs)]  
  
 適用於類別的繼承 \(Inheritance\) 規則也適用於介面：  
  
 [!code-cs[csProgGuideGenerics#32](../../../csharp/programming-guide/generics/codesnippet/csharp/generic-interfaces_4.cs)]  
  
 如果泛型介面是 contra\-variant \(表示只會使用其型別參數當做傳回值\) 時，泛型介面就可以繼承自非泛型介面。  在 .NET Framework 類別庫中，因為 <xref:System.Collections.Generic.IEnumerable%601> 只會在 <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> 的傳回值和 <xref:System.Collections.Generic.IEnumerator%601.Current%2A> 屬性 getter 中使用 `T`，所以 <xref:System.Collections.Generic.IEnumerable%601> 會繼承自 <xref:System.Collections.IEnumerable>。  
  
 具象類別可以實作封閉式建構的介面，如下所示：  
  
 [!code-cs[csProgGuideGenerics#33](../../../csharp/programming-guide/generics/codesnippet/csharp/generic-interfaces_5.cs)]  
  
 只要類別參數清單提供介面所需的全部引數，泛型類別就可以實作泛型介面或封閉式建構的介面，如下所示：  
  
 [!code-cs[csProgGuideGenerics#34](../../../csharp/programming-guide/generics/codesnippet/csharp/generic-interfaces_6.cs)]  
  
 控制方法多載的規則與泛型類別、泛型結構 \(Struct\) 或泛型介面中的方法相同。  如需詳細資訊，請參閱 [泛型方法](../../../csharp/programming-guide/generics/generic-methods.md)。  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [泛型簡介](../../../csharp/programming-guide/generics/introduction-to-generics.md)   
 [interface](../../../csharp/language-reference/keywords/interface.md)   
 [泛型](../Topic/Generics%20in%20the%20.NET%20Framework.md)