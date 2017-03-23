---
title: "如何︰ 修改運算式樹狀架構 (Visual Basic) |Microsoft 文件"
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
ms.assetid: d1309fff-28bd-4d8e-a2cf-75725999e8f2
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
ms.openlocfilehash: fb4e818eed7d6547e091c914d40b3ce87af59512
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-modify-expression-trees-visual-basic"></a>如何︰ 修改運算式樹狀架構 (Visual Basic)
本主題說明如何修改運算式樹狀架構。 運算式樹狀架構是不可變的也就是說，它們無法直接進行修改。 若要變更運算式樹狀架構，您必須建立一份現有運算式樹狀架構，並建立複本時進行必要的變更。 您可以使用<xref:System.Linq.Expressions.ExpressionVisitor>類別來周遊現有運算式樹狀架構，並複製造訪每個節點。</xref:System.Linq.Expressions.ExpressionVisitor>  
  
### <a name="to-modify-an-expression-tree"></a>若要修改運算式樹狀架構  
  
1.  建立新**主控台應用程式**專案。  
  
2.  新增`Imports`陳述式的檔案來`System.Linq.Expressions`命名空間。  
  
3.  新增`AndAlsoModifier`類別，以您的專案。  
  
    ```vb  
    Public Class AndAlsoModifier  
        Inherits ExpressionVisitor  
  
        Public Function Modify(ByVal expr As Expression) As Expression  
            Return Visit(expr)  
        End Function  
  
        Protected Overrides Function VisitBinary(ByVal b As BinaryExpression) As Expression  
            If b.NodeType = ExpressionType.AndAlso Then  
                Dim left = Me.Visit(b.Left)  
                Dim right = Me.Visit(b.Right)  
  
                ' Make this binary expression an OrElse operation instead   
                ' of an AndAlso operation.  
                Return Expression.MakeBinary(ExpressionType.OrElse, left, right, _  
                                             b.IsLiftedToNull, b.Method)  
            End If  
  
            Return MyBase.VisitBinary(b)  
        End Function  
    End Class  
    ```  
  
     此類別會繼承<xref:System.Linq.Expressions.ExpressionVisitor>類別，專門用來修改這些運算式表示條件式`AND`作業。</xref:System.Linq.Expressions.ExpressionVisitor> 它會從在條件變更這些作業`AND`conditional `OR`。 若要這樣做，類別覆寫<xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A>方法的基底型別，因為條件式`AND`運算式表示為二進位運算式。</xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> 在`VisitBinary`方法，如果傳遞給它的運算式代表條件式`AND`作業，程式碼會建構新的運算式，其中包含條件式`OR`而不是條件式運算子`AND`運算子。 如果傳遞給運算式`VisitBinary`不代表條件式`AND`作業，方法會延後的基底類別實作。 建構的節點類似，會傳入的運算式樹狀架構，但節點已取代的運算式樹狀架構及其子樹狀目錄的基底類別方法產生以遞迴方式訪客。  
  
4.  新增`Imports`陳述式的檔案來`System.Linq.Expressions`命名空間。  
  
5.  將程式碼加入`Main`方法來建立運算式樹狀架構，並將它傳遞給方法的 Module1.vb 檔案中將修改它。  
  
    ```vb  
    Dim expr As Expression(Of Func(Of String, Boolean)) = _  
        Function(name) name.Length > 10 AndAlso name.StartsWith("G")  
  
    Console.WriteLine(expr)  
  
    Dim modifier As New AndAlsoModifier()  
    Dim modifiedExpr = modifier.Modify(CType(expr, Expression))  
  
    Console.WriteLine(modifiedExpr)  
  
    ' This code produces the following output:  
    ' name => ((name.Length > 10) && name.StartsWith("G"))  
    ' name => ((name.Length > 10) || name.StartsWith("G"))  
    ```  
  
     程式碼會建立包含條件運算式`AND`作業。 然後它會建立的執行個體`AndAlsoModifier`類別，並將運算式傳遞至`Modify`這個類別的方法。 原始和修改後的運算式樹狀結構會輸出到顯示變更。  
  
6.  編譯並執行應用程式。  
  
## <a name="see-also"></a>另請參閱  
 [如何︰ 執行運算式樹狀架構 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)   
 [運算式樹狀架構 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
