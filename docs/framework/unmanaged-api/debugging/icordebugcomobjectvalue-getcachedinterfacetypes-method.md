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
ms.openlocfilehash: f5f0f11683043f1c287dd3ca3071830bcfb46502
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677553"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacetypes-method"></a>ICorDebugComObjectValue::GetCachedInterfaceTypes 方法

提供目前物件已轉換成或當做使用之介面類別型的列舉值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetCachedInterfaceTypes(  
    [in] BOOL bIInspectableOnly,  
    [out] ICorDebugTypeEnum **ppInterfacesEnum);  
```  
  
## <a name="parameters"></a>參數  

 `bIInspectableOnly`  
 在值，這個值會指出方法是否只傳回 Windows 執行階段介面 (介面) 或執行時間可呼叫包裝函式所快取 `IInspectable` 的所有 COM 介面 (RCW) 。  
  
 `ppInterfacesEnum`  
 擴展ICorDebugTypeEnum 列舉值的位址指標，這個列舉值會提供 ICorDebugType 物件的存取權，這些物件代表根據所篩選的快取介面類別型 `bIInspectableOnly` 。  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugComObjectValue 介面](icordebugcomobjectvalue-interface.md)
- [偵錯介面](debugging-interfaces.md)
