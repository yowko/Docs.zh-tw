---
title: 透過執行個體存取共用成員。將不會評估合格的運算式
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42025
- BC42025
helpviewer_keywords:
- BC42025
ms.assetid: db3337e5-c349-42bf-86df-d9c1e00952a5
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bcf3c37852e73464eec612e9e1d458ca707342e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="access-of-shared-member-through-an-instance-qualifying-expression-will-not-be-evaluated"></a>透過執行個體存取共用成員。將不會評估合格的運算式
使用類別或結構的執行個體變數存取`Shared`變數、 屬性、 程序或該類別或結構中定義的事件。 如果執行個體變數用來存取的類別或結構，例如常數或列舉型別或巢狀的類別或結構的隱含共用的成員，也會發生這個警告。  
  
 共用成員的目的是要建立該成員的單一複本，並將該單一複本提供給類別或結構宣告它的每個執行個體。 它是與存取此用途一致`Shared`成員透過其類別或結構的名稱，而非透過保存該類別或結構的個別執行個體的變數。  
  
 存取`Shared`透過執行個體變數的成員可讓您的程式碼更難以了解藉由模糊的事實，成員是`Shared`。 此外，如果這類存取運算式的一部分，以執行其他動作，例如`Function`傳回的共用成員，執行個體的程序[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]會略過的運算式，否則它會執行任何其他動作。  
  
 如需詳細資訊和範例，請參閱[共用](../../../visual-basic/language-reference/modifiers/shared.md)。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[Visual Basic 中的 設定警告](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤 ID:** BC42025  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   使用類別或結構，定義的名稱`Shared`成員，才能存取它，如下列範例所示。  
  
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
>  兩個的程式設計項目具有相同名稱時，為範圍的效果有警示。 在上述範例中，如果您使用宣告執行個體`Dim testClass as testClass = Nothing`，編譯器會將呼叫`testClass.sayHello()`透過類別名稱，而無警告方法存取權時發生。  
  
## <a name="see-also"></a>另請參閱  
 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)  
 [在 Visual Basic 中的範圍](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
