---
title: ICorDebugStackWalk::Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.Next Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::Next
helpviewer_keywords:
- ICorDebugStackWalk::Next method [.NET Framework debugging]
- Next method, ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 189c36be-028c-4fba-a002-5edfb8fcd07f
topic_type:
- apiref
ms.openlocfilehash: b76d17337408653d130ee0cb8594e759bdade37c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791873"
---
# <a name="icordebugstackwalknext-method"></a>ICorDebugStackWalk::Next 方法
將[ICorDebugStackWalk](icordebugstackwalk-interface.md)物件移至下一個畫面格。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|執行時間已成功地向下一個畫面格展開（請參閱備註）。|  
|E_FAIL|無法將 `ICorDebugStackWalk` 物件 advanced。|  
|CORDBG_S_AT_END_OF_STACK|因為這個回溯的結果，所以已達到堆疊的結尾。|  
|CORDBG_E_PAST_END_OF_STACK|框架指標已在堆疊的結尾;因此，不能存取任何其他框架。|  
  
## <a name="exceptions"></a>例外狀況  
  
## <a name="remarks"></a>備註  
 只有當執行時間可以回溯目前的框架時，`Next` 方法才會將 `ICorDebugStackWalk` 物件前移至呼叫的框架。 否則，物件會前進到執行時間可以回溯的下一個框架。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugStackWalk 介面](icordebugstackwalk-interface.md)
- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
