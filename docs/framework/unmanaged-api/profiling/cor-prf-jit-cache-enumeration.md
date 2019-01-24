---
title: COR_PRF_JIT_CACHE 列舉
ms.date: 03/30/2017
api_name:
- COR_PRF_JIT_CACHE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_JIT_CACHE
helpviewer_keywords:
- COR_PRF_JIT_CACHE enumeration [.NET Framework profiling]
ms.assetid: e7b8f6b4-95bc-4ba5-b9eb-f5590a7326a4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6aaa334c83aff18886c0c2db4462d6baaa4cd70f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54687410"
---
# <a name="corprfjitcache-enumeration"></a>COR_PRF_JIT_CACHE 列舉
指出快取的函式搜尋結果。  
  
> [!NOTE]
>  `COR_PRF_CACHED_FUNCTION_FOUND` 值為零，因此`COR_PRF_JIT_CACHE`不能用做為布林的 surrogate。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum {  
    COR_PRF_CACHED_FUNCTION_FOUND,  
    COR_PRF_CACHED_FUNCTION_NOT_FOUND  
} COR_PRF_JIT_CACHE;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`COR_PRF_FUNCTION_FOUND`|搜尋找不到函式。|  
|`COR_PRF_FUNCTION_NOT_FOUND`|搜尋找不到函式。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [分析列舉](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
