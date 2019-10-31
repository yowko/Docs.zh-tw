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
ms.openlocfilehash: 635cb0c003889beb2f78e8413189cbfc4b064175
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099148"
---
# <a name="cor_gc_reference-structure"></a>COR_GC_REFERENCE 結構
包含要進行記憶體回收之物件的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct _COR_GC_REFERENCE {  
    ICorDebugAppDomain *domain;   
    ICorDebugValue *location;  
    CorGCReferenceType type;  
    UINT64 extraData;  
} COR_GC_REFERENCE;  
```  
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`domain`|控制碼或物件所屬之應用程式域的指標。 其值可能 `null`。|  
|`location`|對應至要進行垃圾收集之物件的 ICorDebugValue 或 ICorDebugReferenceValue 介面。|  
|`type`|指出根來源位置的[CorGCReferenceType](corgcreferencetype-enumeration.md)列舉值。 如需詳細資訊，請參閱＜備註＞一節。|  
|`extraData`|有關要進行垃圾收集之物件的其他資料。 這項資訊取決於物件的來源，如 [`type`] 欄位所示。 如需詳細資訊，請參閱＜備註＞一節。|  
  
## <a name="remarks"></a>備註  
 [`type`] 欄位是[CorGCReferenceType](corgcreferencetype-enumeration.md)列舉值，表示參考的來源位置。 特定的 `COR_GC_REFERENCE` 值可以反映下列任何一種受管理物件：  
  
- 來自所有 managed 堆疊的物件（`CorGCReferenceType.CorReferenceStack`）。 這包括 managed 程式碼中的即時參考，以及 common language runtime 所建立的物件。  
  
- 控制碼資料表中的物件（`CorGCReferenceType.CorHandle*`）。 這包括模組中的強式參考（`HNDTYPE_STRONG` 和 `HNDTYPE_REFCOUNT`）和靜態變數。  
  
- 完成項佇列中的物件（`CorGCReferenceType.CorReferenceFinalizer`）。 完成項會佇列根物件，直到完成項執行為止。  
  
 [`extraData`] 欄位包含額外的資料，視參考的來源（或類型）而定。 可能的值為：  
  
- `DependentSource` 如果 `type` 是 `CorGCREferenceType.CorHandleStrongDependent`，此欄位就是物件，如果正在進行，則會在 `COR_GC_REFERENCE.Location`時將物件進行垃圾收集。  
  
- `RefCount` 如果 `CorGCREferenceType.CorHandleStrongRefCount``type`，此欄位就是控制碼的參考計數。  
  
- `Size` 如果 `CorGCREferenceType.CorHandleStrongSizedByref``type`，此欄位就是垃圾收集行程計算物件根之物件樹狀結構的最後大小。 請注意，這種計算不一定是最新的。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯結構](debugging-structures.md)
- [偵錯](index.md)
