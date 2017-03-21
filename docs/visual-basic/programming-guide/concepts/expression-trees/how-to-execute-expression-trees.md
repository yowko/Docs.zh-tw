---
title: "如何︰ 執行運算式樹狀架構 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 9dfb5ab3-f48f-417e-975f-f8f6f1cdc18d
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e12c45b417310f097d597561b2652ee793a4b2c0
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-execute-expression-trees-visual-basic"></a>如何︰ 執行運算式樹狀架構 (Visual Basic)
本主題說明如何執行運算式樹狀架構。 執行運算式樹狀架構可能會傳回值，或只是執行動作，例如呼叫方法。  
  
 您可以執行 lambda 運算式表示運算式樹狀架構。 運算式樹狀結構，代表 lambda 運算式的型別<xref:System.Linq.Expressions.LambdaExpression>或<xref:System.Linq.Expressions.Expression%601>。</xref:System.Linq.Expressions.Expression%601> </xref:System.Linq.Expressions.LambdaExpression> 若要執行這些運算式樹狀架構，呼叫<xref:System.Linq.Expressions.LambdaExpression.Compile%2A>方法以建立可執行的委派，然後叫用委派。</xref:System.Linq.Expressions.LambdaExpression.Compile%2A>  
  
> [!NOTE]
>  如果不知道委派型別，也就是 lambda 運算式為類型<xref:System.Linq.Expressions.LambdaExpression>而非<xref:System.Linq.Expressions.Expression%601>，您必須呼叫<xref:System.Delegate.DynamicInvoke%2A>方法而不是直接叫用該委派。</xref:System.Delegate.DynamicInvoke%2A> </xref:System.Linq.Expressions.Expression%601> </xref:System.Linq.Expressions.LambdaExpression>  
  
 如果運算式樹狀架構不代表 lambda 運算式，您可以建立新的 lambda 運算式做為其主體中，具有原始的運算式樹狀架構，藉由呼叫<xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29>方法。</xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> 然後，您可以執行 lambda 運算式，如本節先前所述。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何執行運算式樹狀架構代表某個數字乘冪提高藉由建立 lambda 運算式，並執行它。 結果，代表數字乘冪，會顯示。  
  
```vb  
' The expression tree to execute.  
Dim be As BinaryExpression = Expression.Power(Expression.Constant(2.0R), Expression.Constant(3.0R))  
  
' Create a lambda expression.  
Dim le As Expression(Of Func(Of Double)) = Expression.Lambda(Of Func(Of Double))(be)  
  
' Compile the lambda expression.  
Dim compiledExpression As Func(Of Double) = le.Compile()  
  
' Execute the lambda expression.  
Dim result As Double = compiledExpression()  
  
' Display the result.  
MsgBox(result)  
  
' This code produces the following output:  
' 8  
```  
  
## <a name="compiling-the-code"></a>編譯程式碼  
  
-   如果沒有參考，加入專案參考 system.core.dll 的參考。  
  
-   包括 System.Linq.Expressions 命名空間。  
  
## <a name="see-also"></a>另請參閱  
 [運算式樹狀架構 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)   
 [如何︰ 修改運算式樹狀架構 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
