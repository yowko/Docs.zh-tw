---
title: "如何：攔截非 CLS 例外狀況 | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "例外狀況 [C#], 非 CLS"
ms.assetid: db4630b3-5240-471a-b3a7-c7ff6ab31e8d
caps.latest.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 8
---
# 如何：攔截非 CLS 例外狀況
某些 .NET 語言 \(包括 C\+\+\/CLI\) 可讓物件擲回不是衍生自 <xref:System.Exception> 的例外狀況 \(Exception\)，  這類例外狀況稱為「*非 CLS 的例外狀況*」\(Non\-CLS Exception\) 或「*非例外狀況*」\(Non\-Exception\)。  在 [!INCLUDE[csprcs](../../../csharp/includes/csprcs-md.md)] 中，您不能擲回非 CLS 的例外狀況，但是可以用兩種方式攔截這些例外狀況：  
  
-   在 `catch (Exception e)` 區塊內當做 <xref:System.Runtime.CompilerServices.RuntimeWrappedException>。  
  
     根據預設，[!INCLUDE[csprcs](../../../csharp/includes/csprcs-md.md)] 組件 \(Assembly\) 會以包裝例外狀況的形式攔截非 CLS 的例外狀況。  如果您需要存取原始的例外狀況，而該例外狀況可透過 <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> 屬性加以存取時，便可使用這個方法。  本主題稍後的程序會說明如何以這種方式攔截例外狀況。  
  
-   放置在 `catch (Exception)` 或 `catch (Exception e)` 區塊後的一般 catch 區塊內 \(沒有指定例外狀況類型的 catch 區塊\)。  
  
     當您想要執行某個動作 \(例如寫入記錄檔\) 來回應非 CLS 的例外狀況，而且不需要存取例外狀況資訊時，可使用這個方法。  根據預設，Common Language Runtime 會包裝所有的例外狀況。  若要停用這個行為，請將這個組件層級 \(Assembly\-level\) 的屬性 \(Attribute\) 加入您的程式碼中，通常位於 AssemblyInfo.cs 檔案中：`[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`。  
  
### 若要攔截非 CLS 的例外狀況  
  
1.  在 `catch(Exception e) block` 內使用 `as` 關鍵字來測試是否可將 `e` 轉換為 <xref:System.Runtime.CompilerServices.RuntimeWrappedException>。  
  
2.  透過 <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> 屬性存取原始的例外狀況。  
  
## 範例  
 下列範例會示範如何攔截非 CLS 的例外狀況，它是從以 C\+\+\/CLR 撰寫的類別庫 \(Class Library\) 擲回。  請注意，此範例中的 [!INCLUDE[csprcs](../../../csharp/includes/csprcs-md.md)] 用戶端程式碼會預先知道將被擲回的例外狀況類型為 <xref:System.String?displayProperty=fullName>。  您可以將 <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> 屬性轉換回其原始的型別 \(前提是可從程式碼存取該型別\)。  
  
```  
// Class library written in C++/CLR.  
   ThrowNonCLS.Class1 myClass = new ThrowNonCLS.Class1();  
  
   try  
   {  
    // throws gcnew System::String(  
    // "I do not derive from System.Exception!");  
    myClass.TestThrow();   
   }  
  
   catch (Exception e)  
   {  
    RuntimeWrappedException rwe = e as RuntimeWrappedException;  
    if (rwe != null)      
    {  
      String s = rwe.WrappedException as String;  
      if (s != null)  
      {  
        Console.WriteLine(s);  
      }  
    }  
    else  
    {  
       // Handle other System.Exception types.  
    }  
   }             
```  
  
## 請參閱  
 <xref:System.Runtime.CompilerServices.RuntimeWrappedException>   
 [例外狀況和例外狀況處理](../../../csharp/programming-guide/exceptions/exceptions-and-exception-handling.md)