---
title: gcUnmanagedToManaged MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), garbage collection
- GC unmanaged to managed
- transitioning threads unmanaged to managed code
- GcUnmanagedToManaged MDA
- threading [.NET Framework], garbage collection
- managed debugging assistants (MDAs), garbage collection
- threading [.NET Framework], managed debugging assistants
- garbage collection, run-time errors
- unmanaged to managed garbage collection
ms.assetid: 103eb3a3-1cf0-4406-8a9a-a7798fdc22d1
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1679f87276262a08f5717ea81d263f4600542971
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052767"
---
# <a name="gcunmanagedtomanaged-mda"></a>gcUnmanagedToManaged MDA
每當執行緒從 Unmanaged 轉換到 Managed 程式碼時，`gcUnmanagedToManaged` Managed 偵錯助理 (MDA) 會造成記憶體回收。  
  
## <a name="symptoms"></a>徵兆  
 使用 COM 和平台叫用執行 Unmanaged 使用者元件的應用程式在 CLR 中造成不具決定性的存取違規。  
  
## <a name="cause"></a>原因  
 如果應用程式正在執行 Unmanaged 使用者元件，那麼這些元件可能已損毀記憶體回收的堆積。 在 CLR 中，當記憶體回收行程嘗試查核物件圖形時，這會造成存取違規。  
  
## <a name="resolution"></a>解決方式  
 在每次 Managed 轉換之前，啟用此助理會減少從 Unmanaged 元件損毀記憶體回收的堆積到強制執行記憶體回收而發生存取違規的間隔時間。  
  
## <a name="effect-on-the-runtime"></a>對執行階段的影響  
 每當執行緒從 Unmanaged 轉換到 Managed 程式碼時，會造成記憶體回收。  
  
## <a name="output"></a>Output  
 此 MDA 不會產生輸出。  
  
## <a name="configuration"></a>組態  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcUnmanagedToManaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [診斷 Managed 偵錯助理的錯誤](diagnosing-errors-with-managed-debugging-assistants.md)
- [gcManagedToUnmanaged](gcmanagedtounmanaged-mda.md)
- [Interop 封送處理](../interop/interop-marshaling.md)
