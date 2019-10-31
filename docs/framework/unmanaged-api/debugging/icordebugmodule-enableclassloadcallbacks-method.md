---
title: ICorDebugModule::EnableClassLoadCallbacks 方法
ms.date: 03/30/2017
api_name:
- ICorDebugModule.EnableClassLoadCallbacks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::EnableClassLoadCallbacks
helpviewer_keywords:
- ICorDebugModule::EnableClassLoadCallbacks method [.NET Framework debugging]
- EnableClassLoadCallbacks method [.NET Framework debugging]
ms.assetid: 78dad5e4-8e2e-400f-bec3-92ff0205cd82
topic_type:
- apiref
ms.openlocfilehash: c18ed781d44c873b4cd1957bf0102a4ce0cccad4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139225"
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a>ICorDebugModule::EnableClassLoadCallbacks 方法
控制是否針對此模組呼叫[ICorDebugManagedCallback：： LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)和[ICorDebugManagedCallback：： UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)回呼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
## <a name="parameters"></a>參數  
 `bClassLoadCallbacks`  
 在將此值設定為 `true`，讓 common language runtime （CLR）在其相關聯的事件發生時，呼叫 `ICorDebugManagedCallback::LoadClass` 和 `ICorDebugManagedCallback::UnloadClass` 方法。  
  
 非動態模組的預設值為 `false`。 動態模組的值一律為 `true`，而且無法變更。  
  
## <a name="remarks"></a>備註  
 動態模組的 `ICorDebugManagedCallback::LoadClass` 和 `ICorDebugManagedCallback::UnloadClass` 回呼一律會啟用，且無法停用。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱
