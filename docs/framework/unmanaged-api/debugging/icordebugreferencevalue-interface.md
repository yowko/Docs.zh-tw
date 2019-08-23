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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 67006603747abd89f1b635c065860dcbe1c47a29
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965637"
---
# <a name="icordebugreferencevalue-interface"></a>ICorDebugReferenceValue 介面
提供管理物件之參考值的方法。 (亦即, 此介面提供管理指標的方法)。此介面會執行 "ICorDebugValue"。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Dereference 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereference-method.md)|取得所參考的物件。|  
|[DereferenceStrong 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereferencestrong-method.md)|未實作。 請勿呼叫此方法。|  
|[GetValue 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-getvalue-method.md)|取得受參考物件目前的記憶體位址。|  
|[IsNull 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-isnull-method.md)|取得值, 指出這`ICorDebugReferenceValue`是否為 null 值, 在此`ICorDebugReferenceValue`情況下, 不會指向物件。|  
|[SetValue 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-setvalue-method.md)|設定目前的記憶體位址。 也就是說, 這個方法會將此`ICorDebugReferenceValue`設定為指向物件。|  
  
## <a name="remarks"></a>備註  
 通用語言執行平臺 (CLR) 可能會在已調試的進程繼續時, 對物件進行垃圾收集。 垃圾收集可能會在記憶體中移動物件。 `ICorDebugReferenceValue`會與垃圾收集合作, 以便在垃圾收集之後更新其資訊, 或在垃圾收集之前隱含地將其視為無效。  
  
 繼續`ICorDebugReferenceValue`進行已調試的進程之後, 可能會隱含地使物件失效。 衍生的 "ICorDebugHandleValue" 在明確釋放或公開之前不會無效。  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
