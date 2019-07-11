---
title: ICorDebugFunction2::GetJMCStatus 方法
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.GetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::GetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::GetJMCStatus method [.NET Framework debugging]
- GetJMCStatus method [.NET Framework debugging]
ms.assetid: 840a71ed-bf5a-4f5e-8ed6-762222b34493
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed2364c7c47aed1430a86aeee3daabf6b94cbf3b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754474"
---
# <a name="icordebugfunction2getjmcstatus-method"></a>ICorDebugFunction2::GetJMCStatus 方法
取得值，指出是否要將此 ICorDebugFunction2 物件所代表的函式標記為使用者程式碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetJMCStatus (  
    [out] BOOL   *pbIsJustMyCode  
);  
```  
  
## <a name="parameters"></a>參數  
 `pbIsJustMyCode`  
 [out]布林值的指標`true`，則此函式標示為使用者程式碼; 否則值就是`false`。  
  
## <a name="remarks"></a>備註  
 如果函式以表示這`ICorDebugFunction2`無法偵錯，`pbIsJustMyCode`一定會`false`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
