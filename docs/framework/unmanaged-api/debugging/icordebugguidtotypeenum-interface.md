---
title: ICorDebugGuidToTypeEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugGuidToTypeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGuidToTypeEnum
helpviewer_keywords:
- ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: aa32b12b-05fc-4ea8-a904-adae25034269
topic_type:
- apiref
ms.openlocfilehash: 149c5b09639c8809e736ade09566e7b1b530e3eb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705705"
---
# <a name="icordebugguidtotypeenum-interface"></a>ICorDebugGuidToTypeEnum 介面

提供列舉值，這個列舉值會定義一組 Guid 與其對應類型之間的對應，這些類型是由 ICorDebugType 實例表示。 此介面繼承 ICorDebugEnum 介面的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[ICorDebugGuidToTypeEnum：： Next](icordebugguidtotypeenum-next-method.md)|取得將 Guid 對應至類型資訊的指定 [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) 實例數目。|  
  
## <a name="remarks"></a>備註  

 藉 `ICorDebugGuidToTypeEnum` 由呼叫 [ICorDebugAppDomain3：： GetCachedWinRTTypes](icordebugappdomain3-getcachedwinrttypes-method.md) 方法，即可取出介面物件。 偵錯工具可以呼叫這個介面的 [Next](icordebugguidtotypeenum-next-method.md) 方法來取出 [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) 物件，這些物件代表載入至用來呼叫 [ICorDebugAppDomain3：： GetCachedWinRTTypes](icordebugappdomain3-getcachedwinrttypes-method.md) 方法 Windows 執行階段之應用程式域中的 managed 標記法對應。  
  
## <a name="requirements"></a>需求  

 **平臺：** Windows 執行階段  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](debugging-interfaces.md)
