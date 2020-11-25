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
ms.openlocfilehash: fa8d15bc8e504a57d5cc87c170a3a5b022798add
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715780"
---
# <a name="icorconfiguration-interface"></a>ICorConfiguration 介面

提供 (CLR) 設定 common language runtime 的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[AddDebuggerSpecialThread 方法](icorconfiguration-adddebuggerspecialthread-method.md)|向偵錯工具表示，當偵錯工具在 managed 或非受控的偵測情節中停止應用程式時，應該允許特定執行緒繼續執行。|  
|[SetDebuggerThreadControl 方法](icorconfiguration-setdebuggerthreadcontrol-method.md)|設定偵錯工具將呼叫的回呼介面，因為 CLR 執行緒會被封鎖和解除封鎖以進行偵測。|  
|[SetGCHostControl 方法](icorconfiguration-setgchostcontrol-method.md)|設定要由垃圾收集行程用來要求主控制項變更虛擬記憶體限制的回呼介面。|  
|[SetGCThreadControl 方法](icorconfiguration-setgcthreadcontrol-method.md)|設定回呼介面，以排程非執行時間工作的執行緒，否則將會遭到封鎖，以進行垃圾收集。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載介面](hosting-interfaces.md)
- [CorRuntimeHost Coclass](corruntimehost-coclass.md)
