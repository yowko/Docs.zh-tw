---
title: IHostAutoEvent 介面
ms.date: 03/30/2017
api_name:
- IHostAutoEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAutoEvent
helpviewer_keywords:
- IHostAutoEvent interface [.NET Framework hosting]
ms.assetid: 6c1d15c1-a80a-4ee9-b1e4-6e859db6575a
topic_type:
- apiref
ms.openlocfilehash: a24939ac0b0808546ef3615fae4909c6c3cf8a2e
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805002"
---
# <a name="ihostautoevent-interface"></a>IHostAutoEvent 介面
提供主控制項的自動重設事件的執行表示。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Set 方法](ihostautoevent-set-method.md)|將目前的 `IHostAutoEvent` 實例設定為已發出信號的狀態。|  
|[Wait 方法](ihostautoevent-wait-method.md)|導致目前的 `IHostAutoEvent` 實例等到事件擁有或經過指定的時間量之後，才等候。|  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRSyncManager 介面](iclrsyncmanager-interface.md)
- [IHostManualEvent 介面](ihostmanualevent-interface.md)
- [IHostSyncManager 介面](ihostsyncmanager-interface.md)
- [裝載介面](hosting-interfaces.md)
