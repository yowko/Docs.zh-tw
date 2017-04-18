---
title: "Securing Exception Handling | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "code security, exception handling"
  - "security [.NET Framework], exception handling"
  - "secure coding, exception handling"
  - "exception handling, security"
ms.assetid: 1f3da743-9742-47ff-96e6-d0dd1e9e1c19
caps.latest.revision: 10
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 10
---
# Securing Exception Handling
使用 Visual C\+\+ 和 Visual Basic 時，任何 **finally** 陳述式之前都會先執行可提升堆疊的篩選條件運算式。  **finally** 陳述式後面還會執行與該篩選條件關聯的 **catch** 區塊。  如需詳細資訊，請參閱[使用使用者篩選的例外狀況](../../../docs/standard/exceptions/using-user-filtered-exception-handlers.md)。  本章節旨在檢閱這個順序的安全性含意。  請先看看下列說明篩選條件陳述式和 **finally** 陳述式執行順序的虛擬程式碼範例。  
  
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
  
 這個程式碼會列印下列內容。  
  
```  
Throw  
Filter  
Finally  
Catch  
```  
  
 篩選條件會在 **finally** 陳述之前執行，因此使狀態變更的任何物件都可能會引發安全性問題，因為其他程式碼可能會利用這個變更來執行。  例如：  
  
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
  
 這個虛擬程式碼允許篩選條件將堆疊提高，以執行任意程式碼。  類似效果的作業範例還包括其他識別的暫時模擬、設定略過某種安全性檢查的內部旗標，或是變更與執行緒關聯的文化特性 \(Culture\) 等。  建議的解決方法是採用例外狀況處理常式 \(Exception Handler\) 將程式碼中執行緒狀態的變更與呼叫端的篩選條件區塊隔離。  然而，引入例外狀況處理常式的方式必須正確，否則將無法修正這個問題。  以下的範例將切換 UI 文化特性，但同樣地也可能引起執行緒狀態變更的問題。  
  
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
  
 修正這種狀況的正確方法是將現有的 **try**\/**finally** 區塊包裝在 **try**\/**catch** 區塊中。  如以下範例所示，只將 **catch\-throw** 子句引入現有的 **try**\/**finally** 區塊中並不能修正這個問題。  
  
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
  
 這樣並不能修正問題，因為 **finally** 陳述式未在 `FilterFunc` 取得控制之前執行。  
  
 以下的範例則是透過確保 **finally** 子句已先執行，然後才在呼叫端的例外狀況篩選條件區塊上提供例外狀況，以修正問題。  
  
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
  
## 請參閱  
 [Secure Coding Guidelines](../../../docs/standard/security/secure-coding-guidelines.md)