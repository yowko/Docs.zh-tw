---
title: ICorPublishProcess 介面
ms.date: 03/30/2017
api_name:
- ICorPublishProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess
helpviewer_keywords:
- ICorPublishProcess interface [.NET Framework debugging]
ms.assetid: 6d1dc41b-8aa2-4889-bb00-1cbccc00c123
topic_type:
- apiref
ms.openlocfilehash: 8ee59e9d416d1c53312e4fccb6953f20b03b29b3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95693082"
---
# <a name="icorpublishprocess-interface"></a>ICorPublishProcess 介面

提供可存取訊號以顯示有關處理常式的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[EnumAppDomains 方法](icorpublishprocess-enumappdomains-method.md)|取得 [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) 實例，其中包含這個所參考之進程中的應用程式域 `ICorPublishProcess` 。|  
|[GetDisplayName 方法](icorpublishprocess-getdisplayname-method.md)|取得這個所參考之進程的可執行檔完整路徑 `ICorPublishProcess` 。|  
|[GetProcessID 方法](icorpublishprocess-getprocessid-method.md)|取得這個所參考之進程的作業系統識別碼 `ICorPublishProcess` 。|  
|[IsManaged 方法](icorpublishprocess-ismanaged-method.md)|取得值，這個值會指出這個所參考的進程是否 `ICorPublishProcess` 知道是否正在執行 managed 程式碼。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorPub .idl、CorPub。h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](debugging-interfaces.md)
- [CorpubPublish Coclass](corpubpublish-coclass.md)
