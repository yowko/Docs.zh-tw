---
title: "ICorProfilerCallback::RuntimeThreadResumed 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RuntimeThreadResumed
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RuntimeThreadResumed
helpviewer_keywords:
- ICorProfilerCallback::RuntimeThreadResumed method [.NET Framework profiling]
- RuntimeThreadResumed method [.NET Framework profiling]
ms.assetid: da984f89-4f53-4ab0-ae6f-3e2ee6085994
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b460f87ead93c5f375c758a5547c0ae0be2b5691
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackruntimethreadresumed-method"></a>ICorProfilerCallback::RuntimeThreadResumed 方法
通知分析工具指定的執行緒已經在暫停之後繼續。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT RuntimeThreadResumed(  
    [in] ThreadID threadId);  
```  
  
#### <a name="parameters"></a>參數  
 `threadId`  
 [in]已繼續執行緒的識別碼。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorProfilerCallback 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [RuntimeThreadSuspended 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)
