---
title: AssemblyFlags 列舉
ms.date: 03/30/2017
api_name:
- AssemblyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyFlags
helpviewer_keywords:
- AssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: 40f9bd9e-16ec-447e-81b0-168c875e9866
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2fc6d08e960b0ba82c76945a318ec723546f71b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444902"
---
# <a name="assemblyflags-enumeration"></a>AssemblyFlags 列舉
包含描述的組件的執行階段功能的值。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum {  
    afImplicitExportedTypes = 0x0001,  
    afImplicitResources = 0x0002,  
    afNonSideBySideAppDomain = 0x0010,  
    afNonSideBySideProcess = 0x0020,  
    afNonSideBySideMachine = 0x0030  
} AssemblyFlags;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`afImplicitExportedTypes`|指定匯出的類型定義是隱含構成組件檔案中。 在.NET framework 1.0 和 1.1 版中，這個值永遠是設定。|  
|`afImplicitResources`|指定隱含構成組件檔案中定義的資源。 在.NET Framework 1.0 和 1.1 中，這個值永遠是設定。|  
|`afNonSideBySideAppDomain`|指定組件無法執行與其他版本一起執行相同的應用程式定義域中。|  
|`afNonSideBySideProcess`|指定組件無法執行與其他版本一起執行相同的處理序中。|  
|`afNonSideBySideMachine`|指定是否在同一部電腦上執行，無法與其他版本一起執行組件。|  
  
## <a name="remarks"></a>備註  
 0x0070 0x0010 之間的值可用來描述的參考組件-並存相容性功能。 如果這些值未設定，組件會假設為-並存相容。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MsCorEE.h  
  
 **程式庫：** 包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
 [IMetaDataAssemblyEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
