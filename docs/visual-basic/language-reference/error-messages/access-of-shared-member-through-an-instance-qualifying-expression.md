---
title: 透過執行個體存取共用成員。將不會評估合格的運算式
ms.date: 07/20/2015
f1_keywords:
- vbc42025
- BC42025
helpviewer_keywords:
- BC42025
ms.assetid: db3337e5-c349-42bf-86df-d9c1e00952a5
ms.openlocfilehash: 3174d463744303e8c90ed0b2e1a4d86ed08fbcfb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947703"
---
# <a name="access-of-shared-member-through-an-instance-qualifying-expression-will-not-be-evaluated"></a>透過執行個體存取共用成員。將不會評估合格的運算式
類別或結構的執行個體變數是用來存取`Shared`該類別或結構中定義的變數、屬性、程式或事件。 如果執行個體變數是用來存取類別或結構的隱含共用成員, 例如常數或列舉, 或是嵌套的類別或結構, 也可能會發生此警告。  
  
 共用成員的目的是只建立該成員的單一複本, 並將該單一複本提供給其宣告所在類別或結構的每個實例使用。 它會與此用途一致, 以透過`Shared`其類別或結構的名稱存取成員, 而不是透過保存該類別或結構之個別實例的變數。  
  
 透過執行個體變數存取`Shared`成員,可以藉由遮蔽成員的事實,讓您的程式碼更容易瞭解。`Shared` 此外, 如果這類存取是執行其他動作之運算式的一部分, 例如`Function`會傳回共用成員實例的程式, Visual Basic 會略過運算式, 以及其他任何會執行的動作。  
  
 如需詳細資訊和範例, 請參閱[Shared](../../../visual-basic/language-reference/modifiers/shared.md)。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤識別碼:** BC42025  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 使用定義`Shared`要存取之成員的類別或結構的名稱, 如下列範例所示。  
  
```vb  
Public Class testClass  
    Public Shared Sub sayHello()  
        MsgBox("Hello")  
    End Sub  
End Class  
  
Module testModule  
    Public Sub Main()  
        ' Access a shared method through an instance variable.  
        ' This generates a warning.  
        Dim tc As New testClass  
        tc.sayHello()  
  
        ' Access a shared method by using the class name.  
        ' This does not generate a warning.  
        testClass.sayHello()  
    End Sub  
End Module  
```  
  
> [!NOTE]
> 當兩個程式設計項目具有相同的名稱時, 請警示範圍的效果。 在上述範例中, 如果您使用`Dim testClass as testClass = Nothing`來宣告實例, 編譯器會透過類別名稱將`testClass.sayHello()`呼叫視為方法的存取, 而不會發生警告。  
  
## <a name="see-also"></a>另請參閱

- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [Visual Basic 中的範圍](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
