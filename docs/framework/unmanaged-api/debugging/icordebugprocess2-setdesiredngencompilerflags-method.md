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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 94ba2b0cf7d88104eaadd434732edf3c1d4060e2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugprocess2setdesiredngencompilerflags-method"></a>ICorDebugProcess2::SetDesiredNGENCompilerFlags 方法
設定必須先行編譯的映像，為了讓執行階段將該映像載入目前的處理序中內嵌的旗標。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT SetDesiredNGENCompilerFlags (  
    [in] DWORD    pdwFlags  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pdwFlags`  
 [in]值為[CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)列舉，指定的編譯器旗標用來選取正確的先行編譯映像。  
  
## <a name="remarks"></a>備註  
 `SetDesiredNGENCompilerFlags`方法會指定必須內嵌在先行編譯的映像中，以便在執行階段將該映像載入此處理程序的旗標。 這個方法所設定的旗標是僅用來選取正確的先行編譯映像。 如果沒有這類映像存在時，執行階段將 Microsoft 中繼語言 (MSIL) 映像，在 just-in-time (JIT) 編譯器改為載入。 在此情況下，仍然必須使用偵錯工具[icordebugmodule2:: Setjitcompilerflags](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md)方法，以 JIT 編譯，視需要設定之旗標。  
  
 如果載入影像，但某些 JIT 編譯必須進行該映像 （這會是大小寫，如果映像包含泛型），所指定的編譯器旗標`SetDesiredNGENCompilerFlags`方法會套用到額外的 JIT 編譯。  
  
 `SetDesiredNGENCompilerFlags`方法必須在期間呼叫[icordebugmanagedcallback:: Createprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md)回呼。 嘗試呼叫`SetDesiredNGENCompilerFlags`方法之後將會失敗。 此外，嘗試設定旗標，無法定義`CorDebugJITCompilerFlags`列舉型別或不合法的特定處理序將會失敗。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorDebug 介面](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [ICorDebugManagedCallback 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
