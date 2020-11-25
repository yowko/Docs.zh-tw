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
ms.openlocfilehash: 2ca3bf94298b45e404c930ffe52e101085ee482d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726206"
---
# <a name="icordebugthread3getactiveinternalframes-method"></a>ICorDebugThread3::GetActiveInternalFrames 方法

傳回內部框架的陣列， (堆疊上) 的 [ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) 物件。  
  
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
 在預期的內部框架數目 `ppInternalFrames` 。  
  
 `pcInternalFrames`  
 擴展的指標 `ULONG32` ，其中包含堆疊上的內部框架數目。  
  
 `ppInternalFrames`  
 [in，out]堆疊上內部框架陣列的位址指標。  
  
## <a name="return-value"></a>傳回值  

 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功建立 [ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) 物件。|  
|E_INVALIDARG|`cInternalFrames` 不是零，而且 `ppInternalFrames` 是 `null` ， `pcInternalFrames` 或是 `null` 。|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|`ppInternalFrames` 小於內部框架的計數。|  
  
## <a name="exceptions"></a>例外  
  
## <a name="remarks"></a>備註  

 內部畫面是由執行時間推送至堆疊的資料結構，用來儲存暫存資料。  
  
 當您第一次呼叫時 `GetActiveInternalFrames` ，您應該將 `cInternalFrames` 參數設定為 0 (零) ，並將參數設定為 `ppInternalFrames` null。 `GetActiveInternalFrames`第一次傳回時， `pcInternalFrames` 包含堆疊上的內部框架計數。  
  
 `GetActiveInternalFrames` 然後再呼叫第二次。 您應該在參數中傳遞適當的計數 (`pcInternalFrames`) `cInternalFrames` ，並在中指定適當大小的陣列指標 `ppInternalFrames` 。  
  
 使用 [ICorDebugStackWalk：： GetFrame](icordebugthread3-getactiveinternalframes-method.md) 方法來傳回實際的堆疊框架。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
