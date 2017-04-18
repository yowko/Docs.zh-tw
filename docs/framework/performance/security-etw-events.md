---
title: "安全性 ETW 事件 | Microsoft Docs"
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
  - "ETW, 安全性事件 (CLR)"
  - "安全性事件 [.NET Framework]"
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
caps.latest.revision: 8
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# 安全性 ETW 事件
<a name="top"></a> 強式名稱驗證和 Authenticode 驗證期間，會引發安全性事件。  
  
 這個類別包含下列事件：  
  
-   [StrongNameVerificationStart\_V1 和 StrongNameVerificationStop\_V1 事件](#strongnameverificationstart_v1_and_strongnameverificationstop_v1_events)  
  
-   [AuthenticodeVerificationStart\_V1 和 AuthenticodeVerificationStop\_V1 事件](#authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events)  
  
<a name="strongnameverificationstart_v1_and_strongnameverificationstop_v1_events"></a>   
## StrongNameVerificationStart\_V1 和 StrongNameVerificationStop\_V1 事件  
 下表說明關鍵字和層級。 \(如需詳細資訊，請參閱 [CLR ETW 關鍵字和層級](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)\)。  
  
|引發事件的關鍵字|層級|  
|--------------|--------|  
|`SecurityKeyword` \(0x400\)|Informational\(4\)|  
  
 下表說明事件資訊。  
  
|事件|事件 ID|引發的時機|  
|--------|-----------|-----------|  
|`StrongNameVerificationStart_V1`|181|強式名稱驗證的開頭。|  
|`StrongNameVerificationStop_V1`|182|強式名稱驗證的結尾。|  
  
 下表說明事件資料。  
  
|欄位名稱|資料類型|描述|  
|----------|----------|--------|  
|VerificationFlags|win:UInt32|驗證旗標。|  
|ErrorCode|win:UInt32|HResult 錯誤碼。|  
|FullyQualifiedAssemblyName|win:UnicodeString|完整組件名稱。|  
|ClrInstanceID|win:UInt16|CLR 或 CoreCLR 執行個體的唯一 ID。|  
  
 [回到頁首](#top)  
  
<a name="authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events"></a>   
## AuthenticodeVerificationStart\_V1 和 AuthenticodeVerificationStop\_V1 事件  
 下表說明關鍵字和層級。  
  
|引發事件的關鍵字|層級|  
|--------------|--------|  
|`SecurityKeyword` \(0x400\)|Informational\(4\)|  
  
 下表說明事件資訊。  
  
|事件|事件 ID|引發的時機|  
|--------|-----------|-----------|  
|`AuthenticodeVerificationStart_V1`|183|Authenticode 驗證的開頭。|  
|`AuthenticodeVerificationStop_V1`|184|Authenticode 驗證的結尾。|  
  
 下表說明事件資料。  
  
|欄位名稱|資料類型|描述|  
|----------|----------|--------|  
|VerificationFlags|win:UInt32|驗證旗標。|  
|ErrorCode|win:UInt32|HResult 錯誤碼。|  
|ModulePath|win:UnicodeString|模組路徑。|  
|ClrInstanceID|win:UInt16|CLR 或 CoreCLR 執行個體的唯一 ID。|  
  
## 請參閱  
 [CLR ETW 事件](../../../docs/framework/performance/clr-etw-events.md)