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
ms.openlocfilehash: 497dda473e6510cfa31405b2066c63b1a70dd5e9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677319"
---
# <a name="icordebugstackwalknext-method"></a>ICorDebugStackWalk::Next 方法

將 [ICorDebugStackWalk](icordebugstackwalk-interface.md) 物件移至下一個畫面格。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="return-value"></a>傳回值  

 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|執行時間成功展開至下一個畫面格 (請參閱備註) 。|  
|E_FAIL|`ICorDebugStackWalk`物件無法前進。|  
|CORDBG_S_AT_END_OF_STACK|此回溯的結果已達到堆疊的結尾。|  
|CORDBG_E_PAST_END_OF_STACK|框架指標已在堆疊的結尾;因此，不能存取任何其他框架。|  
  
## <a name="exceptions"></a>例外  
  
## <a name="remarks"></a>備註  

 `Next`只有在執行時間可以回溯目前的框架時，此方法 `ICorDebugStackWalk` 才會將物件前移至呼叫框架。 否則，物件會前進到執行時間可以回溯的下一個畫面格。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugStackWalk 介面](icordebugstackwalk-interface.md)
- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
