---
title: IHostPolicyManager 介面
ms.date: 03/30/2017
api_name:
- IHostPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager
helpviewer_keywords:
- IHostPolicyManager interface [.NET Framework hosting]
ms.assetid: 8c4aa124-5e00-46d9-b1e8-57ba6574bb0d
topic_type:
- apiref
ms.openlocfilehash: 3c85bcbe8aee453b19217ebd1f48feea113e3bb1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731213"
---
# <a name="ihostpolicymanager-interface"></a>IHostPolicyManager 介面

提供方法，以通知主機 common language runtime (CLR) 在中止、超時或失敗時所執行的動作。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[OnDefaultAction 方法](ihostpolicymanager-ondefaultaction-method.md)|通知主機，CLR 即將採用呼叫 [ICLRPolicyManager：： SetDefaultAction](iclrpolicymanager-setdefaultaction-method.md) 所指定的預設動作，以回應執行緒中止或卸載 <xref:System.AppDomain> 。|  
|[OnFailure 方法](ihostpolicymanager-onfailure-method.md)|通知主機 CLR 即將採取呼叫 [ICLRPolicyManager：： SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) 所指定的動作，以回應資源配置或回收失敗。|  
|[OnTimeout 方法](ihostpolicymanager-ontimeout-method.md)|通知主機，CLR 即將採取呼叫 [ICLRPolicyManager：： SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) 所指定的動作，以回應超時。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [EClrFailure 列舉](eclrfailure-enumeration.md)
- [EClrOperation 列舉](eclroperation-enumeration.md)
- [EPolicyAction 列舉](epolicyaction-enumeration.md)
- [ICLRPolicyManager 介面](iclrpolicymanager-interface.md)
- [裝載介面](hosting-interfaces.md)
