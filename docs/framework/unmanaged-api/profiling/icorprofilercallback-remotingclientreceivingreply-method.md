---
title: ICorProfilerCallback::RemotingClientReceivingReply 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientReceivingReply
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientReceivingReply
helpviewer_keywords:
- ICorProfilerCallback::RemotingClientReceivingReply method [.NET Framework profiling]
- RemotingClientReceivingReply method [.NET Framework profiling]
ms.assetid: 15cfc300-8231-4ecb-9a04-19851c3eb484
topic_type:
- apiref
ms.openlocfilehash: 058c66af85da6c902e3d628e1b1479bb88c4fa85
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704847"
---
# <a name="icorprofilercallbackremotingclientreceivingreply-method"></a>ICorProfilerCallback::RemotingClientReceivingReply 方法

通知分析工具，遠端呼叫的伺服器端部分已完成，而且用戶端現在已在接收及處理回復。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT RemotingClientReceivingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);
```  
  
## <a name="parameters"></a>參數  

 `pCookie`  
 在在下列情況下，會與 [ICorProfilerCallback：： RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md) 中提供的值對應的值：  
  
- 遠端 GUID cookie 為使用中狀態。  
  
- 通道會成功傳輸訊息。  
  
- GUID cookie 在伺服器端進程中為作用中。  
  
 這可讓您輕鬆配對遠端呼叫。  
  
 `fIsAsync`  
 在值， `true` 如果呼叫是非同步，則為，否則為 `false` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
