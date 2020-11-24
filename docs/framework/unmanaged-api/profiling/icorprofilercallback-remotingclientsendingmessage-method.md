---
title: ICorProfilerCallback::RemotingClientSendingMessage 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientSendingMessage
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientSendingMessage
helpviewer_keywords:
- RemotingClientSendingMessage method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientSendingMessage method [.NET Framework profiling]
ms.assetid: 54d9a5a5-3877-49c1-a503-ce7c7943bc2a
topic_type:
- apiref
ms.openlocfilehash: 2ef8f066831df1437bd0b6a6f155dd459cae1eb2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676838"
---
# <a name="icorprofilercallbackremotingclientsendingmessage-method"></a>ICorProfilerCallback::RemotingClientSendingMessage 方法

通知分析工具用戶端正在將要求傳送至伺服器。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a>參數  

 `pCookie`  
 在在下列情況下，對應于 [ICorProfilerCallback：： RemotingServerReceivingMessage](icorprofilercallback-remotingserverreceivingmessage-method.md) 中所提供值的值：  
  
- 遠端 GUID cookie 為使用中狀態。  
  
- 通道會成功傳輸訊息。  
  
- GUID cookie 在伺服器端進程中為作用中。  
  
 這可讓您輕鬆配對遠端呼叫和建立邏輯呼叫堆疊。  
  
 `fIsAsync`  
 在值， `true` 如果呼叫是非同步，則為，否則為 `false` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
