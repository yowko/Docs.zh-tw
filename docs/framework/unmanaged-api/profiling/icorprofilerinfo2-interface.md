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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4623fecd210ac716824fdc5fede99ec40145e8d5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498865"
---
# <a name="icorprofilerinfo2-interface"></a>ICorProfilerInfo2 介面
提供程式碼分析工具使用與通用語言執行平台 (CLR)，以控制事件監視以及要求資訊進行通訊的方法。 `ICorProfilerInfo2`介面是擴充功能[ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)介面。 也就是說，它提供.NET Framework 2.0 版及更新版本中支援的新方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[DoStackSnapshot 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)|將逐步引導至分析工具報告受管理的呼叫框架指定執行緒的堆疊。|  
|[EnumModuleFrozenObjects 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-enummodulefrozenobjects-method.md)|取得可反覆項目讓您透過指定的模組中的凍結物件的列舉值。|  
|[GetAppDomainStaticAddress 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getappdomainstaticaddress-method.md)|取得在指定的應用程式定義域的範圍中指定的應用程式定義域靜態欄位的位址。|  
|[GetArrayObjectInfo 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getarrayobjectinfo-method.md)|取得與陣列物件有關的詳細的資訊。|  
|[GetBoxClassLayout 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getboxclasslayout-method.md)|取得會進行 boxed 處理指定實值類型的類別配置的相關資訊。|  
|[GetClassFromTokenAndTypeArgs 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)|取得`ClassID`使用指定的中繼資料語彙基元型別和`ClassID`值的任何型別引數。|  
|[GetClassIDInfo2 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md)|取得父模組指定的泛型類別，此類別中，中繼資料語彙基元`ClassID`其父類別和`ClassID`如果有的話，類別的每個類型引數。|  
|[GetClassLayout 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclasslayout-method.md)|取得在記憶體中指定類別所定義欄位的配置相關資訊。 也就是說，這個方法會取得此類別的欄位之位移。|  
|[GetCodeInfo2 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)|取得與指定 `FunctionID` 相關聯的原生程式碼範圍。|  
|[GetContextStaticAddress 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcontextstaticaddress-method.md)|取得位於指定之內容的範圍內的指定內容靜態欄位的位址。|  
|[GetFunctionFromTokenAndTypeArgs 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)|取得`FunctionID`函式使用指定的中繼資料語彙基元，包含類別，和`ClassID`值的任何型別引數。|  
|[GetFunctionInfo2 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)|取得函式的父類別、中繼資料語彙基元和每個型別引數的 `ClassID` (如果有的話)。|  
|[GetGenerationBounds 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getgenerationbounds-method.md)|取得構成的記憶體回收堆積的層代的記憶體區域 （堆積的區段）。|  
|[GetNotifiedExceptionClauseInfo 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)|取得例外狀況子句的原生位址及畫面格資訊 (`catch`/`finally`/`filter`) 是要執行或剛執行。|  
|[GetObjectGeneration 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getobjectgeneration-method.md)|取得包含指定的物件堆積的區段。|  
|[GetRVAStaticAddress 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getrvastaticaddress-method.md)|取得指定之相對虛擬位址 (RVA) 位址-靜態欄位。|  
|[GetStaticFieldInfo 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstaticfieldinfo-method.md)|取得指定的欄位是靜態的範圍。|  
|[GetStringLayout 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md)|取得字串物件配置的相關資訊。|  
|[GetThreadAppDomain 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadappdomain-method.md)|取得指定的執行緒目前執行所在的程式碼之應用程式定義域的 ID。|  
|[GetThreadStaticAddress 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadstaticaddress-method.md)|取得指定執行緒的範圍內指定執行緒靜態欄位的位址。|  
|[SetEnterLeaveFunctionHooks2 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)|指定要呼叫 「 輸入 」、 「 保留 」 和 「 tailcall"勾點的受管理的函式的分析工具實作函式。|  
  
## <a name="remarks"></a>備註  
 程式碼剖析工具呼叫中的方法`ICorProfilerInfo2`CLR 控制事件監視以及要求資訊與通訊的介面。  
  
 方法的`ICorProfilerInfo2`介面由 CLR 使用無限制執行緒模型。 每個方法會傳回 HRESULT，表示成功或失敗。 如需可能的傳回程式碼清單，請參閱 CorError.h 檔案。  
  
 CLR 會傳遞`ICorProfilerInfo2`每個程式碼分析工具在初始化期間，使用分析工具的實作的介面[icorprofilercallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)。 程式碼剖析工具接著可以呼叫的方法`ICorProfilerInfo2`介面，以取得正在執行的 CLR 控制下的 managed 程式碼的相關資訊。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [分析介面](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerInfo 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
