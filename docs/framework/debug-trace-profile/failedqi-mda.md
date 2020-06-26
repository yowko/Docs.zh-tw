---
title: failedQI MDA
description: 請參閱 .NET 中的 failedQI managed 偵錯工具（MDA），這可能會在執行時間可呼叫包裝函式（RCW）中的轉型或 COM 呼叫失敗時啟用。
ms.date: 03/30/2017
helpviewer_keywords:
- failed QueryInterface
- FailedQI MDA
- QueryInterface call failures
- MDAs (managed debugging assistants), failed QueryInterface
- managed debugging assistants (MDAs), failed QueryInterface
ms.assetid: 902dc863-34b3-477c-b433-b8a6bb6133c6
ms.openlocfilehash: 2d7f14c67d47e58bcb88eab4621df63d7c598a7a
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415936"
---
# <a name="failedqi-mda"></a>failedQI MDA
當執行階段代表執行階段可呼叫包裝函式 (RCW)，在 COM 介面指標上呼叫 `QueryInterface`，而 `QueryInterface` 呼叫失敗時，就會啟動 `failedQI` Managed 偵錯助理 (MDA)。  
  
## <a name="symptoms"></a>徵狀  
 在 RCW 上轉換失敗，或從 RCW 呼叫 COM 時意外失敗。  
  
## <a name="cause"></a>原因  
  
- 從錯誤的內容進行呼叫。  
  
- 所註冊的 Proxy 導致 `QueryInterface` 呼叫失敗，因為是嘗試在錯誤的內容中呼叫。  
  
- OLE 擁有的 Proxy 傳回失敗 HRESULT。  
  
## <a name="resolution"></a>解決方案  
 請參閱有關 COM 規則的 MSDN 文件。  
  
## <a name="effect-on-the-runtime"></a>對執行階段的影響  
 如果 `QueryInterface` 呼叫失敗，內容就會切換，然後重新嘗試 `QueryInterface` 呼叫，以查看是否有不正確的內容出錯。  
  
## <a name="output"></a>輸出  
 介面的 Managed 名稱、介面的 GUID，以及失敗的 HRESULT。  
  
## <a name="configuration"></a>設定  
  
```xml  
<mdaConfig>  
  <assistants>  
    <failedQI/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [使用 Managed 偵錯助理診斷錯誤](diagnosing-errors-with-managed-debugging-assistants.md)
- [Interop 封送處理](../interop/interop-marshaling.md)
