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
ms.openlocfilehash: e22269b76c230f702f4712298fddcd0df1fde50d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179323"
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
|`domain`|指向控制碼或物件所屬的應用程式域的指標。 其值可能是`null`。|  
|`location`|ICorDebugValue 或 ICorDebugReferenceValue 介面對應于要垃圾回收的物件。|  
|`type`|一個[CorGC 參考類型](corgcreferencetype-enumeration.md)枚舉值，指示根來自何處。 如需詳細資訊，請參閱＜備註＞一節。|  
|`extraData`|有關要垃圾回收的物件的其他資料。 此資訊取決於物件的源，如`type`欄位所示。 如需詳細資訊，請參閱＜備註＞一節。|  
  
## <a name="remarks"></a>備註  
 該`type`欄位是一個[CorGC 參考類型](corgcreferencetype-enumeration.md)枚舉值，指示引用來自何處。 特定`COR_GC_REFERENCE`值可以反映以下任何類型的託管物件：  
  
- 來自所有託管堆疊的物件`CorGCReferenceType.CorReferenceStack`。 這包括託管代碼中的即時引用，以及由通用語言運行時創建的物件。  
  
- 控制碼表中的物件 （`CorGCReferenceType.CorHandle*`。 這包括模組中的強引用`HNDTYPE_STRONG` `HNDTYPE_REFCOUNT`（ 和 ） 和 靜態變數。  
  
- 終端子佇列中的物件 （`CorGCReferenceType.CorReferenceFinalizer`。 終端子佇列根物件，直到終端子運行。  
  
 該`extraData`欄位包含額外資料，具體取決於引用的源（或類型）。 可能的值包括：  
  
- `DependentSource`. 如果`type`是`CorGCREferenceType.CorHandleStrongDependent`，則此欄位是物件，如果處於活動狀態，則將物件根在 中`COR_GC_REFERENCE.Location`進行垃圾回收。  
  
- `RefCount`. 如果`type`為`CorGCREferenceType.CorHandleStrongRefCount`，則此欄位是控制碼的引用計數。  
  
- `Size`. 如果`type`為`CorGCREferenceType.CorHandleStrongSizedByref`，則此欄位是垃圾回收器為其計算物件根的物件樹的最後一個大小。 請注意，此計算不一定是最新的。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯結構](debugging-structures.md)
- [偵錯](index.md)
