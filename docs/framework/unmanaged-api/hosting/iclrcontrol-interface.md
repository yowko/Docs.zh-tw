---
title: ICLRControl 介面
ms.date: 03/30/2017
api_name:
- ICLRControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl
helpviewer_keywords:
- ICLRControl interface [.NET Framework hosting]
ms.assetid: a24fd905-1fa6-45a0-ad65-e9e2ee58861e
topic_type:
- apiref
ms.openlocfilehash: 54748fdeaf911591c21f4495335e54c777878f04
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615830"
---
# <a name="iclrcontrol-interface"></a>ICLRControl 介面
提供的方法可讓主機取得通用語言執行時間（CLR）的參考，並設定的各個層面。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetCLRManager 方法](iclrcontrol-getclrmanager-method.md)|取得主機可以用來設定 CLR 之任何管理員類型的實例介面指標。|  
|[SetAppDomainManagerType 方法](iclrcontrol-setappdomainmanagertype-method.md)|將衍生自的類型設定 <xref:System.AppDomainManager> 為應用程式域管理員的類型。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRAssemblyIdentityManager 介面](iclrassemblyidentitymanager-interface.md)
- [ICLRDebugManager 介面](iclrdebugmanager-interface.md)
- [ICLRGCManager 介面](iclrgcmanager-interface.md)
- [ICLRHostBindingPolicyManager 介面](iclrhostbindingpolicymanager-interface.md)
- [ICLRHostProtectionManager 介面](iclrhostprotectionmanager-interface.md)
- [ICLROnEventManager 介面](iclroneventmanager-interface.md)
- [ICLRPolicyManager 介面](iclrpolicymanager-interface.md)
- [IHostControl 介面](ihostcontrol-interface.md)
- [裝載介面](hosting-interfaces.md)
