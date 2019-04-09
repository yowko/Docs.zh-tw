---
title: COR_GC_REFERENCE 結構
ms.date: 03/30/2017
api_name:
- COR_GC_REFERENCE
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_GC_REFERENCE
helpviewer_keywords:
- COR_GC_REFERENCE structure [.NET Framework debugging]
ms.assetid: 162e8179-0cd4-4110-8f06-5f387698bd62
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1e31e95473136bf7e7c196eacc278fa8a1caab2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59093653"
---
# <a name="corgcreference-structure"></a>COR_GC_REFERENCE 結構
包含要進行記憶體回收之物件的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct _COR_GC_REFERENCE {  
    ICorDebugAppDomain *domain;   
    ICorDebugValue *location;  
    CorGCReferenceType type;  
    UINT64 extraData;  
} COR_GC_REFERENCE;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`domain`|物件的控制代碼所屬的應用程式定義域的指標。 其值可能是`null`。|  
|`location`|ICorDebugValue 或 ICorDebugReferenceValue 介面對應至要進行記憶體回收的物件。|  
|`type`|A [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)列舉值，指出根來自何處。 如需詳細資訊，請參閱＜備註＞一節。|  
|`extraData`|其他要進行記憶體回收的物件的詳細資料。 這項資訊視物件的來源所示`type`欄位。 如需詳細資訊，請參閱＜備註＞一節。|  
  
## <a name="remarks"></a>備註  
 `type`欄位是[CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)列舉值，指出參考的來源。 特定`COR_GC_REFERENCE`值可反映出任何下列類型的受管理物件：  
  
-   從所有受管理的堆疊物件 (`CorGCReferenceType.CorReferenceStack`)。 這包括即時參考，在 managed 程式碼，以及 common language runtime 所建立的物件。  
  
-   控制代碼資料表中的物件 (`CorGCReferenceType.CorHandle*`)。 這包括強式參考 (`HNDTYPE_STRONG`和`HNDTYPE_REFCOUNT`) 和模組中的靜態變數。  
  
-   完成項佇列中的物件 (`CorGCReferenceType.CorReferenceFinalizer`)。 完成項佇列根物件，直到執行完成項。  
  
 `extraData`欄位包含額外的資料，取決於參考的來源 （或類型）。 可能的值為：  
  
-   `DependentSource`。 如果`type`已`CorGCREferenceType.CorHandleStrongDependent`，這個欄位是物件，如果保持運作，根目錄的物件進行記憶體回收在`COR_GC_REFERENCE.Location`。  
  
-   `RefCount`。 如果`type`是`CorGCREferenceType.CorHandleStrongRefCount`，這個欄位是控制代碼的參考計數。  
  
-   `Size`。 如果`type`是`CorGCREferenceType.CorHandleStrongSizedByref`，這個欄位是記憶體回收行程，導出物件根物件樹狀結構的最後大小。 請注意，這項計算不一定是最新狀態。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯結構](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
