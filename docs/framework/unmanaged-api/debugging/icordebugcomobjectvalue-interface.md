---
title: ICorDebugComObjectValue 介面
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugComObjectValue
helpviewer_keywords:
- ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 505a7f6c-d92b-42b4-b539-433f5102ea9b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4db005e1de043e60ffe958de732a5280fcccbea7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54529943"
---
# <a name="icordebugcomobjectvalue-interface"></a>ICorDebugComObjectValue 介面
提供方法來擷取執行階段可呼叫包裝函式 (RCW) 相關聯的資訊。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetCachedInterfacePointers 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|取得在目前的 RCW 上快取的原始介面指標。|  
|[GetCachedInterfaceTypes 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|目前的物件具有要使用的大小寫或做為介面類型提供列舉值。|  
  
## <a name="remarks"></a>備註  
 若要檢查 「 ICorDebugValue 」 介面的執行個體是否代表 RCW，偵錯工具會呼叫`QueryInterface`"ICorDebugValue 」 與上`IID_ICorDebugComObjectValue`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
