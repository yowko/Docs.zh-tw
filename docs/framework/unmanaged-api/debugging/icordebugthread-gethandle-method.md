---
title: ICorDebugThread::GetHandle 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetHandle method [.NET Framework debugging]
ms.assetid: 172ef8c4-2ead-4cfc-bd2e-dee4fb7191cd
topic_type:
- apiref
ms.openlocfilehash: 33219d9a67379244e23da49c13617a4c4a2fa66d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133458"
---
# <a name="icordebugthreadgethandle-method"></a>ICorDebugThread::GetHandle 方法
取得此 ICorDebugThread 之使用中部分的目前控制碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetHandle (  
    [out] HTHREAD *phThreadHandle  
);  
```  
  
## <a name="parameters"></a>參數  
 `phThreadHandle`  
 脫銷HTHREAD 的指標，這是這個執行緒之作用中部分的控制碼。  
  
## <a name="remarks"></a>備註  
 控制碼可能會在進程執行時變更，而且可能會因為執行緒的不同部分而有所不同。  
  
 這個控制碼是由偵錯工具 API 所擁有。 偵錯工具在使用它之前，應該先複製它。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
