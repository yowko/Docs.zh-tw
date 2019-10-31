---
title: GetIdentityAuthority 函式
ms.date: 03/30/2017
api_name:
- GetIdentityAuthority
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- GetIdentityAuthority
helpviewer_keywords:
- GetIdentityAuthority function [.NET Framework fusion]
ms.assetid: 843cd5ab-d2b7-4ff6-86bd-e68c7a91c098
topic_type:
- apiref
ms.openlocfilehash: acb80f3cc199d4d9f774cb3898335d26fe44b807
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127138"
---
# <a name="getidentityauthority-function"></a>GetIdentityAuthority 函式
取得[IIdentityAuthority](iidentityauthority-interface.md)實例的指標，它會管理程式碼物件的索引鍵。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetIdentityAuthority (  
    [out] IIdentityAuthority   **ppIIdentityAuthority  
 );  
```  
  
## <a name="parameters"></a>參數  
 `ppIIdentityAuthority`  
 脫銷傳回的 `IIdentityAuthority` 指標。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 隔離。h  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [IIdentityAuthority 介面](iidentityauthority-interface.md)
- [融合全域靜態函式](fusion-global-static-functions.md)
