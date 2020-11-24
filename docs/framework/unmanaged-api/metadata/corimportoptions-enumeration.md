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
ms.openlocfilehash: 3d5989d43644088403a77f26c02af9ffaae0732b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677202"
---
# <a name="corimportoptions-enumeration"></a>CorImportOptions 列舉

包含旗標值，這些值可控制在匯入目前範圍之外的組件期間所發生的行為。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
  
|member|描述|  
|------------|-----------------|  
|`MDImportOptionDefault`|指出預設行為，也就是略過已刪除的記錄。|  
|`MDImportOptionAll`|表示應該列舉所有中繼資料。|  
|`MDImportOptionAllTypeDefs`|表示應該列舉所有的 Typedef （包括已刪除的 Typedef）。|  
|`MDImportOptionAllMethodDefs`|表示應該列舉所有 MethodDefs，包括已刪除的所有專案。|  
|`MDImportOptionAllFieldDefs`|表示應該列舉所有 FieldDefs，包括已刪除的所有專案。|  
|`MDImportOptionAllProperties`|表示應該列舉所有 PropertyDefs，包括已刪除的所有專案。|  
|`MDImportOptionAllEvents`|表示應該列舉所有 EventDefs，包括已刪除的所有專案。|  
|`MDImportOptionAllCustomAttributes`|表示應該列舉所有自訂屬性（包括已刪除的屬性）。|  
|`MDImportOptionAllExportedTypes`|表示應該列舉所有匯出的型別（包括已刪除的類型）。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Corhdr.h。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](metadata-enumerations.md)
