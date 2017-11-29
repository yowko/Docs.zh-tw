---
title: "ICorProfilerInfo2 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2
helpviewer_keywords: ICorProfilerInfo2 interface [.NET Framework profiling]
ms.assetid: 91bd49b6-4d12-494f-a8f1-2f251e8c65e3
topic_type: apiref
caps.latest.revision: "21"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cbc0b4ad46c6a49313a42c4c232873988e7f4e99
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2-interface"></a>ICorProfilerInfo2 介面
提供程式碼分析工具用於和 common language runtime (CLR)，以控制事件監視以及要求資訊通訊的方法。 `ICorProfilerInfo2`介面是延伸[ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)介面。 也就是說，它會提供.NET Framework 2.0 版及更新版本中支援的新方法。  
  
## <a name="methods"></a>方法  
  
|方法|說明|  
|------------|-----------------|  
|[DoStackSnapshot 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)|查核 managed 的呼叫框架報告給分析工具指定執行緒的堆疊。|  
|[EnumModuleFrozenObjects 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-enummodulefrozenobjects-method.md)|取得允許反覆項目所指定模組中凍結物件的列舉值。|  
|[GetAppDomainStaticAddress 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getappdomainstaticaddress-method.md)|取得位於指定的應用程式定義域的範圍內指定的應用程式定義域靜態欄位的位址。|  
|[GetArrayObjectInfo 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getarrayobjectinfo-method.md)|取得有關陣列物件的詳細的資訊。|  
|[GetBoxClassLayout 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getboxclasslayout-method.md)|取得指定的值型別，會進行 boxed 處理的類別配置資訊。|  
|[GetClassFromTokenAndTypeArgs 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)|取得`ClassID`使用指定的中繼資料語彙基元的類型和`ClassID`值的任何型別引數。|  
|[GetClassIDInfo2 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md)|取得父模組指定的泛型類別，類別、 中繼資料語彙基元`ClassID`其父類別，而`ClassID`如果有的話，類別的每個型別引數。|  
|[GetClassLayout 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclasslayout-method.md)|取得在記憶體中指定類別所定義欄位的配置相關資訊。 也就是說，這個方法會取得此類別的欄位之位移。|  
|[GetCodeInfo2 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)|取得與指定 `FunctionID` 相關聯的原生程式碼範圍。|  
|[GetContextStaticAddress 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcontextstaticaddress-method.md)|取得位於指定之內容的範圍內指定 context 靜態欄位的位址。|  
|[GetFunctionFromTokenAndTypeArgs 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)|取得`FunctionID`函式，使用指定的中繼資料語彙基元，包含類別，來和`ClassID`值的任何型別引數。|  
|[GetFunctionInfo2 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)|取得函式的父類別、中繼資料語彙基元和每個類型引數的 `ClassID` (如果有的話)。|  
|[GetGenerationBounds 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getgenerationbounds-method.md)|取得記憶體區域 （堆積的區段） 之層代的記憶體回收堆積所組成。|  
|[GetNotifiedExceptionClauseInfo 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)|取得例外狀況子句的原生位址和框架資訊 (`catch`/`finally`/`filter`) 是即將執行或剛執行。|  
|[GetObjectGeneration 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getobjectgeneration-method.md)|取得包含指定的物件在堆積的區段。|  
|[GetRVAStaticAddress 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getrvastaticaddress-method.md)|取得指定之相對虛擬位址 (RVA) 位址的靜態欄位。|  
|[GetStaticFieldInfo 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstaticfieldinfo-method.md)|取得指定的欄位是靜態的範圍。|  
|[GetStringLayout 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md)|取得字串物件配置的相關資訊。|  
|[GetThreadAppDomain 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadappdomain-method.md)|取得在其中指定的執行緒目前正在執行程式碼的應用程式定義域的 ID。|  
|[GetThreadStaticAddress 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadstaticaddress-method.md)|取得指定執行緒的範圍內指定執行緒靜態欄位的位址。|  
|[SetEnterLeaveFunctionHooks2 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)|指定程式碼剖析工具實作函式上 「 輸入 」、 「 保留 」 和 「 tailcall"攔截 managed 函式的呼叫。|  
  
## <a name="remarks"></a>備註  
 程式碼剖析工具呼叫中的方法`ICorProfilerInfo2`與 CLR 以控制事件監視及要求資訊進行通訊的介面。  
  
 方法的`ICorProfilerInfo2`介面由使用無限制執行緒模型的 CLR 實作。 每個方法會傳回 HRESULT，表示成功或失敗。 如需可能的傳回程式碼清單，請參閱 CorError.h 檔案。  
  
 CLR 會傳遞`ICorProfilerInfo2`介面，以每個程式碼分析工具在初始化期間，使用程式碼剖析工具實作[icorprofilercallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)。 接著程式碼分析工具可以呼叫的方法`ICorProfilerInfo2`介面，以取得在 CLR 的控制項下執行的 managed 程式碼的相關資訊。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [分析介面](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [ICorProfilerInfo 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
