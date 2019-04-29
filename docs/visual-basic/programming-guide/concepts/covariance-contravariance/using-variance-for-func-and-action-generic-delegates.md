---
title: 針對 Func 與 Action 泛型委派 (Visual Basic) 中使用變異數
ms.date: 07/20/2015
ms.assetid: 36c3012f-b39c-493b-b90f-079b5912ac1b
ms.openlocfilehash: f2f45a9b6536859499f882b4cd585595176208f2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61787266"
---
# <a name="using-variance-for-func-and-action-generic-delegates-visual-basic"></a>針對 Func 與 Action 泛型委派 (Visual Basic) 中使用變異數
下列範例示範如何在 `Func` 和 `Action` 泛型委派中使用共變數和反變數，以便在您的程式碼中重複使用方法並提供更多彈性。  
  
 如需有關共變數和反變數的詳細資訊，請參閱[委派 (Visual Basic) 中的變異數](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)。  
  
## <a name="using-delegates-with-covariant-type-parameters"></a>使用具有 Covariant 型別參數的委派  
 下列範例說明在泛型 `Func` 委派中支援共變數的好處。 `FindByTitle` 方法使用 `String` 類型的參數，並傳回 `Employee` 類型的物件。 不過，您可以將此方法指派給 `Func(Of String, Person)` 委派，因為 `Employee` 會繼承 `Person`。  
  
```vb  
' Simple hierarchy of classes.  
Public Class Person  
End Class  
  
Public Class Employee  
    Inherits Person  
End Class  
  
Class Finder  
    Public Shared Function FindByTitle(  
        ByVal title As String) As Employee  
        ' This is a stub for a method that returns  
        ' an employee that has the specified title.  
        Return New Employee  
    End Function  
  
    Sub Test()  
        ' Create an instance of the delegate without using variance.  
        Dim findEmployee As Func(Of String, Employee) =  
            AddressOf FindByTitle  
  
        ' The delegate expects a method to return Person,  
        ' but you can assign it a method that returns Employee.  
        Dim findPerson As Func(Of String, Person) =  
            AddressOf FindByTitle  
  
        ' You can also assign a delegate   
        ' that returns a more derived type to a delegate   
        ' that returns a less derived type.  
        findPerson = findEmployee  
    End Sub  
End Class  
```  
  
## <a name="using-delegates-with-contravariant-type-parameters"></a>使用具有 Contravariant 型別參數的委派  
 下列範例說明在泛型 `Action` 委派中支援反變數的好處。 `AddToContacts` 方法使用 `Person` 類型的參數。 不過，您可以將此方法指派給 `Action(Of Employee)` 委派，因為 `Employee` 會繼承 `Person`。  
  
```vb  
Public Class Person  
End Class  
  
Public Class Employee  
    Inherits Person  
End Class  
  
Class AddressBook  
    Shared Sub AddToContacts(ByVal person As Person)  
        ' This method adds a Person object  
        ' to a contact list.  
    End Sub  
  
    Sub Test()  
        ' Create an instance of the delegate without using variance.  
        Dim addPersonToContacts As Action(Of Person) =  
            AddressOf AddToContacts  
  
        ' The Action delegate expects   
        ' a method that has an Employee parameter,  
        ' but you can assign it a method that has a Person parameter  
        ' because Employee derives from Person.  
        Dim addEmployeeToContacts As Action(Of Employee) =  
            AddressOf AddToContacts  
  
        ' You can also assign a delegate   
        ' that accepts a less derived parameter   
        ' to a delegate that accepts a more derived parameter.  
        addEmployeeToContacts = addPersonToContacts  
    End Sub  
End Class  
```  
  
## <a name="see-also"></a>另請參閱

- [共變數和反變數 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/index.md)
- [泛型](~/docs/standard/generics/index.md)
