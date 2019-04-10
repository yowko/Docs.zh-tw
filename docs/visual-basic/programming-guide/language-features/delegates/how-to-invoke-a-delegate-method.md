---
title: HOW TO：叫用委派方法 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: b56866ae-abf9-4a5a-a855-486359455e9c
ms.openlocfilehash: ac3e32010e7c20ba76e39915d694b11ab3a65d40
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59319608"
---
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a>HOW TO：叫用委派方法 (Visual Basic)
此範例示範如何將方法產生關聯的委派，然後叫用該方法，透過委派。  
  
### <a name="create-the-delegate-and-matching-procedures"></a>建立委派和比對程序  
  
1. 建立名為委派`MySubDelegate`。  
  
    ```  
    Delegate Sub MySubDelegate(ByVal x As Integer)  
    ```  
  
2. 宣告類別，其中包含具有相同的簽章與委派的方法。  
  
    ```  
    Class class1  
        Sub Sub1(ByVal x As Integer)  
            MsgBox("The value of x is: " & CStr(x))  
        End Sub  
    End Class  
    ```  
  
3. 定義方法，以建立委派的執行個體，並叫用方法和委派呼叫內建關聯`Invoke`方法。  
  
    ```  
    Protected Sub DelegateTest()  
        Dim c1 As New class1  
        ' Create an instance of the delegate.  
        Dim msd As MySubDelegate = AddressOf c1.Sub1  
        ' Call the method.  
        msd.Invoke(10)  
    End Sub  
    ```  
  
## <a name="see-also"></a>另請參閱

- [Delegate 陳述式](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [委派](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [事件](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [多執行緒應用程式](../../../../standard/threading/using-threads-and-threading.md)
