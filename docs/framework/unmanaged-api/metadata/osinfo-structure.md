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
ms.openlocfilehash: ab9d7eb6f5760b43fe805443bbe1ea4a95c72069
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501062"
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
  
## <a name="members"></a>成員  
  
|成員|說明|  
|------------|-----------------|  
|`dwOSPlatformId`|Microsoft Windows 平臺函數所定義的其中一個識別碼值 `GetVersionEx` 。 支援下列值：<br /><br /> -VER_PLATFORM_WIN32s 或0x0000，以指定 Microsoft Windows 3.1。<br />-VER_PLATFORM_WIN32_WINDOWS 或0x0001，用來指定 Windows 95、Windows 98 或其下的作業系統。<br />-VER_PLATFORM_WIN32_NT 或0x0002，用來指定從它繼承的 Windows NT 或作業系統。|  
|`dwOSMajorVersion`|作業系統主要版本，或表示任何版本的 Null 值。|  
|`dwOSMinorVersion`|作業系統次要版本，或表示任何版本的 Null 值。|  
  
## <a name="remarks"></a>備註  
 `OSINFO`是 `OSVERSIONINFOEX` 以用於呼叫 Microsoft Windows 平臺函式的結構為基礎 `GetVersionEx` 。 ASSEMBLYMETADATA 結構會使用此結構來表示其作業系統支援。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料結構](metadata-structures.md)
- [IMetaDataAssemblyEmit 介面](imetadataassemblyemit-interface.md)
