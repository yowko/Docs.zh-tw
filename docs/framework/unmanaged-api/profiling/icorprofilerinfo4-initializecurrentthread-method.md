---
title: ICorProfilerInfo4::InitializeCurrentThread 方法
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9fd0900e61c57d105439d83430284dc8634d2a1e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000502"
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a>ICorProfilerInfo4::InitializeCurrentThread 方法
初始化目前的執行緒之前後續的程式碼剖析工具 API 呼叫在相同的執行緒，因此可以避免死結。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a>備註  
 我們建議您呼叫`InitializeCurrentThread`在任何執行緒會呼叫程式碼剖析工具 API 有暫止執行緒。 這個方法通常由建立自己的執行緒來呼叫的取樣分析工具[ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)目標執行緒暫停執行時，會逐步引導方法，以執行堆疊。 藉由呼叫`InitializeCurrentThread`分析工具之後當分析工具會先建立取樣執行緒，可以確保的第一個呼叫期間，否則執行 CLR，每個執行緒延遲初始設定`DoStackSnapshot`現在可能安全地當沒有其他執行緒都在暫止。  
  
> [!NOTE]
>  `InitializeCurrentThread` 會初始化事先完成工作，會取得鎖定，並可能會發生死結。 呼叫`InitializeCurrentThread`只在不有任何暫止的執行緒。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo4 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [分析介面](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [程式碼剖析](../../../../docs/framework/unmanaged-api/profiling/index.md)
