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
ms.openlocfilehash: 40b944f6a1204bfe506ed64408be30f68adf3170
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675252"
---
# <a name="icordebugprocess2setdesiredngencompilerflags-method"></a>ICorDebugProcess2::SetDesiredNGENCompilerFlags 方法

設定必須內嵌在先行編譯映射中的旗標，以便執行時間將該影像載入至目前的進程。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetDesiredNGENCompilerFlags (  
    [in] DWORD    pdwFlags  
);  
```  
  
## <a name="parameters"></a>參數  

 `pdwFlags`  
 在 [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) 列舉的值，指定用來選取正確預先編譯影像的編譯器旗標。  
  
## <a name="remarks"></a>備註  

 `SetDesiredNGENCompilerFlags`方法會指定必須內嵌在先行編譯映射中的旗標，以便執行時間將該影像載入至此進程。 這個方法所設定的旗標只會用來選取正確的預先編譯映射。 如果沒有這類影像，則執行時間會改為載入 Microsoft 中繼語言 (MSIL) 映射以及即時 (JIT) 編譯器。 在這種情況下，偵錯工具仍然必須使用 [ICorDebugModule2：： SetJITCompilerFlags](icordebugmodule2-setjitcompilerflags-method.md) 方法來設定 JIT 編譯所需的旗標。  
  
 如果載入影像，但必須針對該映射進行某些 JIT 編譯 (如果映射包含泛型) ，則方法所指定的編譯器旗標 `SetDesiredNGENCompilerFlags` 將會套用到額外的 JIT 編譯。  
  
 您 `SetDesiredNGENCompilerFlags` 必須在 [ICorDebugManagedCallback：： CreateProcess](icordebugmanagedcallback-createprocess-method.md) 回呼中呼叫方法。 之後嘗試呼叫 `SetDesiredNGENCompilerFlags` 方法將會失敗。 此外，嘗試設定列舉中未定義 `CorDebugJITCompilerFlags` 或對指定進程而言不合法的旗標將會失敗。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebug 介面](icordebug-interface.md)
- [ICorDebugManagedCallback 介面](icordebugmanagedcallback-interface.md)
