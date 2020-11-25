---
title: INotifySink2::OnSyncCallReturn 方法
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallReturn
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallReturn
helpviewer_keywords:
- OnSyncCallReturn method [.NET Framework debugging]
- INotifySink2::OnSyncCallReturn method [.NET Framework debugging]
ms.assetid: c1bda761-6292-4750-a14b-7d5db8f33456
topic_type:
- apiref
ms.openlocfilehash: fe2db3df688f91ec6e1aadd8cc3bb43726e5c30f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719953"
---
# <a name="inotifysink2onsynccallreturn-method"></a>INotifySink2::OnSyncCallReturn 方法

當呼叫傳回時，就會叫用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT OnSyncCallReturn  
(  
    [in]  CALL_ID   in_CallID,  
    [in, size_is(in_BufferSize)] BYTE*  in_pBuffer,  
    [in]  DWORD     in_BufferSize  
);  
```  
  
## <a name="parameters"></a>參數  

 `in_CallID`  
 在所傳回之呼叫的識別碼。 請參閱 [CALL_ID 結構](call-id-structure.md)。  
  
 `in_pBuffer`  
 在呼叫緩衝區。  
  
 `in_BufferSize`  
 在呼叫緩衝區的大小（以位元組為單位）。  
  
## <a name="return-value"></a>傳回值  

 如果方法成功，則為 S_OK。  
  
## <a name="requirements"></a>需求  

 **標頭：** ProtocolNotify2 .idl  
  
## <a name="see-also"></a>另請參閱

- [INotifySink2 介面](inotifysink2-interface.md)
- [INotifySource2 介面](inotifysource2-interface.md)
- [INotifyConnection2 介面](inotifyconnection2-interface.md)
