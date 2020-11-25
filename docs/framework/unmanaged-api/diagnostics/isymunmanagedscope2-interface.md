---
title: ISymUnmanagedScope2 介面
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2
helpviewer_keywords:
- ISymUnmanagedScope2 interface [.NET Framework debugging]
ms.assetid: 2ed6a387-ba45-483e-9a1e-b0c69f67998b
topic_type:
- apiref
ms.openlocfilehash: 40c437e109eaa4352a83c5566185593cbc6b0eba
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725829"
---
# <a name="isymunmanagedscope2-interface"></a>ISymUnmanagedScope2 介面

表示方法內的語彙範圍。 這個介面會使用方法來擴充 [ISymUnmanagedScope](isymunmanagedscope-interface.md) 介面，以取得範圍內所定義之常數的相關資訊。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetConstantCount 方法](isymunmanagedscope2-getconstantcount-method.md)|取得在此範圍內定義之常數的計數。|  
|[GetConstants 方法](isymunmanagedscope2-getconstants-method.md)|取得在此範圍內定義的本機常數。|  
  
## <a name="requirements"></a>需求  

 **標頭：** CorSym .idl、CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [診斷符號存放區介面](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedScope 介面](isymunmanagedscope-interface.md)
