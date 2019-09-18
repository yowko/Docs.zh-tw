---
title: 安全性 ETW 事件
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8d09b5b76c39f33848d44beb43d9b09c5e6ed13b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046169"
---
# <a name="security-etw-events"></a>安全性 ETW 事件
<a name="top"></a> 強式名稱驗證和 Authenticode 驗證期間，會引發安全性事件。  
  
 這個類別包含下列事件：  
  
- [StrongNameVerificationStart_V1 和 StrongNameVerificationStop_V1 事件](#strongnameverificationstart_v1_and_strongnameverificationstop_v1_events)  
  
- [AuthenticodeVerificationStart_V1 和 AuthenticodeVerificationStop_V1 事件](#authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events)  
  
<a name="strongnameverificationstart_v1_and_strongnameverificationstop_v1_events"></a>   
## <a name="strongnameverificationstart_v1-and-strongnameverificationstop_v1-events"></a>StrongNameVerificationStart_V1 和 StrongNameVerificationStop_V1 事件  
 下表說明關鍵字和層級。 (如需詳細資訊，請參閱 [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md))。  
  
|引發事件的關鍵字|層級|  
|-----------------------------------|-----------|  
|`SecurityKeyword` (0x400)|Informational(4)|  
  
 下表說明事件資訊。  
  
|Event - 事件|事件 ID|引發的時機|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|181|強式名稱驗證的開頭。|  
|`StrongNameVerificationStop_V1`|182|強式名稱驗證的結尾。|  
  
 下表說明事件資料。  
  
|欄位名稱|資料類型|描述|  
|----------------|---------------|-----------------|  
|VerificationFlags|win:UInt32|驗證旗標。|  
|ErrorCode|win:UInt32|HResult 錯誤碼。|  
|FullyQualifiedAssemblyName|win:UnicodeString|完整組件名稱。|  
|ClrInstanceID|win:UInt16|CLR 或 CoreCLR 執行個體的唯一 ID。|  
  
 [回到頁首](#top)  
  
<a name="authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events"></a>   
## <a name="authenticodeverificationstart_v1-and-authenticodeverificationstop_v1-events"></a>AuthenticodeVerificationStart_V1 和 AuthenticodeVerificationStop_V1 事件  
 下表說明關鍵字和層級。  
  
|引發事件的關鍵字|層級|  
|-----------------------------------|-----------|  
|`SecurityKeyword` (0x400)|Informational(4)|  
  
 下表說明事件資訊。  
  
|Event - 事件|事件 ID|引發的時機|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|183|Authenticode 驗證的開頭。|  
|`AuthenticodeVerificationStop_V1`|184|Authenticode 驗證的結尾。|  
  
 下表說明事件資料。  
  
|欄位名稱|資料類型|描述|  
|----------------|---------------|-----------------|  
|VerificationFlags|win:UInt32|驗證旗標。|  
|ErrorCode|win:UInt32|HResult 錯誤碼。|  
|ModulePath|win:UnicodeString|模組路徑。|  
|ClrInstanceID|win:UInt16|CLR 或 CoreCLR 執行個體的唯一 ID。|  
  
## <a name="see-also"></a>另請參閱

- [CLR ETW 事件](clr-etw-events.md)
