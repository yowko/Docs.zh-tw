---
title: ICorDebugThread2::GetConnectionID 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetConnectionID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetConnectionID
helpviewer_keywords:
- ICorDebugThread2::GetConnectionID method [.NET Framework debugging]
- GetConnectionID method [.NET Framework debugging]
ms.assetid: 9c76b587-f941-4fa1-8b86-f3494fb10c8e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc4963dcf686fe62f473aea1af86868df03718df
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768963"
---
# <a name="icordebugthread2getconnectionid-method"></a>ICorDebugThread2::GetConnectionID 方法
取得這個 ICorDebugThread2 物件的連接識別碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetConnectionID (  
    [out] CONNID *pdwConnectionId  
);  
```  
  
## <a name="parameters"></a>參數  
 `pdwConnectionId`  
 [out]A`CONNID`表示的連接識別碼。  
  
## <a name="remarks"></a>備註  
 `GetConnectionID`方法會傳回零`pdwConnectionId`參數，如果這個執行緒不是連接的一部分。  
  
 如果這個執行緒已連線到執行個體的 Microsoft SQL Server 2005 Analysis Services (SSAS)，`CONNID`對應至伺服器處理序識別碼 (SPID)。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
