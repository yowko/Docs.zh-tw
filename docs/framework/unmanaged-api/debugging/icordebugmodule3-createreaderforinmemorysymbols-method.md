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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 76f7b53f800bc8c5c23f49a0781287a38bf8c959
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmodule3createreaderforinmemorysymbols-method"></a>ICorDebugModule3::CreateReaderForInMemorySymbols 方法
建立動態模組的偵錯符號讀取器。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CreateReaderForInMemorySymbols (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **    ppObj  
```  
  
#### <a name="parameters"></a>參數  
 riid  
 [in]要傳回的 COM 介面的 IID。 一般而言，這是[ISymUnmanagedReader 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)。  
  
 ppObj  
 [out]傳回的介面指標的指標。  
  
## <a name="return-value"></a>傳回值  
 S_OK  
 已成功建立讀取器。  
  
 CORDBG_E_MODULE_LOADED_FROM_DISK  
 模組不是記憶體中或動態模組。  
  
 CORDBG_E_SYMBOLS_NOT_AVAILABLE  
 符號尚未提供應用程式或尚無法使用。  
  
 E_FAIL (或其他 E_ 傳回碼)  
 無法建立讀取器。  
  
## <a name="remarks"></a>備註  
 這個方法也可以用來建立記憶體中 （非動態） 模組的符號讀取器物件，但只有第一次符號之後 (由[UpdateModuleSymbols 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md)回呼)。  
  
 每次呼叫時，這個方法會傳回新的讀取器執行個體 (例如[CComPtrBase::CoCreateInstance](http://msdn.microsoft.com/library/c0965041-6cb6-40c5-b272-2b99f02668a6))。 因此，偵錯工具應該快取結果，並只在基礎資料可能已變更時，要求的新執行個體 (也就是當[LoadClass 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)接收回呼)。  
  
 動態模組並沒有提供任何符號之前已載入的第一個型別 (如所示[LoadClass 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)回呼)。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** 4.5、 4、 3.5 SP1  
  
## <a name="see-also"></a>另請參閱  
 [ICorDebugRemoteTarget 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 [ICorDebug 介面](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
