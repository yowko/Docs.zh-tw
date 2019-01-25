---
title: gcManagedToUnmanaged MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), garbage collection
- GcManagedToUnmanaged MDA
- GC managed to unmanaged
- transitioning threads managed to unmanaged code
- threading [.NET Framework], garbage collection
- managed to unmanaged garbage collection
- managed debugging assistants (MDAs), garbage collection
- threading [.NET Framework], managed debugging assistants
- garbage collection, run-time errors
ms.assetid: 7417f837-805e-4fed-a430-ca919c8421dc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: add5ba59f8f59fc013f8c04a186b34e711c1490c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54537929"
---
# <a name="gcmanagedtounmanaged-mda"></a>gcManagedToUnmanaged MDA
每當執行緒從 Managed 轉換到 Unmanaged 程式碼時，`gcManagedToUnmanaged` Managed 偵錯助理 (MDA) 會造成記憶體回收。  
  
## <a name="symptoms"></a>徵兆   
 嘗試使用已公開至 COM 的 Managed 物件時，Unmanaged 使用者元件會擲回存取違規。 COM 物件似乎已發行。 存取違規不具決定性。  
  
## <a name="cause"></a>原因  
 如果 Unmanaged 元件不是正確計算 Managed COM 物件的參考，執行階段可以收集已公開至 COM 的 Managed 物件，而 Unmanaged 元件仍會保存物件的參考。 執行階段會在記憶體回收期間呼叫 <xref:System.Runtime.InteropServices.Marshal.Release%2A>，因此如果使用者元件在發生記憶體回收之前使用物件，就不會被回收。 這是不具決定性的來源。  
  
## <a name="resolution"></a>解決方式  
 啟用此助理可減少從物件可供回收，到呼叫 <xref:System.Runtime.InteropServices.Marshal.Release%2A> 之間的時間，有助於追蹤哪一個 Unmanaged 元件最先嘗試存取已收集的物件。  
  
## <a name="effect-on-the-runtime"></a>對執行階段的影響  
 每當執行緒從 Managed 轉換到 Unmanaged 程式碼時，會造成記憶體回收。  
  
## <a name="output"></a>輸出  
 此 MDA 不會產生輸出。  
  
## <a name="configuration"></a>組態  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcManagedToUnmanaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [診斷 Managed 偵錯助理的錯誤](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Interop 封送處理](../../../docs/framework/interop/interop-marshaling.md)
- [gcUnmanagedToManaged](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)
