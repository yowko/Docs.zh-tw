---
title: ICorDebugModule3::CreateReaderForInMemorySymbols 方法
ms.date: 03/30/2017
api_name:
- ICorDebugModule3.CreateReaderForInMemorySymbols
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule3::CreateReaderForInMemorySymbols
helpviewer_keywords:
- CreateReaderForInMemorySymbols method, ICorDebugModule3 interface [.NET Framework debugging]
- ICorDebugModule3::CreateReaderForInMemorySymbols method [.NET Framework debugging]
ms.assetid: af317171-d66d-4114-89eb-063554c74940
topic_type:
- apiref
ms.openlocfilehash: 44f4c59f95c28f9982d67875584e2f9803c0ed3b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709566"
---
# <a name="icordebugmodule3createreaderforinmemorysymbols-method"></a>ICorDebugModule3::CreateReaderForInMemorySymbols 方法

建立動態模組的 debug 符號讀取器。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CreateReaderForInMemorySymbols (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **    ppObj  
```  
  
## <a name="parameters"></a>參數  

 riid  
 在要傳回的 COM 介面的 IID。 一般來說，這是 [ISymUnmanagedReader 介面](../diagnostics/isymunmanagedreader-interface.md)。  
  
 ppObj  
 擴展傳回之介面指標的指標。  
  
## <a name="return-value"></a>傳回值  

 S_OK  
 已成功建立讀取器。  
  
 CORDBG_E_MODULE_LOADED_FROM_DISK  
 模組不是記憶體中或動態模組。  
  
 CORDBG_E_SYMBOLS_NOT_AVAILABLE  
 應用程式尚未提供符號，或尚未提供符號。  
  
 E_FAIL (或其他 E_ 傳回碼)  
 無法建立讀取器。  
  
## <a name="remarks"></a>備註  

 這個方法也可以用來建立記憶體中 (非動態) 模組的符號讀取器物件，但只有在第一次使用符號之後， (由 [UpdateModuleSymbols 方法](icordebugmanagedcallback-updatemodulesymbols-method.md) 回呼) 表示。  
  
 這個方法會在每次呼叫時傳回新的讀取器實例， (例如 [CComPtrBase：： CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)) 。 因此，偵錯工具應該快取結果，而且只有當基礎資料可能已變更 (也就是在收到 [LoadClass 方法](icordebugmanagedcallback-loadclass-method.md) 回呼) 時，才要求新的實例。  
  
 動態模組在載入第一個類型之前沒有任何可用的符號 (如 [LoadClass 方法](icordebugmanagedcallback-loadclass-method.md) 回呼) 所示。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：** 4.5、4、3.5 SP1  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugRemoteTarget 介面](icordebugremotetarget-interface.md)
- [ICorDebug 介面](icordebug-interface.md)

- [偵錯介面](debugging-interfaces.md)
