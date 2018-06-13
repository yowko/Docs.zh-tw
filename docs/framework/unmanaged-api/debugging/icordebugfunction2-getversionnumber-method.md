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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fdd2151c4886959647de4f9e27a20a93ffc07429
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420049"
---
# <a name="icordebugfunction2getversionnumber-method"></a>ICorDebugFunction2::GetVersionNumber 方法
取得此函式的編輯後繼續版本。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetVersionNumber (  
    [out] ULONG32   *pnVersion  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pnVersion`  
 [out]此 ICorDebugFunction2 物件所代表的函式的版本號碼的整數指標。  
  
## <a name="remarks"></a>備註  
 執行階段記錄的數目已發生每個模組的偵錯工作階段期間的編輯。 函式的版本號碼是其中一個超過編輯導入函式的數目。 函式的原始版本為第 1 版。 數字遞增模組，每次[icordebugmodule2:: Applychanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)該模組上呼叫。 因此，如果第一個和第三個呼叫中被取代的函式主體`ICorDebugModule2::ApplyChanges`，`GetVersionNumber`可能會傳回版本 1、 2 或 4，該函式，但不是第 3 版。 （該函式會有版本 3）。  
  
 版本號碼是個別追蹤每個模組。 因此，如果您對模組 1 和無模組 2 上執行四個的編輯，您的下一個編輯模組 1 上指派版本號碼為 6 模組 1 中編輯過的函式。 如果相同編輯涉及模組 2，模組 2 中的函式會為 2 的版本號碼。  
  
 取得版本號碼`GetVersionNumber`方法可能會低於取得[icordebugfunction:: Getcurrentversionnumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)。  
  
 [Icordebugcode:: Getversionnumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md)方法會執行相同操作，因為`ICorDebugFunction2::GetVersionNumber`。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
