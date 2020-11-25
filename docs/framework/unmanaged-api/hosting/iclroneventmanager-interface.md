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
ms.openlocfilehash: 1948075d87b5a44397a1eaab3adb4edbc96d7143
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725625"
---
# <a name="iclroneventmanager-interface"></a>ICLROnEventManager 介面

提供可讓主機針對 common language runtime (CLR) 事件註冊和取消註冊回呼的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[RegisterActionOnEvent 方法](iclroneventmanager-registeractiononevent-method.md)|註冊指定事件的回呼指標。|  
|[UnregisterActionOnEvent 方法](iclroneventmanager-unregisteractiononevent-method.md)|針對指定的事件，取消註冊先前註冊的回呼指標。|  
  
## <a name="remarks"></a>備註  

 若要註冊和取消註冊事件回呼，主機會藉 `ICLROnEventManager` 由呼叫 [ICLRControl：： GetCLRManager](iclrcontrol-getclrmanager-method.md) 方法來取得的參考。  
  
> [!NOTE]
> [EClrEvent](eclrevent-enumeration.md)所描述的事件可以從不同的執行緒中引發一次以上，以表示卸載或停用 CLR。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [EClrEvent 列舉](eclrevent-enumeration.md)
- [IActionOnCLREvent 介面](iactiononclrevent-interface.md)
- [ICLRControl 介面](iclrcontrol-interface.md)
- [裝載介面](hosting-interfaces.md)
