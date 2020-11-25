---
title: ICorDebugThread4 介面
ms.date: 03/30/2017
api_name:
- ICorDebugThread4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4
helpviewer_keywords:
- ICorDebugThread4 interface [.NET Framework debugging]
ms.assetid: a8c7719a-322b-4133-8566-4c27218dc104
topic_type:
- apiref
ms.openlocfilehash: 5c108420772be9e6d0932f3759f18da9446f99d6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727935"
---
# <a name="icordebugthread4-interface"></a>ICorDebugThread4 介面

提供執行緒封鎖資訊。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetBlockingObjects 方法](icordebugthread4-getblockingobjects-method.md)|提供 [CorDebugBlockingObject](cordebugblockingobject-structure.md) 結構的已排序列舉，以提供執行緒封鎖資訊。|  
|[HadUnhandledException 方法](icordebugthread4-hadunhandledexception-method.md)|指出執行緒是否曾經有未處理的例外狀況。|  
|[GetCurrentCustomDebuggerNotification 方法](icordebugthread4-getcurrentcustomdebuggernotification-method.md)|取得目前線程上目前的 [ICorDebugManagedCallback3：： CustomNotification](icordebugmanagedcallback3-customnotification-method.md) 物件。|  
  
## <a name="remarks"></a>備註  

 此介面是 ICorDebugThread、ICorDebugThread2 和 [ICorDebugThread3](icordebugthread3-interface.md) 介面的邏輯擴充。  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
