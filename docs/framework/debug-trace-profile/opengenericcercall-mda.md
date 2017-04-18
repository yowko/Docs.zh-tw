---
title: "openGenericCERCall MDA | Microsoft Docs"
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
  - "MDAs (managed debugging assistants), CER calls"
  - "open generic CER calls"
  - "constrained execution regions"
  - "openGenericCERCall MDA"
  - "CER calls"
  - "managed debugging assistants (MDAs), CER calls"
  - "generics [.NET Framework], open generic CER calls"
ms.assetid: da3e4ff3-2e67-4668-9720-fa776c97407e
caps.latest.revision: 13
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# openGenericCERCall MDA
會啟動 `openGenericCERCall` Managed 偵錯助理，警告在根方法上具有泛型型別變數的限制的執行區域 \(CER\) 圖形正在 JIT 編譯或原生映像產生的時間進行處理，且其中至少有一個泛型型別變數為物件參考型別。  
  
## 症狀  
 CER 程式碼不會在中止執行緒或卸載應用程式定義域時執行。  
  
## 原因  
 在 JIT 編譯期間，包含物件參考型別的執行個體化僅具有代表性，因為產生的程式碼是共用的，而且每一個物件參考型別變數都可能是任何物件參考型別；  如此可避免事先預備某些執行階段的資源。  
  
 特別是，具有泛型型別變數的方法可以從容地在背景中配置資源，  這些稱為泛型字典項目。  例如，對於陳述式 `List<T> list = new List<T>();`  \(其中 `T` 是泛型型別變數\) 而言，執行階段 \(Runtime\) 必須在執行階段時查詢 \(也可能建立\) 確切的執行個體化，例如 `List<Object>, List<String>` ``  等。  這可能會因為開發人員無法控制的各種理由而失敗，例如，記憶體耗盡。  
  
 這個 MDA 應該只能在 JIT 編譯時期啟動，而不是在有確切的執行個體化時啟動。  
  
 當這個 MDA 啟動時，很可能發生的症狀是 CER 無法在錯誤的執行個體化中運作。  事實上，執行階段尚未嘗試在造成此 MDA 啟動的情況下實作 CER；  因此，如果開發人員使用 CER 的共用執行個體化，將不會攔截 JIT 編譯錯誤、泛型型別載入錯誤，或是預期的 CER 之區域內的執行緒中止。  
  
## 解決方式  
 如果是可能包含 CER 的方法，不要使用具有物件參考型別的泛型型別變數。  
  
## 對執行階段的影響  
 這個 MDA 對 CLR 無效。  
  
## Output  
 下列是來自這個 MDA 的輸出範例。  
  
 `Method 'GenericMethodWithCer', which contains at least one constrained execution region, cannot be prepared automatically since it has one or more unbound generic type parameters.`  
  
 `The caller must ensure this method is prepared explicitly at run time prior to execution.`  
  
 `method name="GenericMethodWithCer"`  
  
 `declaringType name="OpenGenericCERCall"`  
  
## 組態  
  
```  
<mdaConfig>  
  <assistants>  
    <openGenericCERCall/>  
  </assistants>  
</mdaConfig>  
```  
  
## 範例  
 不會執行 CER 程式碼。  
  
```  
using System;  
using System.Collections.Generic;  
using System.Runtime.CompilerServices;  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        CallGenericMethods();  
    }  
    static void CallGenericMethods()  
    {  
        // This call is correct. The instantiation of the method  
        // contains only nonreference types.  
        MyClass.GenericMethodWithCer<int>();  
  
        // This call is incorrect. A shared version of the method that  
        // cannot be completely analyzed will be JIT-compiled. The   
        // MDA will be activated at JIT-compile time, not at run time.  
        MyClass.GenericMethodWithCer<String>();  
    }  
}  
  
    class MyClass  
{  
    public static void GenericMethodWithCer<T>()  
    {  
        RuntimeHelpers.PrepareConstrainedRegions();  
        try  
        {  
  
        }  
        finally  
        {  
            // This is the start of the CER.  
            Console.WriteLine("In finally block.");  
        }  
    }  
}  
```  
  
## 請參閱  
 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>   
 <xref:System.Runtime.ConstrainedExecution>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)