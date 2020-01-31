---
title: COR_PRF_STATIC_TYPE 列舉
ms.date: 03/30/2017
api_name:
- COR_PRF_STATIC_TYPE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_STATIC_TYPE
helpviewer_keywords:
- COR_PRF_STATIC_TYPE enumeration [.NET Framework profiling]
ms.assetid: 441d7809-5b65-41a5-ba64-2910a8008315
topic_type:
- apiref
ms.openlocfilehash: 880c9bd186d6cb2acb277e9cc55d3063fb8d51d8
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867029"
---
# <a name="cor_prf_static_type-enumeration"></a>COR_PRF_STATIC_TYPE 列舉
指出欄位是否為靜態，若是靜態，則欄位套用的是靜態品質。 這些值可以使用位 OR 運算來結合，表示該欄位有多個不同的靜態品質。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum {  
    COR_PRF_FIELD_NOT_A_STATIC = 0x0,  
    COR_PRF_FIELD_APP_DOMAIN_STATIC = 0x1,  
    COR_PRF_FIELD_THREAD_STATIC = 0x2,  
    COR_PRF_FIELD_CONTEXT_STATIC = 0x4,  
    COR_PRF_FIELD_RVA_STATIC = 0x8  
} COR_PRF_STATIC_TYPE;  
```  
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`COR_PRF_FIELD_NOT_A_STATIC`|欄位不是靜態的。|  
|`COR_PRF_FIELD_APP_DOMAIN_STATIC`|欄位為 [應用程式域-靜態]。|  
|`COR_PRF_FIELD_THREAD_STATIC`|此欄位為執行緒靜態。|  
|`COR_PRF_FIELD_CONTEXT_STATIC`|欄位為內容靜態。|  
|`COR_PRF_FIELD_RVA_STATIC`|此欄位為相對虛擬位址（RVA）-靜態。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [分析列舉](profiling-enumerations.md)
