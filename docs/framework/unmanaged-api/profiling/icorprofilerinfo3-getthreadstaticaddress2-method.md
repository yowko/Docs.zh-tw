---
title: ICorProfilerInfo3::GetThreadStaticAddress2 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetThreadStaticAddress2 Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetThreadStaticAddress2
helpviewer_keywords:
- ICorProfilerInfo3::GetThreadStaticAddress2 method [.NET Framework profiling]
- GetThreadStaticAddress2 method [.NET Framework profiling]
ms.assetid: a9608861-ae64-4467-8a73-be05ad34beac
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 85f3ec6c2e0e452d3410437a7ec7cd45eb38cd5a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779844"
---
# <a name="icorprofilerinfo3getthreadstaticaddress2-method"></a>ICorProfilerInfo3::GetThreadStaticAddress2 方法
取得指定執行緒靜態欄位的位址，這位於指定之執行緒和應用程式定義域的範圍內。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetThreadStaticAddress2(  
                [in] ClassID classId,  
                [in] mdFieldDef fieldToken,  
                [in] AppDomainID appDomainId,  
                [in] ThreadID threadId,  
                [out] void **ppAddress);  
```  
  
## <a name="parameters"></a>參數  
 `classId`  
 [in]包含要求的執行緒靜態欄位的類別識別碼。  
  
 `fieldToken`  
 [in]要求的執行緒靜態欄位的中繼資料語彙基元。  
  
 `appDomainId`  
 [in] 應用程式定義域的 ID。  
  
 `threadId`  
 [in]要求的靜態欄位的範圍的執行緒識別碼。  
  
 `ppAddress`  
 [out]位於指定的執行緒靜態欄位的位址指標。  
  
## <a name="remarks"></a>備註  
 `GetThreadStaticAddress2`方法可能會傳回下列其中之一：  
  
- 如果指定的靜態欄位尚未指派指定的內容中的地址 CORPROF_E_DATAINCOMPLETE HRESULT。  
  
- 可能在記憶體回收堆積中物件的位址。 這些位址可能會變成無效記憶體回收之後，讓記憶體回收之後, 程式碼剖析工具不應該假設其有效。  
  
 類別的類別建構函式完成之前，`GetThreadStaticAddress2`雖然靜態欄位的一些可能已經初始化，將會傳回 CORPROF_E_DATAINCOMPLETE 所有其靜態欄位，及根廢棄項目集合物件。  
  
 [ICorProfilerInfo2::GetThreadStaticAddress](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadstaticaddress-method.md)方式類似於`GetThreadStaticAddress2`方法，但不是接受應用程式網域引數。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo3 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [分析介面](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [程式碼剖析](../../../../docs/framework/unmanaged-api/profiling/index.md)
