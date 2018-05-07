---
title: ICorDebugProcess::GetHandle 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::GetHandle method [.NET Framework debugging]
ms.assetid: e7d3ecf5-09d2-4d94-abb6-ff3483deebb6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60bd7567f541a0bbaa3591d2f2905d13064dec3c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugprocessgethandle-method"></a>ICorDebugProcess::GetHandle 方法
取得處理程序的控制代碼。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetHandle([out] HPROCESS *phProcessHandle);  
```  
  
#### <a name="parameters"></a>參數  
 `phProcessHandle`  
 [out]指標`HPROCESS`也就是處理程序的控制代碼。  
  
## <a name="remarks"></a>備註  
 擷取控制代碼的擁有者偵錯介面。 偵錯工具應該重複的控制代碼後才能使用它。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
