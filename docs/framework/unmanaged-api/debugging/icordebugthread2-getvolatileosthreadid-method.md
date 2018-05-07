---
title: ICorDebugThread2::GetVolatileOSThreadID 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetVolatileOSThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetVolatileOSThreadID
helpviewer_keywords:
- GetVolatileOSThreadID method [.NET Framework debugging]
- ICorDebugThread2::GetVolatileOSThreadID method [.NET Framework debugging]
ms.assetid: f0922545-c2cf-40c8-9ef6-ca033563e682
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2e6798c2574167ec1a013429b380d8fa6c878dad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugthread2getvolatileosthreadid-method"></a>ICorDebugThread2::GetVolatileOSThreadID 方法
取得此 ICorDebugThread2 作業系統執行緒識別項。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetVolatileOSThreadID (  
    [out] DWORD    *pdwTid  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pdwTid`  
 [out]這個執行緒的作業系統執行緒識別項。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
