---
title: "CorPinvokeMap 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorPinvokeMap
api_location: mscoree.dll
api_type: COM
f1_keywords: CorPinvokeMap
helpviewer_keywords: CorPinvokeMap enumeration [.NET Framework metadata]
ms.assetid: f14f986e-f6ce-42bc-aa23-18150c46d28c
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0e0771ce54e7e2973525bfcf4aba4c1f7ddf0a52
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="corpinvokemap-enumeration"></a>CorPinvokeMap 列舉
指定 PInvoke 呼叫的選項。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum  CorPinvokeMap {  
  
    pmNoMangle          = 0x0001,  
  
    pmCharSetMask       = 0x0006,  
    pmCharSetNotSpec    = 0x0000,  
    pmCharSetAnsi       = 0x0002,  
    pmCharSetUnicode    = 0x0004,  
    pmCharSetAuto       = 0x0006,  
  
    pmBestFitUseAssem   = 0x0000,  
    pmBestFitEnabled    = 0x0010,  
    pmBestFitDisabled   = 0x0020,  
    pmBestFitMask       = 0x0030,  
  
    pmThrowOnUnmappableCharUseAssem   = 0x0000,  
    pmThrowOnUnmappableCharEnabled    = 0x1000,  
    pmThrowOnUnmappableCharDisabled   = 0x2000,  
    pmThrowOnUnmappableCharMask       = 0x3000,  
  
    pmSupportsLastError = 0x0040,   
  
    pmCallConvMask      = 0x0700,  
    pmCallConvWinapi    = 0x0100,  
    pmCallConvCdecl     = 0x0200,  
    pmCallConvStdcall   = 0x0300,  
    pmCallConvThiscall  = 0x0400,  
    pmCallConvFastcall  = 0x0500,  
  
    pmMaxValue          = 0xFFFF  
  
} CorPinvokeMap;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`pmNoMangle`|使用指定的每個成員名稱。|  
|`pmCharSetMask`|保留的。|  
|`pmCharSetNotSpec`|保留的。|  
|`pmCharSetAnsi`|封送處理字串為多位元組字元字串。|  
|`pmCharSetUnicode`|封送處理為 Unicode 2 位元組字元的字串。|  
|`pmCharSetAuto`|會自動封送處理字串適用於目標作業系統。 預設值是 Windows NT、 Windows 2000、 Windows XP 和 Windows Server 2003 系列; 上的為 Unicode預設值是 Windows 98 和 Windows me 上的為 ANSI|  
|`pmBestFitUseAssem`|保留的。|  
|`pmBestFitEnabled`|執行沒有完全符合 ANSI 字元集中的 Unicode 字元的自動調整的對應。|  
|`pmBestFitDisabled`|不會執行自動調整的對應 Unicode 字元。 在此情況下，所有無法對應的字元會被 '？ '。|  
|`pmBestFitMask`|保留的。|  
|`pmThrowOnUnmappableCharUseAssem`|保留的。|  
|`pmThrowOnUnmappableCharEnabled`|Interop 封送處理器遇到無法對應的字元時，會擲回例外狀況。|  
|`pmThrowOnUnmappableCharDisabled`|Interop 封送處理器遇到無法對應的字元時，請確實擲回例外狀況。|  
|`pmThrowOnUnmappableCharMask`|保留|  
|`pmSupportsLastError`|可讓被呼叫端呼叫 Win32`SetLastError`屬性化方法在傳回前的函式。|  
|`pmCallConvMask`|保留|  
|`pmCallConvWinapi`|使用預設平台的呼叫慣例。 例如，在 Windows 上預設值是`StdCall`以及它是 Windows CE.NET `Cdecl`。|  
|`pmCallConvCdecl`|使用`Cdecl`呼叫慣例。 在此情況下，呼叫端會清除堆疊。 這可讓呼叫的函式與`varargs`（也就是函式接受多個參數）。|  
|`pmCallConvStdcall`|使用`StdCall`呼叫慣例。 在此情況下，被呼叫端會清除堆疊。 這是呼叫 unmanaged 函式，使用平台叫用的預設慣例。|  
|`pmCallConvThiscall`|使用`ThisCall`呼叫慣例。 在此情況下，第一個參數是`this`指標並儲存在暫存器 ECX。 其他參數會推送至堆疊上。 `ThisCall`呼叫慣例用於呼叫從 unmanaged 的 DLL 匯出的類別上的方法。|  
|`pmCallConvFastcall`|保留的。|  
|`pmMaxValue`|保留的。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorHdr.h  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
