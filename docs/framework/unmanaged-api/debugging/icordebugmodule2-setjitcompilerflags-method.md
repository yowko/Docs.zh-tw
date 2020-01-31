---
title: ICorDebugModule2::SetJITCompilerFlags 方法
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.SetJITCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::SetJITCompilerFlags
helpviewer_keywords:
- ICorDebugModule2::SetJITCompilerFlags method [.NET Framework debugging]
- SetJITCompilerFlags method [.NET Framework debugging]
ms.assetid: ea574c84-c622-4589-9a14-b55771af5e06
topic_type:
- apiref
ms.openlocfilehash: b28e457ea0b51d320581c0fbe36574698081ea36
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792966"
---
# <a name="icordebugmodule2setjitcompilerflags-method"></a>ICorDebugModule2::SetJITCompilerFlags 方法
設定可控制這個 ICorDebugModule2 之即時（JIT）編譯的旗標。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetJITCompilerFlags (  
    [in] DWORD dwFlags  
);  
```  
  
## <a name="parameters"></a>參數  
 `dwFlags`  
 在[CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md)列舉值的位元組合。  
  
## <a name="remarks"></a>備註  
 如果 `dwFlags` 值無效，`SetJITCompilerFlags` 方法將會失敗。  
  
 只能從這個模組的[ICorDebugManagedCallback：： LoadModule](icordebugmanagedcallback-loadmodule-method.md)回呼中呼叫 `SetJITCompilerFlags` 方法。 在傳遞 `ICorDebugManagedCallback::LoadModule` 回呼之後，嘗試呼叫它會失敗。  
  
 64位或 Win9x 平臺不支援 [編輯後繼續]。 因此，如果您在這兩個平臺的其中一個上呼叫 `SetJITCompilerFlags` 方法，並在 `dwFlags`中設定 CORDEBUG_JIT_ENABLE_ENC 旗標，`SetJITCompilerFlags` 方法和 [編輯後繼續] 特定的所有方法（例如[ICorDebugModule2：： ApplyChanges](icordebugmodule2-applychanges-method.md)）將會失敗。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
