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
ms.openlocfilehash: 7c86a4fd2788c8ea2df5d9e54c5c221afd179704
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59091417"
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
|`afImplicitExportedTypes`|指定匯出的型別定義隱含構成組件檔案中。 在.NET framework 1.0 和 1.1 版中，這個值永遠都會假設設定。|  
|`afImplicitResources`|指定的資源定義中是隱含包含組件的檔案。 在.NET Framework 1.0 和 1.1 中，這個值永遠都會假設設定。|  
|`afNonSideBySideAppDomain`|指定是否它們相同的應用程式定義域中執行，無法與其他版本一起執行的組件。|  
|`afNonSideBySideProcess`|指定是否它們在相同的程序執行，無法與其他版本一起執行的組件。|  
|`afNonSideBySideMachine`|指定是否在同一部電腦上執行，無法與其他版本一起執行的組件。|  
  
## <a name="remarks"></a>備註  
 0x0010 與 0x0070 之間的值用來描述所參考組件的並排顯示相容性功能。 如果沒有這些值的設定，則會將組件假設為並排顯示相容。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MsCorEE.h  
  
 **LIBRARY:** 包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [IMetaDataAssemblyEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
