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
ms.openlocfilehash: 9761eb5085a77279c4d07d39946a5ad1453ecaaf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717221"
---
# <a name="icorprofilercallbackshutdown-method"></a>ICorProfilerCallback::Shutdown 方法

通知 profiler 應用程式正在關閉。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a>備註  

 呼叫方法之後，分析工具程式碼無法安全地呼叫 [ICorProfilerInfo](icorprofilerinfo-interface.md) 介面的方法 `Shutdown` 。 方法的任何呼叫都會 `ICorProfilerInfo` 在方法傳回之後產生未定義的行為 `Shutdown` 。 關機之後可能仍會發生某些不可變的事件;當發生這種情況時，分析工具應該會立即傳回。  
  
 `Shutdown`只有當正在剖析的 managed 應用程式是以 managed 程式碼啟動時，才會呼叫此方法 (也就是，進程堆疊上的初始框架是) 管理。 如果應用程式以非受控碼的形式啟動，但稍後跳到 managed 程式碼，則會建立 common language runtime (CLR) 的實例，然後 `Shutdown` 不會呼叫。 在這些情況下，分析工具應該在其程式庫中包含 `DllMain` 使用 DLL_PROCESS_DETACH 值來釋放任何資源，並對其資料執行清除處理的常式，例如將追蹤排清到磁片等等。  
  
 一般而言，分析工具必須處理未預期的關機。 例如，Win32 方法可能會暫停進程， `TerminateProcess` (在 Winbase 中宣告) 。 在其他情況下，CLR 會將某些 managed 執行緒 (在背景執行緒) ，而不會為它們提供有條理的損毀訊息。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
- [Initialize 方法](icorprofilercallback-initialize-method.md)
