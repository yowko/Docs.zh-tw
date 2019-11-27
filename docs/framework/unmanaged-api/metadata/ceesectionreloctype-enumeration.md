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
ms.openlocfilehash: efce0c13944b383c42cbff6a6af4795293ee2989
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444165"
---
# <a name="ceesectionreloctype-enumeration"></a>CeeSectionRelocType 列舉
提供值，以影響呼叫[ICeeGen：： AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)時發出的 `reloc` 指令類型。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`srRelocAbsolute`|只產生區段相關 `reloc`，不傳送任何內容到 reloc 區段。|  
|`srRelocHighLow`|產生指標大小位置的 `reloc`。 這會根據平臺轉換成 BASED_HIGHLOW 或 BASED_DIR64。|  
|`srRelocHighAdj`|為32位數位的前16位產生 `reloc`，其中的下16位會包含在 reloc 資料表中的下一個單字。|  
|`srRelocMapToken`|會產生標記對應重新配置，而不傳送任何內容到 reloc 區段。|  
|`srRelocRelative`|表示此值是相對位址修復。|  
|`srRelocFilePos`|只產生區段相關 `reloc`，不傳送任何內容到 reloc 區段。 此 `reloc` 相對於區段的檔案位置，而不是區段的虛擬位址。|  
|`srRelocCodeRelative`|指定程式碼相對位址修復。|  
|`srRelocIA64Imm64`|在 ia64 `movl` 指令中產生64位位址的 `reloc`。|  
|`srRelocDir64`|產生64位位址的 `reloc`。|  
|`srRelocIA64PcRel25`|在 ia64 `br.call` 指令中，產生25位電腦相對位址的 `reloc`。|  
|`srRelocIA64PcRel64`|在 ia64 `brl.call` 指令中，產生64位電腦相對位址的 `reloc`。|  
|`srRelocAbsoluteTagged`|產生30位區段相對 `reloc`，用於標記的指標值。|  
|`srRelocSentinel`|Sentinel 值，可協助確保此列舉的任何新增專案都會反映到內部 `reloc` 名稱陣列。|  
|`srNoBaseReloc`|指定不發出基底 `reloc`。|  
|`srRelocPtr`|值，表示記憶體的修復前內容是指標，而不是區段位移。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [ICeeGen 介面](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
- [AddSectionReloc 方法](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)
