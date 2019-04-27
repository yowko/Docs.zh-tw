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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61868794"
---
# <a name="securing-exception-handling"></a>設定例外狀況處理的安全性
在視覺效果C++和 Visual Basic 中，執行任何之前的堆疊中往上的進一步篩選條件運算式**最後**陳述式。 **攔截**相關聯的區塊之後執行的該篩選條件**最後**陳述式。 如需詳細資訊，請參閱 <<c0> [ 使用使用者篩選例外狀況](../../../docs/standard/exceptions/using-user-filtered-exception-handlers.md)。 本節將探討此順序的安全性含意。 請考慮下列虛擬程式碼範例說明中的篩選陳述式的順序並**最後**執行的陳述式。  
  
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
  
 此程式碼會列印下列內容。  
  
```  
Throw  
Filter  
Finally  
Catch  
```  
  
 篩選條件之前執行**最後**陳述式，所以安全性問題會造成任何項目會變更其中執行的其他程式碼無法充分利用的狀態。 例如:   
  
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
  
 此虛擬程式碼可讓執行任意程式碼堆疊中較高的篩選。 會有類似的效果的作業的其他範例的另一個身分識別，將會略過部分安全性檢查，內部旗標設定暫時模擬或變更文化特性相關聯的執行緒。 建議的解決方案是引入隔離執行緒狀態的程式碼的變更，從呼叫端的篩選器區塊的例外狀況處理常式。 不過，很重要的例外狀況處理常式會適當地導入，或將不會修正此問題。 下列範例會切換的 UI 文化特性，但可能會同樣地公開所有種類的執行緒狀態變更。  
  
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
  
 正確的修正方法在此情況下是包裝現有**嘗試**/**最後**中的區塊**試**/**攔截**區塊。 只要簡介**catch throw**至現有的子句**嘗試**/**最後**區塊無法解決此問題，如下列範例所示。  
  
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
  
 下列範例可以修正問題，確保**最後**子句執行之前供應項目呼叫端的例外狀況篩選器區塊，例外狀況。  
  
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
  
## <a name="see-also"></a>另請參閱

- [安全程式碼撰寫方針](../../../docs/standard/security/secure-coding-guidelines.md)
