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
ms.openlocfilehash: 59aa904d4c67326b60381d3476eaab179d7fa42b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140799"
---
# <a name="iclrpolicymanager-interface"></a>ICLRPolicyManager 介面
提供的方法可讓主機指定發生失敗和超時事件時所要採取的原則動作。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[SetActionOnFailure 方法](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)|指定當發生指定的失敗時，common language runtime （CLR）應採取的原則動作。|  
|[SetActionOnTimeout 方法](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)|指定當指定的作業超時時，CLR 應採取的原則動作。|  
|[SetDefaultAction 方法](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md)|指定當發生指定的作業時，CLR 應採取的原則動作。|  
|[SetTimeout 方法](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md)|設定指定之作業的超時值。|  
|[SetTimeoutAndAction 方法](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeoutandaction-method.md)|設定指定之作業的超時值，並指定當作業發生時，CLR 應該採取的原則動作。|  
|[SetUnhandledExceptionPolicy 方法](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)|指定發生未處理的例外狀況時，CLR 的行為。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [EClrFailure 列舉](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [EClrOperation 列舉](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [EPolicyAction 列舉](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [ICLRControl 介面](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
