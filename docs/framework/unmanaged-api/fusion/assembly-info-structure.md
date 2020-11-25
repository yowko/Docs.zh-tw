---
title: ASSEMBLY_INFO 結構
ms.date: 03/30/2017
api_name:
- ASSEMBLY_INFO
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASSEMBLY_INFO
helpviewer_keywords:
- ASSEMBLY_INFO structure [.NET Framework fusion]
ms.assetid: b3cbb47c-457f-4083-8895-49562ca99ab8
topic_type:
- apiref
ms.openlocfilehash: 520a24ced6e897d926ce68ef5973ab7083731b9d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717624"
---
# <a name="assembly_info-structure"></a>ASSEMBLY_INFO 結構

包含在全域組件快取中註冊之元件的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct _ASSEMBLY_INFO {  
    ULONG           cbAssemblyInfo;  
    DWORD           dwAssemblyFlags;  
    ULARGE_INTEGER  uliAssemblySizeInKB;  
    LPWSTR          pszCurrentAssemblyPathBuf;  
    ULONG           cchBuf;  
} ASSEMBLY_INFO;  
```  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`cbAssemblyInfo`|結構的大小（以位元組為單位）。 這個欄位是保留給未來的擴充性。|  
|`dwAssemblyFlags`|旗標，指出元件的安裝詳細資料。 支援下列值：<br /><br /> -ASSEMBLYINFO_FLAG_INSTALLED 值，表示已安裝元件。 目前的 .NET Framework 版本一律會設定 `dwAssemblyFlags` 為此值。<br />-ASSEMBLYINFO_FLAG_PAYLOADRESIDENT 值，表示元件是裝載的裝載。 目前的 .NET Framework 版本永遠不會設定 `dwAssemblyFlags` 為此值。|  
|`uliAssemblySizeInKB`|元件所包含檔案的總大小（以 kb 為單位）。|  
|`pszCurrentAssemblyPathBuf`|字串緩衝區的指標，此字串緩衝區會保存資訊清單檔案的目前路徑。 路徑的結尾必須是 null 字元。|  
|`cchBuf`|包含的寬字元數（包括 null 結束字元） `pszCurrentAssemblyPathBuf` 。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 融合。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [融合結構](fusion-structures.md)
- [全域組件快取](../../app-domains/gac.md)
