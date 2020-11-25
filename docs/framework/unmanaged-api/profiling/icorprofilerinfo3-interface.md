---
title: ICorProfilerInfo3 介面
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3
helpviewer_keywords:
- ICorProfilerInfo3 interface [.NET Framework profiling]
ms.assetid: 044a262f-0fa7-485d-b0c1-64cdc359c654
topic_type:
- apiref
ms.openlocfilehash: 9944234da1677608aec10066b61bfc6a6cb72bcb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697853"
---
# <a name="icorprofilerinfo3-interface"></a>ICorProfilerInfo3 介面

提供程式碼分析工具用於和 Common Language Runtime (CLR) 通訊，以控制事件監視以及要求資訊的方法。 `ICorProfilerInfo3`介面是[ICorProfilerInfo2](icorprofilerinfo2-interface.md)介面的延伸。 它提供 .NET Framework 4 和更新版本中支援的新方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[EnumJITedFunctions 方法](icorprofilerinfo3-enumjitedfunctions-method.md)|傳回所有先前 JIT 編譯函式的列舉。|  
|[EnumModules 方法](icorprofilerinfo3-enummodules-method.md)|傳回提供循序逐一查看 Managed 模組集合方法的列舉，其中該模組被載入至應用程式中。|  
|[GetAppDomainsContainingModule 方法](icorprofilerinfo3-getappdomainscontainingmodule-method.md)|取得已載入指定模組之應用程式定義域的識別項。|  
|[GetFunctionEnter3Info 方法](icorprofilerinfo3-getfunctionenter3info-method.md)|提供由 [FunctionEnter3WithInfo](functionenter3withinfo-function.md) 函式回報給 profiler 的函式之堆疊框架和引數資訊;只能在回呼期間呼叫 `FunctionEnter3WithInfo` 。|  
|[GetFunctionLeave3Info 方法](icorprofilerinfo3-getfunctionleave3info-method.md)|提供由 [FunctionLeave3WithInfo 函數](functionleave3withinfo-function.md) 函式回報給 profiler 的函式之堆疊框架和傳回值;只能在回呼期間呼叫 `FunctionLeave3WithInfo` 。|  
|[GetFunctionTailcall3Info 方法](icorprofilerinfo3-getfunctiontailcall3info-method.md)|提供由 [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) 函式回報給 profiler 的函式的堆疊框架;只能在回呼期間呼叫 `FunctionTailcall3WithInfo` 。|  
|[GetModuleInfo2 方法](icorprofilerinfo3-getmoduleinfo2-method.md)|提供模組 ID，傳回該模組的檔案名稱、此模組父代組件的 ID 和描述模組屬性的位元遮罩。|  
|[GetRuntimeInformation 方法](icorprofilerinfo3-getruntimeinformation-method.md)|提供有關正在分析之執行階段的版本資訊。|  
|[GetStringLayout2 方法](icorprofilerinfo3-getstringlayout2-method.md)|取得字串物件配置的相關資訊。|  
|[GetThreadStaticAddress2 方法](icorprofilerinfo3-getthreadstaticaddress2-method.md)|取得指定執行緒靜態欄位的位址，這位於指定之執行緒和應用程式定義域的範圍內。|  
|[RequestProfilerDetach 方法](icorprofilerinfo3-requestprofilerdetach-method.md)|指示該執行階段中斷與分析工具的連結。|  
|[SetEnterLeaveFunctionHooks3 方法](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)|指定將在 [FunctionEnter3](functionenter3-function.md)、 [FunctionLeave3](functionleave3-function.md)和 [FunctionTailcall3](functiontailcall3-function.md) 函式上呼叫的分析工具所執行的函數。|  
|[SetEnterLeaveFunctionHooks3WithInfo 方法](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)|指定將在 managed 函式的 [FunctionEnter3WithInfo](functionenter3withinfo-function.md)、 [FunctionLeave3WithInfo](functionleave3withinfo-function.md)和 [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) 勾點上呼叫的程式碼剖析工具所執行的函式。|  
|[SetFunctionIDMapper2 方法](icorprofilerinfo3-setfunctionidmapper2-method.md)|指定將被呼叫來對應 `FunctionID` 值到替代值的程式碼剖析工具實作函式，這會被傳遞至分析工具函式進入/離開的攔截。 這個方法會以參數擴充 [ICorProfilerInfo：： SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) ，讓分析工具用來區分執行時間。|  
  
## <a name="remarks"></a>備註  

 藉由使用無限制執行緒模型，CLR 會實作 `ICorProfilerInfo3` 介面的方法。 每個方法會傳回 HRESULT，表示成功或失敗。 如需可能的傳回程式碼清單，請參閱 CorError.h 檔案。  
  
 CLR 會在 `ICorProfilerInfo3` 初始化期間流量分析工具的 [ICorProfilerCallback：： Initialize](icorprofilercallback-initialize-method.md) 或 [ICorProfilerCallback3：： InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) 方法，將介面傳遞至每個程式碼分析工具。 然後程式碼分析工具可以呼叫 `ICorProfilerInfo3` 方法，以取得在 CLR 控制下執行的 Managed 程式碼之資訊。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [分析介面](profiling-interfaces.md)
- [ICorProfilerInfo 介面](icorprofilerinfo-interface.md)
