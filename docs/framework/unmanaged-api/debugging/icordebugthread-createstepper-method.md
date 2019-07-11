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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95a00e8646589e7897636c1698b7c2647cd233fd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771798"
---
# <a name="icordebugthreadcreatestepper-method"></a>ICorDebugThread::CreateStepper 方法
建立可讓您逐步完成每個使用中畫面格的這個 ICorDebugThread ICorDebugStepper 物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper **ppStepper  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppStepper`  
 [out]位址指標`ICorDebugStepper`物件，可讓您逐步執行此執行緒的使用中畫面格。  
  
## <a name="remarks"></a>備註  
 使用中畫面格可能未受管理的程式碼。  
  
 `ICorDebugStepper`介面必須用來執行實際的逐步執行。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
