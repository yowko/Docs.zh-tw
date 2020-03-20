---
title: CustomDumpItem 結構
ms.date: 03/30/2017
api_name:
- CustomDumpItem
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CustomDumpItem
helpviewer_keywords:
- CustomDumpItem structure [.NET Framework hosting]
ms.assetid: fd9085ff-7beb-4c38-97f0-037cd8ba4f65
topic_type:
- apiref
ms.openlocfilehash: 154beef9398029f31dcb4d081019b9f292238af4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176470"
---
# <a name="customdumpitem-structure"></a>CustomDumpItem 結構
描述要在錯誤報表中添加到自訂轉儲的項。  
  
## <a name="syntax"></a>語法  
  
```cpp  
struct {  
    ECustomDumpItemKind itemKind;
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`itemKind`|[ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)值，指示要添加的項類型。|  
|`pReserved`|目前無法使用。 添加到聯合的任何項必須不大於指標大小。 如果需要`struct`， 必須單獨分配並指向它。|  
  
## <a name="remarks"></a>備註  
 [ICLR錯誤報表管理器：開始自訂轉儲](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)採用類型的`CustomDumpItem`參數。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** MSCorEE.idl  
  
 **庫：** 作為資源包含在 MSCorEE.dll 中  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載結構](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
