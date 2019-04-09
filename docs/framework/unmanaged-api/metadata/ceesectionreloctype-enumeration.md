---
title: CeeSectionRelocType 列舉
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 882242da493c49a2e6aa09888e9503dcf2933589
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119583"
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
|`srRelocAbsolute`|產生僅區段相對`reloc`、 傳送任何項目到.reloc 區段。|  
|`srRelocHighLow`|會產生`reloc`指標大小的位置。 這會轉換成 BASED_HIGHLOW 或 BASED_DIR64 視平台。|  
|`srRelocHighAdj`|會產生`reloc`前 32 位元數字，其中 16 位元會包含在下一個字.reloc 資料表中的 16 位元。|  
|`srRelocMapToken`|會產生語彙基元對應的重新配置，傳送任何項目到.reloc 區段。|  
|`srRelocRelative`|表示值是相對位址的修復。|  
|`srRelocFilePos`|產生僅區段相對`reloc`、 傳送任何項目到.reloc 區段。 這`reloc`是檔案的相對位置 區段中，不該區段的虛擬位址。|  
|`srRelocCodeRelative`|指定程式碼的相對位址的修復。|  
|`srRelocIA64Imm64`|會產生`reloc`64 位元位址在 ia64`movl`指令。|  
|`srRelocDir64`|會產生`reloc`64 位元位址。|  
|`srRelocIA64PcRel25`|產生`reloc`25 位元電腦相對位址在 ia64`br.call`指令。|  
|`srRelocIA64PcRel64`|會產生`reloc`64 位元電腦相對位址在 ia64`brl.call`指令。|  
|`srRelocAbsoluteTagged`|會產生 30 位元的區段相對於`reloc`，用來標記的指標值。|  
|`srRelocSentinel`|為了協助確保這個列舉任何新增項目之 sentinel 值會反映到內部`reloc`名稱陣列。|  
|`srNoBaseReloc`|指定不要發出基底`reloc`。|  
|`srRelocPtr`|值，指出前修復記憶體內容的指標，而不是區段位移。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **LIBRARY:** 包含做為 MsCorEE.dll 中的資源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [ICeeGen 介面](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
- [AddSectionReloc 方法](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)
