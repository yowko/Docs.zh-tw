---
title: "ICorProfilerInfo2::GetContextStaticAddress 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetContextStaticAddress
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetContextStaticAddress
helpviewer_keywords:
- GetContextStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetContextStaticAddress method [.NET Framework profiling]
ms.assetid: 2b374116-0972-416a-8cf5-79213129be9a
topic_type: apiref
caps.latest.revision: "23"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2d206ca90b2d89ead67f419f0f4511d19d8ce110
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getcontextstaticaddress-method"></a>ICorProfilerInfo2::GetContextStaticAddress 方法
取得位於指定之內容的範圍內指定 context 靜態欄位的位址。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetContextStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] ContextID contextId,  
    [out] void **ppAddress);  
```  
  
#### <a name="parameters"></a>參數  
 `classId`  
 [in]包含要求的內容靜態欄位的類別識別碼。  
  
 `fieldToken`  
 [in]要求的內容靜態欄位中繼資料語彙基元。  
  
 `contextId`  
 [in]要求的內容靜態欄位的資料範圍的內容識別碼。  
  
 `ppAddress`  
 [out]會在指定的內容中的靜態欄位的位址指標。  
  
## <a name="remarks"></a>備註  
 `GetContextStaticAddress`方法可能會傳回下列其中之一：  
  
-   如果在指定的靜態欄位指派指定的內容中的位址 CORPROF_E_DATAINCOMPLETE HRESULT。  
  
-   可能會在記憶體回收堆積中之物件的位址。 這些位址可能會變成記憶體回收之後, 無效，所以記憶體回收之後, 程式碼剖析工具不應該假設都有效。  
  
 類別的類別建構函式完成之前，`GetContextStaticAddress`會針對其所有靜態欄位，傳回 CORPROF_E_DATAINCOMPLETE，雖然部分的靜態欄位可能已經初始化，而且為根建立記憶體回收物件。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorProfilerInfo 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
