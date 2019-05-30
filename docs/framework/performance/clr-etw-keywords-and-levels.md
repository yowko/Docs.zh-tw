---
title: CLR ETW 關鍵字和層級
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW keywords
- CLR ETW levels
- ETW, CLR keywords
- ETW, CLR levels
ms.assetid: fdf5856d-516b-4042-849d-911c4518a6cb
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 519429da275c852ea193e95fe651cc73efc0736a
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/30/2019
ms.locfileid: "66378691"
---
# <a name="clr-etw-keywords-and-levels"></a>CLR ETW 關鍵字和層級
<a name="top"></a> Windows 事件追蹤 (ETW) 的事件可依分類和層級篩選。 事件 [CLR ETW 關鍵字](#keywords) 可以依分類啟用事件篩選；這些在執行階段和取消提供者時會加以組合使用。 [事件層級](#levels) 會標以旗標識別。  
  
<a name="keywords"></a>   
## <a name="clr-etw-keywords"></a>CLR ETW 關鍵字  
 關鍵字即為旗標，加以組合後可用以產生值。 在做法上，當您呼叫命令列公用程式時，是使用關鍵字的十六進位值，而不是關鍵字名稱。  
  
 下表是關鍵字的說明：  
  
- [CLR ETW 執行階段關鍵字](#runtime)  
  
- [CLR ETW 取消關鍵字](#rundown)  
  
- [執行階段提供者之符號解析的關鍵字組合](#runtime_combo)  
  
- [取消提供者之符號解析的關鍵字組合](#rundown_combo)  
  
<a name="runtime"></a>   
### <a name="clr-etw-runtime-keywords"></a>CLR ETW 執行階段關鍵字  
 下表列出 CLR ETW 執行階段關鍵字、其值及用途。  
  
|執行階段關鍵字名稱|值|用途|  
|--------------------------|-----------|-------------|  
|`GCKeyword`|0x00000001|啟用 [記憶體回收事件](../../../docs/framework/performance/garbage-collection-etw-events.md)收集。|  
|`LoaderKeyword`|0x00000008|啟用 [載入器事件](../../../docs/framework/performance/loader-etw-events.md)收集。|  
|`JITKeyword`|0x00000010|啟用 [just-in-time (JIT) 事件](../../../docs/framework/performance/jit-tracing-etw-events.md)收集。|  
|`NGenKeyword`|0x00000020|啟用原生映像方法 (由原生映像產生器 Ngen.exe 處理) 的事件收集；這會與 `StartEnumerationKeyword` 與 `EndEnumerationKeyword`搭配使用。 此關鍵字的額外負荷很高。 它會為所載入之每個 NGen 模組內的所有方法產生事件。 如有可能，建議您使用程式碼剖析工具產生的程式資料庫 (PDB)，從 NGen 模組擷取方法的相關資訊，而不要使用此關鍵字。 另請參閱本表後文的 `OverrideAndSuppressNGenEventsKeyword` 。|  
|`StartEnumerationKeyword`|0x00000040|啟用在執行階段期間列舉所有方法；這會與 `NGenKeyword`搭配使用。|  
|`EndEnumerationKeyword`|0x00000080|啟用在執行階段期間列舉所有方法；這會與 `JITKeyword` 和 `NGenKeyword`搭配使用。|  
|`SecurityKeyword`|0x00000400|啟用 [安全性事件](../../../docs/framework/performance/security-etw-events.md)收集。|  
|`AppDomainResourceManagementKeyword`|0x00000800|啟用在應用程式網域層級之資源監視事件收集。|  
|`JITTracingKeyword`|0x00001000|啟用 [JIT 追蹤事件](../../../docs/framework/performance/jit-tracing-etw-events.md)收集。|  
|`InteropKeyword`|0x00002000|啟用 [Interop 事件](../../../docs/framework/performance/interop-etw-events.md)收集。|  
|`ContentionKeyword`|0x00004000|啟用 [爭用事件](../../../docs/framework/performance/contention-etw-events.md)收集。|  
|`ExceptionKeyword`|0x00008000|啟用 [例外事件](../../../docs/framework/performance/exception-thrown-v1-etw-event.md)收集。|  
|`ThreadingKeyword`|0x00010000|啟用 [執行緒集區](../../../docs/framework/performance/thread-pool-etw-events.md)收集。|  
|`OverrideAndSuppressNGenEventsKeyword`|0x00040000|（可在.NET Framework 4.5 和更新版本。）隱藏高額外負荷的 `NGenKeyword` 關鍵字，並避免 NGen 模組內的方法產生事件。 從.NET Framework 4.5 開始，程式碼剖析工具應該使用`OverrideAndSuppressNGenEventsKeyword`和`NGenKeyword`在一起，以抑制 NGen 模組中的方法產生事件。 這可以讓程式碼剖析工具更有效率地使用 NGen PDB，從而取得 NGen 模組中方法的相關資訊。 .NET Framework 4 與更舊版本中的 CLR 不支援 NGen PDB 建立。 在這些舊版本中，CLR 不會辨識 `OverrideAndSuppressNGenEventsKeyword` ，並會處理 `NGenKeyword` ，以為 NGen 模組中的方法產生事件。|  
|`PerfTrackKeyWord`|0x2000000|啟用 `ModuleLoad` 和 `ModuleRange` 事件的收集。|  
|`StackKeyword`|0x40000000|啟用 CLR [堆疊追蹤事件](../../../docs/framework/performance/stack-etw-event.md)收集。|  
  
 [回到頁首](#top)  
  
<a name="rundown"></a>   
### <a name="clr-etw-rundown-keywords"></a>CLR ETW 取消關鍵字  
 下表列出 CLR ETW 執行階段關鍵字、其值及用途。  
  
|執行階段關鍵字名稱|值|用途|  
|--------------------------|-----------|-------------|  
|`LoaderRundownKeyword`|0x00000008|啟用 `StartRundownKeyword` 和 `EndRundownKeyword`搭配使用時的載入器事件收集。|  
|`JitRundownKeyword`|0x00000010|啟用 `DCStart` 和 `DCEnd` 搭配使用時，方法 `StartRundownKeyword` 和 JIT 編譯之方法的 `EndRundownKeyword`事件收集。|  
|`NGenRundownKeyword`|0x00000020|啟用 `DCStart` 和 `DCEnd` 搭配使用時，方法 `StartRundownKeyword` 和 JIT 編譯之方法的 `EndRundownKeyword`事件收集。 此關鍵字的額外負荷很高。 它會為所載入之每個 NGen 模組內的所有方法產生事件。 如有可能，建議您使用程式碼剖析工具產生的程式資料庫 (PDB)，從 NGen 模組擷取方法的相關資訊，而不要使用此關鍵字。 另請參閱本表後文的 `OverrideAndSuppressNGenEventsRundownKeyword` 。|  
|`StartRundownKeyword`|0x00000040|啟用在開始取消期間的系統狀態列舉。|  
|`EndRundownKeyword`|0x00000100|啟用在結束取消期間的系統狀態列舉。|  
|`AppDomainResourceManagementRundownKeyword`|0x00000800|啟用 <xref:System.AppDomain> 或 `StartRundownKeyword` .搭配使用時， `EndRundownKeyword`層級的資源監控事件收集。|  
|`ThreadingKeyword`|0x00010000|啟用執行緒集區事件收集。|  
|`OverrideAndSuppressNGenEventsRundownKeyword`|0x00040000|（可在.NET Framework 4.5 和更新版本。）隱藏高額外負荷的 `NGenRundownKeyword` 關鍵字，並避免 NGen 模組內的方法產生事件。 從.NET Framework 4.5 開始，程式碼剖析工具應該使用`OverrideAndSuppressNGenEventsRundownKeyword`和`NGenRundownKeyword`在一起，以抑制 NGen 模組中的方法產生事件。 這可以讓程式碼剖析工具更有效率地使用 NGen PDB，從而取得 NGen 模組中方法的相關資訊。 .NET Framework 4 與更舊版本中的 CLR 不支援 NGen PDB 建立。 在這些舊版本中，CLR 不會辨識 `OverrideAndSuppressNGenEventsRundownKeyword` ，並會處理 `NGenRundownKeyword` ，以為 NGen 模組中的方法產生事件。|  
|`PerfTrackKeyWord`|0x2000000|啟用 `ModuleDCStart`、 `ModuleDCEnd`、 `ModuleRangeDCStart`及 `ModuleRangeDCEnd` 事件的收集。|  
  
 [回到頁首](#top)  
  
<a name="runtime_combo"></a>   
### <a name="keyword-combinations-for-symbol-resolution-for-the-runtime-provider"></a>執行階段提供者之符號解析的關鍵字組合  
  
|關鍵字和旗標|應用程式網域、組件、模組載入/卸載事件|方法載入/卸載事件 (動態事件除外)|動態方法載入/終結事件|  
|------------------------|--------------------------------------------------------------|----------------------------------------------------------|-----------------------------------------|  
|`LoaderKeyword`|載入和卸載事件。|無。|無。|  
|`JITKeyword`<br /><br /> (+ `StartEnumerationKeyword` 不會加入任何項目)|無。|載入事件。|載入和卸載事件。|  
|`JITKeyword` +<br /><br /> `EndEnumerationKeyword`|無。|載入和卸載事件。|載入和卸載事件。|  
|`NGenKeyword`|無。|無。|不適用。|  
|`NGenKeyword` +<br /><br /> `StartEnumerationKeyword`|無。|載入事件。|不適用。|  
|`NGenKeyword` +<br /><br /> `EndEnumerationKeyword`|無。|載入事件。|不適用。|  
  
 [回到頁首](#top)  
  
<a name="rundown_combo"></a>   
### <a name="keyword-combinations-for-symbol-resolution-for-the-rundown-provider"></a>取消提供者之符號解析的關鍵字組合  
  
|關鍵字和旗標|應用程式網域、附屬組件、模組 DCStart/DCEnd 事件|方法 DCStart/DCEnd 事件 (包括動態方法事件)|  
|------------------------|----------------------------------------------------------------|----------------------------------------------------------------------|  
|`LoaderRundownKeyword` +<br /><br /> `StartRundownKeyword`|`DCStart` 事件。|無。|  
|`LoaderRundownKeyword` +<br /><br /> `EndRundownKeyword`|`DCEnd` 事件。|無。|  
|`JITKeyword` +<br /><br /> `StartRundownKeyword`|無。|`DCStart` 事件。|  
|`JITKeyword` +<br /><br /> `EndRundownKeyword`|無。|`DCEnd` 事件。|  
|`NGenKeyword` +<br /><br /> `StartRundownKeyword`|無。|`DCStart` 事件。|  
|`NGenKeyword` +<br /><br /> `EndRundownKeyword`|無。|`DCEnd` 事件。|  
  
 [回到頁首](#top)  
  
<a name="levels"></a>   
## <a name="etw-event-levels"></a>ETW 事件層級  
 ETW 事件也可以用層級篩選。 如果層級設定於 0x5，會引發 0x5 以下 (含) 的所有層級事件 (這些事件屬於透過鍵盤啟用的分類) 。 如果層級設定於 0x2，只會引發層級 0x2 以下 (含) 的事件。  
  
 層級具有下列意義：  
  
 0x5 - 詳細資訊  
  
 0x4 - 資訊  
  
 0x3 - 警告  
  
 0x2 - 錯誤  
  
 0x1 - 嚴重  
  
 0x0 - 永遠記錄  
  
## <a name="see-also"></a>另請參閱

- [CLR ETW 提供者](../../../docs/framework/performance/clr-etw-providers.md)
- [CLR ETW 事件](../../../docs/framework/performance/clr-etw-events.md)
- [Common Language Runtime 中的 ETW 事件](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
