---
title: 透過執行個體存取共用成員。將不會評估合格的運算式
ms.date: 07/20/2015
f1_keywords:
- vbc42025
- BC42025
helpviewer_keywords:
- BC42025
ms.assetid: db3337e5-c349-42bf-86df-d9c1e00952a5
ms.openlocfilehash: 8e6ddab16c59d7ce95d96b377e3f372f6ebe5278
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843561"
---
# <a name="access-of-shared-member-through-an-instance-qualifying-expression-will-not-be-evaluated"></a>透過執行個體存取共用成員。將不會評估合格的運算式
使用類別或結構的執行個體變數存取`Shared`變數、 屬性、 程序或該類別或結構中定義的事件。 如果執行個體變數用來存取的類別或結構，例如常數或列舉型別，或巢狀的類別或結構的隱含共用的成員，也會發生這個警告。  
  
 共用成員的目的是建立該成員的單一複本，並讓該單一複本使用類別或結構宣告它的每個執行個體。 若要存取此用途與一致`Shared`透過其類別或結構的名稱，而不是透過此變數會保存個別的執行個體，該類別或結構的成員。  
  
 存取`Shared`透過執行個體變數的成員可以讓程式碼更難以了解藉由模糊的成員是事實`Shared`。 此外，如果這類存取權是運算式的一部分，就會執行其他動作，例如`Function`傳回共用成員的執行個體的程序，Visual Basic 會略過的運算式，否則它會執行任何其他動作。  
  
 如需詳細資訊和範例，請參閱 <<c0> [ 共用](../../../visual-basic/language-reference/modifiers/shared.md)。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤 ID:** BC42025  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   使用類別或結構，其定義的名稱`Shared`成員，才能存取它，如下列範例所示。  
  
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
>  兩個程式設計項目具有相同名稱時，請為警示之範圍的效果。 在上述範例中，如果您使用宣告執行個體`Dim testClass as testClass = Nothing`，編譯器會將呼叫`testClass.sayHello()`透過類別名稱，而不發出警告方法存取權的過程。  
  
## <a name="see-also"></a>另請參閱

- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [在 Visual Basic 中的範圍](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
