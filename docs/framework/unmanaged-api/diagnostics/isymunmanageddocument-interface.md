---
title: ISymUnmanagedDocument 介面
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument
helpviewer_keywords:
- ISymUnmanagedDocument interface [.NET Framework debugging]
ms.assetid: 5c26b366-6e81-467c-9dd0-02dd26fee0a3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 33213aced635549dd439cf679d89367a71baa7c7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59168801"
---
# <a name="isymunmanageddocument-interface"></a>ISymUnmanagedDocument 介面
代表符號存放區所參考的文件。 文件是由統一資源定位器 (URL) 和 GUID 的文件類型定義。 您可以找出文件，不論它使用 URL 的儲存方式和文件類型的 GUID。 您可以在符號存放區中儲存的文件來源，並透過這個介面擷取它。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[FindClosestLine 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-findclosestline-method.md)|在此可能會或可能不是序列點的文件中會傳回是序列點，最接近的一行。|  
|[GetCheckSum 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksum-method.md)|取得總和檢查碼。|  
|[GetCheckSumAlgorithmId 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksumalgorithmid-method.md)|取得總和檢查碼演算法識別項，或如果沒有任何總和檢查碼會傳回全部為零的 GUID。|  
|[GetDocumentType 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getdocumenttype-method.md)|取得此文件的文件類型。|  
|[GetLanguage 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguage-method.md)|取得這份文件的語言識別碼。|  
|[GetLanguageVendor 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguagevendor-method.md)|取得這份文件的語言廠商。|  
|[GetSourceLength 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcelength-method.md)|取得內嵌來源的長度 (以位元組為單位)。|  
|[GetSourceRange 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcerange-method.md)|傳回指定的範圍的內嵌來源到指定的緩衝區。|  
|[GetURL 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-geturl-method.md)|傳回這份文件的 URL。|  
|[HasEmbeddedSource 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-hasembeddedsource-method.md)|會傳回`true`文件具有來源內嵌在偵錯的符號; 否則會傳回`false`。|  
  
## <a name="see-also"></a>另請參閱

- [診斷符號存放區介面](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
