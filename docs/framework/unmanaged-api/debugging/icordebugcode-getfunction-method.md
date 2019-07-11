---
title: ICorDebugCode::GetFunction 方法
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetFunction
helpviewer_keywords:
- GetFunction method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetFunction method [.NET Framework debugging]
ms.assetid: c568b737-fdb2-4816-accd-051f5ab760f1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 10ab92c660353bea85bbd0918a25f716898ef837
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747531"
---
# <a name="icordebugcodegetfunction-method"></a>ICorDebugCode::GetFunction 方法
取得與此 「 ICorDebugCode"相關聯 「 ICorDebugFunction"。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetFunction (  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppFunction`  
 [out]函式的位址指標。  
  
## <a name="remarks"></a>備註  
 `ICorDebugCode` 和`ICorDebugFunction`維護一對一的關聯性。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
