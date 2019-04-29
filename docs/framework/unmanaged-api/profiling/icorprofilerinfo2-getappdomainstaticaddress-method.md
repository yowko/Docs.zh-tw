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
ms.openlocfilehash: 2095f02cb23c3580b0a1109e8f0da669f61adabc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789385"
---
# <a name="icorprofilerinfo2getappdomainstaticaddress-method"></a>ICorProfilerInfo2::GetAppDomainStaticAddress 方法
取得在指定的應用程式定義域的範圍中指定的應用程式定義域靜態欄位的位址。  
  
## <a name="syntax"></a>語法  
  
```  
RESULT GetAppDomainStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] AppDomainID appDomainId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a>參數  
 `classId`  
 [in]包含要求的應用程式定義域靜態欄位的類別類別識別碼。  
  
 `fieldToken`  
 [in]要求的應用程式定義域靜態欄位的中繼資料語彙基元。  
  
 `appDomainId`  
 [in]應用程式定義域所要求的靜態欄位的範圍識別碼。  
  
 `ppAddress`  
 [out]指定的應用程式網域內的靜態欄位的位址指標。  
  
## <a name="remarks"></a>備註  
 `GetAppDomainStaticAddress`方法可能會傳回下列其中之一：  
  
- 如果指定的靜態欄位尚未指派指定的內容中的地址 CORPROF_E_DATAINCOMPLETE HRESULT。  
  
- 可能在記憶體回收堆積中物件的位址。 這些位址可能會變成無效記憶體回收之後，讓記憶體回收之後, 程式碼剖析工具不應該假設其有效。  
  
 類別的類別建構函式完成之前，`GetAppDomainStaticAddress`雖然靜態欄位的一些可能已經初始化，將會傳回 CORPROF_E_DATAINCOMPLETE 所有其靜態欄位，及根廢棄項目集合物件。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
