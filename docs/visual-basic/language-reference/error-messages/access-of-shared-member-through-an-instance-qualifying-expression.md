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
# <a name="access-of-shared-member-through-an-instance-qualifying-expression-will-not-be-evaluated"></a><span data-ttu-id="9ac08-102">透過執行個體存取共用成員。將不會評估合格的運算式</span><span class="sxs-lookup"><span data-stu-id="9ac08-102">Access of shared member through an instance; qualifying expression will not be evaluated</span></span>
<span data-ttu-id="9ac08-103">使用類別或結構的執行個體變數存取`Shared`變數、 屬性、 程序或該類別或結構中定義的事件。</span><span class="sxs-lookup"><span data-stu-id="9ac08-103">An instance variable of a class or structure is used to access a `Shared` variable, property, procedure, or event defined in that class or structure.</span></span> <span data-ttu-id="9ac08-104">如果執行個體變數用來存取的類別或結構，例如常數或列舉型別，或巢狀的類別或結構的隱含共用的成員，也會發生這個警告。</span><span class="sxs-lookup"><span data-stu-id="9ac08-104">This warning can also occur if an instance variable is used to access an implicitly shared member of a class or structure, such as a constant or enumeration, or a nested class or structure.</span></span>  
  
 <span data-ttu-id="9ac08-105">共用成員的目的是建立該成員的單一複本，並讓該單一複本使用類別或結構宣告它的每個執行個體。</span><span class="sxs-lookup"><span data-stu-id="9ac08-105">The purpose of sharing a member is to create only a single copy of that member and make that single copy available to every instance of the class or structure in which it is declared.</span></span> <span data-ttu-id="9ac08-106">若要存取此用途與一致`Shared`透過其類別或結構的名稱，而不是透過此變數會保存個別的執行個體，該類別或結構的成員。</span><span class="sxs-lookup"><span data-stu-id="9ac08-106">It is consistent with this purpose to access a `Shared` member through the name of its class or structure, rather than through a variable that holds an individual instance of that class or structure.</span></span>  
  
 <span data-ttu-id="9ac08-107">存取`Shared`透過執行個體變數的成員可以讓程式碼更難以了解藉由模糊的成員是事實`Shared`。</span><span class="sxs-lookup"><span data-stu-id="9ac08-107">Accessing a `Shared` member through an instance variable can make your code more difficult to understand by obscuring the fact that the member is `Shared`.</span></span> <span data-ttu-id="9ac08-108">此外，如果這類存取權是運算式的一部分，就會執行其他動作，例如`Function`傳回共用成員的執行個體的程序，Visual Basic 會略過的運算式，否則它會執行任何其他動作。</span><span class="sxs-lookup"><span data-stu-id="9ac08-108">Furthermore, if such access is part of an expression that performs other actions, such as a `Function` procedure that returns an instance of the shared member, Visual Basic bypasses the expression and any other actions it would otherwise perform.</span></span>  
  
 <span data-ttu-id="9ac08-109">如需詳細資訊和範例，請參閱 <<c0> [ 共用](../../../visual-basic/language-reference/modifiers/shared.md)。</span><span class="sxs-lookup"><span data-stu-id="9ac08-109">For more information and an example, see [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
 <span data-ttu-id="9ac08-110">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="9ac08-110">By default, this message is a warning.</span></span> <span data-ttu-id="9ac08-111">如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="9ac08-111">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="9ac08-112">**錯誤 ID:** BC42025</span><span class="sxs-lookup"><span data-stu-id="9ac08-112">**Error ID:** BC42025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9ac08-113">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="9ac08-113">To correct this error</span></span>  
  
-   <span data-ttu-id="9ac08-114">使用類別或結構，其定義的名稱`Shared`成員，才能存取它，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="9ac08-114">Use the name of the class or structure that defines the `Shared` member to access it, as shown in the following example.</span></span>  
  
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
>  <span data-ttu-id="9ac08-115">兩個程式設計項目具有相同名稱時，請為警示之範圍的效果。</span><span class="sxs-lookup"><span data-stu-id="9ac08-115">Be alert for the effects of scope when two programming elements have the same name.</span></span> <span data-ttu-id="9ac08-116">在上述範例中，如果您使用宣告執行個體`Dim testClass as testClass = Nothing`，編譯器會將呼叫`testClass.sayHello()`透過類別名稱，而不發出警告方法存取權的過程。</span><span class="sxs-lookup"><span data-stu-id="9ac08-116">In the previous example, if you declare an instance by using `Dim testClass as testClass = Nothing`, the compiler treats a call to `testClass.sayHello()` as an access of the method through the class name, and no warning occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ac08-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ac08-117">See also</span></span>

- [<span data-ttu-id="9ac08-118">Shared</span><span class="sxs-lookup"><span data-stu-id="9ac08-118">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="9ac08-119">在 Visual Basic 中的範圍</span><span class="sxs-lookup"><span data-stu-id="9ac08-119">Scope in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
