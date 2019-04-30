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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0aabff090634f1ecdeec5636336ad1fb77b8b81c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988919"
---
# <a name="icordebugeval2rudeabort-method"></a>ICorDebugEval2::RudeAbort 方法
中止計算這個`ICorDebugEval2`目前正在執行。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT RudeAbort ();  
```  
  
## <a name="remarks"></a>備註  
 `RudeAbort` 不會釋放評估工具會保留任何鎖定，因此在不安全的狀態不會留下偵錯工作階段。 呼叫這個方法時應謹慎小心。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
