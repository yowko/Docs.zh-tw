---
title: CorpubPublish Coclass
ms.date: 03/30/2017
api_name:
- CorpubPublish Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorpubPublish
helpviewer_keywords:
- CorpubPublish coclass [.NET Framework debugging]
ms.assetid: 191015da-f54a-4bac-a28a-1de7ab3c3428
topic_type:
- apiref
ms.openlocfilehash: 24d245bbb0f9ac86e321491e0af3b66b1e011baa
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789210"
---
# <a name="corpubpublish-coclass"></a>CorpubPublish Coclass
提供介面來發行應用程式定義域和處理序的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
coclass CorpubPublish {  
    [default] interface ICorPublish;  
    interface           ICorPublishProcess;  
    interface           ICorPublishAppDomain;  
    interface           ICorPublishProcessEnum;  
    interface           ICorPublishAppDomainEnum;  
};  
```  
  
## <a name="interfaces"></a>介面  
  
|介面|描述|  
|---------------|-----------------|  
|[ICorPublish 介面](icorpublish-interface.md)|提供方法來發行進程的相關資訊，以及這些進程中的應用程式域。|  
|[ICorPublishAppDomain 介面](icorpublishappdomain-interface.md)|表示和提供進程中應用程式域的相關資訊。|  
|[ICorPublishAppDomainEnum 介面](icorpublishappdomainenum-interface.md)|提供方法，以跨越進程中目前存在的應用程式域集合。|  
|[ICorPublishProcess 介面](icorpublishprocess-interface.md)|代表在電腦上執行的處理常式。|  
|[ICorPublishProcessEnum 介面](icorpublishprocessenum-interface.md)|提供方法來流覽電腦上正在執行的進程集合。|  
  
## <a name="remarks"></a>備註  
 典型的發行案例牽涉到想要在應用程式域內的電腦上，對其執行的 managed 程式碼進行 debug 的開發人員。 裝載環境可能會在進程內執行一個以上的應用程式域。 開發人員想要使用圖形化使用者介面或其他方法來列出在電腦上執行的所有處理常式，並挑選特定的進程。 清單應包含執行 managed 程式碼之進程內的所有應用程式域。 然後，開發人員可以識別特定的應用程式域，並將偵錯工具附加至該網域。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorPub .idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯](index.md)
