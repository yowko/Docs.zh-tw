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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 22cd08154268bdf1e819a0ec0067b05a81d60b22
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025820"
---
# <a name="icordebugguidtotypeenum-interface"></a>ICorDebugGuidToTypeEnum 介面
提供列舉值會定義一組的 Guid 和其對應的類型，都由 ICorDebugType 的執行個體之間的對應。 此介面繼承自 ICorDebugEnum 介面的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[ICorDebugGuidToTypeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md)|取得指定的數目[CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md)對應 Guid 型別資訊的執行個體。|  
  
## <a name="remarks"></a>備註  
 `ICorDebugGuidToTypeEnum`介面物件可以藉由呼叫擷取[ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)方法。 偵錯工具可以呼叫此介面[下一步](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md)方法來擷取[CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md)中載入的物件表示受管理的 Windows 執行階段類型的表示法的對應用於呼叫的應用程式定義域[ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)方法。  
  
## <a name="requirements"></a>需求  
 **平台：** Windows 執行階段  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
