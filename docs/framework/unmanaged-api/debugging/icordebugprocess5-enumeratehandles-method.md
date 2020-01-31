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
ms.openlocfilehash: 2a1653055a3834ce1bed0e7de7877b255bea0c38
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792421"
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
 在[CorGCReferenceType](corgcreferencetype-enumeration.md)值的位元組合，這個組合會指定要包含在集合中的控制碼類型。  
  
 `ppENum`  
 脫銷[ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md)位址的指標，這是要進行垃圾收集之物件的列舉值。  
  
## <a name="remarks"></a>備註  
 `EnumerateHandles` 是支援檢查控制碼資料表的 helper 函數。 它類似于[ICorDebugProcess5：： EnumerateGCReferences](icordebugprocess5-enumerategcreferences-method.md)方法，不同之處在于它不會填入要進行垃圾收集之所有物件的[ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md)集合，只會包含具有控制碼資料表之控制碼的物件。  
  
 `types` 參數會指定要包含在集合中的控制碼類型。 `types` 可以是[CorGCReferenceType](corgcreferencetype-enumeration.md)列舉的下列三個成員中的任何一個：  
  
- `CorHandleStrongOnly` （僅限強式參考的控制碼）。  
  
- `CorHandleWeakOnly` （僅限弱式參考的控制碼）。  
  
- `CorHandleAll` （所有控制碼）。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯結構](debugging-structures.md)
- [偵錯](index.md)
