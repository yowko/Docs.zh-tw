---
title: 重新進入 MDA
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged code, debugging
- transitioning threads unmanaged to managed code
- reentrancy MDA
- reentrancy without an orderly transition
- managed debugging assistants (MDAs), reentrancy
- illegal reentrancy
- MDAs (managed debugging assistants), reentrancy
- threading [.NET Framework], managed debugging assistants
- managed code, debugging
- native debugging, MDAs
ms.assetid: 7240c3f3-7df8-4b03-bbf1-17cdce142d45
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7de0a869925816da6df8f17e14ab92964aec8d11
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59094212"
---
# <a name="reentrancy-mda"></a>重新進入 MDA
如果未透過循序轉換執行先前從 Managed 程式碼到機器碼的切換時嘗試從機器碼轉換成 Managed 程式碼，啟用 `reentrancy` Managed 偵錯助理 (MDA)。  
  
## <a name="symptoms"></a>徵兆  
 物件堆積損毀，或從機器碼轉換成 Managed 程式碼時發生其他嚴重錯誤。  
  
 在機器碼與 Managed 程式碼之間依任一方向切換的執行緒，必須執行循序轉換。 不過，作業系統中的特定低階擴充點 (例如向量化例外狀況處理常式) 允許從 Managed 程式碼切換成機器碼，而不需要執行循序轉換。  這些參數是受作業系統控制，而不是受 Common Language Runtime (CLR) 控制。  任何在這些擴充點內執行的機器碼都必須避免回呼 Managed 程式碼。  
  
## <a name="cause"></a>原因  
 執行 Managed 程式碼時，已啟用低階作業系統擴充點 (例如向量化例外狀況處理常式)。  透過該擴充點叫用的應用程式碼將嘗試回呼至 Managed 程式碼。  
  
 這個問題一律是由應用程式碼所造成。  
  
## <a name="resolution"></a>解決方式  
 檢查已啟用此 MDA 的執行緒堆疊追蹤。  執行緒將會嘗試不合法地呼叫 Managed 程式碼。  堆疊追蹤應該顯示使用此擴充點的應用程式碼、提供此擴充點的作業系統程式碼，以及擴充點已中斷的 Managed 程式碼。  
  
 例如，您會看到 MDA 已在嘗試從向量化例外狀況處理常式呼叫 Managed 程式碼時啟用。  在堆疊上，您會看到作業系統例外狀況處理程式碼，以及觸發例外狀況的某個 Managed 程式碼 (例如 <xref:System.DivideByZeroException> 或 <xref:System.AccessViolationException>)。  
  
 在此範例中，正確的解決方式是使用 Unmanaged 程式碼完全實作向量化例外狀況處理常式。  
  
## <a name="effect-on-the-runtime"></a>對執行階段的影響  
 此 MDA 對 CLR 沒有影響。  
  
## <a name="output"></a>Output  
 MDA 報告正在嘗試不合法的重新進入。  檢查執行緒的堆疊，以判斷發生此問題的原因和其更正方式。 以下是範例輸出。  
  
```  
Additional Information: Attempting to call into managed code without   
transitioning out first.  Do not attempt to run managed code inside   
low-level native extensibility points. Managed Debugging Assistant   
'Reentrancy' has detected a problem in 'D:\ConsoleApplication1\  
ConsoleApplication1\bin\Debug\ConsoleApplication1.vshost.exe'.  
```  
  
## <a name="configuration"></a>組態  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reentrancy />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>範例  
 下列程式碼範例會導致擲回 <xref:System.AccessViolationException>。  在支援向量化例外狀況處理的 Windows 版本上，這會呼叫 Managed 向量化例外狀況處理常式。  如果啟用 `reentrancy` MDA，則會在透過作業系統的向量化例外狀況處理支援程式碼嘗試呼叫 `MyHandler` 期間啟用 MDA。  
  
```csharp
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
  
## <a name="see-also"></a>另請參閱

- [診斷 Managed 偵錯助理的錯誤](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
