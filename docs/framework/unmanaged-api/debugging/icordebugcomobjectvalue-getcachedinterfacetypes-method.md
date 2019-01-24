---
title: ICorDebugComObjectValue::GetCachedInterfaceTypes 方法
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue::GetCachedInterfaceTypes
api_location:
- mscordbi.dll
f1_keywords:
- ICorDebugComObjectValue::GetCachedInterfaceTypes
helpviewer_keywords:
- GetCachedInterface method, ICorDebugComObjectValue interface [.NET Framework debugging]
- ICorDebugComObjectValue::GetCachedInterface method [.NET Framework debugging]
ms.assetid: d492284f-d3c5-4614-adb8-d718d5042500
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6d0d2c4af79a7d5a7123c5fe0ba043c2dd6302f5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54525803"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacetypes-method"></a>ICorDebugComObjectValue::GetCachedInterfaceTypes 方法
目前的物件已轉換成或做為介面類型提供列舉值。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetCachedInterfaceTypes(  
    [in] BOOL bIInspectableOnly,  
    [out] ICorDebugTypeEnum **ppInterfacesEnum);  
```  
  
#### <a name="parameters"></a>參數  
 `bIInspectableOnly`  
 [in]值，指出方法是否只傳回[!INCLUDE[wrt](../../../../includes/wrt-md.md)]介面 (`IInspectable`介面) 或快取執行階段可呼叫包裝函式 (RCW) 的所有 COM 介面。  
  
 `ppInterfacesEnum`  
 [out]ICorDebugTypeEnum 列舉程式，提供 ICorDebugType 物件，表示快取的介面類型的存取權的位址指標篩選根據`bIInspectableOnly`。  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [ICorDebugComObjectValue 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
