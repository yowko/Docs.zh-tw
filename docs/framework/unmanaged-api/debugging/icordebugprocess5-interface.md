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
ms.openlocfilehash: cef69ac7e3572b67dd676ce8408e4210d93accf0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717574"
---
# <a name="icordebugprocess5-interface"></a>ICorDebugProcess5 介面

擴充 ICorDebugProcess 介面以支援存取 managed 堆積，以提供 managed 物件的垃圾收集資訊，以及判斷偵錯工具是否從應用程式本機原生映射快取載入影像。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[EnableNGenPolicy 方法](icordebugprocess5-enablengenpolicy-method.md)|設定值，這個值會決定應用程式如何在 managed 偵錯工具下執行時載入原生映射。|  
|[EnumerateGCReferences 方法](icordebugprocess5-enumerategcreferences-method.md)|取得要在進程中進行垃圾收集之所有物件的列舉值。|  
|[EnumerateHandles 方法](icordebugprocess5-enumeratehandles-method.md)|取得進程中物件控制碼的列舉值。|  
|[EnumerateHeap 方法](icordebugprocess5-enumerateheap-method.md)|取得 managed 堆積上物件的列舉值。|  
|[EnumerateHeapRegions 方法](icordebugprocess5-enumerateheapregions-method.md)|取得 managed 堆積區域的列舉值。|  
|[GetArrayLayout 方法](icordebugprocess5-getarraylayout-method.md)|取得記憶體中陣列版面配置的相關資訊。|  
|[GetGCHeapInformation 方法](icordebugprocess5-getgcheapinformation-method.md)|取得 [COR_HEAPINFO](cor-heapinfo-structure.md) 結構的指標，其中包含要在 managed 堆積上進行垃圾收集之物件的相關資訊。|  
|[GetObject 方法](icordebugprocess5-getobject-method.md)|取得 managed 堆積上物件的指標。|  
|[GetTypeFields 方法](icordebugprocess5-gettypefields-method.md)|取得陣列的指標，該陣列包含以其類型識別碼為基礎之類型的欄位資訊。|  
|[GetTypeForTypeID 方法](icordebugprocess5-gettypefortypeid-method.md)|取得型別物件，它會根據物件的型別識別碼來提供物件的相關資訊。|  
|[GetTypeID 方法](icordebugprocess5-gettypeid-method.md)|取得位於指定位址之物件的類型識別碼。|  
|[GetTypeLayout 方法](icordebugprocess5-gettypelayout-method.md)|根據物件的類型識別碼，取得記憶體中物件配置的相關資訊。|  
  
## <a name="remarks"></a>備註  

 這個介面會以邏輯方式擴充 ICorDebugProcess、ICorDebugProcess2 和 [ICorDebugProcess3](icordebugprocess3-interface.md) 介面。  
  
> [!NOTE]
> 此介面不支援從另一部電腦或另一個進程，從遠端呼叫。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
