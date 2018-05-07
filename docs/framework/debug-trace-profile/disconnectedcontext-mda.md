---
title: disconnectedContext MDA
ms.date: 03/30/2017
helpviewer_keywords:
- DisconnectedContext MDA
- MDAs (managed debugging assistants), disconnected context
- dead context
- transitioning disconnected apartment or context
- context disconnections
- managed debugging assistants (MDAs), disconnected context
ms.assetid: 1887d31d-7006-4491-93b3-68fd5b05f71d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b5232a01d877484591df63afc68f672327d4b9d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="disconnectedcontext-mda"></a>disconnectedContext MDA
如果 CLR 在服務有關 COM 物件的要求時，試圖轉換至中斷連接的 Apartment 或內容，就會啟動 `disconnectedContext` Managed 偵錯助理 (MDA)。  
  
## <a name="symptoms"></a>徵兆  
 在[執行階段可呼叫包裝函式](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) 上執行的呼叫會傳遞至目前 Apartment 或內容中的基礎 COM 元件，而不是其所在的 Apartment 或內容中。 如果 COM 元件不是多執行緒，這可能會導致損毀及/或資料遺失，就像在單一執行緒 Apartment (STA) 元件的案例一樣。 或者，如果 RCW 本身是 Proxy，則呼叫可能會導致擲回 <xref:System.Runtime.InteropServices.COMException>，且 HRESULT 為 RPC_E_WRONG_THREAD。  
  
## <a name="cause"></a>原因  
 當 CLR 試圖轉換至 OLE Apartment 或內容時，其已關閉。 最常見的原因，就是在 Apartment 擁有的所有 COM 元件都完成發行之前，STA Apartment 即已關閉。從 RCW 上的使用者程式碼進行明確呼叫，或是 CLR 本身在操作 COM 元件時，就可能會導致這種情況發生，例如當相關聯的 RCW 已進行記憶體回收，而 CLR 還在發行 COM 元件時。  
  
## <a name="resolution"></a>解決方式  
 若要避免此問題，請確定在應用程式完成 Apartment 中留存的所有物件之前，擁有 STA 的執行緒不會終止。 對內容也是套用一樣的方式；請確定在應用程式完成內容中留存的任何 COM 元件之前，內容未關閉。  
  
## <a name="effect-on-the-runtime"></a>對執行階段的影響  
 此 MDA 對 CLR 沒有影響。 它只會提報中斷連接之內容的相關資料。  
  
## <a name="output"></a>輸出  
 提報中斷連接的 Apartment 或內容的內容 Cookie。  
  
## <a name="configuration"></a>組態  
  
```xml  
<mdaConfig>  
  <assistants>  
    <disconnectedContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [診斷 Managed 偵錯助理的錯誤](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Interop 封送處理](../../../docs/framework/interop/interop-marshaling.md)
