---
title: "存取共用成員透過執行個體。運算式將不會評估合格 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42025
- BC42025
dev_langs:
- VB
helpviewer_keywords:
- BC42025
ms.assetid: db3337e5-c349-42bf-86df-d9c1e00952a5
caps.latest.revision: 23
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 39be3c95d5acc20afe3a33be9d4db48c09f99a9c
ms.lasthandoff: 03/13/2017

---
# <a name="access-of-shared-member-through-an-instance-qualifying-expression-will-not-be-evaluated"></a>透過執行個體存取共用成員。將不會評估合格的運算式
類別或結構的執行個體變數用來存取`Shared`變數、 屬性、 程序或該類別或結構中定義的事件。 如果執行個體變數用來存取類別或結構，例如常數或列舉型別或巢狀的類別或結構的隱含共用的成員，也會發生這個警告。  
  
 共用成員的用途是建立該成員的單一複本，並使用類別或結構宣告它的每個執行個體的單一複本。 若要存取此用途與一致`Shared`成員透過其類別或結構的名稱，而不是透過保留該類別或結構的個別執行個體的變數。  
  
 存取`Shared`透過執行個體變數的成員可以讓程式碼更難以了解藉由模糊的成員是事實`Shared`。 此外，如果這類存取運算式的一部分，以執行其他動作，例如`Function`傳回共用成員的執行個體的程序[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]會略過的運算式，否則它會執行任何其他動作。  
  
 如需詳細資訊和範例，請參閱[共用](../../../visual-basic/language-reference/modifiers/shared.md)。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告，或將警告視為錯誤的詳細資訊，請參閱[Visual Basic 中的 設定警告](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤識別碼︰** BC42025  
  
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
>  當兩個程式設計項目具有相同的名稱範圍的效果是警示。 在上述範例中，如果您使用宣告執行個體`Dim testClass as testClass = Nothing`，編譯器會將呼叫`testClass.sayHello()`透過類別名稱，並沒有警告的方法存取發生時。  
  
## <a name="see-also"></a>另請參閱  
 [共用](../../../visual-basic/language-reference/modifiers/shared.md)   
 [在 Visual Basic 中的範圍](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
