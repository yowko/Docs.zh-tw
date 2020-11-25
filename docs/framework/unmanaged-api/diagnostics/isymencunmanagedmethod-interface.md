---
title: ISymENCUnmanagedMethod 介面
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod
helpviewer_keywords:
- ISymENCUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: faebf594-67d5-4abf-b9c1-547fd3a1ff87
topic_type:
- apiref
ms.openlocfilehash: acb8d48ed6314756e2c1a10fff314a303799fb24
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707278"
---
# <a name="isymencunmanagedmethod-interface"></a>ISymENCUnmanagedMethod 介面

提供 [編輯後繼續] 功能的資訊。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetDocumentsForMethod 方法](isymencunmanagedmethod-getdocumentsformethod-method.md)|取得此方法具有行的檔。|  
|[GetDocumentsForMethodCount 方法](isymencunmanagedmethod-getdocumentsformethodcount-method.md)|取得此方法具有行的檔數目。|  
|[GetFileNameFromOffset 方法](isymencunmanagedmethod-getfilenamefromoffset-method.md)|取得與位移相關聯之線條的檔案名。|  
|[GetLineFromOffset 方法](isymencunmanagedmethod-getlinefromoffset-method.md)|取得與位移相關聯的行資訊。|  
|[GetSourceExtentInDocument 方法](isymencunmanagedmethod-getsourceextentindocument-method.md)|取得特定檔中方法的最小開始行和最大結束行。|  
  
## <a name="requirements"></a>需求  

 **標頭：** CorSym .idl、CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [診斷符號存放區介面](diagnostics-symbol-store-interfaces.md)
