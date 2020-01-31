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
ms.openlocfilehash: 05d8c44655d8670194035c336bd62ae5d53bfec3
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862959"
---
# <a name="icorprofilerinfo2getappdomainstaticaddress-method"></a>ICorProfilerInfo2::GetAppDomainStaticAddress 方法
取得指定的應用程式域靜態欄位的位址，該欄位位於指定的應用程式域範圍內。  
  
## <a name="syntax"></a>語法  
  
```cpp  
RESULT GetAppDomainStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] AppDomainID appDomainId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a>參數  
 `classId`  
 在包含所要求應用程式域靜態欄位之類別的類別 ID。  
  
 `fieldToken`  
 在所要求之應用程式域靜態欄位的元資料標記。  
  
 `appDomainId`  
 在應用程式域的識別碼，這是要求的靜態欄位範圍。  
  
 `ppAddress`  
 脫銷指定之應用程式域內靜態欄位位址的指標。  
  
## <a name="remarks"></a>備註  
 `GetAppDomainStaticAddress` 方法可能會傳回下列其中一項：  
  
- 如果未在指定的內容中指派位址給給定的靜態欄位，CORPROF_E_DATAINCOMPLETE HRESULT。  
  
- 可能位於垃圾收集堆積中之物件的位址。 這些位址在垃圾收集後可能會變成無效，因此在垃圾收集之後，分析工具不應假設它們是有效的。  
  
 在類別的類別的函式完成之前，`GetAppDomainStaticAddress` 將會傳回其所有靜態欄位的 CORPROF_E_DATAINCOMPLETE，雖然某些靜態欄位可能已經初始化，並且會對垃圾收集物件進行根。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerInfo 介面](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 介面](icorprofilerinfo2-interface.md)
