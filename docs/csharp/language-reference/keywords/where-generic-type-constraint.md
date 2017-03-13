---
title: "where (泛型類型條件約束) (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "whereconstraint"
  - "whereconstraint_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "where (泛型類型條件約束) [C#]"
ms.assetid: d7aa871b-0714-416a-bab2-96f87ada4310
caps.latest.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 10
---
# where (泛型類型條件約束) (C# 參考)
在泛型型別定義中，`where` 子句的用途是針對泛型宣告中所定義的型別參數，為其指定引數的型別條件約束。  例如，您可以宣告泛型類別 `MyGenericClass`，其中指定由型別參數 `T` 來實作 <xref:System.IComparable%601> 介面：  
  
```  
public class MyGenericClass<T> where T:IComparable { }  
```  
  
> [!NOTE]
>  如需查詢運算式中 where 子句的詳細資訊，請參閱 [where 子句](../../../csharp/language-reference/keywords/where-clause.md)。  
  
 除了介面條件約束，`where` 子句還可包含基底類別條件約束，此條件約束陳述了型別必須有指定類別做為基底類別 \(或該類別本身\)，才能用來當做該泛用型別的型別引數。  使用這種條件約束時，它必須出現於該型別參數任何其他條件約束之前。  
  
 [!code-cs[csrefKeywordsContextual#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_1.cs)]  
  
 `where` 子句也可以包括建構函式 \(Constructor\) 條件約束。  使用者可以使用新的運算子來建立型別參數的執行個體，但是若要這樣做，必須透過建構函式條件約束 `new()`，來限制該型別參數。  [new\(\) 條件約束](../../../csharp/language-reference/keywords/new-constraint.md)可讓編輯器知道，所提供的任何型別引數必須具有可存取的無參數 \(或預設\) 建構函式。  例如：  
  
 [!code-cs[csrefKeywordsContextual#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_2.cs)]  
  
 `new()` 條件約束會出現在 `where` 子句中的最後面。  
  
 如果是多重型別參數，則每個型別參數都要有一個 `where` 子句，例如：  
  
 [!code-cs[csrefKeywordsContextual#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_3.cs)]  
  
 您也可以將條件約束附加到泛型方法的型別參數，如以下所示：  
  
```  
public bool MyMethod<T>(T t) where T : IMyInterface { }  
```  
  
 請注意，描述委派型別參數條件約束的語法與方法型別參數的語法相同：  
  
```  
delegate T MyDelegate<T>() where T : new()  
```  
  
 如需泛型委派的詳細資訊，請參閱[泛型委派](../../../csharp/programming-guide/generics/generic-delegates.md)。  
  
 如需語法和條件約束用法的詳細資訊，請參閱[型別參數的條件約束](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)。  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [泛型簡介](../../../csharp/programming-guide/generics/introduction-to-generics.md)   
 [new 條件約束](../../../csharp/language-reference/keywords/new-constraint.md)   
 [類型參數的條件約束](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)