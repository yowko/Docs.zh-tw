---
title: Interop ETW 事件
ms.date: 03/30/2017
helpviewer_keywords:
- interop events [.NET Framework]
- ETW, interop events (CLR)
ms.assetid: eb6eac2e-45f4-4923-a32c-38f203da66df
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 09b2848619256a255cc27f0268d46e5e6db8cbe4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59083604"
---
# <a name="interop-etw-events"></a>Interop ETW 事件
<a name="top"></a> Interop 事件會擷取 Microsoft 中繼語言 (MSIL) Stub 之產生和快取的相關資訊。  
  
 這個類別包含下列事件：  
  
-   [ILStubGenerated 事件](#ilstubgenerated_event)  
  
-   [ILStubCacheHit 事件](#ilstubcachehit_event)  
  
<a name="ilstubgenerated_event"></a>   
## <a name="ilstubgenerated-event"></a>ILStubGenerated 事件  
 下表說明關鍵字和層級。 (如需詳細資訊，請參閱 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md))。  
  
|引發事件的關鍵字|層級|  
|-----------------------------------|-----------|  
|`InteropKeyword` (0x2000)|Informational(4)|  
  
 下表說明事件資訊。  
  
|Event - 事件|事件 ID|引發的時機|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|88|已產生 MSIL 虛設常式。|  
  
 下表說明事件資料。  
  
|欄位名稱|資料類型|描述|  
|----------------|---------------|-----------------|  
|ModuleID|win:UInt16|模組識別項。|  
|StubMethodID|win:UInt64|虛設常式方法識別項。|  
|StubFlags|win:UInt64|虛設常式的旗標：<br /><br /> 0x1 - 反向 interop。<br /><br /> 0x2 - COM interop。<br /><br /> 0x4 - NGen.exe 所產生的虛設常式。<br /><br /> 0x8 - 委派。<br /><br /> 0x10 - 變數引數。<br /><br /> 0x20 - Unmanaged 被呼叫者。|  
|ManagedInteropMethodToken|win:UInt32|Managed interop 方法的語彙基元。|  
|ManagedInteropMethodNameSpace|win:UnicodeString|Managed interop 方法的命名空間。|  
|ManagedInteropMethodName|win:UnicodeString|Managed interop 方法的名稱。|  
|ManagedInteropMethodSignature|win:UnicodeString|Managed interop 方法的簽章。|  
|NativeMethodSignature|win:UnicodeString|原生方法簽章。|  
|StubMethodSignature|win:UnicodeString|虛設常式方法簽章。|  
|StubMethodILCode|win:UnicodeString|虛設常式方法的 MSIL 程式碼。|  
|ClrInstanceID|win:UInt16|CLR 或 CoreCLR 執行個體的唯一 ID。|  
  
 [回到頁首](#top)  
  
<a name="ilstubcachehit_event"></a>   
## <a name="ilstubcachehit-event"></a>ILStubCacheHit 事件  
 下表說明關鍵字和層級。  
  
|引發事件的關鍵字|層級|  
|-----------------------------------|-----------|  
|`InteropKeyword` (0x2000)|Informational(4)|  
  
 下表說明事件資訊。  
  
|Event - 事件|事件 ID|引發的時機|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|89|已存取 MSIL 快取。|  
  
 下表說明事件資料。  
  
|欄位名稱|資料類型|描述|  
|----------------|---------------|-----------------|  
|ModuleID|win:UInt16|模組識別項。|  
|StubMethodID|win:UInt64|虛設常式方法識別項。|  
|ManagedInteropMethodToken|win:UInt32|Managed interop 方法的語彙基元。|  
|ManagedInteropMethodNameSpace|win:UnicodeString|Managed interop 方法的命名空間。|  
|ManagedInteropMethodName|win:UnicodeString|Managed interop 方法的名稱。|  
|ManagedInteropMethodSignature|win:UnicodeString|Managed interop 方法的簽章。|  
|ClrInstanceID|win:UInt16|CLR 或 CoreCLR 執行個體的唯一 ID。|  
  
 [回到頁首](#top)  
  
## <a name="see-also"></a>另請參閱

- [CLR ETW 事件](../../../docs/framework/performance/clr-etw-events.md)
