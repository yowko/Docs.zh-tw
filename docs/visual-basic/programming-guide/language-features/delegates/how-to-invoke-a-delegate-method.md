---
title: "How to: Invoke a Delegate Method (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
ms.assetid: b56866ae-abf9-4a5a-a855-486359455e9c
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# How to: Invoke a Delegate Method (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

這個範例顯示如何使方法與委派 \(Delegate\) 產生關聯，然後再透過委派來叫用 \(Invoke\) 方法。  
  
### 建立委派和相對應的程序  
  
1.  建立名為 `MySubDelegate` 的委派。  
  
    ```  
    Delegate Sub MySubDelegate(ByVal x As Integer)  
    ```  
  
2.  宣告類別，其中包含的方法具有和委派相同的簽章。  
  
    ```  
    Class class1  
        Sub Sub1(ByVal x As Integer)  
            MsgBox("The value of x is: " & CStr(x))  
        End Sub  
    End Class  
    ```  
  
3.  定義方法來建立委派的執行個體，並藉由呼叫內建的 `Invoke` 方法來叫用與委派關聯的方法。  
  
    ```  
    Protected Sub DelegateTest()  
        Dim c1 As New class1  
        ' Create an instance of the delegate.  
        Dim msd As MySubDelegate = AddressOf c1.Sub1  
        ' Call the method.  
        msd.Invoke(10)  
    End Sub  
    ```  
  
## 請參閱  
 [Delegate Statement](../../../../visual-basic/language-reference/statements/delegate-statement.md)   
 [Delegates](../../../../visual-basic/programming-guide/language-features/delegates/delegates.md)   
 [Events](../../../../visual-basic/programming-guide/language-features/events/events.md)   
 [多執行緒應用程式](../Topic/Multithreaded%20Applications%20\(C%23%20and%20Visual%20Basic\).md)