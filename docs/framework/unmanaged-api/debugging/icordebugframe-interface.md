---
title: ICorDebugFrame 介面
ms.date: 03/30/2017
api_name:
- ICorDebugFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame
helpviewer_keywords:
- ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 0c48f764-3c64-4602-b2f4-4ffc60eb2c65
topic_type:
- apiref
ms.openlocfilehash: 9c2771d1338943406921447d96dd9a8748153a36
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209613"
---
# <a name="icordebugframe-interface"></a>ICorDebugFrame 介面

表示目前堆疊上的框架。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[CreateStepper 方法](icordebugframe-createstepper-method.md)|取得 ICorDebugStepper，以執行相對於這個的逐步操作 `ICorDebugFrame` 。|  
|[GetCallee 方法](icordebugframe-getcallee-method.md)|取得 `ICorDebugFrame` 此框架所呼叫之目前鏈中的指標，如果這是鏈中最內層的框架，則會傳回 null。|  
|[GetCaller 方法](icordebugframe-getcaller-method.md)|取得 `ICorDebugFrame` 目前鏈中呼叫此框架的指標，如果這是鏈中最外層的框架，則會傳回 null。|  
|[GetChain 方法](icordebugframe-getchain-method.md)|取得此所屬 ICorDebugChain 的指標 `ICorDebugFrame` 。|  
|[GetCode 方法](icordebugframe-getcode-method.md)|取得與這個堆疊框架相關聯之 ICorDebugCode 的指標。|  
|[GetFunction 方法](icordebugframe-getfunction-method.md)|取得 ICorDebugFunction 的指標，其中包含與這個堆疊框架相關聯的程式碼。|  
|[GetFunctionToken 方法](icordebugframe-getfunctiontoken-method.md)|取得包含與此堆疊框架相關聯之程式碼的函式的元資料標記。|  
|[GetStackRange 方法](icordebugframe-getstackrange-method.md)|取得這個所表示之堆疊框架的絕對位址範圍 `ICorDebugFrame` 。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](debugging-interfaces.md)
