---
title: overlappedFreeError MDA
ms.date: 03/30/2017
helpviewer_keywords:
- OverlappedFreeError MDA
- overlapped free method call error
- managed debugging assistants (MDAs), overlapped structures
- overlapped structures
- MDAs (managed debugging assistants), overlapped structures
- freeing overlapped structures
ms.assetid: b6ab2d48-6eee-4bab-97a3-046b3b0a5470
author: mairaw
ms.author: mairaw
ms.openlocfilehash: defd7f90fcac8d1e98104796682058638c9bd799
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59127071"
---
# <a name="overlappedfreeerror-mda"></a>overlappedFreeError MDA
重疊作業完成之前，呼叫 <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> 方法時，會啟用 `overlappedFreeError` Managed 偵錯助理 (MDA)。  
  
## <a name="symptoms"></a>徵兆  
 已進行記憶體回收之堆積的存取違規或損毀。  
  
## <a name="cause"></a>原因  
 作業完成之前，已釋放重疊結構。 使用重疊指標的函式稍後可能會在釋出之後寫入結構中。 這可能會造成堆積損毀，因為另一個物件現在可能會佔用該區域。  
  
 如果未成功啟動重疊的作業，則此 MDA 可能不會呈現錯誤。  
  
## <a name="resolution"></a>解決方式  
 請確定使用重疊結構的 I/O 作業完成，再呼叫 <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> 方法。  
  
## <a name="effect-on-the-runtime"></a>對執行階段的影響  
 此 MDA 對 CLR 沒有影響。  
  
## <a name="output"></a>Output  
 以下是此 MDA 的範例輸出。  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlappedStructure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a>組態  
  
```xml  
<mdaConfig>  
  <assistants>  
    <overlappedFreeError/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [診斷 Managed 偵錯助理的錯誤](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Interop 封送處理](../../../docs/framework/interop/interop-marshaling.md)
