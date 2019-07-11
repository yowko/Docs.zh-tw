---
title: ICorDebugCode::GetVersionNumber 方法
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetVersionNumber
helpviewer_keywords:
- GetVersionNumber method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetVersionNumber method [.NET Framework debugging]
ms.assetid: c8e02518-679f-4e9f-8a28-ba4a89a3876f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 155a8d5465e0fb19c55c9d11b67c6031c2b2c4a3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747515"
---
# <a name="icordebugcodegetversionnumber-method"></a>ICorDebugCode::GetVersionNumber 方法
取得識別此 「 ICorDebugCode"表示的程式碼的版本以一為基的號碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetVersionNumber (  
    [out] ULONG32    *nVersion  
);  
```  
  
## <a name="parameters"></a>參數  
 `nVersion`  
 [out]版本號碼，程式碼的指標。  
  
## <a name="remarks"></a>備註  
 版本號碼會遞增每個執行程式碼編輯後繼續 (EnC) 作業的時間。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
