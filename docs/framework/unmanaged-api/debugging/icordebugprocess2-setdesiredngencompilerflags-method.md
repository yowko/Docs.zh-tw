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
ms.openlocfilehash: e061c3f3dc95e63339d6fd5f82b3cb4d38a4b6c6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948820"
---
# <a name="icordebugprocess2setdesiredngencompilerflags-method"></a>ICorDebugProcess2::SetDesiredNGENCompilerFlags 方法
設定必須內嵌在先行編譯的映像，以便將該映像載入目前的程序的執行階段旗標。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT SetDesiredNGENCompilerFlags (  
    [in] DWORD    pdwFlags  
);  
```  
  
## <a name="parameters"></a>參數  
 `pdwFlags`  
 [in]值為[CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)列舉，指定的編譯器旗標用來選取正確的先行編譯映像。  
  
## <a name="remarks"></a>備註  
 `SetDesiredNGENCompilerFlags`方法會指定必須內嵌在先行編譯的映像中，以便在執行階段會載入此程序的該映像的旗標。 這個方法所設定的旗標是只能用來選取正確的先行編譯映像。 如果沒有這類映像存在時，執行階段將 Microsoft intermediate language (MSIL) 映像，而且在 just-in-time (JIT) 編譯器改為載入。 在此情況下，仍然必須使用偵錯工具[ICorDebugModule2::SetJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md)方法，以進行 JIT 編譯，視需要設定之旗標。  
  
 如果已載入的映像，但一些 JIT 編譯必須進行該映像 （這會是大小寫，如果映像包含泛型），所指定的編譯器旗標`SetDesiredNGENCompilerFlags`方法會套用至額外的 JIT 編譯。  
  
 `SetDesiredNGENCompilerFlags`方法必須呼叫期間[icordebugmanagedcallback:: Createprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md)回呼。 嘗試呼叫`SetDesiredNGENCompilerFlags`方法之後將會失敗。 嘗試設定不的旗標而且，定義於`CorDebugJITCompilerFlags`列舉型別或不合法的特定處理序將會失敗。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebug 介面](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [ICorDebugManagedCallback 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
