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
# <a name="access-of-shared-member-through-an-instance-qualifying-expression-will-not-be-evaluated"></a><span data-ttu-id="83f91-102">透過執行個體存取共用成員。將不會評估合格的運算式</span><span class="sxs-lookup"><span data-stu-id="83f91-102">Access of shared member through an instance; qualifying expression will not be evaluated</span></span>
<span data-ttu-id="83f91-103">類別或結構的執行個體變數是用來存取`Shared`該類別或結構中定義的變數、屬性、程式或事件。</span><span class="sxs-lookup"><span data-stu-id="83f91-103">An instance variable of a class or structure is used to access a `Shared` variable, property, procedure, or event defined in that class or structure.</span></span> <span data-ttu-id="83f91-104">如果執行個體變數是用來存取類別或結構的隱含共用成員, 例如常數或列舉, 或是嵌套的類別或結構, 也可能會發生此警告。</span><span class="sxs-lookup"><span data-stu-id="83f91-104">This warning can also occur if an instance variable is used to access an implicitly shared member of a class or structure, such as a constant or enumeration, or a nested class or structure.</span></span>  
  
 <span data-ttu-id="83f91-105">共用成員的目的是只建立該成員的單一複本, 並將該單一複本提供給其宣告所在類別或結構的每個實例使用。</span><span class="sxs-lookup"><span data-stu-id="83f91-105">The purpose of sharing a member is to create only a single copy of that member and make that single copy available to every instance of the class or structure in which it is declared.</span></span> <span data-ttu-id="83f91-106">它會與此用途一致, 以透過`Shared`其類別或結構的名稱存取成員, 而不是透過保存該類別或結構之個別實例的變數。</span><span class="sxs-lookup"><span data-stu-id="83f91-106">It is consistent with this purpose to access a `Shared` member through the name of its class or structure, rather than through a variable that holds an individual instance of that class or structure.</span></span>  
  
 <span data-ttu-id="83f91-107">透過執行個體變數存取`Shared`成員,可以藉由遮蔽成員的事實,讓您的程式碼更容易瞭解。`Shared`</span><span class="sxs-lookup"><span data-stu-id="83f91-107">Accessing a `Shared` member through an instance variable can make your code more difficult to understand by obscuring the fact that the member is `Shared`.</span></span> <span data-ttu-id="83f91-108">此外, 如果這類存取是執行其他動作之運算式的一部分, 例如`Function`會傳回共用成員實例的程式, Visual Basic 會略過運算式, 以及其他任何會執行的動作。</span><span class="sxs-lookup"><span data-stu-id="83f91-108">Furthermore, if such access is part of an expression that performs other actions, such as a `Function` procedure that returns an instance of the shared member, Visual Basic bypasses the expression and any other actions it would otherwise perform.</span></span>  
  
 <span data-ttu-id="83f91-109">如需詳細資訊和範例, 請參閱[Shared](../../../visual-basic/language-reference/modifiers/shared.md)。</span><span class="sxs-lookup"><span data-stu-id="83f91-109">For more information and an example, see [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
 <span data-ttu-id="83f91-110">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="83f91-110">By default, this message is a warning.</span></span> <span data-ttu-id="83f91-111">如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="83f91-111">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="83f91-112">**錯誤識別碼:** BC42025</span><span class="sxs-lookup"><span data-stu-id="83f91-112">**Error ID:** BC42025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="83f91-113">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="83f91-113">To correct this error</span></span>  
  
- <span data-ttu-id="83f91-114">使用定義`Shared`要存取之成員的類別或結構的名稱, 如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="83f91-114">Use the name of the class or structure that defines the `Shared` member to access it, as shown in the following example.</span></span>  
  
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
> <span data-ttu-id="83f91-115">當兩個程式設計項目具有相同的名稱時, 請警示範圍的效果。</span><span class="sxs-lookup"><span data-stu-id="83f91-115">Be alert for the effects of scope when two programming elements have the same name.</span></span> <span data-ttu-id="83f91-116">在上述範例中, 如果您使用`Dim testClass as testClass = Nothing`來宣告實例, 編譯器會透過類別名稱將`testClass.sayHello()`呼叫視為方法的存取, 而不會發生警告。</span><span class="sxs-lookup"><span data-stu-id="83f91-116">In the previous example, if you declare an instance by using `Dim testClass as testClass = Nothing`, the compiler treats a call to `testClass.sayHello()` as an access of the method through the class name, and no warning occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83f91-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83f91-117">See also</span></span>

- [<span data-ttu-id="83f91-118">Shared</span><span class="sxs-lookup"><span data-stu-id="83f91-118">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="83f91-119">Visual Basic 中的範圍</span><span class="sxs-lookup"><span data-stu-id="83f91-119">Scope in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
