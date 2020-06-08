---
title: ICorProfilerObjectEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.Next
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::Next
helpviewer_keywords:
- Next method, ICorProfilerObjectEnum interface [.NET Framework profiling]
- ICorProfilerObjectEnum::Next method [.NET Framework profiling]
ms.assetid: b420433c-5ebe-4986-bba1-97902e6db819
topic_type:
- apiref
ms.openlocfilehash: 850f05520e4146b5016bb574f02aa800dfcaaf32
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494575"
---
# <a name="icorprofilerobjectenumnext-method"></a>ICorProfilerObjectEnum::Next 方法
從序列中列舉值的目前位置開始，從物件的連續集合中取得指定的連續物件數目。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Next (  
    [in] ULONG                    celt,  
    [out, size_is(celt), length_is(*pceltFetched)]
        ObjectID                  objects[],  
    [out] ULONG                   *pceltFetched  
);  
```  
  
## <a name="parameters"></a>參數  
 `celt`  
 [in] 要擷取的物件數目。  
  
 `objects`  
 脫銷值的陣列 `ObjectID` ，其中每一個都代表抓取的物件。  
  
 `pceltFetched`  
 [out] `objects` 陣列中實際傳回之項目數目的指標。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerObjectEnum 介面](icorprofilerobjectenum-interface.md)
