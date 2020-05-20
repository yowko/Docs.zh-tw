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
ms.openlocfilehash: 8d958e949612b502ab218f5c6b75779174d34e19
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421081"
---
# <a name="icorpublishprocess-interface"></a>ICorPublishProcess 介面
提供方法，以存取要顯示的處理常式相關資訊。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[EnumAppDomains 方法](icorpublishprocess-enumappdomains-method.md)|取得[ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md)實例，其中包含這個所參考之進程中的應用程式域 `ICorPublishProcess` 。|  
|[GetDisplayName 方法](icorpublishprocess-getdisplayname-method.md)|取得這個所參考之進程的可執行檔完整路徑 `ICorPublishProcess` 。|  
|[GetProcessID 方法](icorpublishprocess-getprocessid-method.md)|取得這個所參考之進程的作業系統識別碼 `ICorPublishProcess` 。|  
|[IsManaged 方法](icorpublishprocess-ismanaged-method.md)|取得值，指出這個所參考的進程是否 `ICorPublishProcess` 已知正在執行 managed 程式碼。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorPub .idl，CorPub。h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](debugging-interfaces.md)
- [CorpubPublish Coclass](corpubpublish-coclass.md)
