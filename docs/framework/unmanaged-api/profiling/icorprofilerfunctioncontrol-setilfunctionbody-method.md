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
ms.openlocfilehash: bebc0cf6ac7912ea3a6641e0c729b759e865dac3
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864657"
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
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|取代成功。|  
  
## <a name="remarks"></a>備註  
 不同于[ICorProfilerInfo：： SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md)方法，`SetILFunctionBody` 方法會管理新的 CIL 主體所需的記憶體。 這表示分析工具所提供的 CIL 主體不需要使用[IMethodMalloc](imethodmalloc-interface.md)介面來配置，或在特定範圍內配置。 它可以配置於任何堆積上。 分析工具可以在 `SetILFunctionBody` 傳回之後釋放用於其 CIL 主體的記憶體。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerFunctionControl 介面](icorprofilerfunctioncontrol-interface.md)
