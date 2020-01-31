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
ms.openlocfilehash: 3ae48df9e66890161c1aef944d37b0a279939d56
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790548"
---
# <a name="icorpublishprocess-interface"></a>ICorPublishProcess 介面
提供方法，以存取要顯示的處理常式相關資訊。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[EnumAppDomains 方法](icorpublishprocess-enumappdomains-method.md)|取得[ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md)實例，其中包含此 `ICorPublishProcess`所參考之進程中的應用程式域。|  
|[GetDisplayName 方法](icorpublishprocess-getdisplayname-method.md)|取得此 `ICorPublishProcess`所參考之進程的可執行檔完整路徑。|  
|[GetProcessID 方法](icorpublishprocess-getprocessid-method.md)|取得此 `ICorPublishProcess`所參考之進程的作業系統識別碼。|  
|[IsManaged 方法](icorpublishprocess-ismanaged-method.md)|取得值，指出此 `ICorPublishProcess` 所參考的進程是否已知執行 managed 程式碼。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorPub .idl，CorPub。h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](debugging-interfaces.md)
- [CorpubPublish Coclass](corpubpublish-coclass.md)
