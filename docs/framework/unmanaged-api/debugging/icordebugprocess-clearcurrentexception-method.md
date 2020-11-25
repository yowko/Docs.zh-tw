---
title: ICorDebugProcess::ClearCurrentException 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.ClearCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ClearCurrentException
helpviewer_keywords:
- ClearCurrentException method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::ClearCurrentException method [.NET Framework debugging]
ms.assetid: 9e02ee1a-e495-4578-bfb5-b946274bede7
topic_type:
- apiref
ms.openlocfilehash: 0d36390a905561b64b3ca6ca95722f82158450be
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695214"
---
# <a name="icordebugprocessclearcurrentexception-method"></a>ICorDebugProcess::ClearCurrentException 方法

清除指定執行緒上目前的非受控例外狀況。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ClearCurrentException([in] DWORD threadID);  
```  
  
## <a name="parameters"></a>參數  

 `threadID`  
 在將清除目前非受控例外狀況之執行緒的識別碼。  
  
## <a name="remarks"></a>備註  

 呼叫這個方法，然後再呼叫 [ICorDebugController：： Continue](icordebugcontroller-continue-method.md) （當執行緒已報告偵錯工具應該忽略的非受控例外狀況）。 這會將未處理的頻外 (IB) ，以及指定執行緒上的頻外 (OOB) 事件清除。 系統會自動清除所有 OOB 中斷點和單一步驟例外狀況。  
  
 使用 [ICorDebugThread2：： InterceptCurrentException](icordebugthread2-interceptcurrentexception-method.md) 攔截執行緒上目前的 managed 例外狀況。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
