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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eca4b66a3f7c1a96bb06827dde477f34cb904ba3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072710"
---
# <a name="corassemblyflags-enumeration"></a>CorAssemblyFlags 列舉
包含值，這些值描述套用至組件編譯的中繼資料。  
  
## <a name="syntax"></a>語法  
  
```  
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
  
|成員|描述|  
|------------|-----------------|  
|`afPublicKey`|表示組件參考會保留完整的雜湊的公用金鑰。|  
|`afPA_None`|表示未指定的處理器架構。|  
|`afPA_MSIL`|指出處理器架構是中性 (PE32)。|  
|`afPA_x86`|指出處理器架構為 x86 (PE32)。|  
|`afPA_IA64`|指示處理器架構為 Itanium （PE32 +）。|  
|`afPA_AMD64`|指出處理器架構的 AMD X64 （PE32 +）。|  
|`afPA_ARM`|指出處理器架構是 ARM (PE32)。|  
|`afPA_NoPlatform`|表示組件的參考組件;也就是它會套用至任何架構，但無法在任何架構上執行。 因此，此旗標等同於`afPA_Mask`。|  
|`afPA_Specified`|指出處理器架構旗標，應該傳播至`AssemblyRef`記錄。|  
|`afPA_Mask`|遮罩，描述處理器架構。|  
|`afPA_FullMask`|指定包含處理器架構的說明。|  
|`afPA_Shift`|指出處理器架構旗標，從索引中的移位計數。|  
|`afEnableJITcompileTracking`|從對應的值會指出<xref:System.Diagnostics.DebuggableAttribute.DebuggingModes>的<xref:System.Diagnostics.DebuggableAttribute>。|  
|`afDisableJITcompileOptimizer`|從對應的值會指出<xref:System.Diagnostics.DebuggableAttribute.DebuggingModes>的<xref:System.Diagnostics.DebuggableAttribute>。|  
|`afRetargetable`|表示組件可以被重定目標在執行階段組件從不同的 「 發行者 」。|  
|`afContentType_Mask`|遮罩，描述的內容類型。|  
|`afContentType_Default`|表示預設內容類型。|  
|`afContentType_WindowsRuntime`|指出[!INCLUDE[wrt](../../../../includes/wrt-md.md)]內容類型。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorHdr.h  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
