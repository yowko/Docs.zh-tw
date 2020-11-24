---
title: ISymUnmanagedReaderSymbolSearchInfo 介面
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReaderSymbolSearchInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReaderSymbolSearchInfo
helpviewer_keywords:
- ISymUnmanagedReaderSymbolSearchInfo interface [.NET Framework debugging]
ms.assetid: fde7e21d-1169-4bed-a34d-792e69652bf9
topic_type:
- apiref
ms.openlocfilehash: af4124aed823a0a2475a181efe3fa68e1fae0bfe
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678385"
---
# <a name="isymunmanagedreadersymbolsearchinfo-interface"></a>ISymUnmanagedReaderSymbolSearchInfo 介面

提供可取得符號搜尋資訊的方法。 `QueryInterface`在實[ISymUnmanagedReader](isymunmanagedreader-interface.md)介面的物件上呼叫，以取得這個介面。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetSymbolSearchInfo 方法](isymunmanagedreadersymbolsearchinfo-getsymbolsearchinfo-method.md)|取得符號搜尋資訊。|  
|[GetSymbolSearchInfoCount 方法](isymunmanagedreadersymbolsearchinfo-getsymbolsearchinfocount-method.md)|取得符號搜尋資訊的計數。|  
  
## <a name="requirements"></a>需求  

 **標頭：** CorSym .idl、CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [診斷符號存放區介面](diagnostics-symbol-store-interfaces.md)
