---
title: "設定例外狀況處理的安全性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- cpp
helpviewer_keywords:
- code security, exception handling
- security [.NET Framework], exception handling
- secure coding, exception handling
- exception handling, security
ms.assetid: 1f3da743-9742-47ff-96e6-d0dd1e9e1c19
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 548606a0196012fdd21bf5512e8ea7b089c723ab
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="securing-exception-handling"></a><span data-ttu-id="3c435-102">設定例外狀況處理的安全性</span><span class="sxs-lookup"><span data-stu-id="3c435-102">Securing Exception Handling</span></span>
<span data-ttu-id="3c435-103">在 Visual c + + 和 Visual Basic 中，執行才能進行任何進一步篩選條件運算式堆疊**最後**陳述式。</span><span class="sxs-lookup"><span data-stu-id="3c435-103">In Visual C++ and Visual Basic, a filter expression further up the stack runs before any **finally** statement.</span></span> <span data-ttu-id="3c435-104">**攔截**與相關聯的區塊之後，該篩選條件執行**最後**陳述式。</span><span class="sxs-lookup"><span data-stu-id="3c435-104">The **catch** block associated with that filter runs after the **finally** statement.</span></span> <span data-ttu-id="3c435-105">如需詳細資訊，請參閱[使用使用者篩選例外狀況](../../../docs/standard/exceptions/using-user-filtered-exception-handlers.md)。</span><span class="sxs-lookup"><span data-stu-id="3c435-105">For more information, see [Using User-Filtered Exceptions](../../../docs/standard/exceptions/using-user-filtered-exception-handlers.md).</span></span> <span data-ttu-id="3c435-106">本節會檢查此順序的安全性含意。</span><span class="sxs-lookup"><span data-stu-id="3c435-106">This section examines the security implications of this order.</span></span> <span data-ttu-id="3c435-107">請考慮下列虛擬程式碼範例所說明的篩選陳述式中的順序和**最後**執行的陳述式。</span><span class="sxs-lookup"><span data-stu-id="3c435-107">Consider the following pseudocode example that illustrates the order in which filter statements and **finally** statements run.</span></span>  
  
```cpp  
void Main()   
{  
    try   
    {  
        Sub();  
    }   
    except (Filter())   
    {  
        Console.WriteLine("catch");  
    }  
}  
bool Filter () {  
    Console.WriteLine("filter");  
    return true;  
}  
void Sub()   
{  
    try   
    {  
        Console.WriteLine("throw");  
        throw new Exception();  
    }   
    finally   
    {  
        Console.WriteLine("finally");  
    }  
}                        
```  
  
 <span data-ttu-id="3c435-108">此程式碼會列印下列項目。</span><span class="sxs-lookup"><span data-stu-id="3c435-108">This code prints the following.</span></span>  
  
```  
Throw  
Filter  
Finally  
Catch  
```  
  
 <span data-ttu-id="3c435-109">篩選條件之前執行**最後**陳述式，因此可以使狀態變更的其他程式碼的執行位置無法充分利用的任何項目所導入的安全性問題。</span><span class="sxs-lookup"><span data-stu-id="3c435-109">The filter runs before the **finally** statement, so security issues can be introduced by anything that makes a state change where execution of other code could take advantage.</span></span> <span data-ttu-id="3c435-110">例如: </span><span class="sxs-lookup"><span data-stu-id="3c435-110">For example:</span></span>  
  
```cpp  
try   
{  
    Alter_Security_State();  
    // This means changing anything (state variables,  
    // switching unmanaged context, impersonation, and   
    // so on) that could be exploited if malicious   
    // code ran before state is restored.  
    Do_some_work();  
}   
finally   
{  
    Restore_Security_State();  
    // This simply restores the state change above.  
}  
```  
  
 <span data-ttu-id="3c435-111">此虛擬程式碼可讓篩選器來執行任意程式碼的堆疊。</span><span class="sxs-lookup"><span data-stu-id="3c435-111">This pseudocode allows a filter higher up the stack to run arbitrary code.</span></span> <span data-ttu-id="3c435-112">作業會有類似的效果的其他範例的其他身分識別，將會略過部分安全性檢查，內部旗標設定暫時模擬或變更文化特性與執行緒相關聯。</span><span class="sxs-lookup"><span data-stu-id="3c435-112">Other examples of operations that would have a similar effect are temporary impersonation of another identity, setting an internal flag that bypasses some security check, or changing the culture associated with the thread.</span></span> <span data-ttu-id="3c435-113">建議的解決方案是導入執行緒狀態來隔離的程式碼變更，從呼叫端的篩選條件區塊的例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="3c435-113">The recommended solution is to introduce an exception handler to isolate the code's changes to thread state from callers' filter blocks.</span></span> <span data-ttu-id="3c435-114">不過，很重要的例外狀況處理常式會正確導入，或將不會修正此問題。</span><span class="sxs-lookup"><span data-stu-id="3c435-114">However, it is important that the exception handler be properly introduced or this problem will not be fixed.</span></span> <span data-ttu-id="3c435-115">下列範例會切換的 UI 文化特性，但可以同樣地公開任何種類的執行緒狀態變更。</span><span class="sxs-lookup"><span data-stu-id="3c435-115">The following example switches the UI culture, but any kind of thread state change could be similarly exposed.</span></span>  
  
