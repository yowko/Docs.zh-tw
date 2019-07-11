---
title: COR_PRF_RUNTIME_TYPE 列舉
ms.date: 03/30/2017
api_name:
- COR_PRF_RUNTIME_TYPE Enumeration
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_RUNTIME_TYPE
helpviewer_keywords:
- COR_PRF_RUNTIME_TYPE enumeration [.NET Framework profiling]
ms.assetid: 35449514-333f-4918-9c60-7aa198d655d2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6c52f96ad9458dfd5cdedc5cc73154aa570c6759
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751972"
---
# <a name="corprfruntimetype-enumeration"></a>COR_PRF_RUNTIME_TYPE 列舉
包含值，表示 common language runtime (CLR) 版本： 桌面或 CoreCLR，Silverlight 中使用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum  
{  
    COR_PRF_DESKTOP_CLR = 0x1,  
    COR_PRF_CORE_CLR    = 0x2,  
} COR_PRF_RUNTIME_TYPE;  
```  
  
## <a name="members"></a>成員  
  
|成員|說明|  
|------------|-----------------|  
|`COR_PRF_DESKTOP_CLR`|桌面 CLR 的版本。|  
|`COR_PRF_CORE_CLR`|使用 Silverlight 中的 CLR 核心版本。|  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [分析列舉](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
