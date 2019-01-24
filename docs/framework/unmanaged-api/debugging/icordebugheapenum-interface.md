---
title: ICorDebugHeapEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugHeapEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapEnum
helpviewer_keywords:
- ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 99cbc1eb-d539-4f76-a0d8-b93348112f14
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9e9f58a0bc51e8a22672df6ab9bd94009c00f9bb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54688076"
---
# <a name="icordebugheapenum-interface"></a>ICorDebugHeapEnum 介面
為 Managed 堆積上的物件提供列舉值。 這個介面是 ICorDebugEnum 介面的子類別。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Next 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md)|取得指定的數目[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)包含 managed 堆積上物件的相關資訊的執行個體。|  
  
## <a name="remarks"></a>備註  
 `ICorDebugHeapEnum` ICorDebugEnum 介面實作的介面。  
  
 `ICorDebugHeapEnum`執行個體填入[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)藉由呼叫的執行個體[ICorDebugProcess5::EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md)方法。 每個[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)集合中的執行個體代表的是在堆積上的即時物件或物件不根目錄的任何物件，但尚未收集記憶體回收行程。 [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)集合中的物件可以藉由呼叫列舉[icordebugheapenum:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md)方法。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
