---
title: ICorProfilerObjectEnum::Skip 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.Skip
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::Skip
helpviewer_keywords:
- ICorProfilerObjectEnum::Skip method [.NET Framework profiling]
- Skip method, ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: f8e498f8-f93a-4b82-bd22-55bdbf5e8d45
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b5818cb8d7da7415feb61532799df5fa5a16fd3b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781221"
---
# <a name="icorprofilerobjectenumskip-method"></a>ICorProfilerObjectEnum::Skip 方法
將這個列舉值的資料指標從其目前位置前移，以略過指定的數目的項目。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
## <a name="parameters"></a>參數  
 `celt`  
 [in]略過的項目數目。  
  
## <a name="remarks"></a>備註  
 此列舉值的資料指標的新位置是: （目前的位置） + `celt` 。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerObjectEnum 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
