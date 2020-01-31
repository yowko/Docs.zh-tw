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
ms.openlocfilehash: ed5b39ed4b2a14c071bf23fb04efbad6834e8a9d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783977"
---
# <a name="icordebugcomobjectvalue-interface"></a>ICorDebugComObjectValue 介面
提供方法來取得與執行時間可呼叫包裝函式（RCW）相關聯的資訊。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetCachedInterfacePointers 方法](icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|取得目前 RCW 上快取的原始介面指標。|  
|[GetCachedInterfaceTypes 方法](icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|提供目前物件已做為大小寫或當做使用之介面類別型的列舉值。|  
  
## <a name="remarks"></a>備註  
 若要檢查 "ICorDebugValue" 介面的實例是否代表 RCW，偵錯工具會使用 `IID_ICorDebugComObjectValue`呼叫 "ICorDebugValue" 上的 `QueryInterface`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
