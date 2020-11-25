---
title: ICorProfilerFunctionControl 介面
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl
helpviewer_keywords:
- ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: 4e3d3141-4662-4166-8f05-bc857c1b4216
topic_type:
- apiref
ms.openlocfilehash: 733a8f0bc7e8c19823827297a50f9c6906614ca7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698373"
---
# <a name="icorprofilerfunctioncontrol-interface"></a>ICorProfilerFunctionControl 介面

提供的方法可讓程式碼分析工具與通用語言執行平台 (CLR) 進行通訊，以控制在重新編譯特定方法時，JIT 編譯器應如何產生程式碼。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[SetCodegenFlags 方法](icorprofilerfunctioncontrol-setcodegenflags-method.md)|從 [COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md) 列舉設定一或多個旗標，以控制及時 (JIT) 重新編譯函式的程式碼產生。|  
|[SetILFunctionBody 方法](icorprofilerfunctioncontrol-setilfunctionbody-method.md)|取代方法的 Common Intermediate Language (CIL) 主體。|  
|[SetILInstrumentedCodeMap 方法](icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md)|使用指定的通用中間語言 (CIL) 對應項目，為所指定的函式設定程式碼對應。|  
  
## <a name="remarks"></a>備註  

 `ICorProfilerFunctionControl` 介面可提供方法來控制單一重新編譯函式的程式碼產生方式。 Profiler 會透過 [ICorProfilerCallback4：： GetReJITParameters](icorprofilercallback4-getrejitparameters-method.md) 回呼取得這個介面的實例。 `ICorProfilerFunctionControl` 的每個執行個體各控制一個函式的所有執行個體。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo4 介面](icorprofilerinfo4-interface.md)
- [分析介面](profiling-interfaces.md)
- [EnumJITedFunctions2 方法](icorprofilerinfo4-enumjitedfunctions2-method.md)
