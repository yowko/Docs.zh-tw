---
title: "Of Clause (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Of"
  - "vb.Of"
  - "vb.of"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Of keyword"
  - "arguments [Visual Basic], data types"
  - "constraints, Visual Basic generic types"
  - "generic parameters"
  - "generics [Visual Basic], constraints"
  - "parameters, type"
  - "types [Visual Basic], generic"
  - "parameters, generic"
  - "type parameters"
  - "data type arguments"
ms.assetid: 0db8f65c-65af-4089-ab7f-6fcfecb60444
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Of Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

引入 `Of` 子句，這個子句會識別「*泛型*」類別、結構、介面、委派或程序上的「*型別參數*」。  如需泛型型別的詳細資訊，請參閱 [Visual Basic 中的泛型類型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)。  
  
## 使用 Of 關鍵字  
 下列程式碼範例會使用 `Of` 關鍵字，來定義採取兩個型別參數的類別大綱。  它會透過 <xref:System.IComparable> 介面來「*限制*」`keyType` 參數，這表示耗用程式碼必須提供可實作 <xref:System.IComparable> 的型別引數。  這是必要的，以便 `add` 程序可以呼叫 <xref:System.IComparable.CompareTo%2A?displayProperty=fullName> 方法。  如需條件約束的詳細資訊，請參閱[Type List](../../../visual-basic/language-reference/statements/type-list.md)。  
  
```  
Public Class Dictionary(Of entryType, keyType As IComparable)  
    Public Sub add(ByVal e As entryType, ByVal k As keyType)  
        Dim dk As keyType  
        If k.CompareTo(dk) = 0 Then  
        End If  
    End Sub  
    Public Function find(ByVal k As keyType) As entryType  
    End Function  
End Class  
```  
  
 如果您完成了先前的類別定義，便可以根據這個定義建構各種 `dictionary` 類別。  您提供給 `entryType` 和 `keyType` 的型別會決定類別要保存的項目型別，以及要與每個項目產生關聯的索引鍵型別。  因為條件約束，所以您必須提供給 `keyType` 可實作 <xref:System.IComparable> 的型別。  
  
 下列程式碼範例會建立保存 `String` 項目，並將 `Integer` 金鑰與每一個項目相關聯的物件。  `Integer` 實作 <xref:System.IComparable>，並因此滿足 `keyType` 上的條件約束。  
  
```  
Dim d As New dictionary(Of String, Integer)  
```  
  
 `Of` 關鍵字可用於以下內容中：  
  
 [Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Delegate 陳述式](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface 陳述式](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## 請參閱  
 <xref:System.IComparable>   
 [Type List](../../../visual-basic/language-reference/statements/type-list.md)   
 [Visual Basic 中的泛型類型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)   
 [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)