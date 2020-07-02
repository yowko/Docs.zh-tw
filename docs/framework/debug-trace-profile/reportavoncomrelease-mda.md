---
title: reportAvOnComRelease MDA
description: 請參閱 reportAvOnComRelease managed 偵錯工具（MDA），這可能是因為在 .NET 中發生存取違規和記憶體損毀所造成。
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), reference counting errors
- exceptions, reference counting errors
- ReportAvOnComRelease MDA
- COM release access violations
- user reference counting errors
- managed debugging assistants (MDAs), reference counting errors
- report access violation on Com release
- reference counting errors
ms.assetid: a2b86b63-08b2-4943-b344-3c2cf46ccd31
ms.openlocfilehash: f9ba343060cb4d16de5909a5b619353546aca8ca
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803606"
---
# <a name="reportavoncomrelease-mda"></a>reportAvOnComRelease MDA
如果在執行 COM Interop 並使用與原始 COM 呼叫組合的 `reportAvOnComRelease` 或 <xref:System.Runtime.InteropServices.Marshal.Release%2A> 方法時，因為使用者參考計數錯誤而擲回例外狀況，就會啟用 <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> Managed 偵錯助理 (MDA)。  
  
## <a name="symptoms"></a>徵狀  
 存取違規與記憶體損毀。  
  
## <a name="cause"></a>原因  
 有時候，在執行 COM Interop 並使用與原始 COM 呼叫組合的 <xref:System.Runtime.InteropServices.Marshal.Release%2A> 或 <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> 方法時，會因為使用者參考計數錯誤而擲回例外狀況。 通常會捨棄此例外狀況，因為如果不這麼做，就會導致 CLR 發生存取違規，而降低效能。 如果啟用此助理，就會偵測並提報這類例外狀況，而不是直接捨棄。  
  
## <a name="resolution"></a>解決方案  
 檢查您的參考計數程式碼，並搜尋錯誤，另外也要檢查物件的原生用戶端，查看是否有參考計數錯誤。  
  
## <a name="effect-on-the-runtime"></a>對執行階段的影響  
 有兩種模式可用。 如果 `allowAv` 屬性為 `true`，該助理會防止執行階段捨棄存取違規。 如果 `allowAv` 為 `false` (預設值)，則執行階段會捨棄存取違規，但是會向使用者提報警告訊息，指出已擲回並捨棄例外狀況。  
  
## <a name="output"></a>輸出  
 如果可能，輸出會包含 COM 介面指標的原始 vtable。 否則，就會顯示告知性訊息。  
  
## <a name="configuration"></a>組態  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reportAvOnComRelease />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [使用 Managed 偵錯助理診斷錯誤](diagnosing-errors-with-managed-debugging-assistants.md)
- [Interop 封送處理](../interop/interop-marshaling.md)
