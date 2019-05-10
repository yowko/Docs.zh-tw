---
title: CorGCReferenceType 列舉
ms.date: 03/30/2017
api_name:
- CorGCReferenceType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorGCReferenceType
helpviewer_keywords:
- CorGCReferenceType
ms.assetid: d9f16439-5a36-4474-8ffd-4f0b2c2bb686
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 690d556eb3991747d1627bae63b9c59ca68daaaa
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64616221"
---
# <a name="corgcreferencetype-enumeration"></a>CorGCReferenceType 列舉
識別要進行記憶體回收的物件來源。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum {  
    CorHandleStrong = 1,  
    CorHandleStrongPinning = 2,  
    CorHandleWeakShort = 4,  
    CorHandleWeakRefCount = 8,  
    CorHandleStrongRefCount = 32,  
    CorHandleStrongDependent = 64,  
    CorHandleStrongAsyncPinned = 128,  
    CorHandleStrongSizedByref = 256,  
  
    CorReferenceStack = 0x80000001,  
    CorReferenceFinalizer = 0x80000002,  
  
    CorHandleStrongOnly = 0x1E3,  
    CorHandleWeakOnly = 0xC,  
    CorHandleAll = 0x7FFFFFFF  
} CorGCReferenceType  
```  
  
## <a name="members"></a>成員  
  
|成員名稱|描述|  
|-----------------|-----------------|  
|`CorHandleStrong`|物件控制代碼資料表中的強式參考控制代碼。|  
|`CorHandleStrongPinning`|控制代碼已釘選的強式參考的物件控制代碼資料表中。|  
|`CorHandleWeakShort`|控制代碼的弱式參考的物件控制代碼資料表中。|  
|`CorHandleWeakRefCount`|物件的控制代碼弱式參考計數物件控制代碼資料表中。|  
|`CorHandleStrongRefCount`|物件的控制代碼參考計數物件控制代碼資料表中。|  
|`CorHandleStrongDependent`|物件的控制代碼相依物件控制代碼資料表中。|  
|`CorHandleStrongAsyncPinned`|物件控制代碼資料表中的非同步固定物件。|  
|`CorHandleStrongSizedByref`|強式控制代碼，保留記憶體回收時集體關閉之所有物件和根物件的估計大小。|  
|`CorReferenceStack`|從 managed 堆疊的參考。|  
|`CorReferenceFinalizer`|從完成項佇列的參考。|  
|CorHandleStrongOnly|傳回只有強式參考控制代碼資料表中。 這個值由[ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)僅方法。|  
|`CorHandleWeakOnly`|傳回只弱式參考控制代碼資料表中。 這個值由[ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)僅方法。|  
|`CorHandleAll`|傳回控制代碼資料表中的所有參考。 這個值由[ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)僅方法。|  
  
## <a name="remarks"></a>備註  
 `CorGCReferenceType`列舉可用，如下所示：  
  
- 值`type`欄位[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)結構，它會指出參考或控制代碼的來源。  
  
- 作為`types`引數[ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)方法，它會指定要包含在列舉中的控制代碼的類型。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯列舉](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
