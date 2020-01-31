---
title: COR_PRF_REJIT_FLAGS 列舉
ms.date: 08/06/2019
api_name:
- COR_PRF_REJIT_FLAGS Enumeration
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_REJIT_FLAGS
helpviewer_keywords:
- COR_PRF_REJIT_FLAGS enumeration [.NET Framework profiling]
topic_type:
- apiref
author: davmason
ms.author: davmason
ms.openlocfilehash: fabbcd497dc2f321da90188cebbac6ed4e147492
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867083"
---
# <a name="cor_prf_rejit_flags-enumeration"></a>COR_PRF_REJIT_FLAGS 列舉
包含值，指出[ICorProfilerInfo10：： RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md) API 的行為。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum  
{      
    COR_PRF_REJIT_BLOCK_INLINING = 0x1,
    COR_PRF_REJIT_INLINING_CALLBACKS    = 0x2
} COR_PRF_REJIT_FLAGS;  
```  
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`COR_PRF_REJIT_BLOCK_INLINING`| ReJITted 方法將會被封鎖，而無法在其他方法中內嵌。 |  
|`COR_PRF_REJIT_INLINING_CALLBACKS`| 針對內嵌要求 ReJITted 之方法的任何方法，接收 `GetFunctionParameters` 回呼。 |  

## <a name="requirements"></a>需求  
 **平臺：** 請參閱[.Net Core 支援的作業系統](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)] 
  
## <a name="see-also"></a>請參閱

- [分析列舉](profiling-enumerations.md)
