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
# <a name="securing-exception-handling"></a>設定例外狀況處理的安全性
在 Visual c + + 和 Visual Basic 中，執行才能進行任何進一步篩選條件運算式堆疊**最後**陳述式。 **攔截**與相關聯的區塊之後，該篩選條件執行**最後**陳述式。 如需詳細資訊，請參閱[使用使用者篩選例外狀況](../../../docs/standard/exceptions/using-user-filtered-exception-handlers.md)。 本節會檢查此順序的安全性含意。 請考慮下列虛擬程式碼範例所說明的篩選陳述式中的順序和**最後**執行的陳述式。  
  
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
  
 此程式碼會列印下列項目。  
  
```  
Throw  
Filter  
Finally  
Catch  
```  
  
 篩選條件之前執行**最後**陳述式，因此可以使狀態變更的其他程式碼的執行位置無法充分利用的任何項目所導入的安全性問題。 例如:   
  
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
  
 此虛擬程式碼可讓篩選器來執行任意程式碼的堆疊。 作業會有類似的效果的其他範例的其他身分識別，將會略過部分安全性檢查，內部旗標設定暫時模擬或變更文化特性與執行緒相關聯。 建議的解決方案是導入執行緒狀態來隔離的程式碼變更，從呼叫端的篩選條件區塊的例外狀況處理常式。 不過，很重要的例外狀況處理常式會正確導入，或將不會修正此問題。 下列範例會切換的 UI 文化特性，但可以同樣地公開任何種類的執行緒狀態變更。  
  
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
  
 正確的修正程式在此情況下會包裝現有**再試一次**/**最後**中區塊**再試一次**/**攔截**區塊。 只要簡介**catch throw**到現有的子句**再試一次**/**最後**區塊仍無法解決問題，如下列範例所示。  
  
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
  
 這樣無法修正問題，因為**最後**之前尚未執行陳述式`FilterFunc`取得控制項。  
  
 下列範例會修正此問題透過確保**最後**子句已先提供例外狀況，呼叫端的例外狀況篩選條件區塊上執行。  
  
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
  
## <a name="see-also"></a>請參閱  
 [安全程式碼撰寫方針](../../../docs/standard/security/secure-coding-guidelines.md)
