---
title: ICorProfilerFunctionEnum 介面
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum
helpviewer_keywords:
- ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 0a1d4a38-cd0b-4231-91df-13646218ae72
topic_type:
- apiref
ms.openlocfilehash: b69afa7676ad174725f13c1113ff3bd9972995f8
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503077"
---
# <a name="icorprofilerfunctionenum-interface"></a>ICorProfilerFunctionEnum 介面
提供方法以循序逐一查看 Common Language Runtime 中的函式集合。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Clone 方法](icorprofilerfunctionenum-clone-method.md)|取得這個 `ICorProfilerFunctionEnum` 介面複本的介面指標。|  
|[GetCount 方法](icorprofilerfunctionenum-getcount-method.md)|取得應用程式已載入的或分析工具強制載入的函式數目。|  
|[下一個方法](icorprofilerfunctionenum-next-method.md)|從循序函式集合中取得指定的連續函式數目，從序列中列舉值的目前位置開始。|  
|[Reset 方法](icorprofilerfunctionenum-reset-method.md)|將列舉值的資料指標移至序列的開始位置。|  
|[Skip 方法](icorprofilerfunctionenum-skip-method.md)|將列舉值的資料指標從其目前位置前移，以略過指定數目的項目。|  
  
## <a name="remarks"></a>備註  
 `ICorProfilerFunctionEnum` 介面是列舉值。 它可讓陣列的接收端以適合接收端的速率，從傳送端提取項目。 換句話說，接收端能夠明確控制陣列項目的流程，因此可避免與傳遞大型陣列做為方法參數相關的問題發生。  
  
 `ICorProfilerFunctionEnum` 列舉早已 JIT 編譯的函式，但此函式不包含從 Ngen.exe 產生的原生影像載入之函式。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo 介面](icorprofilerinfo-interface.md)
- [分析介面](profiling-interfaces.md)
- [EnumJITedFunctions 方法](icorprofilerinfo3-enumjitedfunctions-method.md)
