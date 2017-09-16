---
title: "如何：執行運算式樹狀架構 (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: get-started-article
dev_langs:
- CSharp
ms.assetid: b8c40db5-2464-4bb9-9001-8c2bc7f006c5
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: d230adee877c214dfef0f60ae2c6e7547fedb869
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-execute-expression-trees-c"></a>如何：執行運算式樹狀架構 (C#)
本主題示範如何執行運算式樹狀架構。 執行運算式樹狀架構可能會傳回一個值，或者只是執行某個動作，例如呼叫方法。  
  
 您只能執行代表 Lambda 運算式的運算式樹狀架構。 代表 Lambda 運算式的運算式樹狀架構為 <xref:System.Linq.Expressions.LambdaExpression> 或 <xref:System.Linq.Expressions.Expression%601> 類型。 若要執行這些運算式樹狀架構，請呼叫 <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> 方法建立可執行委派，然後叫用該委派。  
  
> [!NOTE]
>  如果不知道委派的類型，也就是 lambda 運算式是類型 <xref:System.Linq.Expressions.LambdaExpression> 而非 <xref:System.Linq.Expressions.Expression%601>，您必須對委派呼叫 <xref:System.Delegate.DynamicInvoke%2A> 方法，而不是直接叫用它。  
  
 如果運算式樹狀架構不代表 Lambda 運算式，您可以呼叫 <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> 方法，建立新的 Lambda 運算式，以原始的運算式樹狀架構當做其主體。 然後，您可以如本節稍早所述來執行此 Lambda 運算式。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何藉由建立和執行 Lambda 運算式，來執行代表數字自乘至乘冪的運算式樹狀架構。 顯示的結果會是已自乘至乘冪的數字。  
  
```csharp  
// The expression tree to execute.  
BinaryExpression be = Expression.Power(Expression.Constant(2D), Expression.Constant(3D));  
  
// Create a lambda expression.  
Expression<Func<double>> le = Expression.Lambda<Func<double>>(be);  
  
// Compile the lambda expression.  
Func<double> compiledExpression = le.Compile();  
  
// Execute the lambda expression.  
double result = compiledExpression();  
  
// Display the result.  
Console.WriteLine(result);  
  
// This code produces the following output:  
// 8  
```  
  
## <a name="compiling-the-code"></a>編譯程式碼  
  
-   如果 System.Core.dll 的專案參考原本未參考，請新增這項參考。  
  
-   加入 System.Linq.Expressions 命名空間。  
  
## <a name="see-also"></a>另請參閱  
 [運算式樹狀架構 (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)   
 [如何：修改運算式樹狀架構 (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)

