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
ms.openlocfilehash: a43d5e15c02a97ff10a6a5afd439cadebb6b33d2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73109219"
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
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`cbAssemblyInfo`|結構的大小（以位元組為單位）。 此欄位保留供未來擴充性之用。|  
|`dwAssemblyFlags`|旗標，指出元件的安裝詳細資料。 支援下列值：<br /><br /> -ASSEMBLYINFO_FLAG_INSTALLED 值，表示已安裝元件。 目前的 .NET Framework 版本一律會將 `dwAssemblyFlags` 設定為此值。<br />-ASSEMBLYINFO_FLAG_PAYLOADRESIDENT 值，表示元件是裝載常駐的。 目前的 .NET Framework 版本永遠不會將 `dwAssemblyFlags` 設定為此值。|  
|`uliAssemblySizeInKB`|元件所包含之檔案的總大小（以 kb 為單位）。|  
|`pszCurrentAssemblyPathBuf`|字串緩衝區的指標，其中包含資訊清單檔案的目前路徑。 路徑的結尾必須是 null 字元。|  
|`cchBuf`|`pszCurrentAssemblyPathBuf` 包含的寬字元數，包括 null 結束字元。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 融合。h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [融合結構](fusion-structures.md)
- [全域組件快取](../../app-domains/gac.md)
