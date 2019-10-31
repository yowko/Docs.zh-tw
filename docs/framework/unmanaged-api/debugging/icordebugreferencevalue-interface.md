---
title: ICorDebugReferenceValue 介面
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue
helpviewer_keywords:
- ICorDebugReferenceValue interface [.NET Framework debugging]
ms.assetid: 2040e2be-119a-4cfb-ae52-b0b6f052665c
topic_type:
- apiref
ms.openlocfilehash: 16d7b89ee441e8d634c36fb87185b3f2846860b3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137713"
---
# <a name="icordebugreferencevalue-interface"></a>ICorDebugReferenceValue 介面
提供管理物件之參考值的方法。 （亦即，此介面提供管理指標的方法）。此介面會執行 "ICorDebugValue"。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Dereference 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereference-method.md)|取得所參考的物件。|  
|[DereferenceStrong 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereferencestrong-method.md)|未實作。 請勿呼叫此方法。|  
|[GetValue 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-getvalue-method.md)|取得受參考物件目前的記憶體位址。|  
|[IsNull 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-isnull-method.md)|取得值，指出此 `ICorDebugReferenceValue` 是否為 null 值，在此情況下，`ICorDebugReferenceValue` 不會指向物件。|  
|[SetValue 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-setvalue-method.md)|設定目前的記憶體位址。 也就是說，這個方法會將這個 `ICorDebugReferenceValue` 設定為指向物件。|  
  
## <a name="remarks"></a>備註  
 通用語言執行平臺（CLR）可能會在已調試的進程繼續時，對物件進行垃圾收集。 垃圾收集可能會在記憶體中移動物件。 `ICorDebugReferenceValue` 將與垃圾收集合作，以便在垃圾收集之後更新其資訊，或在垃圾收集之前隱含地使其失效。  
  
 繼續進行已調試的進程之後，`ICorDebugReferenceValue` 物件可能會隱含失效。 衍生的 "ICorDebugHandleValue" 在明確釋放或公開之前不會無效。  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
