---
title: ASSEMBLYMETADATA 結構
ms.date: 03/30/2017
api_name:
- ASSEMBLYMETADATA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ASSEMBLYMETADATA
helpviewer_keywords:
- ASSEMBLYMETADATA structure [.NET Framework metadata]
ms.assetid: 1af98e57-9145-4d35-bb78-77d1da7c91a5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8f0a9b9c149c86b4d9121275aa858dfdc0cdbac7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59195159"
---
# <a name="assemblymetadata-structure"></a>ASSEMBLYMETADATA 結構
包含參考的組件，包括其版本和層級支援地區設定、 處理器和作業系統的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct {  
    USHORT  usMajorVersion;  
    USHORT  usMinorVersion;  
    USHORT  usBuildNumber;  
    USHORT  usRevisionNumber;  
    LPWSTR  szLocale;  
    ULONG   cbLocale;  
    DWORD*  rdwProcessor[];  
    ULONG   ulProcessor  
    OSINFO* rOS[];  
    ULONG   ulOS;  
} ASSEMBLYMETADATA;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`usMajorVersion`|參考的組件的主要版本號碼。 此值不可為零。 如果所有的位元`usMajorVersion`設定，未指定的主要版本。|  
|`usMinorVersion`|參考的組件的次要版本號碼。 此值不可為零。 如果所有的位元`usMinorVersion`設定，未指定的次要版本。|  
|`usBuildNumber`|參考的組件的組建編號。 此值不可為零。 如果所有的位元`usBuildNumber`設定，未指定組建編號。|  
|`usRevisionNumber`|參考的組件的修訂編號。 此值不可為零。 如果所有的位元`usRevisionNumber`設定，未指定的修訂編號。|  
|`szLocale`|符合 RFC1766 規格中，使用分號分隔，指定參考的組件所支援的地區設定的地區設定名稱的清單。 Null 值表示地區設定的獨立性。 **注意：** 在.NET Framework 1.0 版，您無法指定多個地區設定。|  
|`cbLocale`|寬字元大小`szLocale`。|  
|`rdwProcessor`|陣列識別項，因為在 Winnt.h 中定義的類型參考的組件所支援的處理器。 NULL 值表示處理器的獨立性。|  
|`ulProcessor`|長度`rdwProcessor`陣列。|  
|`rOS`|陣列[OSINFO](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md)指定參考的組件所支援的作業系統的執行個體。 NULL 值表示作業系統獨立性。|  
|`ulOS`|長度`rOS`陣列。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **LIBRARY:** 做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料結構](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [IMetaDataAssemblyEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [OSINFO 結構](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md)
