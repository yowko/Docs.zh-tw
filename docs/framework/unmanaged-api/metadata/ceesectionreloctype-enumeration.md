---
title: "CeeSectionRelocType 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CeeSectionRelocType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CeeSectionRelocType
helpviewer_keywords:
- CeeSectionRelocType enumeration [.NET Framework metadata]
ms.assetid: 124656f6-0dad-4ceb-9043-d3869ab65cde
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d257778a9a05e2654d7f91c0205424d001f5ae3e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ceesectionreloctype-enumeration"></a>CeeSectionRelocType 列舉
提供值，以影響的型別`reloc`發出的呼叫中的指示[iceegen:: Addsectionreloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum  {  
    srRelocAbsolute,  
    srRelocHighLow          = 3,  
    srRelocHighAdj,       
    srRelocMapToken,  
    srRelocRelative,  
    srRelocFilePos,  
    srRelocCodeRelative,  
    srRelocIA64Imm64,  
    srRelocDir64,  
    srRelocIA64PcRel25,  
    srRelocIA64PcRel64,    srRelocAbsoluteTagged,    srRelocSentinel,    srNoBaseReloc       = 0x4000,  
    srRelocPtr          = 0x8000,  
    srRelocAbsolutePtr      = srRelocPtr + srRelocAbsolute,  
    srRelocHighLowPtr       = srRelocPtr + srRelocHighLow,  
    srRelocRelativePtr      = srRelocPtr + srRelocRelative,  
    srRelocIA64Imm64Ptr     = srRelocPtr + srRelocIA64Imm64,  
    srRelocDir64Ptr         = srRelocPtr + srRelocDir64  
    } CeeSectionRelocType;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`srRelocAbsolute`|產生僅區段相對`reloc`、 傳送 nothing 到.reloc 區段。|  
|`srRelocHighLow`|會產生`reloc`指標大小的位置。 這會視平台轉換為 BASED_HIGHLOW 或 BASED_DIR64。|  
|`srRelocHighAdj`|會產生`reloc`其中 16 位元會包含在下一個文字.reloc 資料表中之 32 位元數字的 16 位元的頂端。|  
|`srRelocMapToken`|產生語彙基元對應的重新配置，傳送到.reloc 區段的任何項目。|  
|`srRelocRelative`|表示的值是相對位址的修復。|  
|`srRelocFilePos`|產生僅區段相對`reloc`、 傳送 nothing 到.reloc 區段。 這`reloc`是檔案的相對位置 區段中，不該區段的虛擬位址。|  
|`srRelocCodeRelative`|指定程式碼的相對位址的修復。|  
|`srRelocIA64Imm64`|會產生`reloc`在 ia64 64 位元位址`movl`指令。|  
|`srRelocDir64`|會產生`reloc`64 位元位址。|  
|`srRelocIA64PcRel25`|產生`reloc`25 位元電腦的相對位址在 ia64`br.call`指令。|  
|`srRelocIA64PcRel64`|會產生`reloc`在 ia64 64 位元電腦的相對位址`brl.call`指令。|  
|`srRelocAbsoluteTagged`|會產生 30 位元的區段相對於`reloc`，用於已加上標籤的指標值。|  
|`srRelocSentinel`|若要協助您確保任何新增至這個列舉的項目之 sentinel 值會反映到內部`reloc`名稱陣列。|  
|`srNoBaseReloc`|指定不要發出基底`reloc`。|  
|`srRelocPtr`|值，指出前修復記憶體內容的指標，而非區段位移。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
 [ICeeGen 介面](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)  
 [AddSectionReloc 方法](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)
