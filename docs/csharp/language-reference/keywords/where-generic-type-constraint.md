---
title: "where (泛型類型條件約束) (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.assetid: d7aa871b-0714-416a-bab2-96f87ada4310
caps.latest.revision: 10
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 400dfda51d978f35c3995f90840643aaff1b9c13
ms.openlocfilehash: e5baa75c55d58a4d975fc42472f90ff4125cbb5c
ms.contentlocale: zh-tw
ms.lasthandoff: 03/24/2017

---
# <a name="where-generic-type-constraint-c-reference"></a>where (泛型類型條件約束) (C# 參考)
在泛型類型定義中，`where` 子句是用來指定類型的條件約束，而這些類型可以用作泛型宣告中所定義類型參數的引數。 例如，您可以宣告泛型類別 `MyGenericClass`，讓類型參數 `T` 實作 <xref:System.IComparable%601> 介面：  
  
```csharp  
public class MyGenericClass<T> where T:IComparable { }  
```  
  
> [!NOTE]
>  如需查詢運算式中 where 子句的詳細資訊，請參閱 [where 子句](../../../csharp/language-reference/keywords/where-clause.md)。  
  
 除了介面條件約束之外，`where` 子句可以包含基底類別條件約束，說明類型必須將指定的類別作為基底類別 (或該類別本身)，才能用作該泛型類型的類型引數。 如果使用這類條件約束，則它必須出現在該類型參數的任何其他條件約束之前。  
  
 [!code-cs[csrefKeywordsContextual#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_1.cs)]  
  
 `where` 子句也可能包含建構函式條件約束。 您可以建立使用新運算子的類型參數執行個體，但若要這樣做，類型參數必須受限於建構函式條件約束 `new()`。 [new() 條件約束](../../../csharp/language-reference/keywords/new-constraint.md)可讓編譯器知道提供的任何類型引數都必須有可存取的無參數或預設建構函式。 例如:   
  
 [!code-cs[csrefKeywordsContextual#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_2.cs)]  
  
 `new()` 條件約束會出現在 `where` 子句中的最後。  
  
 若有多個類型參數，請對每個類型參數使用一個 `where` 子句，例如：  
  
 [!code-cs[csrefKeywordsContextual#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_3.cs)]  
  
 您也可以將條件約束附加至泛型方法的類型參數，如下所示︰  
  
```csharp  
public bool MyMethod<T>(T t) where T : IMyInterface { }  
```  
  
 請注意，描述委派類型參數條件約束的語法與方法的語法相同︰  
  
```csharp  
delegate T MyDelegate<T>() where T : new()  
```  
  
 如需泛型委派的資訊，請參閱[泛型委派](../../../csharp/programming-guide/generics/generic-delegates.md)。  
  
 如需條件約束語法和用法的詳細資料，請參閱[類型參數的條件約束](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)。  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [泛型簡介](../../../csharp/programming-guide/generics/introduction-to-generics.md)   
 [new 條件約束](../../../csharp/language-reference/keywords/new-constraint.md)   
 [型別參數的條件約束](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)
