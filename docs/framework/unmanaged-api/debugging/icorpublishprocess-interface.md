---
title: "ICorPublishProcess 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishProcess
helpviewer_keywords: ICorPublishProcess interface [.NET Framework debugging]
ms.assetid: 6d1dc41b-8aa2-4889-bb00-1cbccc00c123
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cb62da277ff13bea33969bb9c728cac5d5a15554
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icorpublishprocess-interface"></a>ICorPublishProcess 介面
提供存取處理序的相關資訊，以顯示的方法。  
  
## <a name="methods"></a>方法  
  
|方法|說明|  
|------------|-----------------|  
|[EnumAppDomains 方法](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-enumappdomains-method.md)|取得[ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)包含應用程式定義域中所參考的程序的執行個體`ICorPublishProcess`。|  
|[GetDisplayName 方法](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getdisplayname-method.md)|取得處理序所參考的可執行檔的完整路徑`ICorPublishProcess`。|  
|[GetProcessID 方法](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getprocessid-method.md)|取得處理序所參考的作業系統識別項`ICorPublishProcess`。|  
|[IsManaged 方法](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-ismanaged-method.md)|取得值，指出是否處理程序參考這個`ICorPublishProcess`已知執行 managed 程式碼。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorPub.idl、 CorPub.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [CorpubPublish Coclass](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
