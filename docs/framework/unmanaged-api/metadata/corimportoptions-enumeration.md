---
title: CorImportOptions 列舉
ms.date: 03/30/2017
api_name:
- CorImportOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorImportOptions
helpviewer_keywords:
- CorImportOptions enumeration [.NET Framework metadata]
ms.assetid: 4e5d03cb-97c9-4ff4-8dbd-17d94ee374d3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7078b2eb98c15b7229132076da8af4691032bb08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441788"
---
# <a name="corimportoptions-enumeration"></a>CorImportOptions 列舉
包含旗標值，這些值可控制在匯入目前範圍之外的組件期間所發生的行為。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum CorImportOptions {  
  
    MDImportOptionDefault                = 0x00000000,  
    MDImportOptionAll                    = 0xFFFFFFFF,  
    MDImportOptionAllTypeDefs            = 0x00000001,  
    MDImportOptionAllMethodDefs          = 0x00000002,  
    MDImportOptionAllFieldDefs           = 0x00000004,  
    MDImportOptionAllProperties          = 0x00000008,  
    MDImportOptionAllEvents              = 0x00000010,  
    MDImportOptionAllCustomAttributes    = 0x00000020,  
    MDImportOptionAllExportedTypes       = 0x00000040  
  
} CorImportOptions;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`MDImportOptionDefault`|表示預設行為，也就是略過已刪除的記錄。|  
|`MDImportOptionAll`|表示應該列舉所有中繼資料。|  
|`MDImportOptionAllTypeDefs`|表示應該列舉所有的 Typedef，包括已刪除的。|  
|`MDImportOptionAllMethodDefs`|表示應該列舉所有 MethodDefs，包括已刪除的。|  
|`MDImportOptionAllFieldDefs`|表示應該列舉所有 FieldDefs，包括已刪除的。|  
|`MDImportOptionAllProperties`|表示應該列舉所有 PropertyDefs，包括已刪除的。|  
|`MDImportOptionAllEvents`|表示應該列舉所有 EventDefs，包括已刪除的。|  
|`MDImportOptionAllCustomAttributes`|表示應該列舉所有的自訂屬性，包括已刪除的。|  
|`MDImportOptionAllExportedTypes`|表示應該列舉所有的匯出的類型，包括已刪除的。|  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorHdr.h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
