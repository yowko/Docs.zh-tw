---
title: ICorDebugVariableHomeEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHomeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHomeEnum
helpviewer_keywords:
- ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: c312ae6d-c8dc-48d6-9f1e-ead515c88fdf
topic_type:
- apiref
ms.openlocfilehash: 8e8caad9f0fc60121dbd1c738a6024da3e4d02f6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725998"
---
# <a name="icordebugvariablehomeenum-interface"></a>ICorDebugVariableHomeEnum 介面

提供函數中區域變數和引數的列舉值。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[下一個方法](icordebugvariablehomeenum-next-method.md)|取得 [ICorDebugVariableHome](icordebugvariablehome-interface.md) 實例的指定數目，其中包含函式中區域變數和引數的相關資訊。|  
  
## <a name="remarks"></a>備註  

 介面會實 `ICorDebugVariableHomeEnum` ICorDebugEnum 介面。  
  
 `ICorDebugVariableHomeEnum`實例會藉由呼叫[ICorDebugCode4：： EnumerateVariableHomes](icordebugcode4-enumeratevariablehomes-method.md)方法來填入[ICorDebugVariableHome](icordebugvariablehome-interface.md)實例。 集合中的每個 [ICorDebugVariableHome](icordebugvariablehome-interface.md) 實例都代表函數中的區域變數或引數。 您可以藉由呼叫[ICorDebugVariableHomeEnum：： Next](icordebugvariablehomeenum-next-method.md)方法來列舉集合中的[ICorDebugVariableHome](icordebugvariablehome-interface.md)物件。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugVariableHome 介面](icordebugvariablehome-interface.md)
- [偵錯介面](debugging-interfaces.md)
