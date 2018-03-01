---
title: "ICorProfilerInfo4::InitializeCurrentThread 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerInfo4::InitializeCurrentThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::InitializeCurrentThread
helpviewer_keywords:
- ICorProfilerInfo4::InitializeCurrentThread method [.NET Framework profiling]
- InitializeCurrentThread method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 18a3335c-8c75-476c-b6de-72c0bfedae5d
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4f3c261068b38861dca2633a490e46d9f44371d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a>ICorProfilerInfo4::InitializeCurrentThread 方法
初始化目前的執行緒之前後續程式碼剖析工具應用程式開發介面呼叫，在相同執行緒，因此可以避免發生死結。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a>備註  
 我們建議您呼叫`InitializeCurrentThread`會呼叫程式碼剖析工具的任何執行緒上應用程式開發介面有暫止的執行緒。 這個方法通常由取樣分析工具，建立自己的執行緒來呼叫[icorprofilerinfo2:: Dostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)方法，以執行堆疊會引導目標執行緒暫停。 藉由呼叫`InitializeCurrentThread`之後當分析工具會先建立取樣執行緒，分析工具可確保每個執行緒延遲初始設定，另外執行 CLR 的第一個呼叫期間`DoStackSnapshot`現在可能安全地當沒有其他執行緒都在暫止。  
  
> [!NOTE]
>  `InitializeCurrentThread`未初始化事先完成的工作取得鎖定，鎖定，而且可能會發生死結。 呼叫`InitializeCurrentThread`時，才有任何暫止的執行緒。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [ICorProfilerInfo4 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [分析介面](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [程式碼剖析](../../../../docs/framework/unmanaged-api/profiling/index.md)
