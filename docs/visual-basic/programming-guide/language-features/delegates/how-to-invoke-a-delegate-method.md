---
title: 如何：叫用委派方法 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: b56866ae-abf9-4a5a-a855-486359455e9c
ms.openlocfilehash: c50a32d300aaf52efe0c55cef69d5793a98305ac
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44129205"
---
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a><span data-ttu-id="e8376-102">如何：叫用委派方法 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e8376-102">How to: Invoke a Delegate Method (Visual Basic)</span></span>
<span data-ttu-id="e8376-103">此範例示範如何將方法產生關聯的委派，然後叫用該方法，透過委派。</span><span class="sxs-lookup"><span data-stu-id="e8376-103">This example shows how to associate a method with a delegate and then invoke that method through the delegate.</span></span>  
  
### <a name="create-the-delegate-and-matching-procedures"></a><span data-ttu-id="e8376-104">建立委派和比對程序</span><span class="sxs-lookup"><span data-stu-id="e8376-104">Create the delegate and matching procedures</span></span>  
  
1.  <span data-ttu-id="e8376-105">建立名為委派`MySubDelegate`。</span><span class="sxs-lookup"><span data-stu-id="e8376-105">Create a delegate named `MySubDelegate`.</span></span>  
  
    ```  
    Delegate Sub MySubDelegate(ByVal x As Integer)  
    ```  
  
2.  <span data-ttu-id="e8376-106">宣告類別，其中包含具有相同的簽章與委派的方法。</span><span class="sxs-lookup"><span data-stu-id="e8376-106">Declare a class that contains a method with the same signature as the delegate.</span></span>  
  
    ```  
    Class class1  
        Sub Sub1(ByVal x As Integer)  
            MsgBox("The value of x is: " & CStr(x))  
        End Sub  
    End Class  
    ```  
  
3.  <span data-ttu-id="e8376-107">定義方法，以建立委派的執行個體，並叫用方法和委派呼叫內建關聯`Invoke`方法。</span><span class="sxs-lookup"><span data-stu-id="e8376-107">Define a method that creates an instance of the delegate and invokes the method associated with the delegate by calling the built-in `Invoke` method.</span></span>  
  
    ```  
    Protected Sub DelegateTest()  
        Dim c1 As New class1  
        ' Create an instance of the delegate.  
        Dim msd As MySubDelegate = AddressOf c1.Sub1  
        ' Call the method.  
        msd.Invoke(10)  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e8376-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8376-108">See also</span></span>

- [<span data-ttu-id="e8376-109">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="e8376-109">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)  
- [<span data-ttu-id="e8376-110">委派</span><span class="sxs-lookup"><span data-stu-id="e8376-110">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
- [<span data-ttu-id="e8376-111">事件</span><span class="sxs-lookup"><span data-stu-id="e8376-111">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)  
- [<span data-ttu-id="e8376-112">多執行緒應用程式</span><span class="sxs-lookup"><span data-stu-id="e8376-112">Multithreaded Applications</span></span>](../../../../standard/threading/using-threads-and-threading.md)
