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
ms.openlocfilehash: 1286ce953c96eb3e3164ba5b209031dd1ec5c453
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864696"
---
# <a name="icorprofilerfunctioncontrol-interface"></a>ICorProfilerFunctionControl 介面
提供的方法可讓程式碼分析工具與通用語言執行平台 (CLR) 進行通訊，以控制在重新編譯特定方法時，JIT 編譯器應如何產生程式碼。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[SetCodegenFlags 方法](icorprofilerfunctioncontrol-setcodegenflags-method.md)|設定[COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md)列舉中的一或多個旗標，以控制即時（JIT）重新編譯函式的程式碼產生。|  
|[SetILFunctionBody 方法](icorprofilerfunctioncontrol-setilfunctionbody-method.md)|取代方法的 Common Intermediate Language (CIL) 主體。|  
|[SetILInstrumentedCodeMap 方法](icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md)|使用指定的通用中間語言 (CIL) 對應項目，為所指定的函式設定程式碼對應。|  
  
## <a name="remarks"></a>備註  
 `ICorProfilerFunctionControl` 介面可提供方法來控制單一重新編譯函式的程式碼產生方式。 分析工具會透過[ICorProfilerCallback4：： GetReJITParameters](icorprofilercallback4-getrejitparameters-method.md)回呼來取得此介面的實例。 `ICorProfilerFunctionControl` 的每個執行個體各控制一個函式的所有執行個體。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerInfo4 介面](icorprofilerinfo4-interface.md)
- [分析介面](profiling-interfaces.md)
- [EnumJITedFunctions2 方法](icorprofilerinfo4-enumjitedfunctions2-method.md)
