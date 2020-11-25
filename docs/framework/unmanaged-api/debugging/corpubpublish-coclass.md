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
ms.openlocfilehash: c73eab14bf6f9f9599bed79f4c5f85ed035c0518
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722345"
---
# <a name="corpubpublish-coclass"></a>CorpubPublish Coclass

提供介面來發行應用程式定義域和處理序的相關資訊。  
  
## <a name="syntax"></a>Syntax  
  
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
|[ICorPublish 介面](icorpublish-interface.md)|提供在這些進程中發佈進程和應用程式域相關資訊的方法。|  
|[ICorPublishAppDomain 介面](icorpublishappdomain-interface.md)|代表和提供進程中應用程式域的相關資訊。|  
|[ICorPublishAppDomainEnum 介面](icorpublishappdomainenum-interface.md)|提供方法，這些方法會遍歷目前存在於進程內的應用程式域集合。|  
|[ICorPublishProcess 介面](icorpublishprocess-interface.md)|代表在電腦上執行的處理常式。|  
|[ICorPublishProcessEnum 介面](icorpublishprocessenum-interface.md)|提供可跨越電腦上執行之處理常式集合的方法。|  
  
## <a name="remarks"></a>備註  

 典型的發佈案例牽涉到開發人員，想要在應用程式域內的電腦上執行 managed 程式碼的偵錯工具。 裝載環境可能在進程中執行一個以上的應用程式域。 開發人員想要使用圖形化使用者介面，或使用其他方法來列出電腦上執行的所有處理常式，然後挑選特定的進程。 此清單應包含執行 managed 程式碼之進程內的所有應用程式域。 然後，開發人員可以識別特定的應用程式域，並將偵錯工具附加至該網域。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorPub .idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯](index.md)
