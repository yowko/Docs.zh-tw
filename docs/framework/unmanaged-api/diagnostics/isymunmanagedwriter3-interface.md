---
title: ISymUnmanagedWriter3 介面
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3
helpviewer_keywords:
- ISymUnmanagedWriter3 interface [.NET Framework debugging]
ms.assetid: a034c21e-e371-4360-b470-29e88288948f
topic_type:
- apiref
ms.openlocfilehash: dfc2e39a6a39e7386bd7358d422d5c6978ec42ec
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683286"
---
# <a name="isymunmanagedwriter3-interface"></a>ISymUnmanagedWriter3 介面

表示符號寫入器，並提供定義文件、序列點、語彙範圍和變數的方法。 這個介面會擴充 [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) 介面。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Commit 方法](isymunmanagedwriter3-commit-method.md)|認可到目前為止寫入資料流程的變更。|  
|[OpenMethod2 方法](isymunmanagedwriter3-openmethod2-method.md)|開啟方法，並在影像中提供其實際區段位移。|  
  
## <a name="requirements"></a>需求  

 **標頭：** CorSym .idl、CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [診斷符號存放區介面](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter 介面](isymunmanagedwriter-interface.md)
- [ISymUnmanagedWriter2 介面](isymunmanagedwriter2-interface.md)
