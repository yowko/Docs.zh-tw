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
ms.openlocfilehash: 199a649b0481c2a740926636345eefbda6831ef2
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007542"
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
  
|成員|描述|  
|------------|-----------------|  
|`pmNoMangle`|使用指定的每個成員名稱。|  
|`pmCharSetMask`|已保留。|  
|`pmCharSetNotSpec`|已保留。|  
|`pmCharSetAnsi`|將字串當做多位元組字元字串來封送處理。|  
|`pmCharSetUnicode`|封送處理字串為 Unicode 2 個位元組字元。|  
|`pmCharSetAuto`|自動為目標作業系統妥善地封送處理字串。 Windows NT、Windows 2000、Windows XP 和 Windows Server 2003 系列上的預設值為 Unicode;Windows 98 和 Windows Me 上的預設值是 ANSI。|  
|`pmBestFitUseAssem`|已保留。|  
|`pmBestFitEnabled`|執行 Unicode 字元的自動調整對應，其在 ANSI 字元集中缺少完全相符的項。|  
|`pmBestFitDisabled`|請勿執行 Unicode 字元的自動調整對應。 在此情況下，所有無法映射的字元都會由 '？ ' 取代。|  
|`pmBestFitMask`|已保留。|  
|`pmThrowOnUnmappableCharUseAssem`|已保留。|  
|`pmThrowOnUnmappableCharEnabled`|當 interop 封送處理器遇到無法映射的字元時，擲回例外狀況。|  
|`pmThrowOnUnmappableCharDisabled`|當 interop 封送處理器遇到無法映射的字元時，不會擲回例外狀況。|  
|`pmThrowOnUnmappableCharMask`|Reserved|  
|`pmSupportsLastError`|允許被呼叫者在 `SetLastError` 從屬性化方法傳回之前呼叫 Win32 函式。|  
|`pmCallConvMask`|Reserved|  
|`pmCallConvWinapi`|使用預設的平臺呼叫慣例。 例如，在 Windows 上，預設值是 `StdCall` ，而在 Windows CE .net 則是 `Cdecl` 。|  
|`pmCallConvCdecl`|使用 `Cdecl` 呼叫慣例。 在此情況下，呼叫端會清除堆疊。 這可讓使用呼叫函式 `varargs` （也就是接受可變數目參數的函式）。|  
|`pmCallConvStdcall`|使用 `StdCall` 呼叫慣例。 在此情況下，被呼叫端會清除堆疊。 這是針對用平台叫用呼叫 Unmanaged 函式的預設慣例。|  
|`pmCallConvThiscall`|使用 `ThisCall` 呼叫慣例。 在此情況下，第一個參數是 `this` 指標，並儲存在 REGISTER ECX 中。 其他參數會被推入至堆疊。 `ThisCall`呼叫慣例是用來在從非受控 DLL 匯出的類別上呼叫方法。|  
|`pmCallConvFastcall`|已保留。|  
|`pmMaxValue`|已保留。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Corhdr.h。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](metadata-enumerations.md)
