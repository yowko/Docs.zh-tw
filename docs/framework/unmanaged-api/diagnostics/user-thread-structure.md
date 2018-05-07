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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 93e96d6f8570e6aef7bfc18ef2859dc1e86ec8fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="userthread-structure"></a>USER_THREAD 結構
提供資訊給偵錯工具執行緒。 如需詳細資訊，請參閱[inotifysource2:: Setnotifyfilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md)方法。  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct tagUSER_THREAD  
{  
    BYTE    *pSidBuffer;  
    DWORD   dwSidLen;  
    DWORD   dwTid;  
} USER_THREAD;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`pSidBuffer`|執行緒緩衝區的位址。|  
|`dwSidLen`|執行緒的緩衝區，以位元組為單位的長度。|  
|`dwTid`|執行緒識別碼。|  
  
## <a name="requirements"></a>需求  
 **標頭：** ProtocolNotify2.idl  
  
## <a name="see-also"></a>另請參閱  
 [SetNotifyFilter 方法](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md)  
 [診斷符號存放區結構](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
