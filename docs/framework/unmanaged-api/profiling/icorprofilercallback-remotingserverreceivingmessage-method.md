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
ms.openlocfilehash: 0fc84a15d3250d5103c1dbc6486960f0ea780a2b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676812"
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
 在在下列情況下，會與 [ICorProfilerCallback：： RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md) 中提供的值對應的值：  
  
- 遠端 GUID cookie 為使用中狀態。  
  
- 通道會成功傳輸訊息。  
  
- GUID cookie 在用戶端進程中為作用中。  
  
 這可讓您輕鬆配對遠端呼叫和建立邏輯呼叫堆疊。  
  
 `fIsAsync`  
 在值， `true` 如果呼叫是非同步，則為，否則為 `false` 。  
  
## <a name="remarks"></a>備註  

 如果訊息要求是非同步，則任何任意執行緒都可以提供要求。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