```cpp  
YourObject.YourMethod()  
{  
   CultureInfo saveCulture = Thread.CurrentThread.CurrentUICulture;  
   try {  
      Thread.CurrentThread.CurrentUICulture = new CultureInfo("de-DE");  
      // Do something that throws an exception.  
}  
   finally {  
      Thread.CurrentThread.CurrentUICulture = saveCulture;  
   }  
}  
```  
  
```vb  
Public Class UserCode  
   Public Shared Sub Main()  
      Try  
         Dim obj As YourObject = new YourObject  
         obj.YourMethod()  
      Catch e As Exception When FilterFunc  
         Console.WriteLine("An error occurred: '{0}'", e)  
         Console.WriteLine("Current Culture: {0}",   
Thread.CurrentThread.CurrentUICulture)  
      End Try  
   End Sub  
  
   Public Function FilterFunc As Boolean  
      Console.WriteLine("Current Culture: {0}", Thread.CurrentThread.CurrentUICulture)  
      Return True  
   End Sub  
  
End Class  
```  
  
 <span data-ttu-id="3c435-116">正確的修正程式在此情況下會包裝現有**再試一次**/**最後**中區塊**再試一次**/**攔截**區塊。</span><span class="sxs-lookup"><span data-stu-id="3c435-116">The correct fix in this case is to wrap the existing **try**/**finally** block in a **try**/**catch** block.</span></span> <span data-ttu-id="3c435-117">只要簡介**catch throw**到現有的子句**再試一次**/**最後**區塊仍無法解決問題，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="3c435-117">Simply introducing a **catch-throw** clause into the existing **try**/**finally** block does not fix the problem, as shown in the following example.</span></span>  
  
```cpp  
YourObject.YourMethod()  
{  
    CultureInfo saveCulture = Thread.CurrentThread.CurrentUICulture;  
  
    try   
    {  
        Thread.CurrentThread.CurrentUICulture = new CultureInfo("de-DE");  
        // Do something that throws an exception.  
    }  
    catch { throw; }  
    finally   
    {  
        Thread.CurrentThread.CurrentUICulture = saveCulture;  
    }  
}  
```  
  
 <span data-ttu-id="3c435-118">這樣無法修正問題，因為**最後**之前尚未執行陳述式`FilterFunc`取得控制項。</span><span class="sxs-lookup"><span data-stu-id="3c435-118">This does not fix the problem because the **finally** statement has not run before the `FilterFunc` gets control.</span></span>  
  
 <span data-ttu-id="3c435-119">下列範例會修正此問題透過確保**最後**子句已先提供例外狀況，呼叫端的例外狀況篩選條件區塊上執行。</span><span class="sxs-lookup"><span data-stu-id="3c435-119">The following example fixes the problem by ensuring that the **finally** clause has executed before offering an exception up the callers' exception filter blocks.</span></span>  
  
```cpp  
YourObject.YourMethod()  
{  
    CultureInfo saveCulture = Thread.CurrentThread.CurrentUICulture;  
    try    
    {  
        try   
        {  
            Thread.CurrentThread.CurrentUICulture = new CultureInfo("de-DE");  
            // Do something that throws an exception.  
        }  
        finally   
        {  
            Thread.CurrentThread.CurrentUICulture = saveCulture;  
        }  
    }  
    catch { throw; }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="3c435-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="3c435-120">See Also</span></span>  
 [<span data-ttu-id="3c435-121">安全程式碼撰寫方針</span><span class="sxs-lookup"><span data-stu-id="3c435-121">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
