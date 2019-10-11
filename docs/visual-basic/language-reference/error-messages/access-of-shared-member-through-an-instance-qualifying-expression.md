---
title: 透過執行個體存取共用成員。將不會評估合格的運算式
ms.date: 07/20/2015
f1_keywords:
- vbc42025
- BC42025
helpviewer_keywords:
- BC42025
ms.assetid: db3337e5-c349-42bf-86df-d9c1e00952a5
ms.openlocfilehash: 773a97c301e7cb5bec0234ae466d487ec9716437
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250340"
---
# <a name="access-of-shared-member-through-an-instance-qualifying-expression-will-not-be-evaluated"></a>透過執行個體存取共用成員。將不會評估合格的運算式

類別或結構的執行個體變數是用來存取在該類別或結構中定義的 @no__t 0 變數、屬性、程式或事件。 如果執行個體變數是用來存取類別或結構的隱含共用成員，例如常數或列舉，或是嵌套的類別或結構，也可能會發生此警告。

共用成員的目的是只建立該成員的單一複本，並將該單一複本提供給其宣告所在類別或結構的每個實例使用。 它會與此用途一致，以透過其類別或結構的名稱來存取 @no__t 0 成員，而不是透過保存該類別或結構之個別實例的變數。

透過執行個體變數存取 @no__t 0 的成員，可以藉由遮蔽成員 `Shared` 的事實，讓您的程式碼更容易瞭解。 此外，如果這類存取是執行其他動作之運算式的一部分，例如會傳回共用成員實例的 @no__t 0 程式，Visual Basic 會略過運算式，以及其他任何會執行的動作。  
  
如需詳細資訊和範例，請參閱[Shared](../modifiers/shared.md)。  
  
根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
**錯誤識別碼：** BC42025  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
使用定義要存取之 @no__t 0 成員的類別或結構的名稱，如下列範例所示：
  
```vb
Public Class TestClass
    Public Shared Sub SayHello()
        MsgBox("Hello")
    End Sub
End Class
  
Module Program
    Public Sub Main()  
        ' Access a shared method through an instance variable.  
        ' This generates a warning.  
        Dim tc As New TestClass()
        tc.SayHello()
  
        ' Access a shared method by using the class name.  
        ' This does not generate a warning.  
        TestClass.SayHello()
    End Sub  
End Module  
```  
  
> [!NOTE]
> 當兩個程式設計項目具有相同的名稱時，請警示範圍的效果。 在上述範例中，如果您使用 `Dim testClass as testClass = Nothing` 來宣告實例，編譯器會將呼叫視為透過類別名稱存取方法的 `testClass.sayHello()`，而且不會出現任何警告。
  
## <a name="see-also"></a>另請參閱

- [Shared](../modifiers/shared.md)
- [Visual Basic 中的範圍](../../programming-guide/language-features/declared-elements/scope.md)
