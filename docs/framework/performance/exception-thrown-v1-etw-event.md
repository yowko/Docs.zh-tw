---
title: Exception Thrown_V1 ETW 事件
description: 查看 ExceptionThrown_V1 ETW 事件的詳細資訊。 系統會為擲回的例外狀況指定事件資料，例如功能變數名稱、資料類型和描述。
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
ms.openlocfilehash: c1ba994b291bd278a95e34beb0b02ed6581786e8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263473"
---
# <a name="exception-thrown_v1-etw-event"></a>Exception Thrown_V1 ETW 事件

此事件會擷取被擲回的例外狀況相關資訊。  
  
 下表顯示引發事件的關鍵字以及事件層級。 (如需詳細資訊，請參閱 [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md))。  
  
|引發事件的關鍵字|層級|  
|-----------------------------------|-----------|  
|`ExceptionKeyword` (0x8000)|警告 (2)|  
  
 下表顯示事件資訊。  
  
|事件|事件識別碼|引發的時機|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|80|擲回 Managed 例外狀況。|  
  
 下表顯示事件資料。  
  
|欄位名稱|資料類型|描述|  
|----------------|---------------|-----------------|  
|例外狀況類型|win:UnicodeString|例外狀況類型，例如 `System.NullReferenceException`。|  
|例外狀況訊息|win:UnicodeString|實際的例外狀況訊息。|  
|EIPCodeThrow|win:Pointer|發生例外狀況的指令指標。|  
|ExceptionHR|win:UInt32|例外狀況 [HRESULT](/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a)。|  
|ExceptionFlags|win:UInt16|0x01：HasInnerException (請參閱 Visual Basic 文件的 [CLR ETW 事件](clr-etw-events.md))。<br /><br /> 0x02：IsNestedException。<br /><br /> 0x04：IsRethrownException。<br /><br /> 0x08： IsCorruptedStateException (表示進程狀態已損毀;請參閱 [處理損毀狀態例外狀況](/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)) 。<br /><br /> 0x10：IsCLSCompliant (衍生自 <xref:System.Exception> 的例外狀況符合 CLS 標準，否則與 CLS 不相容)。|  
|ClrInstanceID|win:UInt16|CLR 或 CoreCLR 執行個體的唯一 ID。|  
  
## <a name="see-also"></a>另請參閱

- [CLR ETW 事件](clr-etw-events.md)
