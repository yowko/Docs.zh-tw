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
ms.openlocfilehash: 04f6a088c5bbe96e3909ba600aa8ffab937abe2d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140396"
---
# <a name="icorpublishprocess-interface"></a>ICorPublishProcess 介面
提供方法，以存取要顯示的處理常式相關資訊。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[EnumAppDomains 方法](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-enumappdomains-method.md)|取得[ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)實例，其中包含此 `ICorPublishProcess`所參考之進程中的應用程式域。|  
|[GetDisplayName 方法](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getdisplayname-method.md)|取得此 `ICorPublishProcess`所參考之進程的可執行檔完整路徑。|  
|[GetProcessID 方法](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getprocessid-method.md)|取得此 `ICorPublishProcess`所參考之進程的作業系統識別碼。|  
|[IsManaged 方法](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-ismanaged-method.md)|取得值，指出此 `ICorPublishProcess` 所參考的進程是否已知執行 managed 程式碼。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorPub .idl，CorPub。h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [CorpubPublish Coclass](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
