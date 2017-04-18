---
title: "方法 ETW 事件 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ETW, 方法事件 (CLR)"
  - "方法事件 [.NET Framework]"
ms.assetid: 167a4459-bb6e-476c-9046-7920880f2bb5
caps.latest.revision: 9
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 ETW 事件
<a name="top"></a> 這些事件會收集方法的特定資訊。 若要進行符號解析，需使用這些事件的承載。 此外，這些事件會提供實用資訊，例如呼叫方法的次數。  
  
 所有方法事件都具「告知性 \(4\)」的層級。 所有方法的詳細資訊事件都具「詳細資訊 \(5\)」的層級。  
  
 所有方法事件都是由執行階段提供者下的 `JITKeyword` \(0x10\) 關鍵字或 `NGenKeyword` \(0x20\) 關鍵字，或由取消提供者下的 `JitRundownKeyword` \(0x10\) 或 `NGENRundownKeyword` \(0x20\) 所引發。  
  
 CLR 方法事件會進一步細分為下列：  
  
-   [方法事件](#clr_method_events)  
  
-   [CLR 方法標記事件](#clr_method_marker_events)  
  
-   [CLR 方法詳細資料事件](#clr_method_verbose_events)  
  
-   [MethodJittingStarted 事件](#methodjittingstarted_event)  
  
<a name="clr_method_events"></a>   
## 方法事件  
 下表說明關鍵字和層級。 \(如需詳細資訊，請參閱 [CLR ETW 關鍵字和層級](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)\)。  
  
|引發事件的關鍵字|層級|  
|--------------|--------|  
|`JITKeyword` \(0x10\) 執行階段提供者|告知性 \(4\)|  
|`NGenKeyword` \(0x20\) 執行階段提供者|告知性 \(4\)|  
|`JitRundownKeyword` \(0x10\) 取消提供者|告知性 \(4\)|  
|`NGENRundownKeyword` \(0x20\) 取消提供者|告知性 \(4\)|  
  
 下表說明事件資訊。  
  
|事件|事件 ID|描述|  
|--------|-----------|--------|  
|`MethodLoad_V1`|136|在 Just\-In\-Time 載入 \(JIT 載入\) 方法或 NGEN 映像載入時引發。 動態和泛型的方法並不會使用這個版本的方法載入。 JIT Helper 永遠不會使用這個版本。|  
|`MethodUnLoad_V1`|137|在模組已卸載或應用程式定義域損毀時引發。 動態方法永遠不會使用這個版本的方法卸載。|  
|`MethodDCStart_V1`|137|於啟動取消期間列舉方法。|  
|`MethodDCEnd_V1`|138|於結束取消期間列舉方法。|  
  
 下表說明事件資料。  
  
|欄位名稱|資料類型|描述|  
|----------|----------|--------|  
|MethodID|win:UInt64|方法的唯一識別碼。 若是 JIT Helper 方法，其設為方法的起始位址。|  
|ModuleID|win:UInt64|這個方法所屬之模組的識別碼 \(0 代表 JIT Helper\)。|  
|MethodStartAddress|win:UInt64|方法的起始位址。|  
|MethodSize|win:UInt32|方法的大小。|  
|MethodToken|win:UInt32|0 代表動態方法和 JIT Helper。|  
|MethodFlags|win:UInt32|0x1：動態方法。<br /><br /> 0x2：泛型方法。<br /><br /> 0x4：JIT 編譯的程式碼方法 \(否則為 NGEN 原生映像程式碼\)。<br /><br /> 0x8：Helper 方法。|  
|ClrInstanceID|win:UInt16|CLR 或 CoreCLR 執行個體的唯一 ID。|  
  
 [回到頁首](#top)  
  
<a name="clr_method_marker_events"></a>   
## CLR 方法標記事件  
 只有在取消提供者下會引發這些事件。 它們表示在啟動或結束取消期間的方法列舉結尾。 \(也就是說，啟用 `NGENRundownKeyword`、`JitRundownKeyword`、`LoaderRundownKeyword`、或 `AppDomainResourceManagementRundownKeyword` 關鍵字時會將其引發。\)  
  
 下表說明關鍵字和層級。  
  
|引發事件的關鍵字|層級|  
|--------------|--------|  
|`AppDomainResourceManagementRundownKeyword` \(0x800\) 取消提供者|告知性 \(4\)|  
|`JitRundownKeyword` \(0x10\) 取消提供者|告知性 \(4\)|  
|`NGENRundownKeyword` \(0x20\) 取消提供者|告知性 \(4\)|  
  
 下表說明事件資訊。  
  
|事件|事件識別碼|說明|  
|--------|-----------|--------|  
|`DCStartInit_V1`|147|在啟動取消期間、列舉開始之前傳送。|  
|`DCStartComplete_V1`|145|在啟動取消期間、列舉結尾時傳送。|  
|`DCEndInit_V1`|148|在結束取消期間、開始列舉之前傳送。|  
|`DCEndComplete_V1`|146|在結束取消期間、列舉結尾時傳送。|  
  
 下表說明事件資料。  
  
|欄位名稱|資料類型|描述|  
|----------|----------|--------|  
|ClrInstanceID|win:UInt16|CLR 或 CoreCLR 執行個體的唯一 ID。|  
  
 [回到頁首](#top)  
  
<a name="clr_method_verbose_events"></a>   
## CLR 方法詳細資料事件  
 下表說明關鍵字和層級。  
  
|引發事件的關鍵字|層級|  
|--------------|--------|  
|`JITKeyword` \(0x10\) 執行階段提供者|詳細資訊 \(5\)|  
|`NGenKeyword` \(0x20\) 執行階段提供者|詳細資訊 \(5\)|  
|`JitRundownKeyword` \(0x10\) 取消提供者|詳細資訊 \(5\)|  
|`NGENRundownKeyword` \(0x20\) 取消提供者|詳細資訊 \(5\)|  
  
 下表說明事件資訊。  
  
|事件|事件 ID|描述|  
|--------|-----------|--------|  
|`MethodLoadVerbose_V1`|143|在 JIT 載入方法或 NGEN 映像載入時引發。 動態和泛型的方法一律會使用這個版本的方法載入。 JIT Helper 一律會使用這個版本。|  
|`MethodUnLoadVerbose_V1`|144|在動態方法損毀、模組已卸載或應用程式定義域損毀時引發。 動態方法永遠一律會使用這個版本的方法卸載。|  
|`MethodDCStartVerbose_V1`|141|於啟動取消期間列舉方法。|  
|`MethodDCEndVerbose_V1`|142|於結束取消期間列舉方法。|  
  
 下表說明事件資料。  
  
|欄位名稱|資料類型|描述|  
|----------|----------|--------|  
|MethodID|win:UInt64|方法的唯一識別項。 若是 JIT Helper 方法，其設為方法的起始位址。|  
|ModuleID|win:UInt64|這個方法所屬之模組的識別碼 \(0 代表 JIT Helper\)。|  
|MethodStartAddress|win:UInt64|起始位址：|  
|MethodSize|win:UInt32|方法的長度。|  
|MethodToken|win:UInt32|0 代表動態方法和 JIT Helper。|  
|MethodFlags|win:UInt32|0x1：動態方法。<br /><br /> 0x2：泛型方法。<br /><br /> 0x4：JIT 編譯方法 \(否則由 NGen.exe 產生\)<br /><br /> 0x8：Helper 方法。|  
|MethodNameSpace|win:UnicodeString|與方法相關聯的完整命名空間名稱。|  
|MethodName|win:UnicodeString|與方法相關聯的完整類別名稱。|  
|MethodSignature|win:UnicodeString|方法的簽章 \(以逗號分隔的類型名稱清單\)。|  
|ClrInstanceID|win:UInt16|CLR 或 CoreCLR 執行個體的唯一 ID。|  
  
 [回到頁首](#top)  
  
<a name="methodjittingstarted_event"></a>   
## MethodJittingStarted 事件  
 下表說明關鍵字和層級。  
  
|引發事件的關鍵字|層級|  
|--------------|--------|  
|`JITKeyword` \(0x10\) 執行階段提供者|詳細資訊 \(5\)|  
|`NGenKeyword` \(0x20\) 執行階段提供者|詳細資訊 \(5\)|  
|`JitRundownKeyword` \(0x10\) 取消提供者|詳細資訊 \(5\)|  
|`NGENRundownKeyword` \(0x20\) 取消提供者|詳細資訊 \(5\)|  
  
 下表說明事件資訊。  
  
|事件|事件 ID|描述|  
|--------|-----------|--------|  
|`MethodJittingStarted`|145|當某個方法正在進行 JIT 編譯時引發。|  
  
 下表說明事件資料。  
  
|欄位名稱|資料類型|描述|  
|----------|----------|--------|  
|MethodID|win:UInt64|方法的唯一識別項。|  
|ModuleID|win:UInt64|這個方法所屬之模組的識別碼。|  
|MethodToken|win:UInt32|0 代表動態方法和 JIT Helper。|  
|MethodILSize|win:UInt32|正在進行 JIT 編譯之方法的 Microsoft Intermediate Language \(MSIL\) 大小。|  
|MethodNameSpace|win:UnicodeString|與方法相關聯的完整類別名稱。|  
|MethodName|win:UnicodeString|方法的名稱。|  
|MethodSignature|win:UnicodeString|方法的簽章 \(以逗號分隔的類型名稱清單\)。|  
|ClrInstanceID|win:UInt16|CLR 或 CoreCLR 執行個體的唯一 ID。|  
  
## 請參閱  
 [CLR ETW 事件](../../../docs/framework/performance/clr-etw-events.md)