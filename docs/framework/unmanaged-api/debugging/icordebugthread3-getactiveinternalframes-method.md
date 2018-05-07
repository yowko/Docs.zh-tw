---
title: ICorDebugThread3::GetActiveInternalFrames 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread3.GetActiveInternalFrames Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3::GetActiveInternalFrames
helpviewer_keywords:
- ICorDebugThread3::GetActiveInternalFrames method [.NET Framework debugging]
- GetActiveInternalFrames method [.NET Framework debugging]
ms.assetid: d69796b4-5b6d-457c-85f6-2cf42e8a8773
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2ac87de35478e5eabdc8cdc3568baf2086923e38
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugthread3getactiveinternalframes-method"></a>ICorDebugThread3::GetActiveInternalFrames 方法
傳回內部框架的陣列 ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)物件) 堆疊上。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetActiveInternalFrames  
      (  
      [in] ULONG32 cInternalFrames,  
      [out] ULONG32 *pcInternalFrames,  
      [in, out,size_is(cInternalFrames), length_is(*pcInternalFrames)]  
            ICorDebugInternalFrame2 * ppInternalFrames[]  
      );  
```  
  
#### <a name="parameters"></a>參數  
 `cInternalFrames`  
 [in]中必須要有內部的畫面格數目`ppInternalFrames`。  
  
 `pcInternalFrames`  
 [out]指標`ULONG32`，其中包含內部堆疊上框架的數目。  
  
 `ppInternalFrames`  
 [in、 out]陣列內部堆疊上框架的位址指標。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT 以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|[ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)物件已建立成功。|  
|E_INVALIDARG|`cInternalFrames` 不是零和`ppInternalFrames`是`null`，或`pcInternalFrames`是`null`。|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|`ppInternalFrames` 小於內部框架的計數。|  
  
## <a name="exceptions"></a>例外狀況  
  
## <a name="remarks"></a>備註  
 內部框架是一種資料結構來儲存暫存資料推送到堆疊上由執行階段。  
  
 當您第一次呼叫`GetActiveInternalFrames`，您應該設定`cInternalFrames`參數為 0 （零），而`ppInternalFrames`參數為 null。 當`GetActiveInternalFrames`會先傳回，`pcInternalFrames`包含內部堆疊上框架的計數。  
  
 `GetActiveInternalFrames` 應該接著呼叫第二次。 您應該傳遞正確的計數 (`pcInternalFrames`) 中`cInternalFrames`參數，並指定適當大小的陣列中的指標`ppInternalFrames`。  
  
 使用[icordebugstackwalk:: Getframe](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md)方法以傳回實際堆疊框架。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
