---
title: COR_PRF_SNAPSHOT_INFO 列舉
ms.date: 03/30/2017
api_name:
- COR_PRF_SNAPSHOT_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_SNAPSHOT_INFO
helpviewer_keywords:
- COR_PRF_SNAPSHOT_INFO enumeration [.NET Framework profiling]
ms.assetid: a5906b2a-ad4a-4cc6-a421-2d7d8adf7468
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9d6713a7f54f6a6d8dbf261ad45304e6ddbe24c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="corprfsnapshotinfo-enumeration"></a>COR_PRF_SNAPSHOT_INFO 列舉
指定要傳遞的資料量隨同堆疊中的快照集每次呼叫程式碼剖析工具[StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md)函式。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum _COR_PRF_SNAPSHOT_INFO {  
    COR_PRF_SNAPSHOT_DEFAULT = 0x0,  
    COR_PRF_SNAPSHOT_REGISTER_CONTEXT = 0x1,  
    COR_PRF_SNAPSHOT_X86_OPTIMIZED = 0X2  
} COR_PRF_SNAPSHOT_INFO;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|-------------|-----------------|  
|`COR_PRF_SNAPSHOT_DEFAULT`|表示值必須針對所有傳遞`StackSnapshotCallback`參數，除了`context`參數。|  
|`COR_PRF_SNAPSHOT_REGISTER_CONTEXT`|表示值必須針對所有傳遞`StackSnapshotCallback`參數，包括`context`參數。|  
|`COR_PRF_SNAPSHOT_X86_OPTIMIZED`|表示將會使用更簡單、 替代的堆疊查核行程演算法。|  
  
## <a name="remarks"></a>備註  
 所提供的值`COR_PRF_SNAPSHOT_INFO`列舉型別會當做參數傳遞給[DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)方法。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [DoStackSnapshot 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)  
 [分析列舉](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
