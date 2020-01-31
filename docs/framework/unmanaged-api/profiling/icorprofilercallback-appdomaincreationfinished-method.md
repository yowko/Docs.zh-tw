---
title: ICorProfilerCallback::AppDomainCreationFinished 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainCreationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainCreationFinished
helpviewer_keywords:
- AppDomainCreationFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainCreationFinished method [.NET Framework profiling]
ms.assetid: dbab7d90-d515-4dc9-8195-294d5d04bab6
topic_type:
- apiref
ms.openlocfilehash: 1cf3f2b62b388b6c2d6fcd75b1b07a67d5b2e49f
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866698"
---
# <a name="icorprofilercallbackappdomaincreationfinished-method"></a>ICorProfilerCallback::AppDomainCreationFinished 方法
通知分析工具已建立應用程式域。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT AppDomainCreationFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);   
```  
  
## <a name="parameters"></a>參數

- `appDomainId`

  中的 \[] 可識別已建立的網域。

- `hrStatus`

  \[in]） HRESULT，指出應用程式域的建立是否已順利完成。

## <a name="remarks"></a>備註  
 在呼叫 `AppDomainCreationFinished` 方法之前，應用程式識別碼對任何資訊要求而言都是不正確。  
  
 載入應用程式域的某些部分可能會在 `AppDomainCreationFinished` 回呼之後繼續進行。 `hrStatus` 中的失敗 HRESULT 表示失敗。 不過，`hrStatus` 中的成功 HRESULT 只會指出建立應用程式域的第一個部分已成功。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
