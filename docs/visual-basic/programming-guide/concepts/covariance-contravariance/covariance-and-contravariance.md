---
title: "共變數和反變數 (Visual Basic) |Microsoft 文件"
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
ms.assetid: 59224c46-9931-466b-8c6e-3648c3e609c6
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b785e298c5ba38a8e3d8cc549b2dcf2df1ef6bd8
ms.lasthandoff: 03/13/2017

---
# <a name="covariance-and-contravariance-visual-basic"></a>共變數和反變數 (Visual Basic)
在 Visual Basic 中的共變數和反變數啟用陣列類型、 委派類型和泛型類型引數的隱含參考轉換。 共變數會保留設定相容性和反變數會反轉它。  
  
 下列程式碼示範如何設定相容性、 共變性與逆變性之間的差異。  
  
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
  
 陣列共變數可隱含轉換成較少衍生型別的陣列更多衍生型別的陣列。 但這項作業不是類型安全，如下列程式碼範例所示。  
  
```vb  
Dim array() As Object = New String(10) {}  
' The following statement produces a run-time exception.  
' array(0) = 10  
```  
  
 共變數和反變數支援方法群組允許使用委派型別比對方法簽章。 此可讓您指派給委派不只具有相符簽章，但也會傳回更多衍生類型 （共變數） 或方法的方法會接受具有比指定的委派型別較少衍生型別 （反變數） 的參數。 如需詳細資訊，請參閱[委派 (Visual Basic) 中的變異數](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)和[使用委派 (Visual Basic) 中的變異數](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)。  
  
 下列程式碼範例示範方法群組支援共變數和反變數。  
  
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
  
 在.NET Framework 4 或更新版本的 Visual Basic 中支援的泛型介面及委派中的共變數和反變數，並允許泛型類型參數的隱含轉換。 如需詳細資訊，請參閱[泛型介面 (Visual Basic) 中的變異數](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)和[委派 (Visual Basic) 中的變異數](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)。  
  
 下列程式碼範例將示範隱含參考轉換為泛型介面。  
  
```vb  
Dim strings As IEnumerable(Of String) = New List(Of String)  
Dim objects As IEnumerable(Of Object) = strings  
```  
  
 泛型介面或委派呼叫*變異*如果其泛型參數宣告共變性或逆變性。 Visual Basic 可讓您建立您自己的 variant 介面和委派。 如需詳細資訊，請參閱[建立 Variant 泛型介面 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)和[委派 (Visual Basic) 中的變異數](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)。  
  
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|-----------|-----------------|  
|[泛型介面 (Visual Basic) 中的變異數](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)|討論泛型介面中的共變性與逆變性，並提供.NET Framework 中的 Variant 泛型介面清單。|  
|[建立 Variant 泛型介面 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)|示範如何建立自訂的 variant 介面。|  
|[在介面中使用變異數的泛型集合 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)|顯示的共變數和反變數如何在支援<xref:System.Collections.Generic.IEnumerable%601>和<xref:System.IComparable%601>介面可以幫助您重複使用程式碼。</xref:System.IComparable%601> </xref:System.Collections.Generic.IEnumerable%601>|  
|[委派 (Visual Basic) 中的變異數](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)|討論的共變數和反變數泛型和非泛型委派中的並提供.NET Framework 中的 variant 泛型委派的清單。|  
|[使用委派 (Visual Basic) 中的變異數](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)|示範如何使用非泛型委派中的共變數和反變數的支援比對方法簽章與委派類型。|  
|[針對 Func 與 Action 委派 (Visual Basic) 中使用變異數](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)|顯示的共變數和反變數如何在支援`Func`和`Action`委派可以幫助您重複使用程式碼。|
