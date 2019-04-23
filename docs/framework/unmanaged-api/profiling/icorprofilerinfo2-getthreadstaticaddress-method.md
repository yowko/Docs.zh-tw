---
title: ICorProfilerInfo2::GetThreadStaticAddress 方法
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e8a842dd531576b1029c3924d12b1a4bd95bde37
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59115202"
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
  
## <a name="parameters"></a>參數  
 `classId`  
 [in]包含要求的執行緒靜態欄位的類別識別碼。  
  
 `fieldToken`  
 [in]要求的執行緒靜態欄位的中繼資料語彙基元。  
  
 `threadId`  
 [in]要求的靜態欄位的範圍的執行緒識別碼。  
  
 `ppAddress`  
 [out]位於指定的執行緒靜態欄位的位址指標。  
  
## <a name="remarks"></a>備註  
 `GetThreadStaticAddress`方法可能會傳回下列其中之一：  
  
-   如果指定的靜態欄位尚未指派指定的內容中的地址 CORPROF_E_DATAINCOMPLETE HRESULT。  
  
-   可能在記憶體回收堆積中物件的位址。 記憶體回收之後，這些位址可能會失效之後記憶體回收集合程式碼剖析工具不應該假設其是否有效。  
  
 類別的類別建構函式完成之前，`GetThreadStaticAddress`雖然靜態欄位的一些可能已經初始化，將會傳回 CORPROF_E_DATAINCOMPLETE 所有其靜態欄位，及根廢棄項目集合物件。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
