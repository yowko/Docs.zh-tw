---
title: "ICorDebugThread::GetUserState 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.GetUserState
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::GetUserState
helpviewer_keywords:
- GetUserState method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetUserState method [.NET Framework debugging]
ms.assetid: ae0cfd73-8ead-4d36-9310-dccaac9db0bd
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 48a86317774a3ebba4ed600b880110a7adaa02a7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthreadgetuserstate-method"></a>ICorDebugThread::GetUserState 方法
取得此 ICorDebugThread 的目前使用者狀態。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetUserState (  
    [out] CorDebugUserState   *pState  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pState`  
 [out]CorDebugUserState 列舉值，描述這個執行緒的目前使用者狀態的位元組合指標。  
  
## <a name="remarks"></a>備註  
 執行緒的使用者狀態時進行檢查的程式進行偵錯執行緒的狀態。 執行緒可能會有多個設定的狀態位元。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
