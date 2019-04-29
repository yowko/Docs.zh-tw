---
title: Exception Thrown_V1 ETW 事件
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dd322d25d91bb277a4c817594c968c28a6d61d68
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61723013"
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
|ExceptionFlags|win:UInt16|0x01:0x01:hasinnerexception (請參閱[CLR ETW 事件](../../../docs/framework/performance/clr-etw-events.md)Visual Basic 文件中)。<br /><br /> 0x02:IsNestedException.<br /><br /> 0x04:0x04:isrethrownexception。<br /><br /> 0x08:0x08:iscorruptedstateexception (表示處理序狀態已損毀，請參閱[處理損毀狀態例外狀況](https://go.microsoft.com/fwlink/?LinkId=179681)MSDN 上)。<br /><br /> 0x10:0x10:isclscompliant (衍生自例外狀況<xref:System.Exception>符合 CLS 規範，否則它不符合 CLS 標準)。|  
|ClrInstanceID|win:UInt16|CLR 或 CoreCLR 執行個體的唯一 ID。|  
  
## <a name="see-also"></a>另請參閱

- [CLR ETW 事件](../../../docs/framework/performance/clr-etw-events.md)
