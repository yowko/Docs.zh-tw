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
ms.openlocfilehash: 048fe687e4d979576896f5310bddc855b40bb695
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175222"
---
# <a name="osinfo-structure"></a>OSINFO 結構
包含有關程式集或模組的作業系統的詳細資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;
    DWORD   dwOSMinorVersion;
} OSINFO;  
```  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`dwOSPlatformId`|由微軟 Windows 平臺函數`GetVersionEx`定義的識別碼值之一。 支援下列值：<br /><br /> - VER_PLATFORM_WIN32s，或 0x0000，以指定微軟 Windows 3.1。<br />- VER_PLATFORM_WIN32_WINDOWS，或 0x0001，以指定 Windows 95、Windows 98 或它們產生的作業系統。<br />- VER_PLATFORM_WIN32_NT，或 0x0002，以指定 Windows NT 或作業系統從它下降。|  
|`dwOSMajorVersion`|作業系統主版本，或用於指示任何版本的 Null 值。|  
|`dwOSMinorVersion`|作業系統次要版本，或用於指示任何版本的 Null 值。|  
  
## <a name="remarks"></a>備註  
 `OSINFO`基於調用微軟`OSVERSIONINFOEX`Windows 平臺功能`GetVersionEx`時使用的結構。 此結構由 ASSEMBLYMETADATA 結構用於指示其作業系統支援。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 用作 MsCorEE.dll 中的資源  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料結構](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [IMetaDataAssemblyEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
