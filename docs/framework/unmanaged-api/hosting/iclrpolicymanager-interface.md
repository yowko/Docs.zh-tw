---
title: ICLRPolicyManager 介面
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager
helpviewer_keywords:
- ICLRPolicyManager interface [.NET Framework hosting]
ms.assetid: 5c834aa1-f2db-408a-b230-c7bec093d364
topic_type:
- apiref
ms.openlocfilehash: 7092a1c792fee7f6173dcde211b8e807f6ab02a3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725582"
---
# <a name="iclrpolicymanager-interface"></a>ICLRPolicyManager 介面

提供的方法可讓主機指定在發生失敗和超時時所要採取的原則動作。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[SetActionOnFailure 方法](iclrpolicymanager-setactiononfailure-method.md)|指定當指定的失敗發生時，common language runtime (CLR) 應採取的原則動作。|  
|[SetActionOnTimeout 方法](iclrpolicymanager-setactionontimeout-method.md)|指定當指定的作業超時時，CLR 應採取的原則動作。|  
|[SetDefaultAction 方法](iclrpolicymanager-setdefaultaction-method.md)|指定當指定的作業發生時，CLR 應採取的原則動作。|  
|[SetTimeout 方法](iclrpolicymanager-settimeout-method.md)|設定指定之作業的超時值。|  
|[SetTimeoutAndAction 方法](iclrpolicymanager-settimeoutandaction-method.md)|設定指定之作業的超時值，並指定當作業發生時，CLR 應採取的原則動作。|  
|[SetUnhandledExceptionPolicy 方法](iclrpolicymanager-setunhandledexceptionpolicy-method.md)|指定發生未處理的例外狀況時 CLR 的行為。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [EClrFailure 列舉](eclrfailure-enumeration.md)
- [EClrOperation 列舉](eclroperation-enumeration.md)
- [EPolicyAction 列舉](epolicyaction-enumeration.md)
- [ICLRControl 介面](iclrcontrol-interface.md)
