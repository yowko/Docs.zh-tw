---
title: ICorProfilerInfo2::GetContextStaticAddress 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetContextStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetContextStaticAddress
helpviewer_keywords:
- GetContextStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetContextStaticAddress method [.NET Framework profiling]
ms.assetid: 2b374116-0972-416a-8cf5-79213129be9a
topic_type:
- apiref
ms.openlocfilehash: 067e5093cc3b141936eeec43e77e6e1a9475a8a6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727116"
---
# <a name="icorprofilerinfo2getcontextstaticaddress-method"></a>ICorProfilerInfo2::GetContextStaticAddress 方法

取得位於指定內容約制內之指定內容靜態欄位的位址。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetContextStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] ContextID contextId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a>參數  

 `classId`  
 在包含所要求之內容靜態欄位的類別識別碼。  
  
 `fieldToken`  
 在要求的內容靜態欄位的元資料標記。  
  
 `contextId`  
 在屬於所要求內容靜態欄位範圍的內容識別碼。  
  
 `ppAddress`  
 擴展指定內容中靜態欄位的位址指標。  
  
## <a name="remarks"></a>備註  

 `GetContextStaticAddress`方法可能會傳回下列其中一項：  
  
- 如果指定的靜態欄位未在指定的內容中指派位址，則為 CORPROF_E_DATAINCOMPLETE HRESULT。  
  
- 可能位於垃圾收集堆積中之物件的位址。 這些位址在垃圾收集之後可能會失效，因此在垃圾收集之後，分析工具不應假設它們是有效的。  
  
 在類別的類別的函式完成之前， `GetContextStaticAddress` 將會傳回其所有靜態欄位的 CORPROF_E_DATAINCOMPLETE，雖然某些靜態欄位可能已經初始化，並且會將垃圾收集物件的根。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo 介面](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 介面](icorprofilerinfo2-interface.md)
