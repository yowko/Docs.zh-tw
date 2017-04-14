---
title: "reentrancy MDA | Microsoft Docs"
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
  - "unmanaged code, debugging"
  - "transitioning threads unmanaged to managed code"
  - "reentrancy MDA"
  - "reentrancy without an orderly transition"
  - "managed debugging assistants (MDAs), reentrancy"
  - "illegal reentrancy"
  - "MDAs (managed debugging assistants), reentrancy"
  - "threading [.NET Framework], managed debugging assistants"
  - "managed code, debugging"
  - "native debugging, MDAs"
ms.assetid: 7240c3f3-7df8-4b03-bbf1-17cdce142d45
caps.latest.revision: 8
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# reentrancy MDA
在之前不是透過按照順序的轉換方式從 Managed 程式碼切換成機器碼的情況下，嘗試從機器碼轉換為 Managed 程式碼 時，即會啟動 `reentrancy` Managed 偵錯助理 \(MDA\)。  
  
## 症狀  
 在從機器碼轉換成 Managed 程式碼時，物件堆積損壞，或發生了其他嚴重的錯誤。  
  
 以任一方向在機器碼和 Managed 程式碼之間切換的執行緒，必須執行按照順序的轉換。  但是，作業系統上的某些低階擴充性點 \(例如向量化的例外狀況處理常式\)，可允許從 Managed 程式碼切換成機器碼，而不需要執行按照順序的轉換。這些切換都是在作業系統的控制下進行，而不是在 Common Language Runtime \(CLR\) 控制下。在這些擴充性點之內執行的任何機器碼，都必須避免回呼 Managed 程式碼。  
  
## 原因  
 在執行 Managed 程式碼時，已經啟動低階的作業系統擴充性點 \(例如，向量化的例外狀況處理常式\)；透過該擴充性點叫用的應用程式程式碼正嘗試回呼 Managed 程式碼。  
  
 這個問題一定是由應用程式程式碼所造成。  
  
## 解決方式  
 針對啟動這個 MDA 的執行緒檢查堆疊追蹤，此執行緒嘗試以不合法的方式呼叫 Managed 程式碼。此堆疊追蹤應該顯示使用此擴充性點的應用程式程式碼、提供此擴充性點的作業系統程式碼，以及此擴充性點所中斷的 Managed 程式碼。  
  
 例如，當您嘗試從向量化的例外狀況處理常式中呼叫 Managed 程式碼時，將會看到啟動的 MDA。在此堆疊上，您將會看到作業系統例外處理程式碼及某些 Managed 程式碼，觸發了類似 <xref:System.DivideByZeroException> 或 <xref:System.AccessViolationException> 的例外狀況。  
  
 在此範例中，正確的解決方法是完整地在 Unmanaged 程式碼中實作向量化的例外狀況處理常式。  
  
## 對執行階段的影響  
 這個 MDA 對 CLR 無效。  
  
## Output  
 此 MDA 報告正在嘗試不合法的重新進入動作；請檢查執行緒的堆疊，以判斷這個問題發生的原因及修正的方式。  下列是範例輸出。  
  
```  
Additional Information: Attempting to call into managed code without   
transitioning out first.  Do not attempt to run managed code inside   
low-level native extensibility points. Managed Debugging Assistant   
'Reentrancy' has detected a problem in 'D:\ConsoleApplication1\  
ConsoleApplication1\bin\Debug\ConsoleApplication1.vshost.exe'.  
```  
  
## Configuration  
  
```  
<mdaConfig>  
  <assistants>  
    <reentrancy />  
  </assistants>  
</mdaConfig>  
```  
  
## 範例  
 下列程式碼範例會擲回 <xref:System.AccessViolationException>。在支援向量化例外狀況處理的 Windows 版本上，這會呼叫 Managed 向量化的例外狀況處理常式。如果已啟用 `reentrancy` MDA，在嘗試從作業系統的向量化例外狀況處理支援程式碼呼叫 `MyHandler` 期間，將會啟動此 MDA。  
  
```  
using System;  
public delegate int ExceptionHandler(IntPtr ptrExceptionInfo);  
  
public class Reenter   
{  
    public static ExceptionHandler keepAlive;  
  
    [System.Runtime.InteropServices.DllImport("kernel32", ExactSpelling=true,   
        CharSet=System.Runtime.InteropServices.CharSet.Auto)]  
    public static extern IntPtr AddVectoredExceptionHandler(int bFirst,   
        ExceptionHandler handler);  
  
    static int MyHandler(IntPtr ptrExceptionInfo)   
    {  
        // EXCEPTION_CONTINUE_SEARCH  
        return 0;  
    }  
    void Run() {}  
  
    static void Main()   
    {  
        keepAlive = new ExceptionHandler(Reenter.MyHandler);  
        IntPtr ret = AddVectoredExceptionHandler(1, keepAlive);  
        try   
        {  
            // Dispatch on null should AV.  
            Reenter r = null;   
            r.Run();  
        }   
        catch { }  
    }  
}  
```  
  
## 請參閱  
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)