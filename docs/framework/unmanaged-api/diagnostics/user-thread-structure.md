---
title: USER_THREAD 結構
ms.date: 03/30/2017
api_name:
- USER_THREAD
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- USER_THREAD
helpviewer_keywords:
- USER_THREAD structure [.NET Framework debugging]
ms.assetid: a57c7d71-c4b0-41f9-a964-0c5ee84a3124
topic_type:
- apiref
ms.openlocfilehash: 51db7a2b6464b562e09ce061991898a8d604ead1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437977"
---
# <a name="user_thread-structure"></a>USER_THREAD 結構
Provides information to a debugger about a thread. For more information, see the [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) method.  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct tagUSER_THREAD  
{  
    BYTE    *pSidBuffer;  
    DWORD   dwSidLen;  
    DWORD   dwTid;  
} USER_THREAD;  
```  
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`pSidBuffer`|Address of thread buffer.|  
|`dwSidLen`|Length of thread buffer, in bytes.|  
|`dwTid`|Thread ID.|  
  
## <a name="requirements"></a>需求  
 **Header:** ProtocolNotify2.idl  
  
## <a name="see-also"></a>請參閱

- [SetNotifyFilter 方法](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md)
- [診斷符號存放區結構](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
