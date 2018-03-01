---
title: "ICorProfilerInfo2::GetThreadStaticAddress 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerInfo2.GetThreadStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetThreadStaticAddress
helpviewer_keywords:
- GetThreadStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetThreadStaticAddress method [.NET Framework profiling]
ms.assetid: 8e7dbf14-98a2-4384-a950-58a7640e59df
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1de945d2e6e0dd1ce3fa2da99e265bc304d4f4fc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getthreadstaticaddress-method"></a>ICorProfilerInfo2::GetThreadStaticAddress 方法
取得指定執行緒的範圍內指定執行緒靜態欄位的位址。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetThreadStaticAddress(  
    [in] ClassID     classId,  
    [in] mdFieldDef  fieldToken,  
    [in] ThreadID    threadId,  
    [out] void       **ppAddress);  
```  
  
#### <a name="parameters"></a>參數  
 `classId`  
 [in]包含要求的執行緒靜態欄位的類別識別碼。  
  
 `fieldToken`  
 [in]要求的執行緒靜態欄位中繼資料語彙基元。  
  
 `threadId`  
 [in]要求的靜態欄位的資料範圍的執行緒識別碼。  
  
 `ppAddress`  
 [out]內指定執行緒靜態欄位的位址指標。  
  
## <a name="remarks"></a>備註  
 `GetThreadStaticAddress`方法可能會傳回下列其中之一：  
  
-   如果在指定的靜態欄位指派指定的內容中的位址 CORPROF_E_DATAINCOMPLETE HRESULT。  
  
-   可能會在記憶體回收堆積中之物件的位址。 記憶體回收之後，這些位址可能會失效之後在記憶體回收集合程式碼剖析工具不應該假設都有效。  
  
 類別的類別建構函式完成之前，`GetThreadStaticAddress`會針對其所有靜態欄位，傳回 CORPROF_E_DATAINCOMPLETE，雖然部分的靜態欄位可能已經初始化，而且為根建立記憶體回收物件。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [ICorProfilerInfo 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
