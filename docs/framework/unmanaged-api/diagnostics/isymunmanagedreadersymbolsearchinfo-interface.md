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
ms.openlocfilehash: 3f6cea68a4379f8769ccbdbc6911cc5c425d3369
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614873"
---
# <a name="isymunmanagedreadersymbolsearchinfo-interface"></a>ISymUnmanagedReaderSymbolSearchInfo 介面
提供取得符號搜尋資訊的方法。 `QueryInterface`在執行[ISymUnmanagedReader](isymunmanagedreader-interface.md)介面的物件上呼叫，以取得此介面。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetSymbolSearchInfo 方法](isymunmanagedreadersymbolsearchinfo-getsymbolsearchinfo-method.md)|取得符號搜尋資訊。|  
|[GetSymbolSearchInfoCount 方法](isymunmanagedreadersymbolsearchinfo-getsymbolsearchinfocount-method.md)|取得符號搜尋資訊的計數。|  
  
## <a name="requirements"></a>需求  
 **標頭：** CorSym .idl，CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [診斷符號存放區介面](diagnostics-symbol-store-interfaces.md)
