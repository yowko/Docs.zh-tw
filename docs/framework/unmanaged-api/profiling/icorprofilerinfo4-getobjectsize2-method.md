---
title: ICorProfilerInfo4::GetObjectSize2 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetObjectSize2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetObjectSize2
helpviewer_keywords:
- GetObjectSize2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetObjectSize2 method [.NET Framework profiling]
ms.assetid: 4a3e43ed-3ee3-4395-ab14-f78b903be13e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8ebbc3422f48c0c2b8ff7b807228c63fbb35dd7b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo4getobjectsize2-method"></a>ICorProfilerInfo4::GetObjectSize2 方法
傳回指定之物件的大小。 取代[icorprofilerinfo:: Getobjectsize](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md)報告大於中能表示的物件大小的方法`ULONG`。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetObjectSize2(  
    [in]  ObjectID objectId,  
    [out] SIZE_T *pcSize);  
```  
  
#### <a name="parameters"></a>參數  
 `objectId`  
 [in]物件的識別碼。  
  
 `pcSize`  
 [out]物件的大小 （位元組） 指標。  
  
## <a name="remarks"></a>備註  
 相同的類型不同的物件通常會有相同的大小。 不過，某些類型，例如陣列或字串，可能必須針對每個物件的大小不同。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorProfilerInfo4 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
