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
ms.openlocfilehash: 6cc9c2af62184c83857b82445941f6087a05c2c3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497167"
---
# <a name="icordebugfunction2getversionnumber-method"></a>ICorDebugFunction2::GetVersionNumber 方法
取得此函式的 編輯後繼續版本。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetVersionNumber (  
    [out] ULONG32   *pnVersion  
);  
```  
  
## <a name="parameters"></a>參數  
 `pnVersion`  
 [out]此 ICorDebugFunction2 物件所代表的函式的版本號碼的整數指標。  
  
## <a name="remarks"></a>備註  
 執行階段記錄的編輯已發生每個模組的偵錯工作階段的數目。 函式的版本號碼是其中一個超過編輯導入的函式的數目。 函式的原始版本是第 1 版。 每次遞增的數字的模組[ICorDebugModule2::ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)該模組上呼叫。 因此，如果第一個和第三個呼叫中已取代的函式的主體`ICorDebugModule2::ApplyChanges`，`GetVersionNumber`可能會傳回版本 1、 2 或 4 個該函式，但不是第 3 版。 （該函式會有版本 3）。  
  
 版本號碼分別追蹤每個模組。 因此，如果您在模組 1 和模組 2 上未執行四個編輯，您模組 1 上的下一個編輯會將版本號碼為 6 模組 1 中的所有已編輯函式。 如果相同編輯涉及模組 2，模組 2 中的函式會取得版本數字 2。  
  
 取得版本號碼`GetVersionNumber`方法可能是藉由取得低於[icordebugfunction:: Getcurrentversionnumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)。  
  
 [Icordebugcode:: Getversionnumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md)方法會執行相同的作業`ICorDebugFunction2::GetVersionNumber`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
