---
title: ICorProfilerCallback::ExceptionThrown 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionThrown
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionThrown
helpviewer_keywords:
- ExceptionThrown method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionThrown method [.NET Framework profiling]
ms.assetid: f1a23f3b-ac21-4905-8abf-8ea59f15af53
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e3358150754fd039d6e6107efd61c8d950fd02f0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallbackexceptionthrown-method"></a>ICorProfilerCallback::ExceptionThrown 方法
通知分析工具已擲回的例外狀況。  
  
> [!NOTE]
>  例外狀況到達 managed 程式碼時，才會呼叫此函式。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT ExceptionThrown(  
    [in] ObjectID thrownObjectId);  
```  
  
#### <a name="parameters"></a>參數  
 `thrownObjectId`  
 [in]導致擲回例外狀況物件的識別碼。  
  
## <a name="remarks"></a>備註  
 因為堆疊可能不是處於允許記憶體回收，分析工具不應該在這個方法實作封鎖，因此無法啟用先佔式記憶體回收。 如果分析工具會封鎖這裡並嘗試執行記憶體回收、 執行階段將會封鎖此回呼傳回之前。  
  
 Managed 程式碼或任何方式原因 managed 記憶體配置中，不應該呼叫這個方法的程式碼剖析工具實作。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorProfilerCallback 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
