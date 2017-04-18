---
title: "jitCompilationStart MDA | Microsoft Docs"
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
  - "JIT compilation"
  - "MDAs (managed debugging assistants), JIT compilation"
  - "JitCompilationStart MDA"
  - "managed debugging assistants (MDAs), JIT compilation"
ms.assetid: 5ffd2857-d0ba-4342-9824-9ffe04ec135d
caps.latest.revision: 11
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 11
---
# jitCompilationStart MDA
當 Just\-In\-Time \(JIT\) 編譯器開始編譯函式時，`jitCompilationStart` Managed 偵錯助理 \(MDA\) 就會啟動以提供報告。  
  
## 症狀  
 由於 mscorjit.dll 會載入處理序中，所以已經屬於原生映像格式之程式的工作集大小會因而增加。  
  
## 原因  
 此程式所相依的組件，並非全部都以原生格式產生，或者這些具有原生格式尚未正確地註冊。  
  
## 解決方式  
 啟用這個 MDA 讓您能夠判斷哪些函式是 JIT 編譯的。  判斷包含函式的組件，是否以原生格式產生並且已正確地註冊。  
  
## 對執行階段的影響  
 這個 MDA 會記錄正要以 JIT 編譯方法之前的訊息，因此啟用這個 MDA 會對效能具有顯著的影響。  請注意，如果是內嵌的方法，這個 MDA 就不會產生個別的訊息。  
  
## Output  
 下列程式碼範例會顯示範例輸出。  在這個情況中，輸出會顯示在 Test 組件中，類別 "ns2.CO" 上的 "m" 方法是以 JIT 編譯的。  
  
```  
method name="Test!ns2.C0::m"  
```  
  
## 組態  
 下列組態檔顯示各種不同的篩選條件，在方法首次以 JIT 編譯時，可以使用這些篩選條件以篩選出要報告哪些方法。  您可以將名稱屬性 \(Attribute\) 的值設定為 \*，以指定要報告的所有方法。  
  
```  
<mdaConfig>  
  <assistants>  
    <jitCompilationStart>  
      <methods>  
        <match name="C0::m" />  
        <match name="MyMethod" />  
        <match name="C2::*" />  
        <match name="ns0::*" />  
        <match name="ns1.C0::*" />  
        <match name="ns2.C0::m" />  
        <match name="ns2.C0+N0::m" />  
      </methods>  
    </jitCompilationStart >  
  </assistants>  
</mdaConfig>  
```  
  
## 範例  
 下列程式碼範例主要是與先前的組態檔一起使用的。  
  
```  
using System;  
using System.Reflection;  
using System.Runtime.CompilerServices;  
using System.Runtime.InteropServices;  
  
public class Entry  
{  
    public static void Main(string[] args)  
    {  
        C0.m();  
        C1.MyMethod();  
        C2.m();  
  
        ns0.C0.m();  
        ns0.C0.N0.m();  
        ns0.C1.m();  
  
        ns1.C0.m();  
        ns1.C0.N0.m();  
  
        ns2.C0.m();  
        ns2.C0.N0.m();  
    }  
}  
  
public class C0  
{  
    [MethodImpl(MethodImplOptions.NoInlining)]  
    public static void m() { }  
}  
  
public class C1  
{  
    [MethodImpl(MethodImplOptions.NoInlining)]  
    public static void MyMethod() { }  
}  
  
public class C2  
{  
    [MethodImpl(MethodImplOptions.NoInlining)]  
    public static void m() { }  
}  
  
namespace ns0  
{  
    public class C0  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
  
        public class N0  
        {  
            [MethodImpl(MethodImplOptions.NoInlining)]  
            public static void m() { }  
        }  
    }  
  
    public class C1  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
    }  
}  
  
namespace ns1  
{  
    public class C0  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
        public class N0  
        {  
            [MethodImpl(MethodImplOptions.NoInlining)]  
            public static void m() { }  
        }  
    }  
}  
  
namespace ns2  
{  
    public class C0  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
  
        public class N0  
        {  
            [MethodImpl(MethodImplOptions.NoInlining)]  
            public static void m() { }  
        }  
    }  
}  
```  
  
## 請參閱  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [Interop 封送處理](../../../docs/framework/interop/interop-marshaling.md)