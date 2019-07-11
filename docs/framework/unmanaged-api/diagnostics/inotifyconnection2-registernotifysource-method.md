---
title: INotifyConnection2::RegisterNotifySource 方法
ms.date: 03/30/2017
api_name:
- INotifyConnection2.RegisterNotifySource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifyConnection2::RegisterNotifySource
helpviewer_keywords:
- INotifyConnection2::RegisterNotifySource method [.NET Framework debugging]
- RegisterNotifySource method [.NET Framework debugging]
ms.assetid: 2632da80-6e4b-4429-8dee-b382745a5f81
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7d3c0d833208c91c548ea993bb6aa32e36e1f358
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776645"
---
# <a name="inotifyconnection2registernotifysource-method"></a>INotifyConnection2::RegisterNotifySource 方法
安裝指定的通知來源。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT RegisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource,  
    [out] INotifySink2**   out_ppNotifySink  
);  
```  
  
## <a name="parameters"></a>參數  
 `in_pNotifySource`  
 [in]指定要做為通知來源物件。  
  
 `out_ppNotifySink`  
 [out]接收要用作通知接收的物件。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功為 S_OK。  
  
## <a name="requirements"></a>需求  
 **標頭：** ProtocolNotify2.idl  
  
## <a name="see-also"></a>另請參閱

- [INotifyConnection2 介面](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
- [INotifySource2 介面](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [INotifySink2 介面](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [UnregisterNotifySource 方法](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-unregisternotifysource-method.md)
