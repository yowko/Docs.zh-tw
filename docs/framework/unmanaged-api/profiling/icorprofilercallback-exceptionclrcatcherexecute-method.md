---
title: ICorProfilerCallback::ExceptionCLRCatcherExecute 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCLRCatcherExecute
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCLRCatcherExecute
helpviewer_keywords:
- ExceptionCLRCatcherExecute method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionCLRCatcherExecute method [.NET Framework profiling]
ms.assetid: aaac8f98-5cf4-42c7-b04b-556cce367e36
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6057593362e75044a9b2db32ad5dafe439a551d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallbackexceptionclrcatcherexecute-method"></a>ICorProfilerCallback::ExceptionCLRCatcherExecute 方法
時呼叫`catch`封鎖在 common language runtime (CLR) 本身內執行例外狀況。 這個方法是.NET Framework 2.0 版中已過時。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT ExceptionCLRCatcherExecute();  
```  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** 1.1、 1.0  
  
## <a name="see-also"></a>另請參閱  
 [ICorProfilerCallback 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ExceptionCLRCatcherFound 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherfound-method.md)
