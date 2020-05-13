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
ms.openlocfilehash: 5650a7e6e6cb0108f0d043914ea94debe2b703bf
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213097"
---
# <a name="icordebuggcreferenceenum-interface"></a>ICorDebugGCReferenceEnum 介面
為將要記憶體回收的物件提供列舉值。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[下一個方法](icordebuggcreferenceenum-next-method.md)|取得指定的[COR_GC_REFERENCE](cor-gc-reference-structure.md)實例數目，其中包含將被垃圾收集之物件的相關資訊。|  
  
## <a name="remarks"></a>備註  
 介面會執行 `ICorDebugGCReferenceEnum` "ICorDebugEnum" 介面。  
  
 `ICorDebugGCReferenceEnum`實例會藉由呼叫[ICorDebugProcess5：： EnumerateGCReferences](icordebugprocess5-enumerategcreferences-method.md)方法來填入[COR_GC_REFERENCE](cor-gc-reference-structure.md)實例。 藉由呼叫[ICorDebugGCReference：： Next](icordebuggcreferenceenum-next-method.md)方法，可以列舉[COR_GC_REFERENCE](cor-gc-reference-structure.md)物件。  
  
 這個方法所填入之集合中的[COR_GC_REFERENCE](cor-gc-reference-structure.md)物件代表三種物件：  
  
- 來自所有 managed 堆疊的物件。 這包括 managed 程式碼中的即時參考，以及 common language runtime 所建立的物件。  
  
- 控制碼資料表中的物件。 這包括強式參考（ `HNDTYPE_STRONG` 和 `HNDTYPE_REFCOUNT` ），以及模組中的靜態變數。  
  
- 完成項佇列中的物件。 完成項會佇列根物件，直到完成項執行為止。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](debugging-interfaces.md)
