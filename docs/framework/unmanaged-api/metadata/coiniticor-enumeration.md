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
ms.openlocfilehash: ef7851ddb33003b0b4b51065cf1fea3696ca6abd
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005943"
---
# <a name="coiniticor-enumeration"></a>COINITICOR 列舉
指定在初始化 common language runtime 時， [CoInitializeCor](../hosting/coinitializecor-function.md)所使用的常數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum tagCOINITCOR  
{  
    COINITCOR = 0x0  
} COINITICOR;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`COINITCOR`|表示預設初始化模式。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](metadata-enumerations.md)
