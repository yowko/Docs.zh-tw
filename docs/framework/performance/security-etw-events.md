---
title: 安全性 ETW 事件
description: 瞭解安全性 ETW 事件，這會在 .NET 中的強式名稱驗證和 Authenticode 驗證期間引發。
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
ms.openlocfilehash: 2fd2d450223cd16a7791b8f6c67afe6bcb954eb3
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474211"
---
# <a name="security-etw-events"></a>安全性 ETW 事件

強式名稱驗證和 Authenticode 驗證期間，會引發安全性事件。  

## <a name="strongnameverificationstart_v1-and-strongnameverificationstop_v1-events"></a>StrongNameVerificationStart_V1 和 StrongNameVerificationStop_V1 事件  
 下表說明關鍵字和層級。 (如需詳細資訊，請參閱 [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md))。  
  
|引發事件的關鍵字|層級|  
|-----------------------------------|-----------|  
|`SecurityKeyword` (0x400)|Informational(4)|  
  
 下表說明事件資訊。  
  
|事件|事件識別碼|引發的時機|  
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

## <a name="authenticodeverificationstart_v1-and-authenticodeverificationstop_v1-events"></a>AuthenticodeVerificationStart_V1 和 AuthenticodeVerificationStop_V1 事件  
 下表說明關鍵字和層級。  
  
|引發事件的關鍵字|層級|  
|-----------------------------------|-----------|  
|`SecurityKeyword` (0x400)|Informational(4)|  
  
 下表說明事件資訊。  
  
|事件|事件識別碼|引發的時機|  
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
