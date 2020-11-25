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
ms.openlocfilehash: 11ff430c426c93f1c2a5c0582495e089a33995fa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709800"
---
# <a name="icordebugmodule2setjitcompilerflags-method"></a>ICorDebugModule2::SetJITCompilerFlags 方法

設定旗標，這些旗標會控制此 ICorDebugModule2 的即時 (JIT) 編譯。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetJITCompilerFlags (  
    [in] DWORD dwFlags  
);  
```  
  
## <a name="parameters"></a>參數  

 `dwFlags`  
 在 [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) 列舉值的位元組合。  
  
## <a name="remarks"></a>備註  

 如果 `dwFlags` 值無效， `SetJITCompilerFlags` 方法將會失敗。  
  
 您 `SetJITCompilerFlags` 只能從這個模組的 [ICorDebugManagedCallback：： LoadModule](icordebugmanagedcallback-loadmodule-method.md) 回呼中呼叫方法。 在回呼傳遞之後嘗試呼叫它 `ICorDebugManagedCallback::LoadModule` 將會失敗。  
  
 64位或 Win9x 平臺上不支援 [編輯後繼續]。 因此，如果您在 `SetJITCompilerFlags` 這兩個平臺的任一個上呼叫方法，並在中設定 CORDEBUG_JIT_ENABLE_ENC 旗標 `dwFlags` ，則此方法和 [編輯後繼續] 的特定方法（ `SetJITCompilerFlags` 例如 [ICorDebugModule2：： ApplyChanges](icordebugmodule2-applychanges-method.md)）將會失敗。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
