---
title: StackOverflowInfo 結構
ms.date: 03/30/2017
api_name:
- StackOverflowInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StackOverflowInfo
helpviewer_keywords:
- StackOverflowInfo structure [.NET Framework hosting]
ms.assetid: 519389f2-0217-436c-99d4-93a76ebce5b5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac0f5d522a24394369583692f8c564254529bf13
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137342"
---
# <a name="stackoverflowinfo-structure"></a>StackOverflowInfo 結構
因為溢位而擲回的例外狀況，會儲存發生溢位和資訊的類型。  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct _StackOverflowInfo {  
    StackOverflowType   soType;  
    EXCEPTION_POINTERS  *pExceptionInfo;  
} StackOverflowInfo;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`soType`|值為[StackOverflowType](../../../../docs/framework/unmanaged-api/hosting/stackoverflowtype-enumeration.md)列舉，指定的類型溢位。|  
|`pExceptionInfo`|Win32 指標`EXCEPTION_POINTERS`物件，其中包含與不受機器限制的描述例外狀況的例外狀況記錄，以及內容記錄例外狀況當時的處理器內容的電腦相關描述。|  
  
## <a name="remarks"></a>備註  
 A`StackOverflowInfo`物件會傳遞給[iactiononclrevent:: Onevent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md)方法`Event_StackOverflow`事件。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.idl  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載結構](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
