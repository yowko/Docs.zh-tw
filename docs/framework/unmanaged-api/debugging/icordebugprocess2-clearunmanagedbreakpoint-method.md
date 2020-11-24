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
ms.openlocfilehash: a713fd006f1e9ad8fe7109651c2cda5025da3566
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673939"
---
# <a name="icordebugprocess2clearunmanagedbreakpoint-method"></a>ICorDebugProcess2::ClearUnmanagedBreakpoint 方法

在指定的位址上移除先前設定的中斷點。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ClearUnmanagedBreakpoint (  
    [in] CORDB_ADDRESS   address  
);  
```  
  
## <a name="parameters"></a>參數  

 `address`  
 在 `CORDB_ADDRESS` 值，指定設定中斷點的位址。  
  
## <a name="remarks"></a>備註  

 先前呼叫 [ICorDebugProcess2：： SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md)之前已設定指定的中斷點。  
  
 `ClearUnmanagedBreakpoint`當正在執行的進程正在執行時，可以呼叫方法。  
  
 `ClearUnmanagedBreakpoint`如果偵錯工具是以僅限 managed 模式連接，或在指定的位址沒有中斷點存在，則此方法會傳回失敗碼。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
