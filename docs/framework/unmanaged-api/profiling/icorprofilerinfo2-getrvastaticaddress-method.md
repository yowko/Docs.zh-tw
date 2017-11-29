---
title: "ICorProfilerInfo2::GetRVAStaticAddress 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetRVAStaticAddress
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetRVAStaticAddress
helpviewer_keywords:
- GetRVAStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetRVAStaticAddress method [.NET Framework profiling]
ms.assetid: a25a8f8b-5cfa-440d-9376-a1a1c3a9fc11
topic_type: apiref
caps.latest.revision: "21"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 64553e8f611a8111aaaf9ababd1a7556f1192740
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getrvastaticaddress-method"></a>ICorProfilerInfo2::GetRVAStaticAddress 方法
取得指定的相對虛擬位址 (RVA) 靜態欄位的位址。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetRVAStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [out] void **ppAddress);  
```  
  
#### <a name="parameters"></a>參數  
 `classId`  
 [in]包含要求的 RVA 靜態欄位的類別識別碼。  
  
 `fieldToken`  
 [in]要求的 RVA 靜態欄位的中繼資料語彙基元。  
  
 `ppAddress`  
 [out]RVA 靜態欄位的位址指標。  
  
## <a name="remarks"></a>備註  
 `GetRVAStaticAddress`方法可能會傳回下列其中之一：  
  
-   如果在指定的靜態欄位指派指定的內容中的位址 CORPROF_E_DATAINCOMPLETE HRESULT。  
  
-   可能會在記憶體回收堆積中之物件的位址。 這些位址可能會變成記憶體回收之後, 無效，所以記憶體回收之後, 程式碼剖析工具不應該假設都有效。  
  
 類別的類別建構函式完成之前，`GetRVAStaticAddress`會針對所有的靜態欄位，傳回 CORPROF_E_DATAINCOMPLETE，雖然的靜態欄位的部分可能已初始化，且可能會為根建立的記憶體回收物件。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorProfilerInfo 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
