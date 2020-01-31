---
title: ICorDebugExceptionObjectValue::EnumerateExceptionCallStack 方法
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectValue.EnumerateExceptionCallStack
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectValue::EnumerateExceptionCallStack
helpviewer_keywords:
- EnumerateExceptionCallStack method, ICorDebugExceptionObjectValue interface [.NET Framework debugging]
- ICorDebugExceptionObjectValue::EnumerateExceptionCallStack method [.NET Framework debugging]
ms.assetid: 00c64533-15dd-47f4-bb97-fe80a1ebadef
topic_type:
- apiref
ms.openlocfilehash: 57eb284bfe39ce92b2d6c03a2aeb4ae84d6aba91
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788672"
---
# <a name="icordebugexceptionobjectvalueenumerateexceptioncallstack-method"></a>ICorDebugExceptionObjectValue::EnumerateExceptionCallStack 方法
取得內嵌在例外狀況物件中之呼叫堆疊的列舉值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumerateExceptionCallStack(  
    [out] ICorDebugExceptionObjectCallStackEnum **ppCallStackEnum  
);  
```  
  
## <a name="parameters"></a>參數  
 ppCallStackEnum  
 脫銷[ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md)介面物件之位址的指標，這是 managed 例外狀況物件的堆疊追蹤列舉值。  
  
## <a name="remarks"></a>備註  
 如果沒有可用的呼叫堆疊資訊，方法會傳回 `S_OK`，而[ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md)是長度為0的有效枚舉器。 如果方法無法取得堆疊追蹤資訊，則傳回值會 `E_FAIL`，而且不會傳回任何枚舉器。  
  
 [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md)物件負責從 exception 物件的 `_stackTrace` 欄位解碼堆疊追蹤資料。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugExceptionObjectValue 介面](icordebugexceptionobjectvalue-interface.md)
- [偵錯介面](debugging-interfaces.md)
