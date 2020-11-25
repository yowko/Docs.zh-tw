---
title: CorPinvokeMap 列舉
ms.date: 03/30/2017
api_name:
- CorPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPinvokeMap
helpviewer_keywords:
- CorPinvokeMap enumeration [.NET Framework metadata]
ms.assetid: f14f986e-f6ce-42bc-aa23-18150c46d28c
topic_type:
- apiref
ms.openlocfilehash: da3ee54b1c3361149c11a9cfad8bdb07a5007ecf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706134"
---
# <a name="corpinvokemap-enumeration"></a>CorPinvokeMap 列舉

指定 PInvoke 呼叫的選項。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
  
|member|描述|  
|------------|-----------------|  
|`pmNoMangle`|使用指定的每個成員名稱。|  
|`pmCharSetMask`|保留的。|  
|`pmCharSetNotSpec`|保留的。|  
|`pmCharSetAnsi`|將字串當做多位元組字元字串來封送處理。|  
|`pmCharSetUnicode`|封送處理字串為 Unicode 2 個位元組字元。|  
|`pmCharSetAuto`|自動為目標作業系統妥善地封送處理字串。 預設值是 Windows NT、Windows 2000、Windows XP 及 Windows Server 2003 系列上的 Unicode;預設值是 Windows 98 和 Windows Me 上的 ANSI。|  
|`pmBestFitUseAssem`|保留的。|  
|`pmBestFitEnabled`|對 ANSI 字元集中缺少完全相符的 Unicode 字元執行最符合的對應。|  
|`pmBestFitDisabled`|請勿對 Unicode 字元執行最符合的對應。 在此情況下，所有無法映射的字元都會被 '？ ' 取代。|  
|`pmBestFitMask`|保留的。|  
|`pmThrowOnUnmappableCharUseAssem`|保留的。|  
|`pmThrowOnUnmappableCharEnabled`|當 interop 封送處理器遇到無法映射的字元時，會擲回例外狀況。|  
|`pmThrowOnUnmappableCharDisabled`|當 interop 封送處理器遇到無法映射的字元時，請勿擲回例外狀況。|  
|`pmThrowOnUnmappableCharMask`|保留|  
|`pmSupportsLastError`|允許被呼叫者呼叫 Win32 函式， `SetLastError` 再從屬性化方法傳回。|  
|`pmCallConvMask`|保留|  
|`pmCallConvWinapi`|使用預設的平臺呼叫慣例。 例如，在 Windows 上，預設值為 `StdCall` ，而在 Windows CE .net 則為 `Cdecl` 。|  
|`pmCallConvCdecl`|使用 `Cdecl` 呼叫慣例。 在此情況下，呼叫端會清除堆疊。 這樣就可以使用 (來呼叫函式 `varargs` ，也就是接受) 參數數目的函式。|  
|`pmCallConvStdcall`|使用 `StdCall` 呼叫慣例。 在此情況下，被呼叫端會清除堆疊。 這是針對用平台叫用呼叫 Unmanaged 函式的預設慣例。|  
|`pmCallConvThiscall`|使用 `ThisCall` 呼叫慣例。 在此情況下，第一個參數是 `this` 指標，並儲存在 REGISTER ECX 中。 其他參數會被推入至堆疊。 `ThisCall`呼叫慣例可用來呼叫從非受控 DLL 匯出之類別的方法。|  
|`pmCallConvFastcall`|保留的。|  
|`pmMaxValue`|保留的。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Corhdr.h。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](metadata-enumerations.md)
