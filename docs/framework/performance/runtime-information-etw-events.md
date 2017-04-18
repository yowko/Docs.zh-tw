---
title: "執行階段資訊 ETW 事件 | Microsoft Docs"
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
  - "ETW, 執行階段資訊事件"
  - "執行階段資訊事件 [.NET Framework]"
ms.assetid: 68b4edbc-7f3b-45f6-ab75-4fd066d6af9a
caps.latest.revision: 6
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 6
---
# 執行階段資訊 ETW 事件
這些 ETW 事件會記錄執行階段的相關資訊，包括 SKU、版本號碼、執行階段的啟動方式、用來啟動執行階段的命令列參數、GUID \(如果適用的話\)，以及其他相關資訊。  如果有多個執行階段在某個處理序內部執行，這些事件所提供的資訊 \(ClrInstanceID\) 就有助於區別執行階段。  
  
 下表顯示這兩個執行階段資訊事件。  這些事件可在任何關鍵字或遮罩下引發 \(如需詳細資訊，請參閱 [CLR ETW 關鍵字和層級](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)\)。  
  
|事件|事件識別碼|提供者|說明|  
|--------|-----------|---------|--------|  
|`RuntimeInformationEvent`|187|CLRRuntime|載入執行階段時引發。|  
|`RuntimeInformationDCStart`|187|CLRRundown|列舉已載入的執行階段。|  
  
 下表顯示事件資料。  
  
|欄位名稱|資料型別|說明|  
|----------|----------|--------|  
|ClrInstanceID|win:UInt16|CLR 或 CoreCLR 執行個體的唯一 ID。|  
|Sku|win:UInt16|1 – 桌面 CLR。<br /><br /> 2 – CoreCLR。|  
|BclVersion – 主要版本|win:UInt16|mscorlib.dll 的主要版本。|  
|BclVersion – 次要版本|win:UInt16|mscorlib.dll 的次要版本號碼。|  
|BclVersion – 組建編號|win:UInt16|mscorlib.dll 的組建編號。|  
|BclVersion – QFE|win:UInt16|mscorlib.dll 的 Hotfix 版本號碼。|  
|VMVersion – 主要版本|win:UInt16|clr.dll 或 coreclr.dll 的版本，取決於 SKU。|  
|VMVersion – 次要版本|win:UInt16|clr.dll 或 coreclr.dll 的次要版本，取決於 SKU。|  
|VMVersion – 組建編號|win:UInt16|clr.dll 或 coreclr.dll 的組建編號。|  
|VMVersion – QFE|win:UInt16|clr.dll 或 coreclr.dll 的 Hotfix 版本號碼。|  
|StartupFlags|win:UInt32|在 mscoree.h 中定義的旗標。|  
|StartupMode|win:UInt8|0x01 \- Managed 可執行檔。<br /><br /> 0x02 \- 裝載 CLR。<br /><br /> 0x04 \- C\+\+ Managed Interop。<br /><br /> 0x08 \- COM 啟動。<br /><br /> 0x10 \- 其他。|  
|CommandLine|win:UnicodeString|只有當 StartupMode\=0x01 時，才是非 null。|  
|ComObjectGUID|win:GUID|只有當 StartupMode\=0x08 時，才是非 null。|  
|RuntimeDLLPath|win:UnicodeString|已載入處理序之 CLR .dll 檔案的路徑。|  
  
## 請參閱  
 [CLR ETW 事件](../../../docs/framework/performance/clr-etw-events.md)