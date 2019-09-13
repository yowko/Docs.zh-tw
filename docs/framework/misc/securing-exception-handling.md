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
ms.openlocfilehash: 256d9c9b825081e3bcfafd6e0e09de825d046d20
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894552"
---
# <a name="securing-exception-handling"></a><span data-ttu-id="d8bfe-102">設定例外狀況處理的安全性</span><span class="sxs-lookup"><span data-stu-id="d8bfe-102">Securing Exception Handling</span></span>
<span data-ttu-id="d8bfe-103">在 Visual C++和 Visual Basic 中，堆疊進一步的篩選運算式會在任何**finally**語句之前執行。</span><span class="sxs-lookup"><span data-stu-id="d8bfe-103">In Visual C++ and Visual Basic, a filter expression further up the stack runs before any **finally** statement.</span></span> <span data-ttu-id="d8bfe-104">與該篩選相關聯的**catch**區塊會在**finally**語句之後執行。</span><span class="sxs-lookup"><span data-stu-id="d8bfe-104">The **catch** block associated with that filter runs after the **finally** statement.</span></span> <span data-ttu-id="d8bfe-105">如需詳細資訊，請參閱[使用使用者篩選的例外](../../standard/exceptions/using-user-filtered-exception-handlers.md)狀況。</span><span class="sxs-lookup"><span data-stu-id="d8bfe-105">For more information, see [Using User-Filtered Exceptions](../../standard/exceptions/using-user-filtered-exception-handlers.md).</span></span> <span data-ttu-id="d8bfe-106">本節將探討此順序的安全性含意。</span><span class="sxs-lookup"><span data-stu-id="d8bfe-106">This section examines the security implications of this order.</span></span> <span data-ttu-id="d8bfe-107">請考慮下列可說明篩選語句和**finally**語句執行順序的虛擬程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="d8bfe-107">Consider the following pseudocode example that illustrates the order in which filter statements and **finally** statements run.</span></span>  
  
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
  
 <span data-ttu-id="d8bfe-108">此程式碼會列印下列各項。</span><span class="sxs-lookup"><span data-stu-id="d8bfe-108">This code prints the following.</span></span>  
  
```output
Throw  
Filter  
Finally  
Catch  
```  
  
 <span data-ttu-id="d8bfe-109">此篩選準則會在**finally**語句之前執行，因此在執行其他程式碼時，可能會造成狀態變更的任何專案引進安全性問題。</span><span class="sxs-lookup"><span data-stu-id="d8bfe-109">The filter runs before the **finally** statement, so security issues can be introduced by anything that makes a state change where execution of other code could take advantage.</span></span> <span data-ttu-id="d8bfe-110">例如：</span><span class="sxs-lookup"><span data-stu-id="d8bfe-110">For example:</span></span>  
  
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
  
 <span data-ttu-id="d8bfe-111">這個虛擬程式可讓篩選準則更高堆疊，以執行任意程式碼。</span><span class="sxs-lookup"><span data-stu-id="d8bfe-111">This pseudocode allows a filter higher up the stack to run arbitrary code.</span></span> <span data-ttu-id="d8bfe-112">其他會有類似效果的作業範例是暫時模擬另一個身分識別、設定略過部分安全性檢查的內部旗標，或變更與執行緒相關聯的文化特性。</span><span class="sxs-lookup"><span data-stu-id="d8bfe-112">Other examples of operations that would have a similar effect are temporary impersonation of another identity, setting an internal flag that bypasses some security check, or changing the culture associated with the thread.</span></span> <span data-ttu-id="d8bfe-113">建議的解決方法是引進例外狀況處理常式，以將程式碼的變更與呼叫端的篩選區塊隔離線上程狀態。</span><span class="sxs-lookup"><span data-stu-id="d8bfe-113">The recommended solution is to introduce an exception handler to isolate the code's changes to thread state from callers' filter blocks.</span></span> <span data-ttu-id="d8bfe-114">不過，請務必適當地引進例外狀況處理常式，否則將不會修正此問題。</span><span class="sxs-lookup"><span data-stu-id="d8bfe-114">However, it is important that the exception handler be properly introduced or this problem will not be fixed.</span></span> <span data-ttu-id="d8bfe-115">下列範例會切換 UI 文化特性，但任何一種執行緒狀態變更都可能類似地公開。</span><span class="sxs-lookup"><span data-stu-id="d8bfe-115">The following example switches the UI culture, but any kind of thread state change could be similarly exposed.</span></span>  
  
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
  
 <span data-ttu-id="d8bfe-116">在此情況下，正確的修正方法是在**try** / **catch**區塊中包裝現有的**try** / **finally**區塊。</span><span class="sxs-lookup"><span data-stu-id="d8bfe-116">The correct fix in this case is to wrap the existing **try**/**finally** block in a **try**/**catch** block.</span></span> <span data-ttu-id="d8bfe-117">簡單地將**catch throw**子句引進現有的**try** / **finally**區塊，並不會修正問題，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="d8bfe-117">Simply introducing a **catch-throw** clause into the existing **try**/**finally** block does not fix the problem, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="d8bfe-118">這不會修正問題，因為**finally**語句尚未在`FilterFunc`取得控制項之前執行。</span><span class="sxs-lookup"><span data-stu-id="d8bfe-118">This does not fix the problem because the **finally** statement has not run before the `FilterFunc` gets control.</span></span>  
  
 <span data-ttu-id="d8bfe-119">下列範例會藉由確保**finally**子句在提供呼叫端例外狀況篩選區塊的例外狀況之前先執行，以修正問題。</span><span class="sxs-lookup"><span data-stu-id="d8bfe-119">The following example fixes the problem by ensuring that the **finally** clause has executed before offering an exception up the callers' exception filter blocks.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d8bfe-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8bfe-120">See also</span></span>

- [<span data-ttu-id="d8bfe-121">安全程式碼撰寫方針</span><span class="sxs-lookup"><span data-stu-id="d8bfe-121">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
