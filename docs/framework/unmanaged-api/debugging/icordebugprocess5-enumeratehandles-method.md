---
title: ICorDebugProcess5::EnumerateHandles 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHandles
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHandles
helpviewer_keywords:
- EnumerateHandles method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHandles method [.NET Framework debugging]
ms.assetid: 7d7fa796-0dc6-4ee8-9d56-40166246d91d
topic_type:
- apiref
ms.openlocfilehash: 607847180cca039d4c71f26e446a17a14dc2fb9e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724334"
---
# <a name="icordebugprocess5enumeratehandles-method"></a>ICorDebugProcess5::EnumerateHandles 方法

取得進程中物件控制碼的列舉值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumerateHandles(     [in] CorGCReferenceType types,  
    [out] ICorDebugGCReferenceEnum **ppEnum);  
```  
  
## <a name="parameters"></a>參數  

 `types`  
 在 [CorGCReferenceType](corgcreferencetype-enumeration.md) 值的位元組合，指定要包含在集合中的控制碼類型。  
  
 `ppENum`  
 擴展 [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) 位址的指標，其為要進行垃圾收集之物件的列舉值。  
  
## <a name="remarks"></a>備註  

 `EnumerateHandles` 這是支援檢查控制碼資料表的 helper 函數。 它類似于 [ICorDebugProcess5：： EnumerateGCReferences](icordebugprocess5-enumerategcreferences-method.md) 方法，不同之處在于，它只會包含具有控制碼資料表之控制碼的物件，而不是使用所有要進行垃圾收集的物件來填入 [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) 集合。  
  
 `types`參數會指定要包含在集合中的控制碼類型。 `types` 可以是 [CorGCReferenceType](corgcreferencetype-enumeration.md) 列舉的下列三個成員之一：  
  
- `CorHandleStrongOnly` 只有)  (強式參考的控制碼。  
  
- `CorHandleWeakOnly` 只有)  (弱式參考的控制碼。  
  
- `CorHandleAll` (所有) 的控制碼。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯結構](debugging-structures.md)
- [偵錯](index.md)
