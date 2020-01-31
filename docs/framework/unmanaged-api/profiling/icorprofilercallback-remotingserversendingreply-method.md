---
title: ICorProfilerCallback::RemotingServerSendingReply 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerSendingReply
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerSendingReply
helpviewer_keywords:
- RemotingServerSendingReply method [.NET Framework profiling]
- ICorProfilerCallback::RemotingServerSendingReply method [.NET Framework profiling]
ms.assetid: dfe84a19-2e03-4be2-8b25-f02bad38e4a9
topic_type:
- apiref
ms.openlocfilehash: f77901623ef4df7b43276c18a910cf62fcc4451d
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865970"
---
# <a name="icorprofilercallbackremotingserversendingreply-method"></a>ICorProfilerCallback::RemotingServerSendingReply 方法
通知分析工具，進程已完成處理遠端方法調用要求，而且即將透過通道傳送回復。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT RemotingServerSendingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a>參數  
 `pCookie`  
 在GUID 的指標，在下列情況下會對應至[ICorProfilerCallback：： RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md)中提供的值：  
  
- 遠端 GUID cookie 為作用中。  
  
- 通道會成功傳輸訊息。  
  
- GUID cookie 會在用戶端進程上作用。  
  
 這可讓您輕鬆地配對遠端呼叫和邏輯呼叫堆疊的建立。  
  
 `fIsAsync`  
 在如果呼叫是非同步，則為 `true` 的值;否則，`false`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
