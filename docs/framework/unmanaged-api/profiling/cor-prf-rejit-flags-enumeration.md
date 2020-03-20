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
ms.openlocfilehash: 8fc5f1a488826d8adc6aecb8ef122609bebbe813
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177104"
---
# <a name="cor_prf_rejit_flags-enumeration"></a>COR_PRF_REJIT_FLAGS 列舉
包含指示[ICorProfilerInfo10：：請求 ReJITWithinliners](icorprofilerinfo10-requestrejitwithinliners-method.md) API 應如何使用的值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum  
{
    COR_PRF_REJIT_BLOCK_INLINING = 0x1,
    COR_PRF_REJIT_INLINING_CALLBACKS    = 0x2
} COR_PRF_REJIT_FLAGS;  
```  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`COR_PRF_REJIT_BLOCK_INLINING`| 重新 JITed 方法將阻止在其他方法中內聯。 |  
|`COR_PRF_REJIT_INLINING_CALLBACKS`| 接收`GetFunctionParameters`任何內聯請求重新JITted的方法的方法的回檔。 |  

## <a name="requirements"></a>需求  
 **平臺：** 請參閱[.NET Core 支援的作業系統](../../../core/install/dependencies.md?pivots=os-windows)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET 框架版本：**[!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]
  
## <a name="see-also"></a>另請參閱

- [分析列舉](profiling-enumerations.md)
