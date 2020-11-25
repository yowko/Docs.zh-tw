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
ms.openlocfilehash: 5290db008bfe5727ed5899c2ed6f7e41ae9a353a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716352"
---
# <a name="cor_prf_snapshot_info-enumeration"></a>COR_PRF_SNAPSHOT_INFO 列舉

指定每次呼叫程式碼剖析工具的 [StackSnapshotCallback](stacksnapshotcallback-function.md) 函式時，要傳回的資料量與堆疊快照集。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum _COR_PRF_SNAPSHOT_INFO {  
    COR_PRF_SNAPSHOT_DEFAULT = 0x0,  
    COR_PRF_SNAPSHOT_REGISTER_CONTEXT = 0x1,  
    COR_PRF_SNAPSHOT_X86_OPTIMIZED = 0X2  
} COR_PRF_SNAPSHOT_INFO;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|-------------|-----------------|  
|`COR_PRF_SNAPSHOT_DEFAULT`|指出必須傳遞所有參數的值 `StackSnapshotCallback` ，但 `context` 參數除外。|  
|`COR_PRF_SNAPSHOT_REGISTER_CONTEXT`|指出必須傳遞所有參數的值 `StackSnapshotCallback` ，包括 `context` 參數。|  
|`COR_PRF_SNAPSHOT_X86_OPTIMIZED`|指出將使用較簡單的替代堆疊流覽演算法。|  
  
## <a name="remarks"></a>備註  

 列舉所提供的值 `COR_PRF_SNAPSHOT_INFO` 會以參數形式傳遞至 [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) 方法。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [DoStackSnapshot 方法](icorprofilerinfo2-dostacksnapshot-method.md)
- [分析列舉](profiling-enumerations.md)
