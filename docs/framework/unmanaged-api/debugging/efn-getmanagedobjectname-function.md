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
ms.openlocfilehash: 0fb694cf85256c0f3ac5ae179e53ff504ab707e9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676201"
---
# <a name="_efn_getmanagedobjectname-function"></a>\_EFN \_ GetManagedObjectName 函式

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
 擴展型別的名稱。  
  
 `cbName`  
 擴展字串緩衝區中的可用字元數。  
  
## <a name="remarks"></a>備註  

 如果目前在內容中的執行緒上沒有 managed 程式碼，此函式會傳回 HRESULT SOS_E_NOMANAGEDCODE 具有0xa0 的設備值和錯誤碼0x1000。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** SOS_Stacktrace。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯全域靜態函式](debugging-global-static-functions.md)
