---
title: INotifySink2::OnSyncCallOut 方法
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallOut
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallOut
helpviewer_keywords:
- INotifySink2::OnSyncCallOut method [.NET Framework debugging]
- OnSyncCallOut method [.NET Framework debugging]
ms.assetid: 97f15656-8677-4079-8553-a1d8603355d6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0a38c35f0acd47c9183c043e1c436413a309b138
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="inotifysink2onsynccallout-method"></a>INotifySink2::OnSyncCallOut 方法
取得叫用時呼叫外。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT OnSyncCallOut  
(  
    [in]  CALL_ID  in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*   out_pBufferSize  
);  
```  
  
#### <a name="parameters"></a>參數  
 `in_CallID`  
 [in]向外呼叫的識別碼。請參閱[CALL_ID 結構](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md)。  
  
 `out_ppBuffer`  
 [out]呼叫緩衝區。  
  
 `out_pBufferSize`  
 [out]呼叫緩衝區，以位元組為單位的大小。  
  
## <a name="return-value"></a>傳回值  
 如果此方法成功為 S_OK。  
  
## <a name="requirements"></a>需求  
 **標頭：** ProtocolNotify2.idl  
  
## <a name="see-also"></a>另請參閱  
 [INotifySink2 介面](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [INotifySource2 介面](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 [INotifyConnection2 介面](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
