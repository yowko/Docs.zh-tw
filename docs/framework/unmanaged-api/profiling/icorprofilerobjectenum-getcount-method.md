---
title: ICorProfilerObjectEnum::GetCount 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.GetCount
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::GetCount
helpviewer_keywords:
- ICorProfilerObjectEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: 166b0761-ed80-4ccd-9973-dc20e61bf8fa
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f08b3d9634362d47615fe14287ab9ec35e78ee65
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775052"
---
# <a name="icorprofilerobjectenumgetcount-method"></a>ICorProfilerObjectEnum::GetCount 方法
取得集合中的凍結物件總數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
## <a name="parameters"></a>參數  
 `pcelt`  
 [out]集合中的凍結物件的數目指標。  
  
 這個方法一律會傳回零，在.NET Framework 3.5 版 Service Pack 1 (SP1) 和更新版本。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerObjectEnum 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
