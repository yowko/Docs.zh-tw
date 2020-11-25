---
title: ICorDebugThread::GetID 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetID
helpviewer_keywords:
- ICorDebugThread::GetID method [.NET Framework debugging]
- GetID method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: f1de4584-92df-42f3-9da4-fca03a1c6821
topic_type:
- apiref
ms.openlocfilehash: 85cfd7ba648f21721f1a9689843eac232489cb42
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728013"
---
# <a name="icordebugthreadgetid-method"></a>ICorDebugThread::GetID 方法

取得此 ICorDebugThread 之現用部分的目前作業系統識別碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetID (  
    [out] DWORD *pdwThreadId  
);  
```  
  
## <a name="parameters"></a>參數  

 `pdwThreadId`  
 擴展執行緒的識別碼。  
  
## <a name="remarks"></a>備註  

 作業系統識別碼可能會在程式執行期間變更，而且可能是執行緒不同部分的不同值。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
