---
title: CorAttributeTargets 列舉
ms.date: 03/30/2017
api_name:
- CorAttributeTargets
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorAttributeTargets
helpviewer_keywords:
- CorAttributeTargets enumeration [.NET Framework metadata]
ms.assetid: 694c0fa0-7011-41a9-9dfd-f0e16ea574b5
topic_type:
- apiref
ms.openlocfilehash: 51741aa3a6d965c1e9743081628d8ad62e8fb04e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176197"
---
# <a name="corattributetargets-enumeration"></a>CorAttributeTargets 列舉
指定有效套用屬性的應用程式項目。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum CorAttributeTargets  
{  
    catAssembly            = 0x0001,  
    catModule              = 0x0002,  
    catClass               = 0x0004,  
    catStruct              = 0x0008,  
    catEnum                = 0x0010,  
    catConstructor         = 0x0020,  
    catMethod              = 0x0040,  
    catProperty            = 0x0080,  
    catField               = 0x0100,  
    catEvent               = 0x0200,  
    catInterface           = 0x0400,  
    catParameter           = 0x0800,  
    catDelegate            = 0x1000,  
    catGenericParameter    = 0x4000,  
  
    catAll                 =
        catAssembly | catModule | catClass | catStruct |
        catEnum | catConstructor | catMethod | catProperty |
        catField | catEvent | catInterface | catParameter |
        catDelegate | catGenericParameter,  
  
    catClassMembers        =
        catClass | catStruct | catEnum | catConstructor |
        catMethod | catProperty | catField | catEvent |
        catDelegate | catInterface  
  
} CorAttributeTargets;  
```  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`catAssembly`|屬性可以套用至組件。|  
|`catModule`|屬性可以應用於可移植可執行 （.dll 或 .exe） 模組。|  
|`catClass`|屬性可以套用至類別。|  
|`catStruct`|屬性可以套用至結構，也就是實值型別 (Value Type)。|  
|`catEnum`|屬性可以套用至列舉型別。|  
|`catConstructor`|屬性可以套用至建構函式。|  
|`catMethod`|屬性可以套用至方法。|  
|`catProperty`|屬性 (Attibute) 可以套用至屬性 (Property)。|  
|`catField`|屬性可以套用至欄位。|  
|`catEvent`|屬性可以套用至事件。|  
|`catInterface`|屬性可以套用至介面。|  
|`catParameter`|屬性可以套用至參數。|  
|`catDelegate`|屬性可以套用至委派。|  
|`catGenericParameter`|屬性可以套用至泛型參數。|  
|`catAll`|屬性可以套用至任何應用程式項目。|  
|`catClassMembers`|屬性可以應用於類的成員。|  
  
## <a name="remarks"></a>備註  
 枚`CorAttributeTargets`舉值可以與位或操作組合，以獲得首選組合。  
  
 並行`CorAttributeTargets`化託管<xref:System.AttributeTargets?displayProperty=nameWithType>枚舉。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫德  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
