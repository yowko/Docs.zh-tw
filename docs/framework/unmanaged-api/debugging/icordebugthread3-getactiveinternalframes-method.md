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
ms.openlocfilehash: 680af5afa3ebef5bcaf9e34580e421dcc8093aaf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178458"
---
# <a name="icordebugthread3getactiveinternalframes-method"></a>ICorDebugThread3::GetActiveInternalFrames 方法
返回堆疊上的內部幀陣列[（ICorDebug內部Frame2](icordebuginternalframe2-interface.md)物件）。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetActiveInternalFrames  
      (  
      [in] ULONG32 cInternalFrames,  
      [out] ULONG32 *pcInternalFrames,  
      [in, out,size_is(cInternalFrames), length_is(*pcInternalFrames)]  
            ICorDebugInternalFrame2 * ppInternalFrames[]  
      );  
```  
  
## <a name="parameters"></a>參數  
 `cInternalFrames`  
 [在]中預期的內部幀數`ppInternalFrames`。  
  
 `pcInternalFrames`  
 [出]指向`ULONG32`包含堆疊上內部幀數的 指標。  
  
 `ppInternalFrames`  
 [進出]指向堆疊上內部幀陣列位址的指標。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功創建[ICorDebug 內部Frame2](icordebuginternalframe2-interface.md)物件。|  
|E_INVALIDARG|`cInternalFrames``ppInternalFrames`不是零，`null`是 ，`pcInternalFrames`或`null`是 。|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|`ppInternalFrames`小於內部幀的計數。|  
  
## <a name="exceptions"></a>例外狀況  
  
## <a name="remarks"></a>備註  
 內部幀是運行時推送到堆疊以存儲臨時資料的資料結構。  
  
 首次調用`GetActiveInternalFrames`時，應將`cInternalFrames`參數設置為 0（零），並將`ppInternalFrames`參數設置為 null。 首次`GetActiveInternalFrames`返回時，`pcInternalFrames`包含堆疊上內部幀的計數。  
  
 `GetActiveInternalFrames`然後，應調用第二次。 應在`pcInternalFrames``cInternalFrames`參數中傳遞正確的計數 （ ），並在 中指定指向適當大小的陣列的`ppInternalFrames`指標。  
  
 使用[ICorDebugStackWalk：getFrame](icordebugthread3-getactiveinternalframes-method.md)方法返回實際堆疊幀。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
