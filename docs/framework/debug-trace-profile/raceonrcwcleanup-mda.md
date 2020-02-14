---
title: raceOnRCWCleanup MDA
ms.date: 03/30/2017
helpviewer_keywords:
- RCW
- managed debugging assistants (MDAs), RCWs
- race on RCW cleanup
- MDAs (managed debugging assistants), RCWs
- RaceOnRCWCleanup MDA
- runtime callable wrappers
ms.assetid: bee1e9b1-50a8-4c89-9cd9-7dd6b2458187
ms.openlocfilehash: edf1fe3ee5be631f7f3c42f4a6cdb17f1be722cf
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216188"
---
# <a name="raceonrcwcleanup-mda"></a>raceOnRCWCleanup MDA
當使用 `raceOnRCWCleanup` 方法這類命令呼叫釋放[執行階段可呼叫包裝函式](../../standard/native-interop/runtime-callable-wrapper.md) (RCW) 時，如果 Common Language Runtime (CLR) 偵測到 RCW 正在使用中，則會啟動 <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> Managed 偵錯助理 (MDA)。  
  
## <a name="symptoms"></a>徵狀  
 使用 <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> 或類似方法釋放 RCW 期間或之後，發生存取違規或記憶體損毀的情況。  
  
## <a name="cause"></a>原因  
 另一個執行緒正在使用這個 RCW，或釋放執行緒堆疊時正在使用這個 RCW。  無法釋放使用中的 RCW。  
  
## <a name="resolution"></a>解決方案  
 請勿釋放目前執行緒或其他執行緒可能正在使用的 RCW。  
  
## <a name="effect-on-the-runtime"></a>對執行階段的影響  
 此 MDA 對 CLR 沒有影響。  
  
## <a name="output"></a>輸出  
 描述錯誤的訊息。  
  
## <a name="configuration"></a>組態  
  
```xml  
<mdaConfig>  
  <assistants>  
    <raceOnRCWCleanup/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [使用 Managed 偵錯助理診斷錯誤](diagnosing-errors-with-managed-debugging-assistants.md)
- [Interop 封送處理](../interop/interop-marshaling.md)
