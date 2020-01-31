---
title: ICorDebugValue3::GetSize64 方法
ms.date: 03/30/2017
api_name:
- ICorDebugValue3::GetSize64
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue3::GetSize64
helpviewer_keywords:
- GetSize64 method, ICorDebugValue3 interface [.NET Framework debugging]
- ICorDebugValue3::GetSize64 method [.NET Framework debugging]
ms.assetid: fee56a29-3154-4192-958d-71da2ced3740
topic_type:
- apiref
ms.openlocfilehash: 7ae06d825565faff70b0c8be2ccbee5228737e41
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791107"
---
# <a name="icordebugvalue3getsize64-method"></a>ICorDebugValue3::GetSize64 方法
取得這個[ICorDebugValue3](icordebugvalue3-interface.md)物件的大小（以位元組為單位）。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetSize64(  
    [out] ULONG64 *pSize  
);  
```  
  
## <a name="parameters"></a>參數  
 pSize  
 脫銷這個物件的大小指標（以位元組為單位）。  
  
## <a name="remarks"></a>備註  
 如果此值的類型是參考型別，這個方法會傳回指標的大小，而不是物件的大小。  
  
 `ICorDebugValue3::GetSize` 方法與其輸出參數類型中的[ICorDebugValue：： GetSize](icordebugvalue-getsize-method.md)方法不同。 在[ICorDebugValue：： GetSize](icordebugvalue-getsize-method.md)中，output 參數是 `ULONG32`。在 `ICorDebugValue3::GetSize`中，這是 `ULONG64`。 這可讓[ICorDebugValue3](icordebugvalue3-interface.md)介面報告超過2gb 的陣列大小。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugValue3 介面](icordebugvalue3-interface.md)
- [偵錯介面](debugging-interfaces.md)
