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
ms.openlocfilehash: 3b8c9421dea4040a9f183b886f1ad8575cace780
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762421"
---
# <a name="icorconfiguration-interface"></a>ICorConfiguration 介面
提供設定 common language runtime （CLR）的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[AddDebuggerSpecialThread 方法](icorconfiguration-adddebuggerspecialthread-method.md)|向偵錯工具表示，當偵錯工具在 managed 或非受控的偵測案例中停止時，應該允許特定執行緒繼續執行。|  
|[SetDebuggerThreadControl 方法](icorconfiguration-setdebuggerthreadcontrol-method.md)|設定偵錯工具將會呼叫的回呼介面，因為 CLR 執行緒會被封鎖並解除封鎖以進行偵錯工具。|  
|[SetGCHostControl 方法](icorconfiguration-setgchostcontrol-method.md)|設定要由垃圾收集行程用來要求主控制項變更虛擬記憶體限制的回呼介面。|  
|[SetGCThreadControl 方法](icorconfiguration-setgcthreadcontrol-method.md)|設定回呼介面，用於針對非執行時間工作排程執行緒，否則會封鎖垃圾收集。|  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載介面](hosting-interfaces.md)
- [CorRuntimeHost Coclass](corruntimehost-coclass.md)
