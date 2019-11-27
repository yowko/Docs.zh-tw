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
ms.openlocfilehash: fda890cee5f513ea8cf7e82e710f5451a860c49f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443918"
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
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`afPublicKey`|表示元件參考包含完整、未經過雜湊的公開金鑰。|  
|`afPA_None`|表示未指定處理器架構。|  
|`afPA_MSIL`|表示處理器架構為中性（PE32）。|  
|`afPA_x86`|指出處理器架構為 x86 （PE32）。|  
|`afPA_IA64`|指出處理器架構為 Itanium （PE32 +）。|  
|`afPA_AMD64`|指出處理器架構是 AMD X64 （PE32 +）。|  
|`afPA_ARM`|指出處理器架構為 ARM （PE32）。|  
|`afPA_NoPlatform`|表示元件是參考元件;也就是說，它會套用至任何架構，但無法在任何架構上執行。 因此，旗標與 `afPA_Mask`相同。|  
|`afPA_Specified`|指出處理器架構旗標應該傳播至 `AssemblyRef` 記錄。|  
|`afPA_Mask`|描述處理器架構的遮罩。|  
|`afPA_FullMask`|指定包含處理器架構的描述。|  
|`afPA_Shift`|表示在處理器架構旗標中與索引之間的位移計數。|  
|`afEnableJITcompileTracking`|表示來自 <xref:System.Diagnostics.DebuggableAttribute>之 <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> 的對應值。|  
|`afDisableJITcompileOptimizer`|表示來自 <xref:System.Diagnostics.DebuggableAttribute>之 <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> 的對應值。|  
|`afRetargetable`|表示元件可以在執行時間重定目標，使其成為來自不同發行者的元件。|  
|`afContentType_Mask`|描述內容類型的遮罩。|  
|`afContentType_Default`|表示預設內容類型。|  
|`afContentType_WindowsRuntime`|表示 Windows 執行階段內容類型。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Corhdr.h。h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
