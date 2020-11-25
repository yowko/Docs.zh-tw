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
ms.openlocfilehash: e3dfd3cae83c7891d246ff3a81427c161cc0e2d1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731384"
---
# <a name="icordebugprocess5enablengenpolicy-method"></a>ICorDebugProcess5::EnableNGENPolicy 方法

設定值，這個值會決定應用程式如何在 managed 偵錯工具下執行時載入原生映射。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnableNGENPolicy(  
    [in] CorDebugNGENPolicy ePolicy  
);  
```  
  
## <a name="parameters"></a>參數  

 `ePolicy`  
 在 [CorDebugNGenPolicy](cordebugngenpolicy-enumeration.md) 常數，決定應用程式如何在 managed 偵錯工具下執行時載入原生映射。  
  
## <a name="remarks"></a>備註  

 如果原則已設定成功，則方法會傳回 `S_OK` 。 如果超出 `ePolicy` [CorDebugNGenPolicy](cordebugngenpolicy-enumeration.md)所定義之列舉值的範圍，則方法會傳回 `E_INVALIDARG` ，而且方法呼叫不會有任何作用。 如果無法更新原生映射產生器 ( # A0) 的原則，則方法會傳回 `E_FAIL` 。  
  
 在 `ICorDebugProcess5::EnableNGenPolicy` 進程的存留期內，您隨時都可以呼叫方法。 原則適用于設定原則之後所載入的任何模組。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugProcess5 介面](icordebugprocess5-interface.md)
- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
