---
title: COINITICOR 列舉
ms.date: 03/30/2017
api_name:
- COINITICOR
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COINITICOR
helpviewer_keywords:
- COINITICOR enumeration [.NET Framework metadata]
ms.assetid: 67fefd89-28d6-4588-84ea-dc7a5870e014
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 89d2f9c9cfa7d4c2498710b36796f3e2605bcbf0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763656"
---
# <a name="coiniticor-enumeration"></a>COINITICOR 列舉
指定所使用的常數[CoInitializeCor](../../../../docs/framework/unmanaged-api/hosting/coinitializecor-function.md)在它初始化 common language runtime。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum tagCOINITCOR  
{  
    COINITCOR = 0x0  
} COINITICOR;  
```  
  
## <a name="members"></a>成員  
  
|成員|說明|  
|------------|-----------------|  
|`COINITCOR`|表示預設的初始化模式。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **LIBRARY:** 包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
