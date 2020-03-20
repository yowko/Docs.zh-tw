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
ms.openlocfilehash: 44a84e0752eecc1c694f3b8cf6e568b72b7d0f5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176210"
---
# <a name="ceesectionreloctype-enumeration"></a>CeeSectionRelocType 列舉
提供值以影響調用 ICeeGen 時發出的`reloc`指令類型[：：AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)。  
  
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
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`srRelocAbsolute`|僅生成與節相關的`reloc`，不會將任何內容發送到 .reloc 節。|  
|`srRelocHighLow`|為指標`reloc`大小的位置生成 。 根據平臺的不同，這轉換為BASED_HIGHLOW或BASED_DIR64。|  
|`srRelocHighAdj`|為`reloc`32 位數位的前 16 位生成 一個，其中底部 16 位包含在 .reloc 表中的下一個單詞中。|  
|`srRelocMapToken`|生成權杖映射重新置放，不向 .reloc 部分發送任何內容。|  
|`srRelocRelative`|指示該值是相對位址修復。|  
|`srRelocFilePos`|僅生成與節相關的`reloc`，不會將任何內容發送到 .reloc 節。 這是`reloc`相對於節的檔位置，而不是節的虛擬位址。|  
|`srRelocCodeRelative`|指定與代碼相關的位址修復。|  
|`srRelocIA64Imm64`|在`reloc`ia64 指令中為 64`movl`位位址生成 。|  
|`srRelocDir64`|為`reloc`64 位位址生成 。|  
|`srRelocIA64PcRel25`|在`reloc`ia64`br.call`指令中為 25 位 PC 相關位址生成 。|  
|`srRelocIA64PcRel64`|在`reloc`ia64`brl.call`指令中為 64 位 PC 相關位址生成 。|  
|`srRelocAbsoluteTagged`|生成 30 位節相對`reloc`， 用於標記的指標值。|  
|`srRelocSentinel`|一個哨點值，可説明確保此枚舉的任何添加都反映到內部`reloc`名稱陣列。|  
|`srNoBaseReloc`|指定不發出基`reloc`。|  
|`srRelocPtr`|指示記憶體的預修復內容是指標而不是節偏移量的值。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 作為資源包含在 MsCorEE.dll 中  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [ICeeGen 介面](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
- [AddSectionReloc 方法](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)
