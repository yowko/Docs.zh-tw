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
ms.openlocfilehash: c3e623b0b5f8b49e043fe3a1aa8311558e573573
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95682831"
---
# <a name="icorprofilerinfo4-interface"></a>ICorProfilerInfo4 介面

提供程式碼分析工具用來與 common language runtime 進行通訊的方法， (CLR) 來控制事件監視和要求資訊。 . `ICorProfilerInfo4`介面是其他介面的延伸 `ICorProfilerInfo` 。 它提供新的方法，以支援 .NET Framework 4.5 中新增的即時 (JIT) 重新編譯。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[EnumJITedFunctions2 方法](icorprofilerinfo4-enumjitedfunctions2-method.md)|傳回先前 JIT 編譯和 JIT 重新編譯之所有函式的列舉值。|  
|[EnumThreads 方法](icorprofilerinfo4-enumthreads-method.md)|取得列舉值，這個列舉值會提供方法，以依序逐一查看已分析進程中所有 managed 執行緒的集合。|  
|[GetCodeInfo3 方法](icorprofilerinfo4-getcodeinfo3-method.md)|取得與經過 JIT 重新編譯的指定函式版本關聯的機器碼範圍。|  
|[GetFunctionFromIP2 方法](icorprofilerinfo4-getfunctionfromip2-method.md)|將 managed 程式碼指令指標對應至指定之函式的 JIT 重新編譯版本。|  
|[GetILToNativeMapping2 方法](icorprofilerinfo4-getiltonativemapping2-method.md)|取得 Microsoft 中繼語言 (MSIL 的對應，) 指定函式之 JIT 重新編譯版本中所包含之程式碼的原生位移。|  
|[GetObjectSize2 方法](icorprofilerinfo4-getobjectsize2-method.md)|傳回指定之物件的大小。|  
|[GetReJITIDs 方法](icorprofilerinfo4-getrejitids-method.md)|傳回識別碼陣列，識別仍配置之指定函式的所有 JIT 重新編譯版本。|  
|[InitializeCurrentThread 方法](icorprofilerinfo4-initializecurrentthread-method.md)|在相同執行緒上的後續分析工具 API 呼叫之前，初始化目前的執行緒，因此可以避免鎖死。|  
|[RequestReJIT 方法](icorprofilerinfo4-requestrejit-method.md)|要求指定函式的所有執行個體進行 JIT 重新編譯。|  
|[RequestRevert 方法](icorprofilerinfo4-requestrevert-method.md)|將指定函式的所有執行個體還原成其原始版本。|  
  
## <a name="remarks"></a>備註  

 藉由使用無限制執行緒模型，CLR 會實作 `ICorProfilerInfo4` 介面的方法。 每個方法會傳回 HRESULT，表示成功或失敗。 如需可能的傳回程式碼清單，請參閱 CorError.h 檔案。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [分析介面](profiling-interfaces.md)
- [ICorProfilerInfo 介面](icorprofilerinfo-interface.md)
