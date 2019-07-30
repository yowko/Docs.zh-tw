---
title: HOW TO：叫用委派方法 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: b56866ae-abf9-4a5a-a855-486359455e9c
ms.openlocfilehash: c2bdb65c9d060e854db3319e4aa5b2e93b9681af
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629584"
---
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a><span data-ttu-id="f0b78-102">作法：叫用委派方法 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f0b78-102">How to: Invoke a Delegate Method (Visual Basic)</span></span>

<span data-ttu-id="f0b78-103">這個範例示範如何將方法與委派產生關聯, 然後透過委派叫用該方法。</span><span class="sxs-lookup"><span data-stu-id="f0b78-103">This example shows how to associate a method with a delegate and then invoke that method through the delegate.</span></span>

### <a name="create-the-delegate-and-matching-procedures"></a><span data-ttu-id="f0b78-104">建立委派和比對程式</span><span class="sxs-lookup"><span data-stu-id="f0b78-104">Create the delegate and matching procedures</span></span>

1. <span data-ttu-id="f0b78-105">建立名為`MySubDelegate`的委派。</span><span class="sxs-lookup"><span data-stu-id="f0b78-105">Create a delegate named `MySubDelegate`.</span></span>

    ```vb
    Delegate Sub MySubDelegate(ByVal x As Integer)
    ```

2. <span data-ttu-id="f0b78-106">宣告一個類別, 其中包含具有與委派相同簽章的方法。</span><span class="sxs-lookup"><span data-stu-id="f0b78-106">Declare a class that contains a method with the same signature as the delegate.</span></span>

    ```vb
    Class class1
        Sub Sub1(ByVal x As Integer)
            MsgBox("The value of x is: " & CStr(x))
        End Sub
    End Class
    ```

3. <span data-ttu-id="f0b78-107">定義方法, 以建立委派的實例, 並藉由呼叫內`Invoke`建方法來叫用與委派相關聯的方法。</span><span class="sxs-lookup"><span data-stu-id="f0b78-107">Define a method that creates an instance of the delegate and invokes the method associated with the delegate by calling the built-in `Invoke` method.</span></span>

    ```vb
    Protected Sub DelegateTest()
        Dim c1 As New class1
        ' Create an instance of the delegate.
        Dim msd As MySubDelegate = AddressOf c1.Sub1
        ' Call the method.
        msd.Invoke(10)
    End Sub
    ```

## <a name="see-also"></a><span data-ttu-id="f0b78-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f0b78-108">See also</span></span>

- [<span data-ttu-id="f0b78-109">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="f0b78-109">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="f0b78-110">委派</span><span class="sxs-lookup"><span data-stu-id="f0b78-110">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="f0b78-111">事件</span><span class="sxs-lookup"><span data-stu-id="f0b78-111">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [<span data-ttu-id="f0b78-112">多執行緒應用程式</span><span class="sxs-lookup"><span data-stu-id="f0b78-112">Multithreaded Applications</span></span>](../../../../standard/threading/using-threads-and-threading.md)
