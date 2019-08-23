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
ms.openlocfilehash: 01e407b726ce4426f3b58bc29854b30bd6add257
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953882"
---
# <a name="icorprofilercallbackexceptionthrown-method"></a>ICorProfilerCallback::ExceptionThrown 方法
通知分析工具已擲回例外狀況。  
  
> [!NOTE]
> 只有在例外狀況到達 managed 程式碼時, 才會呼叫這個函式。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ExceptionThrown(  
    [in] ObjectID thrownObjectId);  
```  
  
## <a name="parameters"></a>參數  
 `thrownObjectId`  
 在導致擲回例外狀況之物件的識別碼。  
  
## <a name="remarks"></a>備註  
 分析工具不應在此方法的執行中封鎖, 因為堆疊可能不是處於允許垃圾收集的狀態, 因此無法啟用「搶先垃圾收集」。 如果分析工具在此處封鎖並嘗試垃圾收集, 執行時間將會封鎖, 直到這個回呼傳回為止。  
  
 分析工具的此方法的執行不應呼叫 managed 程式碼, 或以任何方式進行, 以造成 managed 記憶體配置。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Corprof.idl .idl, Corprof.idl。h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
