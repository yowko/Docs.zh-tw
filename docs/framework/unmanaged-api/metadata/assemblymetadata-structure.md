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
ms.openlocfilehash: 5c7211fc2523b70313a1e4d4d9d2da0dcecd1d32
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009427"
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
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`usMajorVersion`|參考元件的主要版本號碼。 這個值不能是零。 如果所有的位 `usMajorVersion` 都已設定，則不會指定主要版本。|  
|`usMinorVersion`|參考元件的次要版本號碼。 這個值不能是零。 如果設定了的所有位 `usMinorVersion` ，則不會指定次要版本。|  
|`usBuildNumber`|參考組件的組建編號。 這個值不能是零。 如果設定了的所有位 `usBuildNumber` ，則不會指定組建編號。|  
|`usRevisionNumber`|參考元件的修訂編號。 這個值不能是零。 如果設定了的所有位 `usRevisionNumber` ，則不會指定修訂編號。|  
|`szLocale`|符合 RFC1766 規格的地區設定名稱清單（以分號分隔），指定參考元件所支援的地區設定。 Null 值表示地區設定獨立性。 **注意：** 在 .NET Framework 版本1.0 中，您不能指定多個地區設定。|  
|`cbLocale`|的大小（以寬字元為單位） `szLocale` 。|  
|`rdwProcessor`|如 Winnt 中所定義的識別碼陣列，適用于所參考元件所支援的處理器類型。 Null 值表示處理器獨立性。|  
|`ulProcessor`|`rdwProcessor` 陣列的長度。|  
|`rOS`|[OSINFO](osinfo-structure.md)實例的陣列，指定受參考元件支援的作業系統。 Null 值表示作業系統獨立性。|  
|`ulOS`|`rOS` 陣列的長度。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料結構](metadata-structures.md)
- [IMetaDataAssemblyEmit 介面](imetadataassemblyemit-interface.md)
- [OSINFO 結構](osinfo-structure.md)
