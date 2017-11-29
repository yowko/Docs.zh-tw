---
title: "ICorProfilerCallback::RemotingServerSendingReply 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RemotingServerSendingReply
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RemotingServerSendingReply
helpviewer_keywords:
- RemotingServerSendingReply method [.NET Framework profiling]
- ICorProfilerCallback::RemotingServerSendingReply method [.NET Framework profiling]
ms.assetid: dfe84a19-2e03-4be2-8b25-f02bad38e4a9
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b99b2de235634b715a6f5ba9fee9ee49ab34063a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackremotingserversendingreply-method"></a>ICorProfilerCallback::RemotingServerSendingReply 方法
通知分析工具，處理程序已完成處理遠端方法叫用要求，而且即將傳送回覆，透過的通道。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT RemotingServerSendingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
#### <a name="parameters"></a>參數  
 `pCookie`  
 [in]與中提供的值將對應的 GUID 指標[icorprofilercallback:: Remotingclientreceivingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md)在這些情況下：  
  
-   遠端處理 GUID cookie 是使用中。  
  
-   成功的訊息傳輸通道。  
  
-   GUID cookie 會啟用用戶端處理程序。  
  
 這可讓您輕易地配對的遠端處理呼叫，以及邏輯呼叫堆疊的建立。  
  
 `fIsAsync`  
 [in]值是`true`呼叫是非同步的; 否則如果`false`。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorProfilerCallback 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
