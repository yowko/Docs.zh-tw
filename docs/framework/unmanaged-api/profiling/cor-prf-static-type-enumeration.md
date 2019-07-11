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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 753c3b38187dd69593dcb0520acef9ce4b137039
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751905"
---
# <a name="corprfstatictype-enumeration"></a>COR_PRF_STATIC_TYPE 列舉
指出欄位是否為靜態，若是靜態，則欄位套用的是靜態品質。 這些值可以表示的欄位具有多個使用位元 OR 運算結合不同的靜態品質。  
  
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
  
## <a name="members"></a>成員  
  
|成員|說明|  
|------------|-----------------|  
|`COR_PRF_FIELD_NOT_A_STATIC`|欄位不是靜態的。|  
|`COR_PRF_FIELD_APP_DOMAIN_STATIC`|應用程式定義域靜態欄位。|  
|`COR_PRF_FIELD_THREAD_STATIC`|執行緒靜態欄位。|  
|`COR_PRF_FIELD_CONTEXT_STATIC`|內容靜態欄位。|  
|`COR_PRF_FIELD_RVA_STATIC`|此欄位是相對虛擬位址 (RVA) 為靜態。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [分析列舉](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
