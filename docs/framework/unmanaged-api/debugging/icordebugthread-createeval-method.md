---
title: ICorDebugThread::CreateEval 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread.CreateEval
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::CreateEval
helpviewer_keywords:
- CreateEval method [.NET Framework debugging]
- ICorDebugThread::CreateEval method [.NET Framework debugging]
ms.assetid: 36605067-33d3-4579-9c72-fb0e551ab0f1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 41bd4c0bb4e84b6d6f267e24808baafa57f71882
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771115"
---
# <a name="icordebugthreadcreateeval-method"></a>ICorDebugThread::CreateEval 方法
建立 ICorDebugEval 物件會收集及公開此 ICorDebugThread 的功能。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CreateEval (  
    [out] ICorDebugEval   **ppEval  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppEval`  
 [out]位址指標`ICorDebugEval`會收集並公開的功能，此執行緒的物件。  
  
## <a name="remarks"></a>備註  
 評估物件會將推送新鏈結的執行緒上才能執行其運算。 這會中斷目前正在執行的執行緒上評估完成之前的計算。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
