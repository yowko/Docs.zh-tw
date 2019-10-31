---
title: ICLROnEventManager 介面
ms.date: 03/30/2017
api_name:
- ICLROnEventManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLROnEventManager
helpviewer_keywords:
- ICLROnEventManager interface [.NET Framework hosting]
ms.assetid: 9e15a0c1-8ab6-43d0-ae28-6ec7a4edd913
topic_type:
- apiref
ms.openlocfilehash: a1b22e77fe20d5e2d755efcd7a63c8f2bdc781e9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140850"
---
# <a name="iclroneventmanager-interface"></a>ICLROnEventManager 介面
提供的方法可讓主機註冊和取消註冊 common language runtime （CLR）事件的回呼。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[RegisterActionOnEvent 方法](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)|為指定的事件註冊回呼指標。|  
|[UnregisterActionOnEvent 方法](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-unregisteractiononevent-method.md)|將先前註冊的回呼指標取消註冊到指定的事件。|  
  
## <a name="remarks"></a>備註  
 若要註冊和取消註冊事件回呼，主機會藉由呼叫[ICLRControl：： GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md)方法來取得 `ICLROnEventManager` 的參考。  
  
> [!NOTE]
> [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)所描述的事件可以從不同的執行緒引發一次以上，以指示卸載或停用 CLR。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [EClrEvent 列舉](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [IActionOnCLREvent 介面](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [ICLRControl 介面](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
