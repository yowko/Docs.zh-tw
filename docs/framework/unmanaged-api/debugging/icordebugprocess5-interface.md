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
ms.openlocfilehash: e3aed85e989313e4778e12a6f6bb789ccef49747
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugprocess5-interface"></a>ICorDebugProcess5 介面
可擴充 ICorDebugProcess 介面以支援存取 managed 堆積，以提供的受管理物件，記憶體回收的相關資訊，以判斷是否在偵錯工具，請從應用程式的本機原生映像快取載入影像。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[EnableNGenPolicy 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md)|設定值，這個值會決定應用程式載入 managed 偵錯工具下執行時的原生映像的方式。|  
|[EnumerateGCReferences 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md)|取得要進行記憶體回收處理序中的所有物件的列舉值。|  
|[EnumerateHandles 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)|取得物件控點的程序中的列舉值。|  
|[EnumerateHeap 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md)|取得 managed 堆積上物件的列舉值。|  
|[EnumerateHeapRegions 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md)|取得 managed 堆積的區域中的列舉值。|  
|[GetArrayLayout 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md)|取得在記憶體中的配置資訊的陣列。|  
|[GetGCHeapInformation 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md)|取得指標[COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)結構，其中包含要進行記憶體回收的 managed 堆積上物件的相關資訊。|  
|[GetObject 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md)|取得 managed 堆積上物件的指標。|  
|[GetTypeFields 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md)|取得陣列，其中包含根據其類型識別項類型的欄位資訊的指標。|  
|[GetTypeForTypeID 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md)|取得型別物件，提供其型別識別項為基礎的物件相關資訊。|  
|[GetTypeID 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypeid-method.md)|取得在指定的位址物件的類型識別項。|  
|[GetTypeLayout 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypelayout-method.md)|根據其類型識別項的記憶體中取得物件的配置資訊。|  
  
## <a name="remarks"></a>備註  
 這個介面會以邏輯方式擴充 ICorDebugProcess，ICorDebugProcess2，和[ICorDebugProcess3](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)介面。  
  
> [!NOTE]
>  這個介面不支援從另一部電腦或另一個處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
