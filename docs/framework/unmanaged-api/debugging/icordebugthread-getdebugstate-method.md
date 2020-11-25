---
title: ICorDebugThread::GetDebugState 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetDebugState
helpviewer_keywords:
- GetDebugState method [.NET Framework debugging]
- ICorDebugThread::GetDebugState method [.NET Framework debugging]
ms.assetid: 9be27b0c-1d99-4722-b0d4-40cf6753ce5c
topic_type:
- apiref
ms.openlocfilehash: 746fef3629e6573d7dfe47d5a3fcf9ee9a1d4250
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728039"
---
# <a name="icordebugthreadgetdebugstate-method"></a>ICorDebugThread::GetDebugState 方法

取得這個 ICorDebugThread 物件的目前偵錯工具狀態。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetDebugState (  
    [out] CorDebugThreadState   *pState  
);  
```  
  
## <a name="parameters"></a>參數  

 `pState`  
 擴展CorDebugThreadState 列舉值的位元組合指標，這些值會描述這個執行緒目前的偵錯工具狀態。  
  
## <a name="remarks"></a>備註  

 如果進程目前已停止， `pState` 表示此執行緒的偵測狀態（如果進程已繼續，而非此執行緒的實際目前狀態）。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
