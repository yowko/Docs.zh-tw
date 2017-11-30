---
title: "透過執行個體存取共用成員。將不會評估合格的運算式"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42025
- BC42025
helpviewer_keywords: BC42025
ms.assetid: db3337e5-c349-42bf-86df-d9c1e00952a5
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bcf3c37852e73464eec612e9e1d458ca707342e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="access-of-shared-member-through-an-instance-qualifying-expression-will-not-be-evaluated"></a><span data-ttu-id="4c54f-102">透過執行個體存取共用成員。將不會評估合格的運算式</span><span class="sxs-lookup"><span data-stu-id="4c54f-102">Access of shared member through an instance; qualifying expression will not be evaluated</span></span>
<span data-ttu-id="4c54f-103">使用類別或結構的執行個體變數存取`Shared`變數、 屬性、 程序或該類別或結構中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="4c54f-103">An instance variable of a class or structure is used to access a `Shared` variable, property, procedure, or event defined in that class or structure.</span></span> <span data-ttu-id="4c54f-104">如果執行個體變數用來存取的類別或結構，例如常數或列舉型別或巢狀的類別或結構的隱含共用的成員，也會發生這個警告。</span><span class="sxs-lookup"><span data-stu-id="4c54f-104">This warning can also occur if an instance variable is used to access an implicitly shared member of a class or structure, such as a constant or enumeration, or a nested class or structure.</span></span>  
  
 <span data-ttu-id="4c54f-105">共用成員的目的是要建立該成員的單一複本，並將該單一複本提供給類別或結構宣告它的每個執行個體。</span><span class="sxs-lookup"><span data-stu-id="4c54f-105">The purpose of sharing a member is to create only a single copy of that member and make that single copy available to every instance of the class or structure in which it is declared.</span></span> <span data-ttu-id="4c54f-106">它是與存取此用途一致`Shared`成員透過其類別或結構的名稱，而非透過保存該類別或結構的個別執行個體的變數。</span><span class="sxs-lookup"><span data-stu-id="4c54f-106">It is consistent with this purpose to access a `Shared` member through the name of its class or structure, rather than through a variable that holds an individual instance of that class or structure.</span></span>  
  
 <span data-ttu-id="4c54f-107">存取`Shared`透過執行個體變數的成員可讓您的程式碼更難以了解藉由模糊的事實，成員是`Shared`。</span><span class="sxs-lookup"><span data-stu-id="4c54f-107">Accessing a `Shared` member through an instance variable can make your code more difficult to understand by obscuring the fact that the member is `Shared`.</span></span> <span data-ttu-id="4c54f-108">此外，如果這類存取運算式的一部分，以執行其他動作，例如`Function`傳回的共用成員，執行個體的程序[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]會略過的運算式，否則它會執行任何其他動作。</span><span class="sxs-lookup"><span data-stu-id="4c54f-108">Furthermore, if such access is part of an expression that performs other actions, such as a `Function` procedure that returns an instance of the shared member, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] bypasses the expression and any other actions it would otherwise perform.</span></span>  
  
 <span data-ttu-id="4c54f-109">如需詳細資訊和範例，請參閱[共用](../../../visual-basic/language-reference/modifiers/shared.md)。</span><span class="sxs-lookup"><span data-stu-id="4c54f-109">For more information and an example, see [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
 <span data-ttu-id="4c54f-110">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="4c54f-110">By default, this message is a warning.</span></span> <span data-ttu-id="4c54f-111">如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[Visual Basic 中的 設定警告](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="4c54f-111">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="4c54f-112">**錯誤 ID:** BC42025</span><span class="sxs-lookup"><span data-stu-id="4c54f-112">**Error ID:** BC42025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4c54f-113">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="4c54f-113">To correct this error</span></span>  
  
-   <span data-ttu-id="4c54f-114">使用類別或結構，定義的名稱`Shared`成員，才能存取它，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="4c54f-114">Use the name of the class or structure that defines the `Shared` member to access it, as shown in the following example.</span></span>  
  
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
>  <span data-ttu-id="4c54f-115">兩個的程式設計項目具有相同名稱時，為範圍的效果有警示。</span><span class="sxs-lookup"><span data-stu-id="4c54f-115">Be alert for the effects of scope when two programming elements have the same name.</span></span> <span data-ttu-id="4c54f-116">在上述範例中，如果您使用宣告執行個體`Dim testClass as testClass = Nothing`，編譯器會將呼叫`testClass.sayHello()`透過類別名稱，而無警告方法存取權時發生。</span><span class="sxs-lookup"><span data-stu-id="4c54f-116">In the previous example, if you declare an instance by using `Dim testClass as testClass = Nothing`, the compiler treats a call to `testClass.sayHello()` as an access of the method through the class name, and no warning occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c54f-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c54f-117">See Also</span></span>  
 [<span data-ttu-id="4c54f-118">Shared</span><span class="sxs-lookup"><span data-stu-id="4c54f-118">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)  
 [<span data-ttu-id="4c54f-119">在 Visual Basic 中的範圍</span><span class="sxs-lookup"><span data-stu-id="4c54f-119">Scope in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
