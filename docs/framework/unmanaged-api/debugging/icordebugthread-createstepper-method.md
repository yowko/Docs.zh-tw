---
title: ICorDebugThread::CreateStepper 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread.CreateStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::CreateStepper
helpviewer_keywords:
- ICorDebugThread::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 4657443f-dd12-431b-a648-175c23f13c83
topic_type:
- apiref
ms.openlocfilehash: d1b058aef66ed32c2cadcc3cfd72320dd8eb7729
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133585"
---
# <a name="icordebugthreadcreatestepper-method"></a>ICorDebugThread::CreateStepper 方法
建立 ICorDebugStepper 物件，允許逐步執行此 ICorDebugThread 的現用框架。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper **ppStepper  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppStepper`  
 脫銷允許逐步執行這個執行緒之作用中框架的 `ICorDebugStepper` 物件位址的指標。  
  
## <a name="remarks"></a>備註  
 使用中的框架可能是非受控碼。  
  
 `ICorDebugStepper` 介面必須用來執行實際的逐步執行。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
