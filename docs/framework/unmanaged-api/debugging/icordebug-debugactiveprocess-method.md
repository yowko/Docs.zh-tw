---
title: ICorDebug::DebugActiveProcess 方法
ms.date: 03/30/2017
api_name:
- ICorDebug.DebugActiveProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::DebugActiveProcess
helpviewer_keywords:
- DebugActiveProcess method [.NET Framework debugging]
- ICorDebug::DebugActiveProcess method [.NET Framework debugging]
ms.assetid: fdab0ade-7f56-4fa2-b3ef-f7a1d2852bba
topic_type:
- apiref
ms.openlocfilehash: 5b988b110100cd159b8e262573df409847d635c6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134130"
---
# <a name="icordebugdebugactiveprocess-method"></a>ICorDebug::DebugActiveProcess 方法
將偵錯工具附加至現有的進程。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DebugActiveProcess (  
    [in]  DWORD               id,  
    [in]  BOOL                win32Attach,  
    [out] ICorDebugProcess    **ppProcess  
);  
```  
  
## <a name="parameters"></a>參數  
 `id`  
 在要附加偵錯工具之進程的識別碼。  
  
 `win32Attach`  
 在布林值，如果偵錯工具應該做為進程的 Win32 偵錯工具，並分派非受控回呼，則設定為 `true`：否則，`false`。  
  
 `ppProcess`  
 脫銷"ICorDebugProcess" 物件位址的指標，表示已附加偵錯工具的進程。  
  
## <a name="remarks"></a>備註  
 在 Win9x 和非 x86 平臺（例如，IA-64 型和以 AMD64 為基礎的平臺）上不支援 Interop 調試。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebug 介面](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
