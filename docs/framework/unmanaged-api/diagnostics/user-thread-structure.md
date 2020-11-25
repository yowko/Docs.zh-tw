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
ms.openlocfilehash: 409651aa69e957418ad46f61e1bd57add0eb10a6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722891"
---
# <a name="user_thread-structure"></a>USER_THREAD 結構

提供有關執行緒的資訊給偵錯工具。 如需詳細資訊，請參閱 [INotifySource2：： SetNotifyFilter](inotifysource2-setnotifyfilter-method.md) 方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct tagUSER_THREAD  
{  
    BYTE    *pSidBuffer;  
    DWORD   dwSidLen;  
    DWORD   dwTid;  
} USER_THREAD;  
```  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`pSidBuffer`|執行緒緩衝區的位址。|  
|`dwSidLen`|執行緒緩衝區的長度（以位元組為單位）。|  
|`dwTid`|執行緒識別碼。|  
  
## <a name="requirements"></a>需求  

 **標頭：** ProtocolNotify2 .idl  
  
## <a name="see-also"></a>另請參閱

- [SetNotifyFilter 方法](inotifysource2-setnotifyfilter-method.md)
- [診斷符號存放區結構](diagnostics-symbol-store-structures.md)
