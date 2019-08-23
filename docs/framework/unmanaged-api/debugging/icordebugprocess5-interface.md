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
ms.openlocfilehash: 31ecea4857dabc55e8acd3c22a025895a686efcd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931083"
---
# <a name="icordebugprocess5-interface"></a>ICorDebugProcess5 介面
擴充 ICorDebugProcess 介面以支援存取 managed 堆積, 以提供有關受管理物件之垃圾收集的資訊, 以及判斷偵錯工具是否從應用程式本機原生映射快取載入影像。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[EnableNGenPolicy 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md)|設定值, 決定應用程式在 managed 偵錯工具下執行時, 載入原生影像的方式。|  
|[EnumerateGCReferences 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md)|取得要在進程中進行垃圾收集之所有物件的列舉值。|  
|[EnumerateHandles 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)|取得進程中物件控制碼的列舉值。|  
|[EnumerateHeap 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md)|取得 managed 堆積上物件的列舉值。|  
|[EnumerateHeapRegions 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md)|取得受控堆積區域的列舉值。|  
|[GetArrayLayout 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md)|取得記憶體中陣列版面配置的相關資訊。|  
|[GetGCHeapInformation 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md)|取得[COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)結構的指標, 其中包含要在 managed 堆積上進行垃圾收集之物件的相關資訊。|  
|[GetObject 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md)|取得 managed 堆積上物件的指標。|  
|[GetTypeFields 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md)|取得陣列的指標, 其中包含根據類型識別碼之類型的欄位資訊。|  
|[GetTypeForTypeID 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md)|取得型別物件, 根據物件的型別識別碼提供物件的相關資訊。|  
|[GetTypeID 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypeid-method.md)|取得位於指定位址之物件的類型識別碼。|  
|[GetTypeLayout 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypelayout-method.md)|根據物件的類型識別碼, 取得記憶體中之配置的相關資訊。|  
  
## <a name="remarks"></a>備註  
 這個介面會以邏輯方式擴充 ICorDebugProcess、ICorDebugProcess2 和[ICorDebugProcess3](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)介面。  
  
> [!NOTE]
> 此介面不支援從其他電腦或從其他進程遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
