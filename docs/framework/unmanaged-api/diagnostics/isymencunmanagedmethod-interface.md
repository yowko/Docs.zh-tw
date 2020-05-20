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
ms.openlocfilehash: 54c8c7f5c3ba6b4afd4ff352a8afb947a92e2d61
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441873"
---
# <a name="isymencunmanagedmethod-interface"></a>ISymENCUnmanagedMethod 介面
提供 [編輯後繼續] 功能的資訊。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetDocumentsForMethod 方法](isymencunmanagedmethod-getdocumentsformethod-method.md)|取得此方法在中具有行的檔。|  
|[GetDocumentsForMethodCount 方法](isymencunmanagedmethod-getdocumentsformethodcount-method.md)|取得此方法在中具有行的檔數目。|  
|[GetFileNameFromOffset 方法](isymencunmanagedmethod-getfilenamefromoffset-method.md)|取得與位移相關聯之行的檔案名。|  
|[GetLineFromOffset 方法](isymencunmanagedmethod-getlinefromoffset-method.md)|取得與位移相關聯的線條資訊。|  
|[GetSourceExtentInDocument 方法](isymencunmanagedmethod-getsourceextentindocument-method.md)|取得特定檔中方法的最小起始行和最大結尾行。|  
  
## <a name="requirements"></a>需求  
 **標頭：** CorSym .idl，CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [診斷符號存放區介面](diagnostics-symbol-store-interfaces.md)
