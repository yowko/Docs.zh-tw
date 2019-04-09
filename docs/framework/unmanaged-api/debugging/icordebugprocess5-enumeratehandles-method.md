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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b3cc158c48e8bb9f833429bbddaa74ed459f1b6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108821"
---
# <a name="icordebugprocess5enumeratehandles-method"></a>ICorDebugProcess5::EnumerateHandles 方法
取得處理序中物件控制代碼的列舉值。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT EnumerateHandles(     [in] CorGCReferenceType types,  
    [out] ICorDebugGCReferenceEnum **ppEnum);  
```  
  
## <a name="parameters"></a>參數  
 `types`  
 [in]位元組合[CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)值，指定要包含在集合中的控制代碼的型別。  
  
 `ppENum`  
 [out]位址指標[ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)也就是列舉值的物件進行記憶體回收。  
  
## <a name="remarks"></a>備註  
 `EnumerateHandles` 是 helper 函式支援的控制代碼資料表檢查。 類似於[ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md)方法，不同之處在於而不是填入[ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)集合與所有的物件進行記憶體回收，它包含具有控制代碼資料表中的控制代碼的物件。  
  
 `types`參數會指定要包含在集合中的控制代碼類型。 `types` 可以是下列三個成員的任何[CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)列舉型別：  
  
-   `CorHandleStrongOnly` （僅限使用強式參考至控點）。  
  
-   `CorHandleWeakOnly` （僅限弱式參考以控點）。  
  
-   `CorHandleAll` （所有控制代碼）。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯結構](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
