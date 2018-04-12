---
title: 方法 &#39;System.Nullable (Of T) &#39;不能做為運算元的 &#39;AddressOf &#39;運算子
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32126
- bc32126
helpviewer_keywords:
- BC32126
ms.assetid: 2325668b-e2ad-40ee-a1ec-30450236c20d
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ce0e9bc6abd71f22e3f6c3486ef40493e74d820f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="methods-of-39systemnullableof-t39-cannot-be-used-as-operands-of-the-39addressof39-operator"></a>方法 &#39;System.Nullable (Of T) &#39;不能做為運算元的 &#39;AddressOf &#39;運算子
陳述式使用`AddressOf`運算子和運算元的程序表示<xref:System.Nullable%601>結構。  
  
 **錯誤 ID:** BC32126  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   取代中的程序名稱`AddressOf`子句，但不是成員的運算元<xref:System.Nullable%601>。  
  
-   撰寫類別所包裝的方法<xref:System.Nullable%601>您想要使用的。 在下列範例中，`NullableWrapper`類別會定義名為的新方法`GetValueOrDefault`。 因為這個新的方法不是成員的<xref:System.Nullable%601>，它可以套用至`nullInstance`，可為 null 的類型，以形成的引數的執行個體`AddressOf`。  
  
```vb  
Module Module1  
  
    Delegate Function Deleg() As Integer  
  
    Sub Main()  
        Dim nullInstance As New Nullable(Of Integer)(1)  
  
        Dim del As Deleg  
  
        ' GetValueOrDefault is a method of the Nullable generic  
        ' type. It cannot be used as an operand of AddressOf.  
        ' del = AddressOf nullInstance.GetValueOrDefault  
  
        ' The following line uses the GetValueOrDefault method  
        ' defined in the NullableWrapper class.  
        del = AddressOf (New NullableWrapper(  
            Of Integer)(nullInstance)).GetValueOrDefault  
  
        Console.WriteLine(del.Invoke())  
    End Sub  
  
    Class NullableWrapper(Of T As Structure)  
        Private m_Value As Nullable(Of T)  
  
        Sub New(ByVal Value As Nullable(Of T))  
            m_Value = Value  
        End Sub  
  
        Public Function GetValueOrDefault() As T  
            Return m_Value.Value  
        End Function  
    End Class  
End Module  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Nullable%601>  
 [AddressOf 運算子](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [可為 Null 的值類型](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [Visual Basic 中的泛型型別](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
