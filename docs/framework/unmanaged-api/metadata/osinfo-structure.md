---
title: OSINFO 結構
ms.date: 03/30/2017
api_name:
- OSINFO
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- OSINFO
helpviewer_keywords:
- OSINFO structure [.NET Framework metadata]
ms.assetid: fac7b480-7adb-4450-a5e9-690fed81ffae
topic_type:
- apiref
ms.openlocfilehash: 89111bf7eb03d20c2010c7a20c4cd055c2a021e3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430727"
---
# <a name="osinfo-structure"></a>OSINFO 結構
包含元件或模組之作業系統的詳細資料。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;   
    DWORD   dwOSMinorVersion;   
} OSINFO;  
```  
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`dwOSPlatformId`|Microsoft Windows 平臺函數所定義的其中一個識別碼值 `GetVersionEx`。 支援下列值：<br /><br /> -VER_PLATFORM_WIN32s 或0x0000，以指定 Microsoft Windows 3.1。<br />-VER_PLATFORM_WIN32_WINDOWS 或0x0001，用來指定 Windows 95、Windows 98 或其下的作業系統。<br />-VER_PLATFORM_WIN32_NT 或0x0010，用來指定從它繼承的 Windows NT 或作業系統。|  
|`dwOSMajorVersion`|作業系統主要版本，或表示任何版本的 Null 值。|  
|`dwOSMinorVersion`|作業系統次要版本，或表示任何版本的 Null 值。|  
  
## <a name="remarks"></a>備註  
 `OSINFO` 是以呼叫 Microsoft Windows 平臺函式 `GetVersionEx`所用的 `OSVERSIONINFOEX` 結構為基礎。 ASSEMBLYMETADATA 結構會使用此結構來表示其作業系統支援。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [中繼資料結構](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [IMetaDataAssemblyEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
