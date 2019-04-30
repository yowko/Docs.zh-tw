---
title: ICorProfilerInfo4 介面
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4
helpviewer_keywords:
- ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 80a5308e-c22f-4201-ba89-31cc8562515b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 177e5ef8054f408dc8ec3475c56043394a636bc0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049449"
---
# <a name="icorprofilerinfo4-interface"></a>ICorProfilerInfo4 介面
提供程式碼分析工具使用與通用語言執行平台 (CLR)，以控制事件監視以及要求資訊進行通訊的方法。 。 `ICorProfilerInfo4`介面是其他延伸模組`ICorProfilerInfo`介面。 它提供新的方法，以支援在 just-in-time (JIT) 重新編譯中加入[!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[EnumJITedFunctions2 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)|傳回所有先前 JIT 編譯和 JIT 重新編譯的函式的列舉值。|  
|[EnumThreads 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumthreads-method.md)|取得列舉值，提供方法，以循序逐一查看分析的處理序中的所有 managed 執行緒的集合。|  
|[GetCodeInfo3 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)|取得與經過 JIT 重新編譯的指定函式版本關聯的機器碼範圍。|  
|[GetFunctionFromIP2 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getfunctionfromip2-method.md)|將 managed 程式碼指令指標對應到指定的函式的 JIT 重新編譯版本。|  
|[GetILToNativeMapping2 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)|取得從 Microsoft intermediate language (MSIL) 位移到原生位移指定的函式的 JIT 重新編譯版本中包含的程式碼對應。|  
|[GetObjectSize2 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md)|傳回指定之物件的大小。|  
|[GetReJITIDs 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getrejitids-method.md)|傳回識別 JIT 重新編譯的所有版本指定的函式仍配置的識別碼陣列。|  
|[InitializeCurrentThread 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-initializecurrentthread-method.md)|初始化目前的執行緒之前後續的程式碼剖析工具 API 呼叫在相同的執行緒，因此可以避免死結。|  
|[RequestReJIT 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md)|要求指定函式的所有執行個體進行 JIT 重新編譯。|  
|[RequestRevert 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md)|將指定函式的所有執行個體還原成其原始版本。|  
  
## <a name="remarks"></a>備註  
 藉由使用無限制執行緒模型，CLR 會實作 `ICorProfilerInfo4` 介面的方法。 每個方法會傳回 HRESULT，表示成功或失敗。 如需可能的傳回程式碼清單，請參閱 CorError.h 檔案。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [分析介面](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerInfo 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
