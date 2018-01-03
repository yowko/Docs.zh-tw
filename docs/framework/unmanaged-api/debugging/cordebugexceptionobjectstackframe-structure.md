---
title: "CorDebugExceptionObjectStackFrame 結構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugExceptionObjectStackFrame
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugExceptionObjectStackFrame
helpviewer_keywords: CorDebugExceptionObjectStackFrame structure [.NET Framework debugging]
ms.assetid: 542cdd81-5ae7-4361-b0ef-1ae4775df258
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4f2d3f0d0c17c0fdf8b772ba38ae97fd8e406be8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugexceptionobjectstackframe-structure"></a>CorDebugExceptionObjectStackFrame 結構
代表例外狀況物件所產生的堆疊框架資訊。  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct CorDebugExceptionObjectStackFrame {  
    ICorDebugModule* pModule;  
    CORDB_ADDRESS ip;  
    mdMethodDef methodDef;  
    BOOL isLastForeignExceptionFrame;  
} CorDebugExceptionObjectStackFrame;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`pModule`|ICorDebugModule 物件目前畫面格指標。|  
|`ip`|指令指標 (EIP/RIP) 目前畫面格的值。|  
|`methodDef`|目前的框架方法語彙基元。|  
|`isLastForeignExceptionFrame`|值，指出的框架是在外部例外狀況中的最後一個框架。|  
  
## <a name="remarks"></a>備註  
 呼叫端必須釋放 ICorDebugModule 物件的指標之後就無法再使用中。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [偵錯結構](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
