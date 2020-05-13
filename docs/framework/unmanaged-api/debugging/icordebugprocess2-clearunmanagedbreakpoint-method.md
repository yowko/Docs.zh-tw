---
title: ICorDebugProcess2::ClearUnmanagedBreakpoint 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.ClearUnmanagedBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::ClearUnmanagedBreakpoint
helpviewer_keywords:
- ClearUnmanagedBreakpoint method [.NET Framework debugging]
- ICorDebugProcess2::ClearUnmanagedBreakpoint method [.NET Framework debugging]
ms.assetid: 12ed0fff-7f0e-4d7a-bb70-b3376371f36c
topic_type:
- apiref
ms.openlocfilehash: 2b228383c3b393fe43f60d39e59cca37af36233f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212486"
---
# <a name="icordebugprocess2clearunmanagedbreakpoint-method"></a>ICorDebugProcess2::ClearUnmanagedBreakpoint 方法
移除先前在指定位址上設定的中斷點。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ClearUnmanagedBreakpoint (  
    [in] CORDB_ADDRESS   address  
);  
```  
  
## <a name="parameters"></a>參數  
 `address`  
 在`CORDB_ADDRESS`值，指定設定中斷點的位址。  
  
## <a name="remarks"></a>備註  
 先前呼叫[ICorDebugProcess2：： SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md)之前已設定指定的中斷點。  
  
 `ClearUnmanagedBreakpoint`當正在進行調試的進程正在執行時，可以呼叫方法。  
  
 `ClearUnmanagedBreakpoint`如果偵錯工具是以僅限 managed 模式連接，或如果指定的位址沒有中斷點存在，則方法會傳回失敗代碼。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
