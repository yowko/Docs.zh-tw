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
ms.openlocfilehash: 74b3c7bed54f3735efbd5d2c56962d427518f71a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790939"
---
# <a name="icordebugvariablehomeenum-interface"></a>ICorDebugVariableHomeEnum 介面
提供函式中區域變數和引數的列舉值。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Next 方法](icordebugvariablehomeenum-next-method.md)|取得指定的[ICorDebugVariableHome](icordebugvariablehome-interface.md)實例數目，其中包含函式中區域變數和引數的相關資訊。|  
  
## <a name="remarks"></a>備註  
 `ICorDebugVariableHomeEnum` 介面會執行 ICorDebugEnum 介面。  
  
 `ICorDebugVariableHomeEnum` 實例會藉由呼叫[ICorDebugCode4：： EnumerateVariableHomes](icordebugcode4-enumeratevariablehomes-method.md)方法來填入[ICorDebugVariableHome](icordebugvariablehome-interface.md)實例。 集合中的每個[ICorDebugVariableHome](icordebugvariablehome-interface.md)實例都代表函式中的區域變數或引數。 您可以藉由呼叫[ICorDebugVariableHomeEnum：： Next](icordebugvariablehomeenum-next-method.md)方法來列舉集合中的[ICorDebugVariableHome](icordebugvariablehome-interface.md)物件。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugVariableHome 介面](icordebugvariablehome-interface.md)
- [偵錯介面](debugging-interfaces.md)
