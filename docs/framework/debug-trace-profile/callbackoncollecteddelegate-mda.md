---
title: callbackOnCollectedDelegate MDA
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- MDAs (managed debugging assistants), garbage collection
- managed debugging assistants (MDAs), callback on collected delegates
- MDAs (managed debugging assistants), callback on collected delegates
- callback on delegate after garbage collection
- callbackOnCollectedDelegate MDA
- managed debugging assistants (MDAs), garbage collection
- call back collected delegates
- garbage collection, run-time errors
- delegates [.NET Framework], garbage collection
ms.assetid: 398b0ce0-5cc9-4518-978d-b8263aa21e5b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0aa9ecd357a192eba64cc14f8940b264461b5e74
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33356351"
---
# <a name="callbackoncollecteddelegate-mda"></a>callbackOnCollectedDelegate MDA
如果委派以函式指標形式從 Managed 程式碼封送處理至 Unmanaged 程式碼，而在對委派進行記憶體回收之後，將回呼放在該函式指標上，`callbackOnCollectedDelegate` Managed 偵錯助理 (MDA) 就會啟動。  
  
## <a name="symptoms"></a>徵兆   
 嘗試透過從 Managed 委派取得的函式指標，呼叫至 Managed 程式碼中時，就會發生存取違規。 這些失敗雖然不是 Common Language Runtime (CLR) 錯誤，但看起來可能很像，因為 CLR 程式碼中發生存取違規。  
  
 失敗情況不一致，有時在函式指標上呼叫成功，有時則失敗。 只有在負載過重，或嘗試不定次數時，可能會發生失敗。  
  
## <a name="cause"></a>原因  
 用來建立函式指標並向 Unmanaged 程式碼公開的委派被回收記憶體。 當 Unmanaged 元件嘗試在函式指標上呼叫時，會產生存取違規。  
  
 此失敗會隨機發生，因為要視發生記憶體回收的時機而定。 如果委派符合記憶體回收資格，在回呼之後就會發生記憶體回收，且呼叫成功。 在其他時候，記憶體回收會發生在回呼之前，回呼會產生存取違規，而程式會停止。  
  
 失敗的機率取決於將委派封送處理與在函式指標上回呼之間的時間，以及記憶體回收的頻率。 如果將委派封送處理與後續回呼之間的時間很短，則偶爾會失敗。 如果接收函式指標的 Unmanaged 方法沒有儲存函式指標以供稍後使用，而是立即在函式指標上回呼，完成其作業後再返回，通常都會發生這種情況。 同樣地，當系統負載過重時，會發生更多記憶體回收，這樣更有可能會在回呼之前發生記憶體回收。  
  
## <a name="resolution"></a>解決方式  
 一旦將委派封送處理出去成為 Unmanaged 函式指標，記憶體回收行程即無法追蹤其存留期。 相反地，您的程式碼必須保留委派的參考，以供 Unmanaged 函式指標的存留期使用。 但是，您必須先識別已回收哪個委派，才能這麼做。 當啟用 MDA 時，它會提供委派的類型名稱。 使用此名稱，在您的程式碼中搜尋平台叫用，或是將該委派傳出至 Unmanaged 程式碼的 COM 簽章。 違規的委派會透過其中一個呼叫位置傳遞出去。 您也可以啟用 `gcUnmanagedToManaged` MDA，以在每次回呼至執行階段中之前，強制進行記憶體回收。 如此可以確保在回呼之前，一律會發生記憶體回收，進而消除因記憶體回收而產生的不確定性。 您知道哪些委派已回收之後，立即變更程式碼，以在已封送處理之 Unmanaged 函式指標的存留期間，將該委派的參考保留在 Managed 端。  
  
## <a name="effect-on-the-runtime"></a>對執行階段的影響  
 當委派被封送處理為函式指標時，執行階段會配置從 Unmanaged 轉換到 Managed 的 Thunk。 這個 Thunk 是最後叫用 Managed 委派之前，Unmanaged 程式碼實際呼叫的項目。 若未啟用 `callbackOnCollectedDelegate` MDA，當委派被回收時，會刪除 Unmanaged 封送處理程式碼。 若已啟用 `callbackOnCollectedDelegate` MDA，當委派被回收時，就不會立即刪除 Unmanaged 封送處理程式碼。 相反地，最後 1,000 個執行個體會依預設保持運作，並且在被呼叫時，變更為啟用 MDA。 在回收超過 1,001 個封送處理的委派之後，最後會刪除 Thunk。  
  
## <a name="output"></a>輸出  
 MDA 會報告在其 Unmanaged 函式指標上嘗試回呼之前，所回收之委派的類型名稱。  
  
## <a name="configuration"></a>組態  
 下列範例顯示應用程式組態選項。 它將 MDA 保持運作的 Thunk 數目設為 1,500。 預設的 `listSize` 值為 1,000，最小值為 50，最大值為  2,000。  
  
```xml  
<mdaConfig>  
  <assistants>  
    <callbackOnCollectedDelegate listSize="1500" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>範例  
 下列範例示範可以啟動此 MDA 的情況：  
  
```  
// Library.cpp : Defines the unmanaged entry point for the DLL application.  
#include "windows.h"  
#include "stdio.h"  
  
void (__stdcall *g_pfTarget)();  
  
void __stdcall Initialize(void __stdcall pfTarget())  
{  
    g_pfTarget = pfTarget;  
}  
  
void __stdcall Callback()  
{  
    g_pfTarget();  
}  
// ---------------------------------------------------  
// C# Client  
using System;  
using System.Runtime.InteropServices;  
  
public class Entry  
{  
    public delegate void DCallback();  
  
    public static void Main()  
    {  
        new Entry();  
        Initialize(Target);  
        GC.Collect();  
        GC.WaitForPendingFinalizers();  
        Callback();  
    }  
  
    public static void Target()  
    {          
    }  
  
    [DllImport("Library", CallingConvention = CallingConvention.StdCall)]  
    public static extern void Initialize(DCallback pfDelegate);  
  
    [DllImport ("Library", CallingConvention = CallingConvention.StdCall)]  
    public static extern void Callback();  
  
    ~Entry() { Console.Error.WriteLine("Entry Collected"); }  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [診斷 Managed 偵錯助理的錯誤](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Interop 封送處理](../../../docs/framework/interop/interop-marshaling.md)  
 [gcUnmanagedToManaged](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)
