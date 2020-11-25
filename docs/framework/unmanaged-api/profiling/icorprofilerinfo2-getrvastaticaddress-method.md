---
title: ICorProfilerInfo2::GetRVAStaticAddress 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetRVAStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetRVAStaticAddress
helpviewer_keywords:
- GetRVAStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetRVAStaticAddress method [.NET Framework profiling]
ms.assetid: a25a8f8b-5cfa-440d-9376-a1a1c3a9fc11
topic_type:
- apiref
ms.openlocfilehash: ea4f6f129cf2919124b1bef1fd837f2b1e13760e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727051"
---
# <a name="icorprofilerinfo2getrvastaticaddress-method"></a>ICorProfilerInfo2::GetRVAStaticAddress 方法

取得指定的相對虛擬位址 (RVA) 靜態欄位的位址。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetRVAStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a>參數  

 `classId`  
 在包含所要求之 RVA 靜態欄位之類別的識別碼。  
  
 `fieldToken`  
 在要求的 RVA-靜態欄位的元資料標記。  
  
 `ppAddress`  
 擴展RVA-靜態欄位的位址指標。  
  
## <a name="remarks"></a>備註  

 `GetRVAStaticAddress`方法可能會傳回下列其中一項：  
  
- 如果指定的靜態欄位未在指定的內容中指派位址，則為 CORPROF_E_DATAINCOMPLETE HRESULT。  
  
- 可能位於垃圾收集堆積中之物件的位址。 這些位址在垃圾收集之後可能會失效，因此在垃圾收集之後，分析工具不應假設它們是有效的。  
  
 在類別的類別的函式完成之前， `GetRVAStaticAddress` 將會傳回其所有靜態欄位的 CORPROF_E_DATAINCOMPLETE，雖然某些靜態欄位可能已經初始化，而且可能是根垃圾收集物件。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo 介面](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 介面](icorprofilerinfo2-interface.md)
