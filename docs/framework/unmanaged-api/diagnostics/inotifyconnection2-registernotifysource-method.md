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
ms.openlocfilehash: b7fa777466e2c7edd7b3110dd91e776785c63c58
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442068"
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
 在指定要當做通知來源使用的物件。  
  
 `out_ppNotifySink`  
 脫銷接收要當做通知接收使用的物件。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則 S_OK。  
  
## <a name="requirements"></a>需求  
 **標頭：** ProtocolNotify2 .idl  
  
## <a name="see-also"></a>另請參閱

- [INotifyConnection2 介面](inotifyconnection2-interface.md)
- [INotifySource2 介面](inotifysource2-interface.md)
- [INotifySink2 介面](inotifysink2-interface.md)
- [UnregisterNotifySource 方法](inotifyconnection2-unregisternotifysource-method.md)
