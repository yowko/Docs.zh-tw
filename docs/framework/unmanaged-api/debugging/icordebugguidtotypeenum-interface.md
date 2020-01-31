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
ms.openlocfilehash: 2663e5604cdd55472cc148b2d2b38599df81f11e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794444"
---
# <a name="icordebugguidtotypeenum-interface"></a>ICorDebugGuidToTypeEnum 介面
提供的列舉值會定義一組 Guid 與其對應類型（由 ICorDebugType 實例表示）之間的對應。 這個介面會繼承 ICorDebugEnum 介面中的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[ICorDebugGuidToTypeEnum：： Next](icordebugguidtotypeenum-next-method.md)|取得將 Guid 對應至類型資訊的指定[CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md)實例數目。|  
  
## <a name="remarks"></a>備註  
 藉由呼叫[ICorDebugAppDomain3：： GetCachedWinRTTypes](icordebugappdomain3-getcachedwinrttypes-method.md)方法，可以抓取 `ICorDebugGuidToTypeEnum` 介面物件。 偵錯工具可以呼叫這個介面的[下一個](icordebugguidtotypeenum-next-method.md)方法，來抓取[CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md)物件，以代表載入在用於呼叫[ICorDebugAppDomain3：： GetCachedWinRTTypes](icordebugappdomain3-getcachedwinrttypes-method.md)方法之應用程式域中的 Windows 執行階段類型的 managed 標記法。  
  
## <a name="requirements"></a>需求  
 **平臺：** Windows 執行階段  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](debugging-interfaces.md)
