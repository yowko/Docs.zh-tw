---
title: ICorDebugChain 介面
ms.date: 03/30/2017
api_name:
- ICorDebugChain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain
helpviewer_keywords:
- ICorDebugChain interface [.NET Framework debugging]
ms.assetid: f671f519-1cb3-4ae5-b9f1-abc5e783459f
topic_type:
- apiref
ms.openlocfilehash: f4bacfe94178ea78b1c3afd15a2e100076c38a84
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777988"
---
# <a name="icordebugchain-interface"></a>ICorDebugChain 介面

表示實體或邏輯呼叫堆疊的區段。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[EnumerateFrames 方法](icordebugchain-enumerateframes-method.md)|取得列舉值，其中包含鏈中的所有 managed 堆疊框架，從最新的框架開始。|  
|[GetActiveFrame 方法](icordebugchain-getactiveframe-method.md)|取得鏈上的現用（也就是最新的）框架。|  
|[GetCallee 方法](icordebugchain-getcallee-method.md)|取得這個鏈所呼叫的鏈。|  
|[GetCaller 方法](icordebugchain-getcaller-method.md)|取得呼叫這個鏈的鏈。|  
|[GetContext 方法](icordebugchain-getcontext-method.md)|未實作。|  
|[GetNext 方法](icordebugchain-getnext-method.md)|取得執行緒的下一個框架鏈。|  
|[GetPrevious 方法](icordebugchain-getprevious-method.md)|取得執行緒的先前框架鏈。|  
|[GetReason 方法](icordebugchain-getreason-method.md)|取得此呼叫鏈的創世原因。|  
|[GetRegisterSet 方法](icordebugchain-getregisterset-method.md)|取得此連鎖之使用中部分的暫存器集。|  
|[GetStackRange 方法](icordebugchain-getstackrange-method.md)|取得此鏈之堆疊區段的位址範圍。|  
|[GetThread 方法](icordebugchain-getthread-method.md)|取得此呼叫鏈所屬的實體執行緒。|  
|[IsManaged 方法](icordebugchain-ismanaged-method.md)|取得值，指出這個鏈是否正在執行 managed 程式碼。|  
  
## <a name="remarks"></a>備註  
 鏈中的堆疊框架會佔用連續的堆疊空間，並共用相同的執行緒和內容。 連鎖可能代表受控或非受控碼鏈。 空的 `ICorDebugChain` 實例代表非受控碼鏈。  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](debugging-interfaces.md)
