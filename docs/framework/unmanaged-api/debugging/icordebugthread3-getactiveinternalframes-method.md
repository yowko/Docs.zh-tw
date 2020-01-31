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
ms.openlocfilehash: 25cd3e05bc80dd39d2ca558bb4dd5fb77d255f5a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791402"
---
# <a name="icordebugthread3getactiveinternalframes-method"></a>ICorDebugThread3::GetActiveInternalFrames 方法
傳回堆疊上的內部框架（[ICorDebugInternalFrame2](icordebuginternalframe2-interface.md)物件）陣列。  
  
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
 在`ppInternalFrames`中預期的內部框架數目。  
  
 `pcInternalFrames`  
 脫銷`ULONG32` 的指標，其中包含堆疊上的內部框架數目。  
  
 `ppInternalFrames`  
 [in、out]堆疊上內部框架陣列位址的指標。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功建立[ICorDebugInternalFrame2](icordebuginternalframe2-interface.md)物件。|  
|E_INVALIDARG|`cInternalFrames` 不是零，而且 `ppInternalFrames` `null`，或 `pcInternalFrames` 是 `null`。|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|`ppInternalFrames` 小於內部框架的計數。|  
  
## <a name="exceptions"></a>例外狀況  
  
## <a name="remarks"></a>備註  
 內部框架是執行時間推送至堆疊的資料結構，用來儲存暫存資料。  
  
 當您第一次呼叫 `GetActiveInternalFrames`時，您應該將 `cInternalFrames` 參數設定為0（零），並將 `ppInternalFrames` 參數設為 null。 當 `GetActiveInternalFrames` 第一次傳回時，`pcInternalFrames` 包含堆疊上的內部框架計數。  
  
 接著，應該再次呼叫 `GetActiveInternalFrames`。 您應該在 `cInternalFrames` 參數中傳遞適當的計數（`pcInternalFrames`），並在 `ppInternalFrames`中指定適當大小陣列的指標。  
  
 請使用[ICorDebugStackWalk：： GetFrame](icordebugthread3-getactiveinternalframes-method.md)方法來傳回實際的堆疊框架。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
