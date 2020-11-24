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
ms.openlocfilehash: 6c146f3deed31601411bef39ab12b52dfec8cd39
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95681571"
---
# <a name="icorprofilerinfo2-interface"></a>ICorProfilerInfo2 介面

提供程式碼分析工具用來與 common language runtime 進行通訊的方法， (CLR) 來控制事件監視和要求資訊。 `ICorProfilerInfo2`介面是[ICorProfilerInfo](icorprofilerinfo-interface.md)介面的延伸。 也就是說，它會提供 .NET Framework 2.0 版和更新版本中支援的新方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[DoStackSnapshot 方法](icorprofilerinfo2-dostacksnapshot-method.md)|逐步解說指定執行緒的堆疊，以將 managed 呼叫框架報告給分析工具。|  
|[EnumModuleFrozenObjects 方法](icorprofilerinfo2-enummodulefrozenobjects-method.md)|取得枚舉器，允許在指定模組中的凍結物件上進行反復專案。|  
|[GetAppDomainStaticAddress 方法](icorprofilerinfo2-getappdomainstaticaddress-method.md)|取得指定的應用程式域靜態欄位的位址，該欄位位於指定之應用程式域的範圍內。|  
|[GetArrayObjectInfo 方法](icorprofilerinfo2-getarrayobjectinfo-method.md)|取得陣列物件的詳細資訊。|  
|[GetBoxClassLayout 方法](icorprofilerinfo2-getboxclasslayout-method.md)|取得已封裝之指定數值型別的類別配置相關資訊。|  
|[GetClassFromTokenAndTypeArgs 方法](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)|`ClassID`使用指定的元資料標記和 `ClassID` 任何類型引數的值，取得型別的。|  
|[GetClassIDInfo2 方法](icorprofilerinfo2-getclassidinfo2-method.md)|取得指定之泛型類別的父模組、類別的元資料標記、 `ClassID` 其父類別的，以及 `ClassID` 類別的每個類型引數（如果有的話）。|  
|[GetClassLayout 方法](icorprofilerinfo2-getclasslayout-method.md)|取得在記憶體中指定類別所定義欄位的配置相關資訊。 也就是說，這個方法會取得此類別的欄位之位移。|  
|[GetCodeInfo2 方法](icorprofilerinfo2-getcodeinfo2-method.md)|取得與指定 `FunctionID` 相關聯的原生程式碼範圍。|  
|[GetContextStaticAddress 方法](icorprofilerinfo2-getcontextstaticaddress-method.md)|取得位於指定內容約制內之指定內容靜態欄位的位址。|  
|[GetFunctionFromTokenAndTypeArgs 方法](icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)|`FunctionID`使用指定的元資料標記、包含類別以及 `ClassID` 任何類型引數的值，取得函數的。|  
|[GetFunctionInfo2 方法](icorprofilerinfo2-getfunctioninfo2-method.md)|取得函式的父類別、中繼資料語彙基元和每個類型引數的 `ClassID` (如果有的話)。|  
|[GetGenerationBounds 方法](icorprofilerinfo2-getgenerationbounds-method.md)|取得記憶體區域 (堆積) 的區段，這些區段組成垃圾收集堆積的層代。|  
|[GetNotifiedExceptionClauseInfo 方法](icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)|取得例外狀況子句的原生位址和框架資訊， (`catch` / `finally` / `filter` 即將執行或剛剛執行的) 。|  
|[GetObjectGeneration 方法](icorprofilerinfo2-getobjectgeneration-method.md)|取得包含指定物件之堆積的區段。|  
|[GetRVAStaticAddress 方法](icorprofilerinfo2-getrvastaticaddress-method.md)|取得指定的相對虛擬位址 (RVA) -靜態欄位的位址。|  
|[GetStaticFieldInfo 方法](icorprofilerinfo2-getstaticfieldinfo-method.md)|取得指定之欄位為靜態的範圍。|  
|[GetStringLayout 方法](icorprofilerinfo2-getstringlayout-method.md)|取得字串物件配置的相關資訊。|  
|[GetThreadAppDomain 方法](icorprofilerinfo2-getthreadappdomain-method.md)|取得指定執行緒目前執行程式碼之應用程式域的識別碼。|  
|[GetThreadStaticAddress 方法](icorprofilerinfo2-getthreadstaticaddress-method.md)|取得指定執行緒的範圍中指定之執行緒靜態欄位的位址。|  
|[SetEnterLeaveFunctionHooks2 方法](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)|指定要在 managed 函式的 "enter"、"leave" 和 "tailcall" 攔截上呼叫的程式碼剖析工具所執行的函式。|  
  
## <a name="remarks"></a>備註  

 分析工具會在介面中呼叫方法 `ICorProfilerInfo2` ，以與 CLR 通訊以控制事件監視和要求資訊。  
  
 介面的方法 `ICorProfilerInfo2` 是使用無限制執行緒模型，由 CLR 所執行。 每個方法會傳回 HRESULT，表示成功或失敗。 如需可能的傳回程式碼清單，請參閱 CorError.h 檔案。  
  
 CLR 會在 `ICorProfilerInfo2` 初始化期間流量分析工具的 [ICorProfilerCallback：： Initialize](icorprofilercallback-initialize-method.md)來將介面傳遞至每個程式碼分析工具。 然後，程式碼分析工具可以呼叫介面的方法 `ICorProfilerInfo2` ，以取得在 CLR 控制下執行之 managed 程式碼的相關資訊。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [分析介面](profiling-interfaces.md)
- [ICorProfilerInfo 介面](icorprofilerinfo-interface.md)
