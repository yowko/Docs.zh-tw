---
title: GetCLRIdentityManager 函式
ms.date: 03/30/2017
api_name:
- GetCLRIdentityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetCLRIdentityManager
helpviewer_keywords:
- GetCLRIdentityManager function [.NET Framework hosting]
ms.assetid: 66eeca30-adb4-45f4-aff5-347564c95724
topic_type:
- apiref
ms.openlocfilehash: 9d1196749e033c71b0c8923d0325eb4886122d1a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733655"
---
# <a name="getclridentitymanager-function"></a>GetCLRIdentityManager 函式

取得介面的指標，該介面可讓 common language runtime (CLR) 管理身分識別。  
  
 此函式已在 .NET Framework 4 中被取代。  
  
## <a name="syntax"></a>語法  
  
```cpp  
STDAPI GetCLRIdentityManager(  
    [in]  REFIID      riid,  
    [out] IUnknown  **ppManager  
);  
```  
  
## <a name="parameters"></a>參數  

 `riid`  
 在 `REFIID` (介面識別碼) ，可指定要取得的介面。 此值必須是 IID_ICLRAssemblyIdentityManager 或 IID_ICLRHostBindingPolicyManager。  
  
 `ppManager`  
 擴展 [ICLRAssemblyIdentityManager](iclrassemblyidentitymanager-interface.md) 或 [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) 物件的位址指標。  
  
## <a name="remarks"></a>備註  

 呼叫 [GetRealProcAddress](getrealprocaddress-function.md) 函式來取得函式的指標 `GetCLRIdentityManager` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** MSCorWks.dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [已被取代的 CLR 裝載函式](deprecated-clr-hosting-functions.md)
