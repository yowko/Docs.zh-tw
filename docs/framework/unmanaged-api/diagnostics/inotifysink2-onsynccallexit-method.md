---
title: INotifySink2::OnSyncCallExit 方法
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallExit
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallExit
helpviewer_keywords:
- INotifySink2::OnSyncCallExit method [.NET Framework debugging]
- OnSyncCallExit method [.NET Framework debugging]
ms.assetid: d9d7600e-a8f5-443a-96de-67d26e130f2d
topic_type:
- apiref
ms.openlocfilehash: 9049cd42e9c10cdcff62b005094b56c9df9ce975
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719992"
---
# <a name="inotifysink2onsynccallexit-method"></a>INotifySink2::OnSyncCallExit 方法

在結束呼叫時叫用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT OnSyncCallExit  
(  
    [in]  CALL_ID   in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*    out_pBufferSize  
);  
```  
  
## <a name="parameters"></a>參數  

 `in_CallID`  
 在要結束之呼叫的識別碼。 請參閱 [CALL_ID 結構](call-id-structure.md)。  
  
 `out_ppBuffer`  
 擴展呼叫緩衝區。  
  
 `out_pBufferSize`  
 擴展呼叫緩衝區的大小（以位元組為單位）。  
  
## <a name="return-value"></a>傳回值  

 如果方法成功，則為 S_OK。  
  
## <a name="requirements"></a>需求  

 **標頭：** ProtocolNotify2 .idl  
  
## <a name="see-also"></a>另請參閱

- [INotifySink2 介面](inotifysink2-interface.md)
- [INotifySource2 介面](inotifysource2-interface.md)
- [INotifyConnection2 介面](inotifyconnection2-interface.md)
