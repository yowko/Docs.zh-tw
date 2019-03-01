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
ms.openlocfilehash: 4709d1b8126436d4400c788891960100915cd1bc
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971431"
---
# <a name="icordebugreferencevalue-interface"></a>ICorDebugReferenceValue 介面
提供方法，可管理的參考物件的值。 （也就是這個介面提供管理指標的方法）。這個介面會實作 「 ICorDebugValue"。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Dereference 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereference-method.md)|取得參考的物件。|  
|[DereferenceStrong 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereferencestrong-method.md)|未實作。 請勿呼叫這個方法。|  
|[GetValue 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-getvalue-method.md)|取得參考物件的目前記憶體位址。|  
|[IsNull 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-isnull-method.md)|取得值，指出是否這`ICorDebugReferenceValue`為 null 值，在此情況下`ICorDebugReferenceValue`未指向物件。|  
|[SetValue 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-setvalue-method.md)|設定目前的記憶體位址。 也就是說，這個方法會設定這個`ICorDebugReferenceValue`指向物件。|  
  
## <a name="remarks"></a>備註  
 Common language runtime (CLR) 偵錯的處理序會繼續時，可以執行回收物件。 記憶體回收可能會移動物件在記憶體中。 `ICorDebugReferenceValue`會是與合作的記憶體回收，讓記憶體回收之後, 會更新其資訊，或它之前的記憶體回收會以隱含方式失效。  
  
 `ICorDebugReferenceValue`物件可能會因為隱含失效之後繼續執行偵錯的處理序。 衍生的 」 ICorDebugHandleValue 」 不會失效，直到明確釋放或公開。  
  
> [!NOTE]
>  這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱


- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
