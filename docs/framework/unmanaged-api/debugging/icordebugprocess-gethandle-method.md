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
ms.openlocfilehash: 56f1dd892429724866182248b0c0413a7d2437cd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766068"
---
# <a name="icordebugprocessgethandle-method"></a>ICorDebugProcess::GetHandle 方法
取得處理程序的控制代碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetHandle([out] HPROCESS *phProcessHandle);  
```  
  
## <a name="parameters"></a>參數  
 `phProcessHandle`  
 [out]指標`HPROCESS`也就是處理程序的控制代碼。  
  
## <a name="remarks"></a>備註  
 擷取的控制代碼是由偵錯介面所擁有。 偵錯工具應該重複使用它之前的控制代碼。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
