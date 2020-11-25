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
ms.openlocfilehash: f7aa9699e9929608c90020c6b2d66c301fc11955
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732706"
---
# <a name="ceesectionreloctype-enumeration"></a>CeeSectionRelocType 列舉

提供值，以影響 `reloc` [ICeeGen：： AddSectionReloc](iceegen-addsectionreloc-method.md)呼叫中發出的指令類型。  
  
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
|`srRelocAbsolute`|只產生區段相關，不傳送 `reloc` 任何內容至 reloc 區段。|  
|`srRelocHighLow`|`reloc`針對指標大小位置產生。 這會轉換成 BASED_HIGHLOW 或 BASED_DIR64，視平臺而定。|  
|`srRelocHighAdj`|`reloc`針對32位數位的前16位產生，其中的下16位會包含在 reloc 資料表的下一個單字中。|  
|`srRelocMapToken`|產生權杖對應重新配置，將 nothing 傳送至 reloc 區段。|  
|`srRelocRelative`|指出值是相對位址修復。|  
|`srRelocFilePos`|只產生區段相關，不傳送 `reloc` 任何內容至 reloc 區段。 這 `reloc` 是相對於區段的檔案位置，而不是區段的虛擬位址。|  
|`srRelocCodeRelative`|指定與程式碼相關的位址修復。|  
|`srRelocIA64Imm64`|`reloc`針對 ia64 指令中的64位位址產生 `movl` 。|  
|`srRelocDir64`|產生 `reloc` 64 位位址的。|  
|`srRelocIA64PcRel25`|`reloc`在 ia64 指令中為25位的電腦相對位址產生 `br.call` 。|  
|`srRelocIA64PcRel64`|`reloc`針對 ia64 指令中的64位電腦相對位址產生 `brl.call` 。|  
|`srRelocAbsoluteTagged`|產生與標記指標值相關的30位區段 `reloc` 。|  
|`srRelocSentinel`|Sentinel 值，可協助確保此列舉的任何新增專案都會反映在內部 `reloc` 名稱陣列中。|  
|`srNoBaseReloc`|指定不發出基底 `reloc` 。|  
|`srRelocPtr`|值，表示記憶體的預先修復內容是指標，而不是區段位移。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](metadata-enumerations.md)
- [ICeeGen 介面](iceegen-interface.md)
- [AddSectionReloc 方法](iceegen-addsectionreloc-method.md)
