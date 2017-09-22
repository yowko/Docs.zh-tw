---
title: "應用程式定義域資源監視 (ARM) ETW 事件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
caps.latest.revision: 8
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a93e8cc1ab0b7488f920b556d2073d2813c3b7a9
ms.contentlocale: zh-tw
ms.lasthandoff: 08/21/2017

---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a>應用程式定義域資源監視 (ARM) ETW 事件
<a name="top"></a> 這些事件可提供有關應用程式網域狀態的詳細診斷資訊。 您可以使用這些事件或使用應用程式網域資源監視 (ARM) 功能，取得相同的資訊。  
  
 這個類別包含下列事件：  
  
-   [ThreadCreated 事件](#threadcreated_event)  
  
-   [AppDomainMemAllocated 事件](#appdomainmemallocated_event)  
  
-   [AppDomainMemSurvived 事件](#appdomainmemsurvived_event)  
  
-   [ThreadAppDomainEnter 事件](#threadappdomainenter_event)  
  
-   [ThreadTerminated 事件](#threadterminated_event)  
  
<a name="threadcreated_event"></a>   
## <a name="threadcreated-event"></a>ThreadCreated 事件  
 此事件在取消提供者之下也會引發為 `ThreadDC` (在 `AppDomainResourceManagementRundownKeyword` 關鍵字之下)。 此為在這類取消提供者之下引發的唯一事件  
  
 下表說明關鍵字和層級。 (如需詳細資訊，請參閱 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md))。  
  
|引發事件的關鍵字|層級|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` (0x800)|Informational(4)|  
|`ThreadingKeyword` (0x10000)|Informational(4)|  
  
 下表說明事件資訊。  
  
|事件|事件 ID|引發的時機|  
|-----------|--------------|-----------------|  
|`ThreadCreated`|85|已為應用程式網域建立執行緒。|  
  
 下表說明事件資料。  
  
|欄位名稱|資料類型|描述|  
|----------------|---------------|-----------------|  
|ThreadID|win:UInt64|已建立執行緒的識別碼。|  
|AppDomainID|win:UInt64|目前回報其執行緒活動之應用程式網域的識別項。|  
|旗標|win:UInt32|執行緒建立旗標。|  
|ManagedThreadIndex|win:UInt32|已建立之執行緒的 Managed 索引。|  
|OSThreadID|win:UInt32|已建立之執行緒的作業系統識別碼。|  
|ClrInstanceID|win:UInt16|CLR 或 CoreCLR 執行個體的唯一 ID。|  
  
 [回到頁首](#top)  
  
<a name="appdomainmemallocated_event"></a>   
## <a name="appdomainmemallocated-event"></a>AppDomainMemAllocated 事件  
 下表說明關鍵字和層級。  
  
|引發事件的關鍵字|層級|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` (0x800)|Informational(4)|  
  
 下表說明事件資訊。  
  
|事件|事件 ID|引發的時機|  
|-----------|--------------|-----------------|  
|`AppDomainMemAllocated`|83|每 4 MB 的記憶體 (大約)，配置於應用程式網域中。|  
  
 下表說明事件資料。  
  
|欄位名稱|資料類型|描述|  
|----------------|---------------|-----------------|  
|AppDomainID|win:UInt64|已回報其資源使用量之應用程式網域的識別項。|  
|已配置|win:UInt64|建立應用程式網域以來，配置於其中的位元組總數 (未減去釋放的記憶體總數)。|  
|ClrInstanceID|win:UInt16|CLR 或 CoreCLR 執行個體的唯一 ID。|  
  
 [回到頁首](#top)  
  
<a name="appdomainmemsurvived_event"></a>   
## <a name="appdomainmemsurvived-event"></a>AppDomainMemSurvived 事件  
 下表說明關鍵字和層級。  
  
|引發事件的關鍵字|層級|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` (0x800)|Informational(4)|  
  
 下表說明事件資訊。  
  
|事件|事件 ID|引發的時機|  
|-----------|--------------|-----------------|  
|`AppDomainMemSurvived`|84|已結束回收每個記憶體。|  
  
 下表說明事件資料。  
  
|欄位名稱|資料類型|描述|  
|----------------|---------------|-----------------|  
|AppDomainID|win:UInt64|已回報其資源使用量的網域識別項。|  
|存活的|win:UInt64|自上次回收作業後存留下來，且已知此應用程式網域持有之位元組的數目。 在完整收集之後，此數字即會正確且完整，但在短暫收集後可能會是不完整的。|  
|ProcessSurvived|win:UInt64|從最後一次集合中存活下來的位元組總數。 收集完成後，此數字代表存在於 Managed 堆積中的位元組數目。 暫時收集之後，此數字代表存在於短暫世代中的位元組數目。|  
|ClrInstanceID|win:UInt16|CLR 或 CoreCLR 執行個體的唯一 ID。|  
  
 [回到頁首](#top)  
  
<a name="threadappdomainenter_event"></a>   
## <a name="threadappdomainenter-event"></a>ThreadAppDomainEnter 事件  
 下表說明關鍵字和層級。  
  
|引發事件的關鍵字|層級|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` (0x800)|Informational(4)|  
|`ThreadingKeyword` (0x10000)|Informational(4)|  
  
 下表說明事件資訊。  
  
|事件|事件 ID|引發的時機|  
|-----------|--------------|-----------------|  
|`ThreadAppDomainEnter`|87|進入應用程式網域的執行緒。|  
  
 下表說明事件資料。  
  
|欄位名稱|資料類型|描述|  
|----------------|---------------|-----------------|  
|ThreadID|win:UInt64|執行緒識別碼。|  
|AppDomainID|win:UInt64|應用程式網域識別項。|  
|ClrInstanceID|win:UInt16|CLR 或 CoreCLR 執行個體的唯一 ID。|  
  
 [回到頁首](#top)  
  
<a name="threadterminated_event"></a>   
## <a name="threadterminated-event"></a>ThreadTerminated 事件  
 下表說明關鍵字和層級。  
  
|引發事件的關鍵字|層級|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` (0x800)|Informational(4)|  
|`ThreadingKeyword` (0x10000)|Informational(4)|  
  
 下表說明事件資訊。  
  
|事件|事件 ID|引發的時機|  
|-----------|--------------|-----------------|  
|`ThreadTerminated`|86|一個執行緒終止。|  
  
 下表說明事件資料：  
  
|欄位名稱|資料類型|描述|  
|----------------|---------------|-----------------|  
|ThreadID|win:UInt64|執行緒識別碼。|  
|AppDomainID|win:UInt64|應用程式網域識別項。|  
|ClrInstanceID|win:UInt16|CLR 或 CoreCLR 執行個體的唯一 ID。|  
  
## <a name="see-also"></a>另請參閱  
 [CLR ETW 事件](../../../docs/framework/performance/clr-etw-events.md)

