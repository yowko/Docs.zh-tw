---
title: ICorDebugProcess5 介面
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5
helpviewer_keywords:
- ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 30a39d79-1f10-4328-9c5d-094ed824e2ba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b5904083be66d4bd6dc69729bebc28db8a800e77
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089227"
---
# <a name="icordebugprocess5-interface"></a>ICorDebugProcess5 介面
擴充 ICorDebugProcess 介面，以支援存取 managed 堆積，以提供受管理的物件，記憶體回收的相關資訊，並判斷是否在偵錯工具會在 從應用程式本機的原生映像快取載入映像。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[EnableNGenPolicy 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md)|設定值，這個值會決定應用程式載入 managed 偵錯工具下執行時的原生映像的方式。|  
|[EnumerateGCReferences 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md)|取得要進行記憶體回收處理序中的所有物件的列舉值。|  
|[EnumerateHandles 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)|取得處理序中物件控制代碼的列舉值。|  
|[EnumerateHeap 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md)|取得 managed 堆積上物件的列舉值。|  
|[EnumerateHeapRegions 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md)|取得 managed 堆積的區域中的列舉值。|  
|[GetArrayLayout 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md)|取得相關資訊的版面配置陣列的記憶體中。|  
|[GetGCHeapInformation 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md)|取得指標[COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)結構，其中包含要進行記憶體回收 managed 堆積上物件的相關資訊。|  
|[GetObject 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md)|取得 managed 堆積上物件的指標。|  
|[GetTypeFields 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md)|取得陣列，其中包含根據其型別識別項類型的欄位資訊的指標。|  
|[GetTypeForTypeID 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md)|取得型別物件，提供其型別識別項為基礎之物件的相關資訊。|  
|[GetTypeID 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypeid-method.md)|取得物件的型別識別項，在指定的位址。|  
|[GetTypeLayout 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypelayout-method.md)|取得根據其型別識別項的記憶體中的物件配置資訊。|  
  
## <a name="remarks"></a>備註  
 這個介面會以邏輯方式擴充 ICorDebugProcess，ICorDebugProcess2，並[ICorDebugProcess3](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)介面。  
  
> [!NOTE]
>  此介面不支援從另一部電腦，或是從另一個處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
