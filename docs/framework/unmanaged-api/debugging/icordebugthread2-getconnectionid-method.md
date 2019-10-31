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
ms.openlocfilehash: a81842132769934a6f5f34e6dc462bba77b3854a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138680"
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
 脫銷表示連接識別碼的 `CONNID`。  
  
## <a name="remarks"></a>備註  
 如果這個執行緒不是連接的一部分，`GetConnectionID` 方法會在 `pdwConnectionId` 參數中傳回零。  
  
 如果這個執行緒連接到 Microsoft SQL Server 2005 Analysis Services （SSAS）的實例，`CONNID` 會對應到伺服器處理序識別碼（SPID）。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
