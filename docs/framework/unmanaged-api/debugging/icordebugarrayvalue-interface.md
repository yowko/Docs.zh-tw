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
ms.openlocfilehash: 0944f3379c18cba56ab65fe40a5b94a64d8a8991
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76778194"
---
# <a name="icordebugarrayvalue-interface"></a>ICorDebugArrayValue 介面

ICorDebugHeapValue 的子類別，表示一維或多維陣列。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetBaseIndicies 方法](icordebugarrayvalue-getbaseindicies-method.md)|取得陣列中每個維度的基底索引。|  
|[GetCount 方法](icordebugarrayvalue-getcount-method.md)|取得陣列中的元素總數。|  
|[GetDimensions 方法](icordebugarrayvalue-getdimensions-method.md)|取得陣列的維度。|  
|[GetElement 方法](icordebugarrayvalue-getelement-method.md)|取得值，表示陣列中的指定元素。|  
|[GetElementAtPosition 方法](icordebugarrayvalue-getelementatposition-method.md)|取得位於指定位置的專案，將陣列視為以零為基底的一維陣列。|  
|[GetElementType 方法](icordebugarrayvalue-getelementtype-method.md)|取得陣列中元素的簡單類型。|  
|[GetRank 方法](icordebugarrayvalue-getrank-method.md)|取得陣列的維度數目。|  
|[HasBaseIndicies 方法](icordebugarrayvalue-hasbaseindicies-method.md)|判斷陣列是否有基底索引。|  
  
## <a name="remarks"></a>備註  
 `ICorDebugArrayValue` 支援一維和多維度陣列。  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](debugging-interfaces.md)
