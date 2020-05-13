---
title: ICorDebugFunction2::GetVersionNumber 方法
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.GetVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::GetVersionNumber
helpviewer_keywords:
- ICorDebugFunction2::GetVersionNumber method [.NET Framework debugging]
- GetVersionNumber method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: e3a1ce48-9bb9-4ed6-a5fe-5e1819a6333f
topic_type:
- apiref
ms.openlocfilehash: f47263872b1baf1038a5fa9816c96e3e2569e705
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213214"
---
# <a name="icordebugfunction2getversionnumber-method"></a>ICorDebugFunction2::GetVersionNumber 方法
取得此函式的編輯後繼續版本。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetVersionNumber (  
    [out] ULONG32   *pnVersion  
);  
```  
  
## <a name="parameters"></a>參數  
 `pnVersion`  
 脫銷整數的指標，這是這個 ICorDebugFunction2 物件所表示之函式的版本號碼。  
  
## <a name="remarks"></a>備註  
 執行時間會持續追蹤在「偵錯工具」會話期間，每個模組所進行的編輯次數。 函式的版本號碼比引進函數的編輯次數還要多。 函式的原始版本為第1版。 每次在該模組上呼叫[ICorDebugModule2：： ApplyChanges](icordebugmodule2-applychanges-method.md)時，模組的數目就會遞增。 因此，如果在的第一個和第三個呼叫中取代函式的主體 `ICorDebugModule2::ApplyChanges` ， `GetVersionNumber` 可能會針對該函式傳回版本1、2或4，但不會傳回第3版。 （該函數不會有第3版）。  
  
 針對每個模組分別追蹤版本號碼。 因此，如果您在模組1上執行四項編輯，而在模組2上執行了 [無]，則下一次編輯模組1將會為模組1中所有編輯的函式指派6的版本號碼。 如果相同的編輯觸及模組2，則模組2中的函式會取得版本號碼2。  
  
 方法所取得的版本號碼 `GetVersionNumber` 可能會低於[ICorDebugFunction：： GetCurrentVersionNumber](icordebugfunction-getcurrentversionnumber-method.md)所取得。  
  
 [ICorDebugCode：： GetVersionNumber](icordebugcode-getversionnumber-method.md)方法會執行與相同的作業 `ICorDebugFunction2::GetVersionNumber` 。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
