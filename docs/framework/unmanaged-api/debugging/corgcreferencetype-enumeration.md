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
ms.openlocfilehash: e2903637faa11a3c0a62080cc6fafcf1fc668a56
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704990"
---
# <a name="corgcreferencetype-enumeration"></a>CorGCReferenceType 列舉

識別要進行記憶體回收的物件來源。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
|`CorHandleStrongPinning`|物件控制碼資料表中釘選強式參考的控制碼。|  
|`CorHandleWeakShort`|物件控制碼資料表中的弱式參考控制碼。|  
|`CorHandleWeakRefCount`|物件控制碼資料表中弱式參考計數物件的控制碼。|  
|`CorHandleStrongRefCount`|物件控制碼資料表中參考計數物件的控制碼。|  
|`CorHandleStrongDependent`|物件控制碼資料表中相依物件的控制碼。|  
|`CorHandleStrongAsyncPinned`|物件控制代碼資料表中的非同步固定物件。|  
|`CorHandleStrongSizedByref`|強式控制代碼，保留記憶體回收時集體關閉之所有物件和根物件的估計大小。|  
|`CorReferenceStack`|受控堆疊中的參考。|  
|`CorReferenceFinalizer`|完成項佇列的參考。|  
|CorHandleStrongOnly|只傳回控制碼資料表中的強式參考。 只有 [ICorDebugProcess5：： EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) 方法會使用這個值。|  
|`CorHandleWeakOnly`|只傳回控制碼資料表中的弱式參考。 只有 [ICorDebugProcess5：： EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) 方法會使用這個值。|  
|`CorHandleAll`|傳回控制碼資料表中的所有參考。 只有 [ICorDebugProcess5：： EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) 方法會使用這個值。|  
  
## <a name="remarks"></a>備註  

 `CorGCReferenceType`列舉的使用方式如下：  
  
- 做為 `type` [COR_GC_REFERENCE](cor-gc-reference-structure.md) 結構的欄位值，它會指出參考或控制碼的來源。  
  
- 作為 `types` [ICorDebugProcess5：： EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) 方法的引數，它會指定要包含在列舉中的控制碼類型。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯列舉](debugging-enumerations.md)
