---
title: ICorDebug::Terminate 方法
ms.date: 03/30/2017
api_name:
- ICorDebug.Terminate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::Terminate
helpviewer_keywords:
- Terminate method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::Terminate method [.NET Framework debugging]
ms.assetid: fffe5616-0896-4426-ab5e-21869b514883
topic_type:
- apiref
ms.openlocfilehash: 44bb98f54debb129f951cc388fea81ca0f17b20c
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895313"
---
# <a name="icordebugterminate-method"></a>ICorDebug::Terminate 方法
終止`ICorDebug`物件。  
  
> [!NOTE]
> `Terminate`必須等到針對所有正在進行調試的進程收到[ICorDebugManagedCallback：： ExitProcess](icordebugmanagedcallback-exitprocess-method.md)回呼之後，才能呼叫。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Terminate ();  
```  
  
## <a name="remarks"></a>備註  
 `Terminate`當不再需要物件時`ICorDebug` ，必須呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebug 介面](icordebug-interface.md)
