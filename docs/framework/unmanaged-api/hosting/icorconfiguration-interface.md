---
title: ICorConfiguration 介面
ms.date: 03/30/2017
api_name:
- ICorConfiguration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorConfiguration
helpviewer_keywords:
- ICorConfiguration interface [.NET Framework hosting]
ms.assetid: aaf96116-372b-4538-afb1-9e0fcdac1f98
topic_type:
- apiref
ms.openlocfilehash: 80bb68486e555d6c96cf8ee56ed6d60e41c7c5c6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127808"
---
# <a name="icorconfiguration-interface"></a>ICorConfiguration 介面
提供設定 common language runtime （CLR）的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[AddDebuggerSpecialThread 方法](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-adddebuggerspecialthread-method.md)|向偵錯工具表示，當偵錯工具在 managed 或非受控的偵測案例中停止時，應該允許特定執行緒繼續執行。|  
|[SetDebuggerThreadControl 方法](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setdebuggerthreadcontrol-method.md)|設定偵錯工具將會呼叫的回呼介面，因為 CLR 執行緒會被封鎖並解除封鎖以進行偵錯工具。|  
|[SetGCHostControl 方法](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgchostcontrol-method.md)|設定要由垃圾收集行程用來要求主控制項變更虛擬記憶體限制的回呼介面。|  
|[SetGCThreadControl 方法](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgcthreadcontrol-method.md)|設定回呼介面，用於針對非執行時間工作排程執行緒，否則會封鎖垃圾收集。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [CorRuntimeHost Coclass](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
