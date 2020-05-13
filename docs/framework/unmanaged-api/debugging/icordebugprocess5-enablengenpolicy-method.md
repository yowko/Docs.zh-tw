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
ms.openlocfilehash: fa3cbfee0359b8477f9efe88fe72837b86611bf7
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212798"
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
 如果已成功設定原則，則方法會傳回 `S_OK` 。 如果超出 `ePolicy` [CorDebugNGenPolicy](cordebugngenpolicy-enumeration.md)所定義之列舉值的範圍，此方法會傳回 `E_INVALIDARG` ，且方法呼叫不會有任何作用。 如果無法更新原生映射產生器（Ngen.exe）的原則，則方法會傳回 `E_FAIL` 。  
  
 在 `ICorDebugProcess5::EnableNGenPolicy` 進程的存留期間內，任何時間都可以呼叫方法。 原則會在設定原則之後載入的任何模組生效。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugProcess5 介面](icordebugprocess5-interface.md)
- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
