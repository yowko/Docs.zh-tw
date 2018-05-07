---
title: ICorProfilerInfo2::GetAppDomainStaticAddress 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetAppDomainStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetAppDomainStaticAddress
helpviewer_keywords:
- ICorProfilerInfo2::GetAppDomainStaticAddress method [.NET Framework profiling]
- GetAppDomainStaticAddress method [.NET Framework profiling]
ms.assetid: 2a9e0ea7-a9e2-4817-b1c4-fcf15b215ea9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c8e1886a3e33b533eb525f5b35480a8a7d326da0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo2getappdomainstaticaddress-method"></a>ICorProfilerInfo2::GetAppDomainStaticAddress 方法
取得位於指定的應用程式定義域的範圍內指定的應用程式定義域靜態欄位的位址。  
  
## <a name="syntax"></a>語法  
  
```  
RESULT GetAppDomainStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] AppDomainID appDomainId,  
    [out] void **ppAddress);  
```  
  
#### <a name="parameters"></a>參數  
 `classId`  
 [in]包含要求的應用程式定義域靜態欄位之類別的類別 ID。  
  
 `fieldToken`  
 [in]要求的應用程式定義域靜態欄位中繼資料語彙基元。  
  
 `appDomainId`  
 [in]應用程式定義域所要求的靜態欄位的範圍 ID。  
  
 `ppAddress`  
 [out]指定應用程式定義域內的靜態欄位的位址指標。  
  
## <a name="remarks"></a>備註  
 `GetAppDomainStaticAddress`方法可能會傳回下列其中之一：  
  
-   如果在指定的靜態欄位指派指定的內容中的位址 CORPROF_E_DATAINCOMPLETE HRESULT。  
  
-   可能會在記憶體回收堆積中之物件的位址。 這些位址可能會變成記憶體回收之後, 無效，所以記憶體回收之後, 程式碼剖析工具不應該假設都有效。  
  
 類別的類別建構函式完成之前，`GetAppDomainStaticAddress`會針對其所有靜態欄位，傳回 CORPROF_E_DATAINCOMPLETE，雖然部分的靜態欄位可能已經初始化，而且為根建立記憶體回收物件。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorProfilerInfo 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
