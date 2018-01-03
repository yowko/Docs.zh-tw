---
title: "CorDebugSetContextFlag 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugSetContextFlag
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugSetContextFlag
helpviewer_keywords: CorDebugSetContextFlag enumeration [.NET Framework debugging]
ms.assetid: b30280bb-fe75-44ed-8589-bcff081fae44
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 27e9fd561da74a3b88015e7820c2cbbd56ab2a7a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugsetcontextflag-enumeration"></a>CorDebugSetContextFlag 列舉
指出內容是來自堆疊的作用中 (或分葉) 框架，還是藉由從其他框架回溯而計算出來的。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum CorDebugSetContextFlag  
{  
   SET_CONTEXT_FLAG_ACTIVE_FRAME = 1  
   SET_CONTEXT_FLAG_UNWIND_FRAME = 2  
}  CorDebugSetContextFlag;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|SET_CONTEXT_FLAG_ACTIVE_FRAME|內容是在執行緒的作用中的內容。|  
|SET_CONTEXT_FLAG_UNWIND_FRAME|內容已經過計算，藉由從其他框架回溯。|  
  
## <a name="remarks"></a>備註  
 `CorDebugSetContextFlag`提供值，可供[icordebugstackwalk:: Setcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md)方法。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [偵錯列舉](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
