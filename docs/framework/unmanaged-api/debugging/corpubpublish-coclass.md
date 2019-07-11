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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7d1ca8ea9d00de8a07c67977cf108c50268802e6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739351"
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
|[ICorPublish 介面](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)|提供方法來發行這些處理序中的程序和應用程式定義域的相關資訊。|  
|[ICorPublishAppDomain 介面](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)|表示，並提供有關應用程式定義域的處理序中的資訊。|  
|[ICorPublishAppDomainEnum 介面](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)|提供方法來周遊目前存在於處理程序的應用程式定義域的集合。|  
|[ICorPublishProcess 介面](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)|表示執行的電腦的處理序。|  
|[ICorPublishProcessEnum 介面](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)|提供方法來周遊的電腦執行的處理序的集合。|  
  
## <a name="remarks"></a>備註  
 典型的發佈案例牽涉到的開發人員想要偵錯應用程式定義域中的電腦執行的 managed 程式碼。 裝載的環境可能正在執行的處理序中的多個應用程式定義域。 開發人員想要使用圖形化使用者介面或其他一些方法來列出所有的電腦執行的處理程序，並挑選特定的處理程序。 清單中應該包含的所有應用程式定義域內執行 managed 程式碼的處理序。 開發人員接著識別特定的應用程式定義域，並將偵錯工具附加至該定義域。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorPub.idl  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
