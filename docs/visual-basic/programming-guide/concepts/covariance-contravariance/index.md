---
title: 共變數和反變數 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59224c46-9931-466b-8c6e-3648c3e609c6
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1df3b01573ae1a9dc5c106efa5e387927c57c55f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="covariance-and-contravariance-visual-basic"></a>共變數和反變數 (Visual Basic)
在 Visual Basic 中，共變數和反變數可讓您進行陣列類型、委派類型和泛型型別引數的隱含參考轉換。 共變數會保留指派相容性，而反變數則會將它反轉。  
  
 下列程式碼示範指派相容性、共變數和反變數之間的差異。  
  
```vb  
' Assignment compatibility.   
Dim str As String = "test"  
' An object of a more derived type is assigned to an object of a less derived type.   
Dim obj As Object = str  
  
' Covariance.   
Dim strings As IEnumerable(Of String) = New List(Of String)()  
' An object that is instantiated with a more derived type argument   
' is assigned to an object instantiated with a less derived type argument.   
' Assignment compatibility is preserved.   
Dim objects As IEnumerable(Of Object) = strings  
  
' Contravariance.             
' Assume that there is the following method in the class:   
' Shared Sub SetObject(ByVal o As Object)  
' End Sub  
Dim actObject As Action(Of Object) = AddressOf SetObject  
  
' An object that is instantiated with a less derived type argument   
' is assigned to an object instantiated with a more derived type argument.   
' Assignment compatibility is reversed.   
Dim actString As Action(Of String) = actObject  
```  
  
 陣列的共變數可將衍生程度較大類型的陣列，隱含轉換成衍生程度較小類型的陣列。 但這項作業不是型別安全的，如下列程式碼範例所示。  
  
```vb  
Dim array() As Object = New String(10) {}  
' The following statement produces a run-time exception.  
' array(0) = 10  
```  
  
 共變數和反變數的方法群組支援可讓您比對方法簽章和委派類型。 這可讓您指派方法給委派，不只是具有相符簽章的方法，也可以是會傳回衍生程度較大類型 (共變數) 的方法，或接受衍生程度比委派類型所指定更小類型 (反變數) 的方法。 如需詳細資訊，請參閱[委派中的變異數 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) 和[在委派中使用變異數 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)。  
  
 下列程式碼範例示範共變數和反變數的方法群組支援。  
  
```vb  
Shared Function GetObject() As Object  
    Return Nothing  
End Function  
  
Shared Sub SetObject(ByVal obj As Object)  
End Sub  
  
Shared Function GetString() As String  
    Return ""  
End Function  
  
Shared Sub SetString(ByVal str As String)  
  
End Sub  
  
Shared Sub Test()  
    ' Covariance. A delegate specifies a return type as object,  
    ' but you can assign a method that returns a string.  
    Dim del As Func(Of Object) = AddressOf GetString  
  
    ' Contravariance. A delegate specifies a parameter type as string,  
    ' but you can assign a method that takes an object.  
    Dim del2 As Action(Of String) = AddressOf SetObject  
End Sub  
```  
  
 在 .NET Framework 4 或更新版本中，Visual Basic 支援泛型介面和委派中的共變數和反變數，並可讓您進行泛型型別參數的隱含轉換。 如需詳細資訊，請參閱[泛型介面中的變異數 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) 和[委派中的變異數 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)。  
  
 下列程式碼範例示範泛型介面的隱含參考轉換。  
  
```vb  
Dim strings As IEnumerable(Of String) = New List(Of String)  
Dim objects As IEnumerable(Of Object) = strings  
```  
  
 如果泛型介面或委派的泛型參數宣告為共變數或反變數，此泛型介面或委派稱為 *variant*。 Visual Basic 可讓您建立自己的 Variant 介面和委派。 如需詳細資訊，請參閱[建立 Variant 泛型介面 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) 和[委派中的變異數 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)。  
  
## <a name="related-topics"></a>相關主題  
  
|標題|說明|  
|-----------|-----------------|  
|[泛型介面中的變異數 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)|討論泛型介面中的共變性與逆變性，並提供.NET Framework 中的 Variant 泛型介面清單。|  
|[建立 Variant 泛型介面 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)|示範如何建立自訂 Variant 介面。|  
|[使用泛型集合介面中的變異數 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)|示範 <xref:System.Collections.Generic.IEnumerable%601> 和 <xref:System.IComparable%601> 介面中的共變數和反變數支援如何協助您重複使用程式碼。|  
|[委派中的變異數 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)|討論泛型和非泛型委派中的共變性和反變數，並提供 .NET Framework 中的 Variant 泛型委派清單。|  
|[使用委派中的變異數 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)|示範如何在非泛型委派中使用共變數和反變數支援，以比對方法簽章和委派類型。|  
|[針對 Func 與 Action 泛型委派使用變異數 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)|示範 `Func` 和 `Action` 委派中的共變數和反變數支援如何協助您重複使用程式碼。|
