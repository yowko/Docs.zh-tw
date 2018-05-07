---
title: COR_PRF_GC_GENERATION_RANGE 結構
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_GENERATION_RANGE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_GENERATION_RANGE
helpviewer_keywords:
- COR_PRF_GC_GENERATION_RANGE structure [.NET Framework profiling]
ms.assetid: e7e07273-8d10-4a68-807e-59634e3f8c5e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1f4c8e9a7ce5eddde18c1266cb724d5c3b0d5f41
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="corprfgcgenerationrange-structure"></a>COR_PRF_GC_GENERATION_RANGE 結構
說明正在進行記憶體回收的記憶體範圍 (亦即區塊)。  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct COR_PRF_GC_GENERATION_RANGE {  
    COR_PRF_GC_GENERATION generation;  
    ObjectID rangeStart;  
    UINT_PTR rangeLength;  
    UINT_PTR rangeLengthReserved;  
} COR_PRF_GC_GENERATION_RANGE;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`generation`|值為[COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md)所屬列舉，指定要產生的記憶體區塊。|  
|`rangeStart`|指定的記憶體區塊的起始位置的物件識別碼。|  
|`rangeLength`|指定使用的記憶體區塊 （也就是在區塊內使用的記憶體數量） 部分的大小的整數指標。|  
|`rangeLengthReserved`|指定的記憶體區塊 （也就是保留的區塊的記憶體數量） 大小的整數指標。|  
  
## <a name="remarks"></a>備註  
 `rangeLength`保證是精確值只有當[icorprofilerinfo2:: Getgenerationbounds](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getgenerationbounds-method.md)或[icorprofilerinfo2:: Getobjectgeneration](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getobjectgeneration-method.md)，這兩個其中使用`COR_PRF_GC_GENERATION_RANGE`結構，請從呼叫[icorprofilercallback2:: Garbagecollectionstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)或[icorprofilercallback2:: Garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)方法。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [分析結構](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
