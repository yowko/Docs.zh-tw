---
title: "INotifySink2::OnSyncCallReturn 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: INotifySink2.OnSyncCallReturn
api_location: diasymreader.dll
api_type: COM
f1_keywords: INotifySink2::OnSyncCallReturn
helpviewer_keywords:
- OnSyncCallReturn method [.NET Framework debugging]
- INotifySink2::OnSyncCallReturn method [.NET Framework debugging]
ms.assetid: c1bda761-6292-4750-a14b-7d5db8f33456
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8f09d9ced41ecfe933a22ac41ee7f2065f1afcc6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="inotifysink2onsynccallreturn-method"></a>INotifySink2::OnSyncCallReturn 方法
取得叫用呼叫傳回時。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT OnSyncCallReturn  
(  
    [in]  CALL_ID   in_CallID,  
    [in, size_is(in_BufferSize)] BYTE*  in_pBuffer,  
    [in]  DWORD     in_BufferSize  
);  
```  
  
#### <a name="parameters"></a>參數  
 `in_CallID`  
 [in]呼叫傳回的識別碼。 請參閱[CALL_ID 結構](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md)。  
  
 `in_pBuffer`  
 [in]呼叫緩衝區。  
  
 `in_BufferSize`  
 [in]呼叫緩衝區，以位元組為單位的大小。  
  
## <a name="return-value"></a>傳回值  
 如果此方法成功為 S_OK。  
  
## <a name="requirements"></a>需求  
 **標頭：** ProtocolNotify2.idl  
  
## <a name="see-also"></a>另請參閱  
 [INotifySink2 介面](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [INotifySource2 介面](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 [INotifyConnection2 介面](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
