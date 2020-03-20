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
ms.openlocfilehash: ad27e62197f6fdaa6b5e706f4ae02c03fecae9f1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181143"
---
# <a name="securing-exception-handling"></a>設定例外狀況處理的安全性
在 Visual C++ 和 Visual Basic 中，進一步向上堆疊的篩選器運算式在任何**最終**語句之前運行。 與該篩選器關聯的**catch**塊在**最終**語句之後運行。 有關詳細資訊，請參閱[使用使用者篩選的異常](../../standard/exceptions/using-user-filtered-exception-handlers.md)。 本節將檢查此訂單的安全影響。 請考慮以下偽代碼示例，該示例說明了篩選器語句**和最後語句**的運行順序。  
  
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
  
 此代碼列印以下內容。  
  
```output
Throw  
Filter  
Finally  
Catch  
```  
  
 篩選器在**最終**語句之前運行，因此任何進行狀態更改都可以引入安全問題，從而可以利用其他代碼的執行。 例如：  
  
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
  
 此偽代碼允許堆疊上較高的篩選器運行任意代碼。 具有類似效果的其他操作示例包括臨時類比另一個標識、設置繞過某些安全檢查的內部標誌或更改與執行緒關聯的區域性。 建議的解決方案是引入一個例外處理常式，以將代碼對執行緒狀態的更改與調用方的篩選器塊隔離開來。 但是，正確引入例外處理常式或無法解決此問題非常重要。 下面的示例切換 UI 區域性，但任何類型的執行緒狀態更改可能同樣公開。  
  
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
  
 在這種情況下，正確的解決方法是在**try**/**catch**塊中包裝現有**try**/**finally**塊。 簡單地將**catch-throw**子句引入到現有**try**/**finally**塊中並不能解決問題，如下例所示。  
  
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
  
 這不能解決問題，因為**finally**語句在`FilterFunc`獲取控制項之前未運行。  
  
 下面的示例通過在提供調用方的異常篩選器塊的異常之前已執行**最終**子句來解決此問題。  
  
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

- [安全程式碼撰寫方針](../../standard/security/secure-coding-guidelines.md)
