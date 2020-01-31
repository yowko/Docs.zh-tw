---
title: ICorDebugProcess5::EnableNGENPolicy 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5::EnableNGenPolicy
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnableNGENPolicy
helpviewer_keywords:
- ICorDebugProcess5::EnableNGENPolicy method [.NET Framework debugging]
- EnableNGENPolicy method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 3b8e15ca-3c72-4685-a937-da4c739cb9e9
topic_type:
- apiref
ms.openlocfilehash: 9497bea9b7cc5eb98876c923858dbcbc6adf9d07
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792455"
---
# <a name="icordebugprocess5enablengenpolicy-method"></a>ICorDebugProcess5::EnableNGENPolicy 方法
設定值，決定應用程式在 managed 偵錯工具下執行時，載入原生影像的方式。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnableNGENPolicy(  
    [in] CorDebugNGENPolicy ePolicy  
);  
```  
  
## <a name="parameters"></a>參數  
 `ePolicy`  
 在[CorDebugNGenPolicy](cordebugngenpolicy-enumeration.md)常數，可決定應用程式在 managed 偵錯工具下執行時，載入原生影像的方式。  
  
## <a name="remarks"></a>備註  
 如果原則設定成功，此方法會傳回 `S_OK`。 如果 `ePolicy` 超出[CorDebugNGenPolicy](cordebugngenpolicy-enumeration.md)所定義之列舉值的範圍，此方法會傳回 `E_INVALIDARG` 而方法呼叫則不會有任何作用。 如果無法更新原生映射產生器（Ngen.exe）的原則，則此方法會傳回 `E_FAIL`。  
  
 在進程的存留期間，任何時間都可以呼叫 `ICorDebugProcess5::EnableNGenPolicy` 方法。 原則會在設定原則之後載入的任何模組生效。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugProcess5 介面](icordebugprocess5-interface.md)
- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
