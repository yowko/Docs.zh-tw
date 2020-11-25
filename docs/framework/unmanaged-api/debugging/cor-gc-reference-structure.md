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
ms.openlocfilehash: bb4a8f7ff3ee54474804e3e5620dcce7c9f79fb5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726609"
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
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`domain`|控制碼或物件所屬應用程式域的指標。 其值可能為 `null` 。|  
|`location`|對應至要進行垃圾收集之物件的 ICorDebugValue 或 ICorDebugReferenceValue 介面。|  
|`type`|指出根目錄來源的 [CorGCReferenceType](corgcreferencetype-enumeration.md) 列舉值。 如需詳細資訊，請參閱＜備註＞一節。|  
|`extraData`|要進行垃圾收集之物件的其他相關資料。 此資訊取決於物件的來源，如欄位所示 `type` 。 如需詳細資訊，請參閱＜備註＞一節。|  
  
## <a name="remarks"></a>備註  

 此 `type` 欄位是 [CorGCReferenceType](corgcreferencetype-enumeration.md) 列舉值，指出參考的來源位置。 特定 `COR_GC_REFERENCE` 值可反映下列任何一種 managed 物件：  
  
- 所有 managed 堆疊中的物件 (`CorGCReferenceType.CorReferenceStack`) 。 這包括 managed 程式碼中的即時參考，以及 common language runtime 所建立的物件。  
  
- 控制碼資料表中的物件 (`CorGCReferenceType.CorHandle*`) 。 這包括 (中的強式參考 `HNDTYPE_STRONG` ，以及 `HNDTYPE_REFCOUNT` 模組中的) 和靜態變數。  
  
- 完成項佇列中的物件 (`CorGCReferenceType.CorReferenceFinalizer`) 。 完成項會將根物件排在佇列中，直到完成項執行為止。  
  
 此 `extraData` 欄位包含額外的資料，這取決於參考的來源 (或類型) 。 可能的值包括：  
  
- `DependentSource`. 如果 `type` 是 `CorGCREferenceType.CorHandleStrongDependent` ，這個欄位就是物件，如果是「作用中」，則為要在其中進行垃圾收集的物件 `COR_GC_REFERENCE.Location` 。  
  
- `RefCount`. 如果 `type` 為 `CorGCREferenceType.CorHandleStrongRefCount` ，則此欄位為控制碼的參考計數。  
  
- `Size`. 如果 `type` 為 `CorGCREferenceType.CorHandleStrongSizedByref` ，則此欄位為垃圾收集行程計算物件根之物件樹狀結構的最後大小。 請注意，這項計算不一定是最新的。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯結構](debugging-structures.md)
- [偵錯](index.md)
