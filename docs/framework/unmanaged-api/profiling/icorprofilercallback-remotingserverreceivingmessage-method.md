---
title: ICorProfilerCallback::RemotingServerReceivingMessage 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerReceivingMessage
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerReceivingMessage
helpviewer_keywords:
- ICorProfilerCallback::RemotingServerReceivingMessage method [.NET Framework profiling]
- RemotingServerReceivingMessage method [.NET Framework profiling]
ms.assetid: 5604d21f-e6b7-490e-b469-42122a7568e1
topic_type:
- apiref
ms.openlocfilehash: 6e045a99de9ad30516fd12a7b490e26c860bde7e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866009"
---
# <a name="icorprofilercallbackremotingserverreceivingmessage-method"></a>ICorProfilerCallback::RemotingServerReceivingMessage 方法
通知分析工具，進程已收到遠端方法調用或啟用要求。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a>參數  
 `pCookie`  
 在在下列情況下，將會對應至[ICorProfilerCallback：： RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md)中所提供之值的值：  
  
- 遠端 GUID cookie 為作用中。  
  
- 通道會成功傳輸訊息。  
  
- GUID cookie 會在用戶端進程上作用。  
  
 這可讓您輕鬆地配對遠端呼叫和邏輯呼叫堆疊的建立。  
  
 `fIsAsync`  
 在如果呼叫是非同步，則為 `true` 的值;否則，`false`。  
  
## <a name="remarks"></a>備註  
 如果訊息要求是非同步，則要求可由任何任意執行緒服務。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
