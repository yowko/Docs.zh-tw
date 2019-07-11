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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2bc3e48185c3bc289a4f7bfd865f69d9c06a720c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750505"
---
# <a name="icorprofilercallbackremotingserverreceivingmessage-method"></a>ICorProfilerCallback::RemotingServerReceivingMessage 方法
通知分析工具處理序已收到的遠端方法叫用或啟用要求。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a>參數  
 `pCookie`  
 [in]值，這個值會對應中提供的價值[icorprofilercallback:: Remotingclientsendingmessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)在這些情況下：  
  
- 遠端處理 GUID cookie 在作用中。  
  
- 成功的訊息傳輸通道。  
  
- GUID cookie 上為作用中的用戶端程序。  
  
 這可讓您輕易地配對的遠端呼叫，以及建立的邏輯呼叫堆疊。  
  
 `fIsAsync`  
 [in]值是`true`的呼叫是非同步，否則如果`false`。  
  
## <a name="remarks"></a>備註  
 如果是非同步的訊息要求，要求可以處理任何任意的執行緒。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
