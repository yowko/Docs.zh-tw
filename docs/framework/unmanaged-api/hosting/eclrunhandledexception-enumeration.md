---
title: EClrUnhandledException 列舉
ms.date: 03/30/2017
api_name:
- EClrUnhandledException
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrUnhandledException
helpviewer_keywords:
- EClrUnhandledException enumeration [.NET Framework hosting]
ms.assetid: d231044e-2b53-4836-93f9-8117ff0e5c3a
topic_type:
- apiref
ms.openlocfilehash: bccd44e1bead4feadf67929dc104557715904577
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686432"
---
# <a name="eclrunhandledexception-enumeration"></a>EClrUnhandledException 列舉

描述可用來管理使用者程式碼中未處理之例外狀況的選項。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum {  
    eRuntimeDeterminedPolicy,  
    eHostDeterminedPolicy  
} EClrUnhandledException;  
```  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`eRuntimeDeterminedPolicy`|指定發生預設行為。 進程已中斷。|  
|`eHostDeterminedPolicy`|指定 common language runtime (CLR) 忽略未處理的例外狀況，並讓主機判斷任何進一步的動作。|  
  
## <a name="remarks"></a>備註  

 若要指定 CLR 的行為類似于較舊的版本，請使用 `eHostDeterminedPolicy` 成員。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** MSCorEE.dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [EClrFailure 列舉](eclrfailure-enumeration.md)
- [EClrOperation 列舉](eclroperation-enumeration.md)
- [ICLRPolicyManager 介面](iclrpolicymanager-interface.md)
- [SetUnhandledExceptionPolicy 方法](iclrpolicymanager-setunhandledexceptionpolicy-method.md)
- [IHostPolicyManager 介面](ihostpolicymanager-interface.md)
- [裝載列舉](hosting-enumerations.md)
