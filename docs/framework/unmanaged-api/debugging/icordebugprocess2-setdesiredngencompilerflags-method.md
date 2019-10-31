---
title: ICorDebugProcess2::SetDesiredNGENCompilerFlags 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.SetDesiredNGENCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::SetDesiredNGENCompilerFlags
helpviewer_keywords:
- ICorDebugProcess2::SetDesiredNGENCompilerFlags method [.NET Framework debugging]
- SetDesiredNGENCompilerFlags method [.NET Framework debugging]
ms.assetid: 98320175-7c5e-4dbb-8683-86fa82e2641f
topic_type:
- apiref
ms.openlocfilehash: 9313fc58dec8099f42dbff07685ca14791fa324f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137168"
---
# <a name="icordebugprocess2setdesiredngencompilerflags-method"></a>ICorDebugProcess2::SetDesiredNGENCompilerFlags 方法
設定必須內嵌在先行編譯影像中的旗標，執行時間才會將該影像載入目前的進程中。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetDesiredNGENCompilerFlags (  
    [in] DWORD    pdwFlags  
);  
```  
  
## <a name="parameters"></a>參數  
 `pdwFlags`  
 在[CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)列舉的值，指定用來選取正確預先編譯影像的編譯器旗標。  
  
## <a name="remarks"></a>備註  
 `SetDesiredNGENCompilerFlags` 方法會指定必須內嵌在先行編譯影像中的旗標，讓執行時間將該影像載入這個進程中。 這個方法所設定的旗標只能用來選取正確的先行編譯映射。 如果沒有這類影像，執行時間將會改為載入 Microsoft 中繼語言（MSIL）影像和即時（JIT）編譯器。 在這種情況下，偵錯工具仍然必須使用[ICorDebugModule2：： SetJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md)方法來設定 JIT 編譯所需的旗標。  
  
 如果載入影像，但必須針對該影像進行某些 JIT 編譯（如果影像包含泛型，則會是這種情況），則 `SetDesiredNGENCompilerFlags` 方法所指定的編譯器旗標將會套用至額外的 JIT 編譯。  
  
 在[ICorDebugManagedCallback：： CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md)回呼期間，必須呼叫 `SetDesiredNGENCompilerFlags` 方法。 之後嘗試呼叫 `SetDesiredNGENCompilerFlags` 方法將會失敗。 此外，也會嘗試設定未在 `CorDebugJITCompilerFlags` 列舉中定義或不合法的旗標，而不是指定的處理常式將會失敗。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebug 介面](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [ICorDebugManagedCallback 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
