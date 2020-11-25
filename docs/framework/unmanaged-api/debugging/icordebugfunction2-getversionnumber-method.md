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
ms.openlocfilehash: 88fb205235cfaf3566fbd74b05a4e9833058f4a0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696091"
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
 擴展整數的指標，此為這個 ICorDebugFunction2 物件所表示之函式的版本號碼。  
  
## <a name="remarks"></a>備註  

 執行時間會持續追蹤在 debug 會話期間對每個模組所進行的編輯次數。 函式的版本號碼比引入函式的編輯次數還要多。 函式的原始版本為第1版。 每次在該模組上呼叫 [ICorDebugModule2：： ApplyChanges](icordebugmodule2-applychanges-method.md) 時，模組的數目就會遞增。 因此，如果在第一次和第三次呼叫中取代函式主體，可能會傳回該函式的第 `ICorDebugModule2::ApplyChanges` `GetVersionNumber` 1 版、第2版或第4版，但不是第3版。  (該函式不會有第3版。 )   
  
 版本號碼會針對每個模組分開追蹤。 因此，如果您在模組1上執行四個編輯，而在模組2上執行 [無]，則在模組1上的下一次編輯會將版本號碼6指派給模組1中所有編輯過的函式。 如果相同的編輯觸控模組2，模組2中的函式會取得版本號碼2。  
  
 方法所取得的版本號碼 `GetVersionNumber` 可能會低於 [ICorDebugFunction：： GetCurrentVersionNumber](icordebugfunction-getcurrentversionnumber-method.md)所取得的版本號碼。  
  
 [ICorDebugCode：： GetVersionNumber](icordebugcode-getversionnumber-method.md)方法會執行與相同的作業 `ICorDebugFunction2::GetVersionNumber` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
