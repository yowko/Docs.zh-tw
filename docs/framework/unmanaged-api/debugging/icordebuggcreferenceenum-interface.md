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
ms.openlocfilehash: 12ce800cb83ef4f79710aa441b50be860526023c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728117"
---
# <a name="icordebuggcreferenceenum-interface"></a>ICorDebugGCReferenceEnum 介面

為將要記憶體回收的物件提供列舉值。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[下一個方法](icordebuggcreferenceenum-next-method.md)|取得指定數目的 [COR_GC_REFERENCE](cor-gc-reference-structure.md) 實例，其中包含將會進行垃圾收集之物件的相關資訊。|  
  
## <a name="remarks"></a>備註  

 介面會實 `ICorDebugGCReferenceEnum` ICorDebugEnum 的介面。  
  
 藉 `ICorDebugGCReferenceEnum` 由呼叫[ICorDebugProcess5：： EnumerateGCReferences](icordebugprocess5-enumerategcreferences-method.md)方法，將實例填入[COR_GC_REFERENCE](cor-gc-reference-structure.md)實例。 您可以藉由呼叫[ICorDebugGCReference：： Next](icordebuggcreferenceenum-next-method.md)方法來列舉[COR_GC_REFERENCE](cor-gc-reference-structure.md)物件。  
  
 由這個方法填入之集合中的 [COR_GC_REFERENCE](cor-gc-reference-structure.md) 物件代表三種物件：  
  
- 所有 managed 堆疊中的物件。 這包括 managed 程式碼中的即時參考，以及 common language runtime 所建立的物件。  
  
- 控制碼資料表中的物件。 這包括 (中的強式參考 `HNDTYPE_STRONG` ，以及 `HNDTYPE_REFCOUNT` 模組中的) 和靜態變數。  
  
- 完成項佇列中的物件。 完成項會將根物件排在佇列中，直到完成項執行為止。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](debugging-interfaces.md)
