---
title: _EFN_GetManagedObjectName 函式
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedObjectName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedObjectName
helpviewer_keywords:
- _EFN_GetManagedObjectName function [.NET Framework debugging]
ms.assetid: 6e7c6bee-7ced-495f-bf6c-2a5f0c716f7e
topic_type:
- apiref
ms.openlocfilehash: c7333f8f7b95655ac821e9a2977d5db3794486a2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122997"
---
# <a name="_efn_getmanagedobjectname-function"></a>\_EFN\_GetManagedObjectName 函式
使用提供的 managed 物件指標，取得型別的名稱。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT _EFN_GetManagedObjectName(  
    [in]  PDEBUG_CLIENT  Client,  
    [in]  ULONG64        objAddr,  
    [out] __out_ecount(cbName) PSTR szName,  
    [out] ULONG          cbName  
);  
```  
  
## <a name="parameters"></a>參數  
 `Client`  
 在Debug 用戶端的指標。  
  
 `objAddr`  
 在Managed 物件指標。  
  
 szName  
 脫銷類型的名稱。  
  
 `cbName`  
 脫銷字串緩衝區中可用的字元數。  
  
## <a name="remarks"></a>備註  
 如果目前在內容中的執行緒上沒有 managed 程式碼，則函式會傳回具有設備值0xa0 的 HRESULT SOS_E_NOMANAGEDCODE，以及錯誤碼為0x1000。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** SOS_Stacktrace。h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯全域靜態函式](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
