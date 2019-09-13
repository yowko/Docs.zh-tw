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
# <a name="securing-exception-handling"></a>設定例外狀況處理的安全性
在 Visual C++和 Visual Basic 中，堆疊進一步的篩選運算式會在任何**finally**語句之前執行。 與該篩選相關聯的**catch**區塊會在**finally**語句之後執行。 如需詳細資訊，請參閱[使用使用者篩選的例外](../../standard/exceptions/using-user-filtered-exception-handlers.md)狀況。 本節將探討此順序的安全性含意。 請考慮下列可說明篩選語句和**finally**語句執行順序的虛擬程式碼範例。  
  
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
  
 此程式碼會列印下列各項。  
  
```output
Throw  
Filter  
Finally  
Catch  
```  
  
 此篩選準則會在**finally**語句之前執行，因此在執行其他程式碼時，可能會造成狀態變更的任何專案引進安全性問題。 例如：  
  
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
  
 這個虛擬程式可讓篩選準則更高堆疊，以執行任意程式碼。 其他會有類似效果的作業範例是暫時模擬另一個身分識別、設定略過部分安全性檢查的內部旗標，或變更與執行緒相關聯的文化特性。 建議的解決方法是引進例外狀況處理常式，以將程式碼的變更與呼叫端的篩選區塊隔離線上程狀態。 不過，請務必適當地引進例外狀況處理常式，否則將不會修正此問題。 下列範例會切換 UI 文化特性，但任何一種執行緒狀態變更都可能類似地公開。  
  
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
  
 在此情況下，正確的修正方法是在**try** / **catch**區塊中包裝現有的**try** / **finally**區塊。 簡單地將**catch throw**子句引進現有的**try** / **finally**區塊，並不會修正問題，如下列範例所示。  
  
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
  
 這不會修正問題，因為**finally**語句尚未在`FilterFunc`取得控制項之前執行。  
  
 下列範例會藉由確保**finally**子句在提供呼叫端例外狀況篩選區塊的例外狀況之前先執行，以修正問題。  
  
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
