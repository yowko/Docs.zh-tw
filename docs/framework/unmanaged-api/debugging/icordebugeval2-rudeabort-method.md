---
title: ICorDebugEval2::RudeAbort 方法
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.RudeAbort
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::RudeAbort
helpviewer_keywords:
- ICorDebugEval2::RudeAbort method [.NET Framework debugging]
- RudeAbort method, ICorDebugEval2 interface [.NET Framework debugging]
ms.assetid: 02468edf-d32b-4cb3-aaa8-3dd2abfc8b25
topic_type:
- apiref
ms.openlocfilehash: 478772925dfb7ca7389b5267433f9b06ace3d5a3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729612"
---
# <a name="icordebugeval2rudeabort-method"></a>ICorDebugEval2::RudeAbort 方法

中止目前正在執行的計算 `ICorDebugEval2` 。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT RudeAbort ();  
```  
  
## <a name="remarks"></a>備註  

 `RudeAbort` 不會釋放評估工具所持有的任何鎖定，因此它會讓偵錯工具保持不安全的狀態。 請特別小心呼叫這個方法。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
