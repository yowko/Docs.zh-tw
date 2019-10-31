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
ms.openlocfilehash: 0c622e0eba27f501446d2b7d9d264ee0834e869c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133623"
---
# <a name="icordebugthreadcreateeval-method"></a>ICorDebugThread::CreateEval 方法
建立 ICorDebugEval 物件，它會收集並公開此 ICorDebugThread 的功能。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CreateEval (  
    [out] ICorDebugEval   **ppEval  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppEval`  
 脫銷收集並公開這個執行緒之功能的 `ICorDebugEval` 物件位址的指標。  
  
## <a name="remarks"></a>備註  
 評估物件會先線上程上推送新的鏈，再進行其計算。 這會中斷目前正線上程上執行的計算，直到評估完成為止。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
