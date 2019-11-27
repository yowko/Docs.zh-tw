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
ms.openlocfilehash: 24ec1f7d553a59425f7eb02af8e91010d940eb07
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444262"
---
# <a name="assemblymetadata-structure"></a>ASSEMBLYMETADATA 結構
包含參考元件的相關資訊，包括其版本，以及其地區設定、處理器和作業系統的支援層級。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`usMajorVersion`|參考元件的主要版本號碼。 這個值不能是零。 如果已設定 `usMajorVersion` 的所有位，則不會指定主要版本。|  
|`usMinorVersion`|參考元件的次要版本號碼。 這個值不能是零。 如果已設定 `usMinorVersion` 的所有位，則不會指定次要版本。|  
|`usBuildNumber`|參考元件的組建編號。 這個值不能是零。 如果已設定 `usBuildNumber` 的所有位，則不會指定組建編號。|  
|`usRevisionNumber`|參考元件的修訂編號。 這個值不能是零。 如果已設定 `usRevisionNumber` 的所有位，則不會指定修訂編號。|  
|`szLocale`|符合 RFC1766 規格的地區設定名稱清單（以分號分隔），指定參考元件所支援的地區設定。 Null 值表示地區設定獨立性。 **注意：** 在 .NET Framework 版本1.0 中，您不能指定多個地區設定。|  
|`cbLocale`|`szLocale`的寬字元大小。|  
|`rdwProcessor`|如 Winnt 中所定義的識別碼陣列，適用于所參考元件所支援的處理器類型。 Null 值表示處理器獨立性。|  
|`ulProcessor`|`rdwProcessor` 陣列的長度。|  
|`rOS`|[OSINFO](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md)實例的陣列，指定受參考元件支援的作業系統。 Null 值表示作業系統獨立性。|  
|`ulOS`|`rOS` 陣列的長度。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料結構](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [IMetaDataAssemblyEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [OSINFO 結構](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md)
