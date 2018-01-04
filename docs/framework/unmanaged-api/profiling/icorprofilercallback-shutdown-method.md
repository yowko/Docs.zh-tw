---
title: "ICorProfilerCallback::Shutdown 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.Shutdown
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::Shutdown
helpviewer_keywords:
- ICorProfilerCallback::Shutdown method [.NET Framework profiling]
- Shutdown method [.NET Framework profiling]
ms.assetid: 1ea194f0-a331-4855-a2ce-37393b8e5f84
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 42c9abc3c255f7ddda5e7934c495b073a7b1f6fd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackshutdown-method"></a>ICorProfilerCallback::Shutdown 方法
通知分析工具的應用程式即將關閉。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a>備註  
 分析工具程式碼無法安全地呼叫方法[ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)介面之後`Shutdown`方法呼叫。 任何呼叫`ICorProfilerInfo`方法導致未定義的行為之後`Shutdown`方法會傳回。 在關閉之後，仍然可能發生特定不可變的事件程式碼剖析工具應謹慎地發生這種情況時，立即傳回。  
  
 `Shutdown`正在分析 managed 應用程式啟動為 managed 程式碼，才會呼叫方法 （也就是初始堆疊上的框架處理程序負責管理）。 如果應用程式啟動為 unmanaged 程式碼，但稍後跳至 managed 程式碼，藉此建立的執行個體 common language runtime (CLR)，然後`Shutdown`將不會呼叫。 這些情況下，程式碼剖析工具應該在其文件庫中包含`DllMain`釋放任何資源，並執行清除其資料，例如追蹤等等磁碟排清處理常式，它會使用 DLL_PROCESS_DETACH 值。  
  
 一般情況下，分析工具必須處理未預期的關機。 處理程序，例如可能因 Win32 的`TerminateProcess`（宣告於 Winbase.h） 的方法。 在其他情況下，CLR 會暫止特定受管理的執行緒 （背景執行緒），而不以正確順序解構訊息傳遞它們。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [ICorProfilerCallback 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [Initialize 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)
