---
title: "使用委派 (Visual Basic) 中的變異數 |Microsoft 文件"
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
ms.assetid: 7b5c20f1-6416-46a3-94b6-f109c31c842c
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
ms.openlocfilehash: 5bd3e60031eac713cee3dee1399af8c6b83e6656
ms.lasthandoff: 03/13/2017

---
# <a name="using-variance-in-delegates-visual-basic"></a>使用委派 (Visual Basic) 中的變異數
當您指派給委派的方法*共變數*和*反變數*進行比對方法簽章與委派型別提供的彈性。 共變數允許的方法有更多衍生於所定義的委派中的傳回型別。 反變數允許具有較少衍生比委派型別中的參數類型的方法。  
  
## <a name="example-1-covariance"></a>範例 1︰ 共變數  
  
### <a name="description"></a>描述  
 這個範例會示範如何使用委派的傳回型別衍生自委派簽章中的傳回類型的方法。 傳回的資料型別`DogsHandler`的型別`Dogs`，衍生自`Mammals`定義在委派中的型別。  
  
### <a name="code"></a>程式碼  
  
```vb  
Class Mammals  
End Class  
  
Class Dogs  
    Inherits Mammals  
End Class  
Class Test  
    Public Delegate Function HandlerMethod() As Mammals  
    Public Shared Function MammalsHandler() As Mammals  
        Return Nothing  
    End Function  
    Public Shared Function DogsHandler() As Dogs  
        Return Nothing  
    End Function  
    Sub Test()  
        Dim handlerMammals As HandlerMethod = AddressOf MammalsHandler  
        ' Covariance enables this assignment.  
        Dim handlerDogs As HandlerMethod = AddressOf DogsHandler  
    End Sub  
End Class  
```  
  
## <a name="example-2-contravariance"></a>範例 2︰ 反變數  
  
### <a name="description"></a>描述  
 這個範例會示範如何使用委派的參數類型的委派簽章的參數型別的基底型別的方法。 與反變數，您可以使用一個事件處理常式，而不是個別的處理常式。 例如，您可以建立事件處理常式可接受`EventArgs`輸入參數，並將它與`Button.MouseClick`所傳送的事件`MouseEventArgs`類型做為參數，也可以與`TextBox.KeyDown`所傳送的事件`KeyEventArgs`參數。  
  
### <a name="code"></a>程式碼  
  
```vb  
' Event hander that accepts a parameter of the EventArgs type.  
Private Sub MultiHandler(ByVal sender As Object,  
                         ByVal e As System.EventArgs)  
    Label1.Text = DateTime.Now  
End Sub  
  
Private Sub Form1_Load(ByVal sender As System.Object,  
    ByVal e As System.EventArgs) Handles MyBase.Load  
  
    ' You can use a method that has an EventArgs parameter,  
    ' although the event expects the KeyEventArgs parameter.  
    AddHandler Button1.KeyDown, AddressOf MultiHandler  
  
    ' You can use the same method   
    ' for the event that expects the MouseEventArgs parameter.  
    AddHandler Button1.MouseClick, AddressOf MultiHandler  
End Sub  
```  
  
## <a name="see-also"></a>另請參閱  
 [委派 (Visual Basic) 中的變異數](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)   
 [針對 Func 與 Action 委派 (Visual Basic) 中使用變異數](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
