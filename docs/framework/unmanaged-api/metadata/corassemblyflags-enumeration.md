---
title: "CorAssemblyFlags 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorAssemblyFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: CorAssemblyFlags
helpviewer_keywords: CorAssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: bb8db3b6-d81d-49fc-b74c-dbc908a9eab9
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 67057944705a1cecd1754c3c11da08725c9a93f9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
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
  
|成員|說明|  
|------------|-----------------|  
|`afPublicKey`|表示組件參考會保留完整的未雜湊的公用金鑰。|  
|`afPA_None`|表示未指定的處理器架構。|  
|`afPA_MSIL`|指示處理器架構是中性 (PE32)。|  
|`afPA_x86`|指示處理器架構為 x86 (PE32)。|  
|`afPA_IA64`|指示處理器架構為 Itanium （PE32 +）。|  
|`afPA_AMD64`|表示的處理器架構的 AMD X64 （PE32 +）。|  
|`afPA_ARM`|指示處理器架構是 ARM (PE32)。|  
|`afPA_NoPlatform`|表示組件的參考組件。也就是說，它會適用於任何架構，但無法在任何架構上執行。 因此，此旗標等同於`afPA_Mask`。|  
|`afPA_Specified`|指示處理器架構旗標，應該傳播至`AssemblyRef`記錄。|  
|`afPA_Mask`|遮罩描述處理器架構。|  
|`afPA_FullMask`|指定包含處理器架構的說明。|  
|`afPA_Shift`|表示排班中的計數與索引的處理器架構旗標。|  
|`afEnableJITcompileTracking`|表示對應的值從<xref:System.Diagnostics.DebuggableAttribute.DebuggingModes>的<xref:System.Diagnostics.DebuggableAttribute>。|  
|`afDisableJITcompileOptimizer`|表示對應的值從<xref:System.Diagnostics.DebuggableAttribute.DebuggingModes>的<xref:System.Diagnostics.DebuggableAttribute>。|  
|`afRetargetable`|指出的組件可能會被重定在執行階段組件從不同的發行者。|  
|`afContentType_Mask`|遮罩描述的內容類型。|  
|`afContentType_Default`|表示預設內容類型。|  
|`afContentType_WindowsRuntime`|指出[!INCLUDE[wrt](../../../../includes/wrt-md.md)]內容類型。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorHdr.h  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
