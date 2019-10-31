---
title: ICorDebugGCReferenceEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugGCReferenceEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGCReferenceEnum
helpviewer_keywords:
- ICorDebugGCReferenceEnum interface [.NET Framework debugging]
ms.assetid: 5f3c91c9-c035-454f-96cc-011cab1ea06b
topic_type:
- apiref
ms.openlocfilehash: 49f89f7d36e74b1fa5921230d7dc6d271d4c0883
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134637"
---
# <a name="icordebuggcreferenceenum-interface"></a>ICorDebugGCReferenceEnum 介面
為將要記憶體回收的物件提供列舉值。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Next 方法](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md)|取得指定的[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)實例數目，其中包含將被垃圾收集之物件的相關資訊。|  
  
## <a name="remarks"></a>備註  
 `ICorDebugGCReferenceEnum` 介面會執行 "ICorDebugEnum" 介面。  
  
 `ICorDebugGCReferenceEnum` 實例會藉由呼叫[ICorDebugProcess5：： EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md)方法來填入[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)實例。 您可以藉由呼叫[ICorDebugGCReference：： Next](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md)方法來列舉[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)物件。  
  
 這個方法所填入之集合中的[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)物件代表三種物件：  
  
- 來自所有 managed 堆疊的物件。 這包括 managed 程式碼中的即時參考，以及 common language runtime 所建立的物件。  
  
- 控制碼資料表中的物件。 這包括模組中的強式參考（`HNDTYPE_STRONG` 和 `HNDTYPE_REFCOUNT`）和靜態變數。  
  
- 完成項佇列中的物件。 完成項會佇列根物件，直到完成項執行為止。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
