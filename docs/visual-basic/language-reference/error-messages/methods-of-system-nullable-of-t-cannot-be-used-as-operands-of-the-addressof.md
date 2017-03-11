---
title: "Methods of &#39;System.Nullable(Of T)&#39; cannot be used as operands of the &#39;AddressOf&#39; operator | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc32126"
  - "bc32126"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC32126"
ms.assetid: 2325668b-e2ad-40ee-a1ec-30450236c20d
caps.latest.revision: 5
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 5
---
# Methods of &#39;System.Nullable(Of T)&#39; cannot be used as operands of the &#39;AddressOf&#39; operator
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

陳述式將 `AddressOf` 運算子與代表 <xref:System.Nullable%601> 結構之程序或的運算元一起使用。  
  
 **錯誤 ID**：BC32126  
  
### 若要更正這個錯誤  
  
-   以 <xref:System.Nullable%601> 成員以外的運算元取代 `AddressOf` 子句中的程序名稱。  
  
-   撰寫類別，這個類別會包裝您要使用之 <xref:System.Nullable%601> 的方法。  在下列範例中，`NullableWrapper` 類別會定義名為 `GetValueOrDefault` 的新方法。  由於這個新方法不是 <xref:System.Nullable%601> 的成員，因此可以套用至 `nullInstance` \(可為 Null 型別的執行個體\) 以形成 `AddressOf` 的引數。  
  
    ```vb#  
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
  
## 請參閱  
 <xref:System.Nullable%601>   
 [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [Nullable Value Types](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)   
 [Visual Basic 中的泛型類型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)