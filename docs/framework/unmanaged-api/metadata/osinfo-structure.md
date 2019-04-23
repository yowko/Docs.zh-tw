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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0aba49fb4a60b2e471c541a8d8531a1cbc8627f9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59096195"
---
# <a name="osinfo-structure"></a>OSINFO 結構
包含組件或模組的作業系統的相關詳細資料。  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;   
    DWORD   dwOSMinorVersion;   
} OSINFO;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`dwOSPlatformId`|Microsoft Windows 平台函式所定義的識別碼值的其中一個`GetVersionEx`。 支援下列值：<br /><br /> -VER_PLATFORM_WIN32s 或 0x0000，指定 Microsoft Windows 3.1。<br />-VER_PLATFORM_WIN32_WINDOWS 或 0x0001，指定 Windows 95、 Windows 98 或從它們繼承而來的作業系統。<br />-VER_PLATFORM_WIN32_NT 或 0x0010，指定 Windows NT 或從它繼承而來的作業系統。|  
|`dwOSMajorVersion`|作業系統主要版本或 NULL 值，指出任何版本。|  
|`dwOSMinorVersion`|作業系統次要版本或 NULL 值，指出任何版本。|  
  
## <a name="remarks"></a>備註  
 `OSINFO` 根據`OSVERSIONINFOEX`結構，也就是用於的 Microsoft Windows 平台函式呼叫`GetVersionEx`。 ASSEMBLYMETADATA 結構使用這個結構表示其作業系統支援。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **LIBRARY:** 做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料結構](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [IMetaDataAssemblyEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
