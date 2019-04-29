---
title: COR_PRF_TRANSITION_REASON 列舉
ms.date: 03/30/2017
api_name:
- COR_PRF_TRANSITION_REASON
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_TRANSITION_REASON
helpviewer_keywords:
- COR_PRF_TRANSITION_REASON enumeration [.NET Framework profiling]
ms.assetid: da941118-01b7-4197-ae5b-9f2f8adcd623
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2556196b7c8f81709e6880962e8ff36e126dd8b0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61599035"
---
# <a name="corprftransitionreason-enumeration"></a>COR_PRF_TRANSITION_REASON 列舉
指出從 Managed 程式碼轉換為 Unmanaged 程式碼 (反之亦然) 的原因。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum {  
    COR_PRF_TRANSITION_CALL,  
    COR_PRF_TRANSITION_RETURN  
} COR_PRF_TRANSITION_REASON;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`COR_PRF_TRANSITION_CALL`|轉換是因為呼叫函式。|  
|`COR_PRF_TRANSITION_RETURN`|轉換是因為從函式傳回。|  
  
## <a name="remarks"></a>備註  
 轉換時，分析工具收到[icorprofilercallback:: Managedtounmanagedtransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md)或是[icorprofilercallback:: Unmanagedtomanagedtransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md)回呼，兩者都提供的值`COR_PRF_TRANSITION_REASON`列舉型別來表示轉換的原因。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
