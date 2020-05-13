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
ms.openlocfilehash: 953b7c1cb5e471072776fe03e53a46d3ff19c0ac
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379857"
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
 在中預期的內部框架數目 `ppInternalFrames` 。  
  
 `pcInternalFrames`  
 脫銷的指標 `ULONG32` ，其中包含堆疊上的內部框架數目。  
  
 `ppInternalFrames`  
 [in、out]堆疊上內部框架陣列位址的指標。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功建立[ICorDebugInternalFrame2](icordebuginternalframe2-interface.md)物件。|  
|E_INVALIDARG|`cInternalFrames`不是零，且 `ppInternalFrames` 為 `null` ，或 `pcInternalFrames` 為 `null` 。|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|`ppInternalFrames`小於內部框架的計數。|  
  
## <a name="exceptions"></a>例外狀況  
  
## <a name="remarks"></a>備註  
 內部框架是執行時間推送至堆疊的資料結構，用來儲存暫存資料。  
  
 當您第一次呼叫時 `GetActiveInternalFrames` ，您應該將 `cInternalFrames` 參數設定為0（零），並將 `ppInternalFrames` 參數設為 null。 當 `GetActiveInternalFrames` 第一次傳回時，會 `pcInternalFrames` 包含堆疊上的內部框架計數。  
  
 `GetActiveInternalFrames`然後，第二次呼叫。 您應該在參數中傳遞適當的 count （ `pcInternalFrames` ） `cInternalFrames` ，並在中指定適當大小之陣列的指標 `ppInternalFrames` 。  
  
 請使用[ICorDebugStackWalk：： GetFrame](icordebugthread3-getactiveinternalframes-method.md)方法來傳回實際的堆疊框架。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
