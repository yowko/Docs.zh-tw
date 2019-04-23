---
title: 設定例外狀況處理的安全性
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- code security, exception handling
- security [.NET Framework], exception handling
- secure coding, exception handling
- exception handling, security
ms.assetid: 1f3da743-9742-47ff-96e6-d0dd1e9e1c19
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bc8cd20a4183ffd002f1399b6b50c8956208a21b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59173667"
---
# <a name="securing-exception-handling"></a><span data-ttu-id="99556-102">設定例外狀況處理的安全性</span><span class="sxs-lookup"><span data-stu-id="99556-102">Securing Exception Handling</span></span>
<span data-ttu-id="99556-103">在視覺效果C++和 Visual Basic 中，執行任何之前的堆疊中往上的進一步篩選條件運算式**最後**陳述式。</span><span class="sxs-lookup"><span data-stu-id="99556-103">In Visual C++ and Visual Basic, a filter expression further up the stack runs before any **finally** statement.</span></span> <span data-ttu-id="99556-104">**攔截**相關聯的區塊之後執行的該篩選條件**最後**陳述式。</span><span class="sxs-lookup"><span data-stu-id="99556-104">The **catch** block associated with that filter runs after the **finally** statement.</span></span> <span data-ttu-id="99556-105">如需詳細資訊，請參閱 <<c0> [ 使用使用者篩選例外狀況](../../../docs/standard/exceptions/using-user-filtered-exception-handlers.md)。</span><span class="sxs-lookup"><span data-stu-id="99556-105">For more information, see [Using User-Filtered Exceptions](../../../docs/standard/exceptions/using-user-filtered-exception-handlers.md).</span></span> <span data-ttu-id="99556-106">本節將探討此順序的安全性含意。</span><span class="sxs-lookup"><span data-stu-id="99556-106">This section examines the security implications of this order.</span></span> <span data-ttu-id="99556-107">請考慮下列虛擬程式碼範例說明中的篩選陳述式的順序並**最後**執行的陳述式。</span><span class="sxs-lookup"><span data-stu-id="99556-107">Consider the following pseudocode example that illustrates the order in which filter statements and **finally** statements run.</span></span>  
  
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
  
 <span data-ttu-id="99556-108">此程式碼會列印下列內容。</span><span class="sxs-lookup"><span data-stu-id="99556-108">This code prints the following.</span></span>  
  
```  
Throw  
Filter  
Finally  
Catch  
```  
  
 <span data-ttu-id="99556-109">篩選條件之前執行**最後**陳述式，所以安全性問題會造成任何項目會變更其中執行的其他程式碼無法充分利用的狀態。</span><span class="sxs-lookup"><span data-stu-id="99556-109">The filter runs before the **finally** statement, so security issues can be introduced by anything that makes a state change where execution of other code could take advantage.</span></span> <span data-ttu-id="99556-110">例如：</span><span class="sxs-lookup"><span data-stu-id="99556-110">For example:</span></span>  
  
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
  
 <span data-ttu-id="99556-111">此虛擬程式碼可讓執行任意程式碼堆疊中較高的篩選。</span><span class="sxs-lookup"><span data-stu-id="99556-111">This pseudocode allows a filter higher up the stack to run arbitrary code.</span></span> <span data-ttu-id="99556-112">會有類似的效果的作業的其他範例的另一個身分識別，將會略過部分安全性檢查，內部旗標設定暫時模擬或變更文化特性相關聯的執行緒。</span><span class="sxs-lookup"><span data-stu-id="99556-112">Other examples of operations that would have a similar effect are temporary impersonation of another identity, setting an internal flag that bypasses some security check, or changing the culture associated with the thread.</span></span> <span data-ttu-id="99556-113">建議的解決方案是引入隔離執行緒狀態的程式碼的變更，從呼叫端的篩選器區塊的例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="99556-113">The recommended solution is to introduce an exception handler to isolate the code's changes to thread state from callers' filter blocks.</span></span> <span data-ttu-id="99556-114">不過，很重要的例外狀況處理常式會適當地導入，或將不會修正此問題。</span><span class="sxs-lookup"><span data-stu-id="99556-114">However, it is important that the exception handler be properly introduced or this problem will not be fixed.</span></span> <span data-ttu-id="99556-115">下列範例會切換的 UI 文化特性，但可能會同樣地公開所有種類的執行緒狀態變更。</span><span class="sxs-lookup"><span data-stu-id="99556-115">The following example switches the UI culture, but any kind of thread state change could be similarly exposed.</span></span>  
  
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
  
 <span data-ttu-id="99556-116">正確的修正方法在此情況下是包裝現有**嘗試**/**最後**中的區塊**試**/**攔截**區塊。</span><span class="sxs-lookup"><span data-stu-id="99556-116">The correct fix in this case is to wrap the existing **try**/**finally** block in a **try**/**catch** block.</span></span> <span data-ttu-id="99556-117">只要簡介**catch throw**至現有的子句**嘗試**/**最後**區塊無法解決此問題，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="99556-117">Simply introducing a **catch-throw** clause into the existing **try**/**finally** block does not fix the problem, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="99556-118">這樣無法修正問題，因為**最後**之前尚未執行陳述式`FilterFunc`取得控制項。</span><span class="sxs-lookup"><span data-stu-id="99556-118">This does not fix the problem because the **finally** statement has not run before the `FilterFunc` gets control.</span></span>  
  
 <span data-ttu-id="99556-119">下列範例可以修正問題，確保**最後**子句執行之前供應項目呼叫端的例外狀況篩選器區塊，例外狀況。</span><span class="sxs-lookup"><span data-stu-id="99556-119">The following example fixes the problem by ensuring that the **finally** clause has executed before offering an exception up the callers' exception filter blocks.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="99556-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99556-120">See also</span></span>

- [<span data-ttu-id="99556-121">安全程式碼撰寫方針</span><span class="sxs-lookup"><span data-stu-id="99556-121">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
