---
title: ICorDebugArrayValue 介面
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue interface
helpviewer_keywords:
- ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: dc437751-7093-44e2-bfdc-191d9ce3c192
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 67fd1a9174b04e42b53f2b866a1dfdd504362aa9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645613"
---
# <a name="icordebugarrayvalue-interface"></a>ICorDebugArrayValue 介面

ICorDebugHeapValue，表示一維或多維陣列的子類別。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetBaseIndicies 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getbaseindicies-method.md)|取得陣列中的每個維度的基底的索引。|  
|[GetCount 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getcount-method.md)|取得陣列中的項目總數。|  
|[GetDimensions 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getdimensions-method.md)|取得陣列維度。|  
|[GetElement 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelement-method.md)|取得值，表示陣列中指定的項目。|  
|[GetElementAtPosition 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementatposition-method.md)|取得陣列視為的以零為起始的一維陣列的指定位置的項目。|  
|[GetElementType 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementtype-method.md)|取得陣列中的簡單類型的項目。|  
|[GetRank 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getrank-method.md)|取得陣列的維度數目。|  
|[HasBaseIndicies 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-hasbaseindicies-method.md)|判斷陣列是否有基底的索引。|  
  
## <a name="remarks"></a>備註  
 `ICorDebugArrayValue` 支援一維及多維陣列。  
  
> [!NOTE]
>  這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
