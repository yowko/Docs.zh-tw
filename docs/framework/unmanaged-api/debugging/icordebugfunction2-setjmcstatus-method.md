---
title: ICorDebugFunction2::SetJMCStatus 方法
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::SetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 22c27b01-2869-4214-b840-5921f7c874fc
topic_type:
- apiref
ms.openlocfilehash: 758364b2d63343e464b727d5a1c1817533a6acea
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137787"
---
# <a name="icordebugfunction2setjmcstatus-method"></a>ICorDebugFunction2::SetJMCStatus 方法
標示此 ICorDebugFunction2 所代表的函式，以 Just My Code 逐步執行。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a>參數  
 `bIsJustMyCode`  
 在設定為 `true` 以將函式標記為使用者程式碼;否則，請將設定為 `false`。  
  
## <a name="return-values"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|`S_OK`|已成功標記函數。|  
|`CORDBG_E_FUNCTION_NOT_DEBUGGABLE`|無法將函式標記為使用者程式碼，因為它無法進行調試。|  
  
## <a name="remarks"></a>備註  
 Just My Code 的分檔器會略過非使用者程式碼。 使用者程式碼必須是可偵錯工具代碼的子集。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
