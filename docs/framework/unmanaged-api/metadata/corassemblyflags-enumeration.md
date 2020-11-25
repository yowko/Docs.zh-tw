---
title: CorAssemblyFlags 列舉
ms.date: 03/30/2017
api_name:
- CorAssemblyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorAssemblyFlags
helpviewer_keywords:
- CorAssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: bb8db3b6-d81d-49fc-b74c-dbc908a9eab9
topic_type:
- apiref
ms.openlocfilehash: 615c4ac95ab777e8081e630cafb6671e64dea78a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718978"
---
# <a name="corassemblyflags-enumeration"></a>CorAssemblyFlags 列舉

包含值，這些值描述套用至組件編譯的中繼資料。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum CorAssemblyFlags {  
  
    afPublicKey             =   0x0001,  
    afPA_None               =   0x0000,  
    afPA_MSIL               =   0x0010,  
    afPA_x86                =   0x0020,  
    afPA_IA64               =   0x0030,  
    afPA_AMD64              =   0x0040,  
    afPA_ARM                =   0x0050,  
    afPA_NoPlatform         =   0x0070,  
    afPA_Specified          =   0x0080,  
    afPA_Mask               =   0x0070,  
    afPA_FullMask           =   0x00F0,  
    afPA_Shift              =   0x0004,  
  
    afEnableJITcompileTracking  =   0x8000,  
    afDisableJITcompileOptimizer=   0x4000,  
  
    afRetargetable          =   0x0100,  
    afContentType_Default        =   0x0000,  
    afContentType_WindowsRuntime =   0x0200,  
    afContentType_Mask           =   0x0E00,  
  
} CorAssemblyFlags;  
```  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`afPublicKey`|指出元件參考包含完整、未雜湊的公開金鑰。|  
|`afPA_None`|指出未指定處理器架構。|  
|`afPA_MSIL`|表示處理器架構為中性 (PE32) 。|  
|`afPA_x86`|指出處理器架構為 x86 (PE32) 。|  
|`afPA_IA64`|指出處理器架構為 Itanium (PE32 +) 。|  
|`afPA_AMD64`|指出處理器架構為 AMD X64 (PE32 +) 。|  
|`afPA_ARM`|指出處理器架構為 ARM (PE32) 。|  
|`afPA_NoPlatform`|表示元件為參考元件;也就是說，它會套用至任何架構，但無法在任何架構上執行。 因此，旗標與相同 `afPA_Mask` 。|  
|`afPA_Specified`|指出處理器架構旗標應傳播至 `AssemblyRef` 記錄。|  
|`afPA_Mask`|描述處理器架構的遮罩。|  
|`afPA_FullMask`|指定包含處理器架構描述。|  
|`afPA_Shift`|指出處理器架構旗標中與索引之間的移位元數目。|  
|`afEnableJITcompileTracking`|指出的對應值 <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> <xref:System.Diagnostics.DebuggableAttribute> 。|  
|`afDisableJITcompileOptimizer`|指出的對應值 <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> <xref:System.Diagnostics.DebuggableAttribute> 。|  
|`afRetargetable`|表示元件在執行時間可以從不同發行者的元件重定目標。|  
|`afContentType_Mask`|描述內容類型的遮罩。|  
|`afContentType_Default`|表示預設內容類型。|  
|`afContentType_WindowsRuntime`|指出 Windows 執行階段的內容類型。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Corhdr.h。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](metadata-enumerations.md)
