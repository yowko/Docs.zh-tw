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
ms.openlocfilehash: 886ba693183a6b99eb03635e95a9661d105de40e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610856"
---
# <a name="isymunmanagedscope2-interface"></a>ISymUnmanagedScope2 介面
表示方法內的詞法範圍。 這個介面會使用可取得範圍內所定義常數相關資訊的方法來擴充[ISymUnmanagedScope](isymunmanagedscope-interface.md)介面。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetConstantCount 方法](isymunmanagedscope2-getconstantcount-method.md)|取得在此範圍內定義的常數計數。|  
|[GetConstants 方法](isymunmanagedscope2-getconstants-method.md)|取得在此範圍內定義的本機常數。|  
  
## <a name="requirements"></a>需求  
 **標頭：** CorSym .idl，CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [診斷符號存放區介面](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedScope 介面](isymunmanagedscope-interface.md)
