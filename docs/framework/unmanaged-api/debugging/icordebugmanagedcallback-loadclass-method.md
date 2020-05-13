---
title: ICorDebugManagedCallback::LoadClass 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadClass
helpviewer_keywords:
- ICorDebugManagedCallback::LoadClass method [.NET Framework debugging]
- LoadClass method [.NET Framework debugging]
ms.assetid: e58dac7b-85c3-41ca-b9aa-3a7fc9ae6680
topic_type:
- apiref
ms.openlocfilehash: 5d35ab4610ffa04d15dd2404fdf8010308bcb42a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212723"
---
# <a name="icordebugmanagedcallbackloadclass-method"></a>ICorDebugManagedCallback::LoadClass 方法
通知偵錯工具已載入類別。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT LoadClass (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugClass     *c  
);  
```  
  
## <a name="parameters"></a>參數  
 `pAppDomain`  
 在ICorDebugAppDomain 物件的指標，表示已載入類別的應用程式域。  
  
 `c`  
 在表示類別之 ICorDebugClass 物件的指標。  
  
## <a name="remarks"></a>備註  
 只有在已針對包含類別的模組啟用類別載入時，才會發生此回呼。 動態模組的類別載入一律為啟用狀態。  
  
 `LoadClass`回呼會提供適當的時間，將中斷點系結至動態模組中新產生的類別。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [UnloadClass 方法](icordebugmanagedcallback-unloadclass-method.md)
- [ICorDebugManagedCallback 介面](icordebugmanagedcallback-interface.md)
