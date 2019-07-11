---
title: ICorProfilerInfo2::GetArrayObjectInfo 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetArrayObjectInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetArrayObjectInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetArrayObjectInfo method [.NET Framework profiling]
- GetArrayObjectInfo method [.NET Framework profiling]
ms.assetid: bda75017-739f-4ce5-9000-f3b526e8473c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3ebf8c736cdd1362cae1b1e0b734ce14bea49b18
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751894"
---
# <a name="icorprofilerinfo2getarrayobjectinfo-method"></a>ICorProfilerInfo2::GetArrayObjectInfo 方法
取得與陣列物件有關的詳細的資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetArrayObjectInfo(  
    [in] ObjectID objectId,  
    [in] ULONG32 cDimensions,  
    [out, size_is(cDimensions), length_is(cDimensions)] ULONG32 pDimensionSizes[],  
    [out, size_is(cDimensions), length_is(cDimensions)] int pDimensionLowerBounds[],  
    [out] BYTE **ppData);  
```  
  
## <a name="parameters"></a>參數  
 `objectId`  
 [in]有效的陣列物件的識別碼。  
  
 `cDimensions`  
 [in]陣列陣序 （維度數目）。  
  
 `pDimensionSizes`  
 [out]陣列，其中包含整數，每個均代表陣列的維度的大小。  
  
 `pDimensionLowerBounds`  
 [out]包含整數的陣列，表示較低的每個繫結的陣列的維度。  
  
 `ppData`  
 [out]未經處理的陣列，根據配置緩衝區的位址指標C++慣例。  
  
## <a name="remarks"></a>備註  
 `pDimensionSizes`和`pDimensionLowerBounds`是平行陣列，因此位於相同的索引，每個陣列中的項目相同的實體特性。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
