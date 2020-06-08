---
title: ICorProfilerFunctionControl::SetILFunctionBody 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerFunctionControl::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: 2c33f0f7-75b2-4c19-b2c7-c94b54997576
topic_type:
- apiref
ms.openlocfilehash: a6b24fd59a183a4a59b117663772417d55cc67db
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503132"
---
# <a name="icorprofilerfunctioncontrolsetilfunctionbody-method"></a>ICorProfilerFunctionControl::SetILFunctionBody 方法
取代方法的 Common Intermediate Language (CIL) 主體。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetILFunctionBody(  
    [in]  ULONG   cbNewILMethodHeader,  
    [in, size_is(cbNewILMethodHeader)] LPCBYTE pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a>參數  
 `cbNewILMethodHeader`  
 [in] 新 CIL 的大小總計，包括主體後面的標頭和任何結構。  
  
 `pbNewILMethodHeader`  
 [in] 新 CIL 標頭的指標。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT。  
  
|HRESULT|說明|  
|-------------|-----------------|  
|S_OK|取代成功。|  
  
## <a name="remarks"></a>備註  
 不同于[ICorProfilerInfo：： SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md)方法， `SetILFunctionBody` 方法會管理新的 CIL 主體所需的記憶體。 這表示分析工具所提供的 CIL 主體不需要使用[IMethodMalloc](imethodmalloc-interface.md)介面來配置，或在特定範圍內配置。 它可以配置於任何堆積上。 分析工具可以在傳回之後釋放用於其 CIL 主體的記憶體 `SetILFunctionBody` 。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerFunctionControl 介面](icorprofilerfunctioncontrol-interface.md)
