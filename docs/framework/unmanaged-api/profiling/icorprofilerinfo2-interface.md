---
title: ICorProfilerInfo2 介面
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2
helpviewer_keywords:
- ICorProfilerInfo2 interface [.NET Framework profiling]
ms.assetid: 91bd49b6-4d12-494f-a8f1-2f251e8c65e3
topic_type:
- apiref
ms.openlocfilehash: 23fd44a6865b0487296f3ade37c1219e8feba288
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862577"
---
# <a name="icorprofilerinfo2-interface"></a>ICorProfilerInfo2 介面
提供程式碼分析工具用來與 common language runtime （CLR）通訊的方法，以控制事件監視和要求資訊。 `ICorProfilerInfo2` 介面是[ICorProfilerInfo](icorprofilerinfo-interface.md)介面的延伸。 也就是，它會提供 .NET Framework 版本2.0 和更新版本中支援的新方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[DoStackSnapshot 方法](icorprofilerinfo2-dostacksnapshot-method.md)|逐步解說指定執行緒的堆疊，以向分析工具報告受管理的呼叫框架。|  
|[EnumModuleFrozenObjects 方法](icorprofilerinfo2-enummodulefrozenobjects-method.md)|取得列舉值，允許在指定模組中的凍結物件上反覆運算。|  
|[GetAppDomainStaticAddress 方法](icorprofilerinfo2-getappdomainstaticaddress-method.md)|取得指定的應用程式域靜態欄位的位址，該欄位位於指定的應用程式域範圍內。|  
|[GetArrayObjectInfo 方法](icorprofilerinfo2-getarrayobjectinfo-method.md)|取得陣列物件的詳細資訊。|  
|[GetBoxClassLayout 方法](icorprofilerinfo2-getboxclasslayout-method.md)|取得已裝箱之指定實數值型別的類別配置相關資訊。|  
|[GetClassFromTokenAndTypeArgs 方法](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)|使用指定的元資料標記和任何類型引數的 `ClassID` 值，取得類型的 `ClassID`。|  
|[GetClassIDInfo2 方法](icorprofilerinfo2-getclassidinfo2-method.md)|取得指定之泛型類別的父模組、類別的元資料標記、其父類別的 `ClassID`，以及類別的每個類型引數的 `ClassID` （如果有的話）。|  
|[GetClassLayout 方法](icorprofilerinfo2-getclasslayout-method.md)|取得在記憶體中指定類別所定義欄位的配置相關資訊。 也就是說，這個方法會取得此類別的欄位之位移。|  
|[GetCodeInfo2 方法](icorprofilerinfo2-getcodeinfo2-method.md)|取得與指定 `FunctionID` 相關聯的原生程式碼範圍。|  
|[GetContextStaticAddress 方法](icorprofilerinfo2-getcontextstaticaddress-method.md)|取得位於指定內容約制內的指定內容靜態欄位的位址。|  
|[GetFunctionFromTokenAndTypeArgs 方法](icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)|使用指定的元資料標記、包含類別，以及任何類型引數的 `ClassID` 值，取得函式的 `FunctionID`。|  
|[GetFunctionInfo2 方法](icorprofilerinfo2-getfunctioninfo2-method.md)|取得函式的父類別、中繼資料語彙基元和每個類型引數的 `ClassID` (如果有的話)。|  
|[GetGenerationBounds 方法](icorprofilerinfo2-getgenerationbounds-method.md)|取得組成垃圾收集堆積之層代的記憶體區域（堆積的區段）。|  
|[GetNotifiedExceptionClauseInfo 方法](icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)|取得即將執行或剛執行的 exception 子句（`catch`/`finally`/`filter`）的原生位址和框架資訊。|  
|[GetObjectGeneration 方法](icorprofilerinfo2-getobjectgeneration-method.md)|取得堆積的區段，其中包含指定的物件。|  
|[GetRVAStaticAddress 方法](icorprofilerinfo2-getrvastaticaddress-method.md)|取得指定的相對虛擬位址（RVA）-靜態欄位的位址。|  
|[GetStaticFieldInfo 方法](icorprofilerinfo2-getstaticfieldinfo-method.md)|取得指定欄位為靜態的範圍。|  
|[GetStringLayout 方法](icorprofilerinfo2-getstringlayout-method.md)|取得字串物件配置的相關資訊。|  
|[GetThreadAppDomain 方法](icorprofilerinfo2-getthreadappdomain-method.md)|取得指定的執行緒目前正在執行程式碼的應用程式域識別碼。|  
|[GetThreadStaticAddress 方法](icorprofilerinfo2-getthreadstaticaddress-method.md)|取得指定的執行緒靜態欄位的位址，該欄位位於指定之執行緒的範圍內。|  
|[SetEnterLeaveFunctionHooks2 方法](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)|指定要在「輸入」、「離開」和 managed 函式的「tailcall」攔截器上呼叫的分析工具所實函數。|  
  
## <a name="remarks"></a>備註  
 分析工具會呼叫 `ICorProfilerInfo2` 介面中的方法，以便與 CLR 通訊以控制事件監視和要求資訊。  
  
 `ICorProfilerInfo2` 介面的方法是由 CLR 使用自由執行緒模型來執行。 每個方法會傳回 HRESULT，表示成功或失敗。 如需可能的傳回程式碼清單，請參閱 CorError.h 檔案。  
  
 CLR 會在初始化期間，流量分析工具的[ICorProfilerCallback：： Initialize](icorprofilercallback-initialize-method.md)的執行，將 `ICorProfilerInfo2` 介面傳遞給每個程式碼 profiler。 然後，程式碼分析工具可以呼叫 `ICorProfilerInfo2` 介面的方法，以取得在 CLR 控制下執行之 managed 程式碼的相關資訊。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [分析介面](profiling-interfaces.md)
- [ICorProfilerInfo 介面](icorprofilerinfo-interface.md)
