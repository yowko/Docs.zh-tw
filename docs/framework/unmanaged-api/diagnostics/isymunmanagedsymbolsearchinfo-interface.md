---
title: ISymUnmanagedSymbolSearchInfo 介面
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo
helpviewer_keywords:
- ISymUnmanagedSymbolSearchInfo interface [.NET Framework debugging]
ms.assetid: 30817373-0a21-49c1-a0c4-8e8daeecb8db
topic_type:
- apiref
ms.openlocfilehash: 95ad3cbea4269173f22e662d15772ff97f7ee900
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705445"
---
# <a name="isymunmanagedsymbolsearchinfo-interface"></a>ISymUnmanagedSymbolSearchInfo 介面

提供可取得搜尋路徑相關資訊的方法。 `QueryInterface`在實[ISymUnmanagedReader](isymunmanagedreader-interface.md)介面的物件上呼叫，以取得這個介面。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetHRESULT 方法](isymunmanagedsymbolsearchinfo-gethresult-method.md)|取得 HRESULT。|  
|[GetSearchPath 方法](isymunmanagedsymbolsearchinfo-getsearchpath-method.md)|取得搜尋路徑。|  
|[GetSearchPathLength 方法](isymunmanagedsymbolsearchinfo-getsearchpathlength-method.md)|取得搜尋路徑長度。|  
  
## <a name="requirements"></a>需求  

 **標頭：** CorSym .idl、CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [診斷符號存放區介面](diagnostics-symbol-store-interfaces.md)
