---
title: ICorProfilerCallback::Shutdown 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.Shutdown
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::Shutdown
helpviewer_keywords:
- ICorProfilerCallback::Shutdown method [.NET Framework profiling]
- Shutdown method [.NET Framework profiling]
ms.assetid: 1ea194f0-a331-4855-a2ce-37393b8e5f84
topic_type:
- apiref
ms.openlocfilehash: 63e41df8af85d94df068526ef69708687b341e78
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446938"
---
# <a name="icorprofilercallbackshutdown-method"></a>ICorProfilerCallback::Shutdown 方法
通知 profiler 應用程式正在關閉。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a>備註  
 呼叫 `Shutdown` 方法之後，分析工具程式碼無法安全地呼叫[ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)介面的方法。 `ICorProfilerInfo` 方法的任何呼叫都會在 `Shutdown` 方法傳回之後導致未定義的行為。 某些不可變事件在關機後可能仍會發生;分析工具應該小心在發生這種情況時立即傳回。  
  
 只有當正在分析的 managed 應用程式啟動為受控碼（也就是管理進程堆疊上的初始框架）時，才會呼叫 `Shutdown` 方法。 如果應用程式是以非受控碼啟動，但之後跳到 managed 程式碼，藉此建立 common language runtime （CLR）的實例，則不會呼叫 `Shutdown`。 在這些情況下，分析工具應該包含在其程式庫中的 `DllMain` 常式，其中使用 DLL_PROCESS_DETACH 值來釋放任何資源，並執行其資料的清除處理，例如將追蹤排清到磁片等等。  
  
 一般來說，分析工具必須處理非預期的關機。 例如，Win32 `TerminateProcess` 方法（在 Winbase 中宣告）可能會暫停處理常式。 在其他情況下，CLR 將會停止特定的 managed 執行緒（背景執行緒），而不會為它們傳遞有序的析構訊息。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerCallback 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Initialize 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)
