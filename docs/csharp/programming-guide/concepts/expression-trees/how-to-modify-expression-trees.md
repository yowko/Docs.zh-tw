---
title: '如何修改運算式樹狀架構 (c # ) '
description: 瞭解如何藉由建立現有運算式樹狀架構的複本並進行必要的變更，以修改運算式樹狀架構。
ms.date: 07/20/2015
ms.assetid: 9b0cd8c2-457e-4833-9e36-31e79545f442
ms.openlocfilehash: 01176f489794a0f4ca29d229d29507fdba0fd5a8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167687"
---
# <a name="how-to-modify-expression-trees-c"></a>如何修改運算式樹狀架構 (c # ) 

本主題示範如何修改運算式樹狀架構。 運算式樹狀架構為不可變，這表示無法直接對其進行修改。 若要變更運算式樹狀架構，您必須建立現有運算式樹狀架構的複本，並且在建立複本時進行必要的變更。 您可以使用 <xref:System.Linq.Expressions.ExpressionVisitor> 類別周遊現有的運算式樹狀架構，並複製每個瀏覽的節點。  
  
### <a name="to-modify-an-expression-tree"></a>修改運算式樹狀架構  
  
1. 建立新的 **主控台應用程式** 專案。  
  
2. 將 `using` 指示詞新增至 `System.Linq.Expressions` 命名空間的檔案。  
  
3. 將 `AndAlsoModifier` 類別新增至專案。  
  
    ```csharp  
    public class AndAlsoModifier : ExpressionVisitor  
    {  
        public Expression Modify(Expression expression)  
        {  
            return Visit(expression);  
        }  
  
        protected override Expression VisitBinary(BinaryExpression b)  
        {  
            if (b.NodeType == ExpressionType.AndAlso)  
            {  
                Expression left = this.Visit(b.Left);  
                Expression right = this.Visit(b.Right);  
  
                // Make this binary expression an OrElse operation instead of an AndAlso operation.  
                return Expression.MakeBinary(ExpressionType.OrElse, left, right, b.IsLiftedToNull, b.Method);  
            }  
  
            return base.VisitBinary(b);  
        }  
    }  
    ```  
  
     此類別會繼承 <xref:System.Linq.Expressions.ExpressionVisitor> 類別，並針對代表 `AND` 條件運算的運算式進行修改。 它會將這些運算從 `AND` 條件運算變更為 `OR` 條件運算。 為了執行這項操作，此類別會覆寫基底類型的 <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> 方法，因為 `AND` 條件運算式會以二元運算式來表示。 在 `VisitBinary` 方法中，如果傳遞給它的運算式代表 `AND` 條件運算，程式碼會建構新的運算式，以包含 `OR` 條件運算子來取代 `AND` 條件運算子。 如果傳遞給 `VisitBinary` 的運算式不代表 `AND` 條件運算，此方法會延後到基底類別實作。 基底類別方法會建構類似傳入之運算式樹狀架構的節點，但這些節點的樹狀子目錄會由造訪者以遞迴方式產生的運算式樹狀架構來取代。  
  
4. 將 `using` 指示詞新增至 `System.Linq.Expressions` 命名空間的檔案。  
  
5. 將程式碼新增至 Program.cs 檔案中的 `Main` 方法以建立運算式樹狀架構，然後將運算式樹狀架構傳遞給要修改其內容的方法。  
  
    ```csharp  
    Expression<Func<string, bool>> expr = name => name.Length > 10 && name.StartsWith("G");  
    Console.WriteLine(expr);  
  
    AndAlsoModifier treeModifier = new AndAlsoModifier();  
    Expression modifiedExpr = treeModifier.Modify((Expression) expr);  
  
    Console.WriteLine(modifiedExpr);  
  
    /*  This code produces the following output:  
  
        name => ((name.Length > 10) && name.StartsWith("G"))  
        name => ((name.Length > 10) || name.StartsWith("G"))  
    */  
    ```  
  
     此程式碼會建立包含 `AND` 條件運算的運算式。 然後建立 `AndAlsoModifier` 類別的執行個體，並將運算式傳遞給此類別的 `Modify` 的方法。 此時會輸出原始和修改後的運算式樹狀架構，以顯示變更的情形。  
  
6. 編譯並執行應用程式。  
  
## <a name="see-also"></a>另請參閱

- [如何執行運算式樹狀架構 (c # ) ](./how-to-execute-expression-trees.md)
- [運算式樹狀架構 (C#)](./index.md)
