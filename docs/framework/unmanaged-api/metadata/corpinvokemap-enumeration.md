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
ms.openlocfilehash: 8216dc3030b18428ab52fbf8385d392f81057aa0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176145"
---
# <a name="corpinvokemap-enumeration"></a>CorPinvokeMap 列舉
指定 PInvoke 調用的選項。  
  
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
|`pmCharSetMask`|已保留。|  
|`pmCharSetNotSpec`|已保留。|  
|`pmCharSetAnsi`|將字串當做多位元組字元字串來封送處理。|  
|`pmCharSetUnicode`|封送處理字串為 Unicode 2 個位元組字元。|  
|`pmCharSetAuto`|自動為目標作業系統妥善地封送處理字串。 預設值為 Windows NT、Windows 2000、Windows XP 和 Windows Server 2003 系列上的 Unicode;預設值為 Windows 98 上的 ANSI 和 Windows Me。|  
|`pmBestFitUseAssem`|已保留。|  
|`pmBestFitEnabled`|對 ANSI 字元集中缺少完全符合的 Unicode 字元執行最佳映射。|  
|`pmBestFitDisabled`|不要執行最適合的 Unicode 字元映射。 在這種情況下，所有不可映射的字元將替換為"？"。|  
|`pmBestFitMask`|已保留。|  
|`pmThrowOnUnmappableCharUseAssem`|已保留。|  
|`pmThrowOnUnmappableCharEnabled`|當互通封送器遇到不可映射的字元時引發異常。|  
|`pmThrowOnUnmappableCharDisabled`|當互通封送器遇到不可映射的字元時，不要引發異常。|  
|`pmThrowOnUnmappableCharMask`|Reserved|  
|`pmSupportsLastError`|允許被調用人調用 Win32`SetLastError`函數，然後再從屬性化方法返回。|  
|`pmCallConvMask`|Reserved|  
|`pmCallConvWinapi`|使用預設平台叫用約定。 例如，在 Windows 上，`StdCall`預設值為 ，在 Windows `Cdecl`CE .NET 上，預設值為 。|  
|`pmCallConvCdecl`|使用`Cdecl`調用約定。 在這種情況下，調用方清理堆疊。 這允許調用函數（`varargs`即接受可變數量的參數的函數）。|  
|`pmCallConvStdcall`|使用`StdCall`調用約定。 在這種情況下，被叫人清理堆疊。 這是針對用平台叫用呼叫 Unmanaged 函式的預設慣例。|  
|`pmCallConvThiscall`|使用`ThisCall`調用約定。 在這種情況下，第一個參數是指標，`this`並存儲在寄存器 ECX 中。 其他參數會被推入至堆疊。 調用`ThisCall`約定用於調用從非託管 DLL 匯出的類上的方法。|  
|`pmCallConvFastcall`|已保留。|  
|`pmMaxValue`|已保留。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫德  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
