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
ms.openlocfilehash: f6873de1a864489d144a671b1a9e1349eaf77d15
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503174"
---
# <a name="icorprofilercallbackshutdown-method"></a>ICorProfilerCallback::Shutdown 方法
通知 profiler 應用程式正在關閉。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a>備註  
 呼叫方法之後，分析工具程式碼無法安全地呼叫[ICorProfilerInfo](icorprofilerinfo-interface.md)介面的方法 `Shutdown` 。 對方法的任何呼叫都會 `ICorProfilerInfo` 在方法傳回之後導致未定義的行為 `Shutdown` 。 某些不可變事件在關機後可能仍會發生;分析工具應該小心在發生這種情況時立即傳回。  
  
 `Shutdown`只有當正在分析的 managed 應用程式啟動為受控碼（也就是管理進程堆疊上的初始框架）時，才會呼叫方法。 如果應用程式是以非受控碼的形式啟動，但後來跳到 managed 程式碼，藉此建立 common language runtime （CLR）的實例，則 `Shutdown` 不會呼叫。 在這些情況下，分析工具應該包含在其程式庫中的 `DllMain` 常式，其中會使用 DLL_PROCESS_DETACH 值來釋放任何資源，並執行其資料的清除處理，例如將追蹤排清到磁片等等。  
  
 一般來說，分析工具必須處理非預期的關機。 例如，Win32 `TerminateProcess` 方法（在 Winbase 中宣告）可能會停止進程。 在其他情況下，CLR 將會停止特定的 managed 執行緒（背景執行緒），而不會為它們傳遞有序的析構訊息。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
- [Initialize 方法](icorprofilercallback-initialize-method.md)
