---
title: Exception Thrown_V1 ETW 事件
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 865b7b16d5807bd9161855f453128a63c84eab96
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43505219"
---
# <a name="exception-thrownv1-etw-event"></a>Exception Thrown_V1 ETW 事件
此事件會擷取被擲回的例外狀況相關資訊。  
  
 下表顯示引發事件的關鍵字以及事件層級。 (如需詳細資訊，請參閱 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md))。  
  
|引發事件的關鍵字|層級|  
|-----------------------------------|-----------|  
|`ExceptionKeyword` (0x8000)|警告 (2)|  
  
 下表顯示事件資訊。  
  
|Event - 事件|事件 ID|引發的時機|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|80|擲回 Managed 例外狀況。|  
  
 下表顯示事件資料。  
  
|欄位名稱|資料類型|描述|  
|----------------|---------------|-----------------|  
|例外狀況類型|win:UnicodeString|例外狀況類型，例如 `System.NullReferenceException`。|  
|例外狀況訊息|win:UnicodeString|實際的例外狀況訊息。|  
|EIPCodeThrow|win:Pointer|發生例外狀況的指令指標。|  
|ExceptionHR|win:UInt32|例外狀況 [HRESULT](https://go.microsoft.com/fwlink/?LinkId=179679)。|  
|ExceptionFlags|win:UInt16|0x01：HasInnerException (請參閱 Visual Basic 文件的 [CLR ETW 事件](../../../docs/framework/performance/clr-etw-events.md))。<br /><br /> 0x02：IsNestedException。<br /><br /> 0x04：IsRethrownException。<br /><br /> 0x08：IsCorruptedStateException (表示處理序狀態已損毀，請參閱 MSDN 上的[處理損毀狀態的例外狀況](https://go.microsoft.com/fwlink/?LinkId=179681))。<br /><br /> 0x10：IsCLSCompliant (衍生自 <xref:System.Exception> 的例外狀況符合 CLS 標準，否則與 CLS 不相容)。|  
|ClrInstanceID|win:UInt16|CLR 或 CoreCLR 執行個體的唯一 ID。|  
  
## <a name="see-also"></a>另請參閱  
 [CLR ETW 事件](../../../docs/framework/performance/clr-etw-events.md)
